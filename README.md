[comment]: # "Auto-generated SOAR connector documentation"
# Fuse Box

Publisher: Mhike  
Connector Version: 1\.0\.1  
Product Vendor: Mhike  
Product Name: Fuse Box  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.0  

Fuse Box is an app to help deconflict incoming events within playbooks

# Splunk> Phantom

Welcome to the open-source repository for Splunk> Phantom's fuseboxutility App.

Please have a look at our [Contributing Guide](https://github.com/Splunk-SOAR-Apps/.github/blob/main/.github/CONTRIBUTING.md) if you are interested in contributing, raising issues, or learning more about open-source Phantom apps.

## Legal and License

This Phantom App is licensed under the Apache 2.0 license. Please see our [Contributing Guide](https://github.com/Splunk-SOAR-Apps/.github/blob/main/.github/CONTRIBUTING.md#legal-notice) for further details.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Fuse Box asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**dedicated\_custom\_list** |  optional  | string | Specify the name of the custom list that will be used as the data record for Fuse Box
**retention\_limit** |  optional  | numeric | The number of days to retain records in the list\. If Fuse Box runs slower than expected, lower retention
**https\_port** |  optional  | string | Splunk SOAR HTTPS port if your instance uses one other than 443
**debug** |  optional  | boolean | Print debugging statements to log

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[check fuse](#action-check-fuse) - Check to see if this is the first with this unique identifier  
[on poll](#action-on-poll) - Clean up the custom list based on retention day count  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'check fuse'
Check to see if this is the first with this unique identifier

Type: **generic**  
Read only: **False**

Check to see if this is the first with this unique identifier\. If so, it will return false for tripped\_fuse \(and is\_duplicate if you don't like all this fuse shenanigans\)\. Otherwise it will 'trip the fuse' and return True\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**unique\_identifier** |  required  | A value that identifies collisions ie\. an account, a user, or a combination of fields | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.unique\_identifier | string | 
action\_result\.data\.\*\.is\_duplicate | boolean | 
action\_result\.data\.\*\.playbook\_name | string | 
action\_result\.data\.\*\.tripped\_fuse | boolean | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'on poll'
Clean up the custom list based on retention day count

Type: **ingest**  
Read only: **False**

Use the retention limit in the configuration to remove old entries from the Fuse Box custom list\. Failing to schedule this polling action will prevent the list from being cleaned up over time\.

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output