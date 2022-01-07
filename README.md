[comment]: # "Auto-generated SOAR connector documentation"
# Symantec Management Center

Publisher: Splunk Community  
Connector Version: 1\.0\.5  
Product Vendor: Symantec  
Product Name: Symantec Management Center  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.8\.24304  

This app connects to Symantec Management Center to perform actions against BlueCoat SG Proxies

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Symantec Management Center asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | Hostname or IP
**api\_token** |  optional  | password | API Token
**username** |  optional  | string | Username
**password** |  optional  | password | Password
**verify\_server\_cert** |  optional  | boolean | Verify server certificate

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using the supplied configuration  
[get version](#action-get-version) - Get Symantec Management Center version  
[list policies](#action-list-policies) - List Symantec Management Center policies  
[get policy](#action-get-policy) - Get Symantec Management Center policy  
[add listitem](#action-add-listitem) - Add url/category to local database file URL list shared object  
[remove listitem](#action-remove-listitem) - Remove url/category from local database file or URL list shared object  

## action: 'test connectivity'
Validate the asset configuration for connectivity using the supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'get version'
Get Symantec Management Center version

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.data\.\*\.buildNumber | string | 
action\_result\.data\.\*\.id | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.version | string | 
action\_result\.status | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list policies'
List Symantec Management Center policies

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**content\_type** |  optional  | Content\-type of the policies | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.content\_type | string | 
action\_result\.data\.\*\.policies\.\*\.author | string | 
action\_result\.data\.\*\.policies\.\*\.contentType | string | 
action\_result\.data\.\*\.policies\.\*\.name | string | 
action\_result\.data\.\*\.policies\.\*\.referenceId | string | 
action\_result\.data\.\*\.policies\.\*\.replaceVariables | boolean | 
action\_result\.data\.\*\.policies\.\*\.shared | boolean | 
action\_result\.data\.\*\.policies\.\*\.tenant | string | 
action\_result\.data\.\*\.policies\.\*\.uuid | string |  `symantecmc policy uuid` 
action\_result\.status | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get policy'
Get Symantec Management Center policy

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**uuid** |  optional  | UUID | string |  `symantecmc policy uuid` 
**name** |  optional  | Policy name | string | 
**reference\_id** |  optional  | Policy reference ID | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.reference\_id | string | 
action\_result\.parameter\.uuid | string |  `symantecmc policy uuid` 
action\_result\.data\.\*\.policies\.\*\.author | string | 
action\_result\.data\.\*\.policies\.\*\.contentType | string | 
action\_result\.data\.\*\.policies\.\*\.name | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.author | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.content\.categories\.\*\.entries\.\*\.comment | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.content\.categories\.\*\.entries\.\*\.type | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.content\.categories\.\*\.entries\.\*\.url | string |  `url`  `url list` 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.content\.categories\.\*\.name | string |  `symantecmc category name` 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.content\.categories\.\*\.type | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.revisionDate | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.revisionDescription | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.revisionInfo\.revisionNumber | string | 
action\_result\.data\.\*\.policies\.\*\.policy\_details\.schemaVersion | string | 
action\_result\.data\.\*\.policies\.\*\.referenceId | string | 
action\_result\.data\.\*\.policies\.\*\.replaceVariables | boolean | 
action\_result\.data\.\*\.policies\.\*\.shared | boolean | 
action\_result\.data\.\*\.policies\.\*\.tenant | string | 
action\_result\.data\.\*\.policies\.\*\.uuid | string |  `symantecmc policy uuid` 
action\_result\.status | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'add listitem'
Add url/category to local database file URL list shared object

Type: **generic**  
Read only: **False**

Category is not relevant when adding URL to URL list shared object\. IP and URL cannot be provided in the same action call\. IP is only usable with IP list shared objects\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  optional  | URL to add to local database file or URL list shared object | string |  `url`  `url list` 
**ip** |  optional  | IP to remove from local database file or IP list shared object | string |  `ip` 
**uuid** |  required  | Policy UUID | string |  `symantecmc policy uuid` 
**comment** |  optional  | Comment | string | 
**category** |  optional  | URL category to add | string |  `symantecmc category name` 
**add\_category** |  optional  | Add category | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.add\_category | boolean | 
action\_result\.parameter\.category | string |  `symantecmc category name` 
action\_result\.parameter\.comment | string | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.parameter\.url | string |  `url`  `url list` 
action\_result\.parameter\.uuid | string |  `symantecmc policy uuid` 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.summary\.action\_name | string | 
action\_result\.summary\.app\_run\_id | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'remove listitem'
Remove url/category from local database file or URL list shared object

Type: **generic**  
Read only: **False**

Category is not relevant when removing URL from URL list shared object\. IP and URL cannot be provided in the same action call\. IP is only usable with IP list shared objects\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  optional  | URL to remove from local database file or URL list shared object | string |  `url`  `url list` 
**ip** |  optional  | IP to remove from local database file or IP list shared object | string |  `ip` 
**uuid** |  required  | Policy UUID | string |  `symantecmc policy uuid` 
**category** |  optional  | URL category to remove | string |  `symantecmc category name` 
**delete\_all** |  optional  | Delete all occurrences of URL | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.category | string |  `symantecmc category name` 
action\_result\.parameter\.delete\_all | boolean | 
action\_result\.parameter\.ip | string |  `ip` 
action\_result\.parameter\.url | string |  `url`  `url list` 
action\_result\.parameter\.uuid | string |  `symantecmc policy uuid` 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 