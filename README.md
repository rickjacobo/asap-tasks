# AsapTaskModule
A PowerShell Module to manage tasks using a Microsoft SQL backend.

## Requirements
* Container Platform (ie., Docker, Kubernetes, Rancher Desktop, etc...)
* Microsoft SQL Database
* PowerShell
  * sqlserver module
  ````
  Install-Module -Name sqlserver
  Import-Module -Name sqlserver
  ````
* Git

## Setup Environment
* Download bits
````
git clone https://github.com/rickjacobo/asap-tasks
````
* If you don't already have a Microsoft SQL encvironment run Start-SQLContainer.ps1 setup wizard (MUST BE RUN FROM MODULE DIRECTORY)
````
./Start-SQLContainer.ps1
````
or
````
docker run -d --name="<name of container>" -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<secure password>" -e "MSSQL_PID=Express" -p $Port mcr.microsoft.com/mssql/server:2019-latest
````

* Import AsapTasks Module (MUST BE RUN FROM MODULE DIRECTORY)
````
Import-Module asap-tasks.psm1
````

* Setup Database  (MUST BE RUN FROM MODULE DIRECTORY)
````
Add-AsapTasksDatabase
````

* Add Task (MUST BE RUN FROM MODULE DIRECTORY)
````
Add-AsapTask -Task <task> -Description <description> -Notes <notes> -Status <status>
````

* Get tasks (MUST BE RUN FROM MODULE DIRECTORY)
````
Get-AsapTask
````

* Update Task (MUST BE RUN FROM MODULE DIRECTORY)
  * Get Id with Get-AsapTask
````
Set-AsapTask -Id <obtain from Get-AsapTask> -Task <task> -Description <description> -Notes <notes> -Status <status>
````

* Remove Task (MUST BE RUN FROM MODULE DIRECTORY)
  * Get Id with Get-AsapTask
```
Remove-AsapTask -Id <obtain from Get-AsapTask>
````

