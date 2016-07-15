# Cortana Intelligence Workshop Prereq Deployment

This GitHub repo exists to deploy the assets needed to complete the Cortana Intelligence Workshop. We are leveraging a capability of Azure called ARM templates which allow you to specifiy what your solution looks like from a deployment perspetive simply by using JSON code. This is a fairly simple use of ARM templates, but you can actually deploy very complex topologies using this technology - straight from source control. Pretty cool!!

This particular ARM template will deploy the following resources into a new Resource Group:

* An HDInsight Spark cluster with 2 worker nodes.
* A Windows 2012 R2 VM that will act as a Lab VM where you will run the Data Factory Data Management Gateway. This VM is basically a workstation for you so you do not have to install software on your personal/work device.
* Supporting resources - both the Spark cluster and the Lab VM need a few requisite resources in order to operate such as storage accounts, networks, a public IP, etc.

All you need to do is click the "Deploy to Azure" button below and fill out the following parameters in Azure. NOTE: you will want to be signed in to your Azure subscription before clicking the button below.

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftoddkitta%2FCortanaIntelligenceWorkshopPrereqDeployment%2Fmaster%2Fazuredeploy.json)

When you click the "Deploy to Azure" button, you will be taken to the Azure portal and presented with a form for a new custom deployment (which uses the ARM template in this GitHub repo). You will be presented with a blade to provide some custom parameters as shown in the screenshot below.

![alt text](/images/prereqparms.PNG "Azure Deployment GUI")

* APPNAME - This should be a short (10 or fewer characters), but unique string that will be a prefix to all of the resources deployed. For example, if you type in *smithcis*, your Spark cluster will be called *smithcisspark* and your Lab VM will be called *smithcislab*.
* CLUSTERLOGINUSERNAME - The username that will be created for the Spark cluster.
* CLUSTERLOGINPASSWORD - The associated password with the Spark username. The password must be at least 10 characters in length and must contain at least one digit, one non-alphanumeric character, and one upper or lower case letter.
* LABVMUSERNAME - The username that will be created for the Lab VM.
* LABVMPASSWORD - The associated password with the Lab VM user. The password must be at least 12 characters and must have 3 of the following: 1 lower case character, 1 upper case character, 1 number, and 1 special character.
