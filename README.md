# Fifty Ninety Dependencies
This repo is used to deploy the dependent packages separate from the code that depends on these packages.  The reason is that when depolying the code, the dependent packages can be included in the source pushes to the scratch org multiple times cause increased deploy times.  Clone this repo and follow the remainder of this document to install them and setup the org.

## Installing the Dependencies
This section will go through the steps needed to deploy and configure the dependencies.  This document uses the Salesforce CLI, but most of the steps could be done within VS Code using the Salesforce CLI.  See the Salesforce documentation on setting up and using VS Code. [Package Development Model with VS Code](https://forcedotcom.github.io/salesforcedx-vscode/articles/user-guide/package-development-model). For details about the model, see the [Package Development Model](https://trailhead.salesforce.com/en/content/learn/modules/sfdx_dev_model) Trailhead module.

### Crete the Scratch Org
using the salesforce cli, execute the following command:
```console
sfdx force:org:create --loglevel debug --json -s -d 30 -a my-fn-org -f [your/path/to/config/file]
```

### Deploy the Packages
using the salesforce cli, execute the following command:
```console
sfdx force:source:push -u my-fn-org
```

### Assign Permission Sets to the user
using the salesforce cli, execute the following commands:
```console
sfdx force:user:permset:assign -n Agile_Accelerator_Admin -u my-fn-org

sfdx force:user:permset:assign -n Agile_Accelerator_User -u my-fn-org
```