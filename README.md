AngularJSDemos
==============
Data binding

<html ng-app>
<head>
    <title>Data-Binding Basics</title>
</head>
<body>
<div>
<input type="text" ng-model="textValue"/> {{textValue}}
 <br/>
</div>
<script src="angular.min.js"></script>
</body>
</html>

Looping

<html ng-app>
<head>
    <title>Looping Using nf-repeat</title>
</head>
<body ng-init="names=['Zeus','Apollo','Poseison','Kronos']">
<div>
<input type="text" ng-model="name"/> {{name}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names">{{personNames}}</li>
</ul>
<script src="angular.min.js"></script>
</body>
</html>

Filters

<html ng-app>
<head>
    <title>Using Controllers</title>
</head>
<body ng-init="names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}]">
<div>
<input type="text" ng-model="inputName"/> {{inputName | currency}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
<script src="angular.min.js"></script>
</body>
</html>


Controller

<html ng-app>
<head>
    <title>Looping Using nf-repeat</title>
</head>
<body ng-controller="SimpleController">
<div>
Name: <input type="text" ng-model="inputName"/> {{inputName}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
<script src="angular.min.js"></script>
<script type="text/javascript">
    function SimpleController($scope){
        $scope.names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}];
    }
</script>
</body>
</html>


Module

<html ng-app="demoApp">
<head>
    <title>Looping Using nf-repeat</title>
</head>
<body ng-controller="SimpleController">
<div>
Name: <input type="text" ng-model="inputName"/> {{inputName}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
<script src="angular.min.js"></script>
<script type="text/javascript">
var demoApp=angular.module('demoApp',[]);
demoApp.controller('SimpleController',function($scope){
$scope.names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}];
});

</script>
</body>
</html>

Module Cont


<html ng-app="demoApp">
<head>
    <title>Controllers</title>
</head>
<body ng-controller="SimpleController">
<div>
Name: <input type="text" ng-model="inputName"/> {{inputName}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
<script src="angular.min.js"></script>
<script type="text/javascript">
var demoApp=angular.module('demoApp',[]);
function SimpleController($scope){
        $scope.names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}];
    }
demoApp.controller('SimpleController',SimpleController);
</script>
</body>
</html>


Module Controller


<html ng-app="demoApp">
<head>
    <title>Controllers</title>
</head>
<body ng-controller="SimpleController">
<div>
Name: <input type="text" ng-model="inputName"/> {{inputName}}
 <br/>
</div>
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
<script src="angular.min.js"></script>
<script type="text/javascript">
var demoApp=angular.module('demoApp',[]);
var controllers={};
controllers.SimpleController=function($scope){
$scope.names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}];
};
demoApp.controller(controllers);


</script>
</body>
</html>






Routes

<html ng-app="demoApp">
<head>
    <title>Controllers</title>
</head>
<body>
<div ng-view="">
</div>
<script src="angular.min.js"></script>
<script type="text/javascript">
var demoApp=angular.module('demoApp',[]);
var controllers={};
controllers.SimpleController=function($scope){
$scope.names=[{name:'Zeus',city:'Olympus'},{name:'Apollo',city:'Rhodes'},{name:'Poseidon',city:'Atlantis'},{name:'Kronos',city:'Tartarus'}];
$scope.addNewPerson=function($scope){
$scope.names.push({name:$scope.newPerson.name,city:$scope.newPerson.city});
};
};
demoApp.controller(controllers);

demoApp.config(function($routeProvider){
$routeProvider.when('/view1',
                {
                    controller: 'SimpleController',
                    templateUrl:'FilterByName.html'
                })
            .when('/view2',
                {
                    controller: 'SimpleController',
                    templateUrl:'FilterByCity.html'
                })
            .otherwise({ redirectTo: '/view1' });

});


</script>
</body>
</html>


FC

<div>
<h2>View-FilterByName</h2>
Name:<input type="text" ng-model="filter.name"/> {{filter.name}}
<ul>
<li ng-repeat="personNames in names | filter:filter.name |orderBy:'name'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul>
</br>
PersonName:<input type="text" ng-model="newPerson.name"/>
</div>
</br>
City:<input type="text" ng-model="newPerson.city"/>
</br>
<button ng-click="addNewPerson()">Add Person</button>
<a href="#/FilterByCity">FilterByCity</a>
</div>


FN


<div>
<h2>View-FilterByCity </h2>
Name:<input type="text" ng-model="inputName"/> {{inputName}}
<ul>
<li ng-repeat="personNames in names | filter:inputName |orderBy:'city'">{{personNames.name}} - {{personNames.city | uppercase}}</li>
</ul></div>




class
<html ng-app>
<head>
    <title>Data-Binding Basics</title>
</head>
<body>
<style>
.strike {
  text-decoration: line-through;
}
.bold {
    font-weight: bold;
}
.red {
    color: red;
}
</style>
<div>
<p ng-class="{strike: deleted, bold: important, red: error}">Map Syntax Example</p>
<input type="checkbox" ng-model="deleted"> deleted (apply "strike" class)<br>
<input type="checkbox" ng-model="important"> important (apply "bold" class)<br>
<input type="checkbox" ng-model="error"> error (apply "red" class)
<hr>
</div>
<script src="angular.min.js"></script>

</body>
</html>


hide show


<html ng-app>
<head>
    <title>Data-Binding Basics</title>
</head>
<body>

Click me: <input type="checkbox" ng-model="checked"><br/>
<div>
 <div ng-show="checked">
  I show up when your checkbox is checked.
  </div>
</div>
<div>
<div ng-hide="checked">
    I hide when your checkbox is checked.
  </div>
</div>
<script src="angular.min.js"></script>

</body>
</html>



if


<html ng-app>
<head>
    <title>Data-Binding Basics</title>
</head>
<body>

Click me: <input type="checkbox" ng-model="checked"><br/>
<div>
 <div ng-if="checked">
  I show up when your checkbox is checked.
  </div>
</div>
<div>

<script src="angular.min.js"></script>

</body>
</html>



switch


<html ng-app>
<head>
    <title>Using Simple Controller</title>
</head>
<body ng-controller="SimpleController">
<div>
 <select ng-model="selection" ng-options="item for item in items">
  </select>
 <br/>
</div>
 <br/>
<div ng-switch on="selection">
      <div class="animate-switch" ng-switch-when="settings">Settings Div</div>

      <div class="animate-switch" ng-switch-when="home">Home Span</div>
      <div class="animate-switch" ng-switch-default>default</div>
  </div>
<script src="angular.min.js"></script>
<script type="text/javascript">
    function SimpleController($scope){
       $scope.items = ['settings', 'home', 'other'];
  $scope.selection = $scope.items[0];
    }
</script>
</body>
</html>




