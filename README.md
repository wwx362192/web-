# web-
性能调试方法/工具
1、内存泄漏调试步骤：
    1）进入google中，打开调试工具，触发start方法，选中触发start方法的元素
    2）执行Memory-->Profiles-->Take heap snapshot-->Take snapshot，会创建一张快照
    3）在类型是Summary中搜索占用内存的方法名
    3）触发end方法，选中触发end方法的元素
    4）执行Profiles-->Take heap snapshot-->Take snapshot，会创建另外一张快照
    5）在类型是Comparison中搜索占用内存的方法名，查看#Delta的值是否为-1，是则内存回收，否则，内存占用泄露，需要优化
       或者 ： 在类型是Comparison中，查看所有#Delta的值是-1的方法有哪些
       
2、监听dom加载完成的方法
    1）AngularJs中，监听$viewContentLoaded字段，使用$scope.$watch("$viewContentLoaded",function(event){});
       或者使用ng-init方法
    2）Js中，window.onload = function(){}
    3)Jquery中,$(function() {});| $(document).ready(function(){})
