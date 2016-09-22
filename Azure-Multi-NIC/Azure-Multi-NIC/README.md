# Azure Mulit-NIC BIG-IP
Deploy a Multi-NIC BIG-IP in Azure  

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftstanley93%2FAzure-Multi-NIC%2Fmaster%2FAzure-Multi-NIC%2FAzure-Multi-NIC%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

### Description:
This template will deploy a F5 BIG-IP into Azure with 2 network interfaces.  This template could be modified for additional NIC's as needed.

### Parameter Definitions: ###

* location
  * Required
  * Choose the data center you want to install these Web Applicatin Firewall's into from the drop down list.
* numberOFWAFs
  * Required
  * The number of Web Applicatin Firewall's (Up to 4) that will be deployed infront of your application.
* vmSize
  * Required
  * Choose the size of the Virtual Machine Instance from the list.
* adminUsername
  * Required
  * User name to login to the Web Applicatin Firewall.
* adminPassword
  * Required
  * Password to login to the Web Applicatin Firewall.
* dnsNameForPublicIP
  * Required
  * Unique DNS Name for the Public IP used to access the Web Application Firewalls for management.
* licenseToken1
  * Required
  * The License Token for the first BYOL F5 Web Application Firewall.
* licenseToken2
  * Optional
  * The License Token for the first BYOL F5 Web Application Firewall.
  * Use only if you need more than one.
* licenseToken3
  * Optional
  * The License Token for the first BYOL F5 Web Application Firewall.
  * Use only if you need more than one.
* licenseToken4
  * Optional
  * The License Token for the first BYOL F5 Web Application Firewall.
  * Use only if you need more than one.
* applicationName
  * Required
  * Please provide a simple name for your application.
* applicationProtocols
  * Required
  * A semi-colon separated list of protocols (http;https) that will be used to configure the WAF's VIP's, (e.g. http for port 80 and https for SSL).
* applicationAddress
  * Required
  * The public IP address or DNS FQDN of the Application that this WAF is for.
* applicationPorts
  * Required
  * A semi-colon separated list of ports, (80;443) that your applicaiton is listening on, (e.g. 80 and 443).
* applicationType
  * Required
  * Select the operating system that your application is running on. (Linux OS or a Windows OS)
* blockingLevel
  * Required
  * Please select how aggressive you would like the blocking level of this WAF to be.  Remember that the more aggressive the blocking level, the more potential there is for false-positives that the WAF might detect.
* applicationFQDN
  * Required
  * The Fully Qualified Domain Name of your application. (e.g. www.example.com).
* applicationCertificate
  * Optional
  * The path to the SSL certificate file.
* applicationKey
  * Optional
  * The path to the SSL key file.
* applicationChain
  * Optional
  * The path to the SSL chain file.


### What get's deployed:

This template will create a new resource group, and inside this new resource group it will configure the following;

* Storage Container
* Public IP Address
* NIC objects for the F5 BIG-IP VM.
* F5 BIG-IP Virtual Machine

### How to connect to your Web Application Firewalls to manage them:

After the deployment successfuly finishes, you can find the BIG-IP Management UI\SSH URLs by doing the following;  Find the resource group that was deployed, which is the same name as the "dnsNameForPublicIP".  When you click on this object you will see the deployment status.  Click on the deployment status, and then the deployment.  In the "Outputs" section you will find the URL's and ports that you can use to connect to the F5 BIG-IP. 