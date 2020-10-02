# Azure Powershell Login Using Service Principal

```
# Create a new Service Principal with Empty Role Assignment. This principal will be visible under App Registration section on the Azure portal.
 az ad sp create-for-rbac -n "{sp name}" --skip-assignment

# Define clear text string for username and password
[string]$appId = '{sp app id}'
[string]$password = '{service principal password}'
[string]$tenant = '{tenant Id}'

# Convert to SecureString
[securestring]$secureStringpassword = ConvertTo-SecureString $password -AsPlainText -Force

#Generate a PS credential object
[pscredential]$credential = New-Object System.Management.Automation.PSCredential ($appId, $secureStringpassword)

# Connect to Azure Account
Connect-AzureRmAccount -ServicePrincipal -Credential $credential -TenantId $tenant

```
