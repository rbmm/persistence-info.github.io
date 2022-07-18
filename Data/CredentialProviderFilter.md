## Image File Execution Options <!-- general "title" of the persistence. Good to be unique. -->
<!-- separate sections by two empty lines -->
<!-- do not remove empty sections  -->


### Location: <!-- where to find it -->
`HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options`


### Classification: <!-- see "how it works" document. Empty lime must go next. -->

|Criteria|Value|
|:---|:---|
|Permissions|Admin|
|Security context| System |
|Persistence type| Registry |
|Code type|DLL|
|Launch type|Automatic;|
|Impact|Non-Destructive|
|OS Version|vista+|
|Dependencies|OS only|
|Toolset|regsvr32.exe+internal code in DLL|


### Description:<!-- add two EOLs or two spaces at the end of line to create a line break -->
\registry\MACHINE\SOFTWARE\Classes\CLSID\{guid}\InprocServer32  
and  
\registryMACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Authentication\Credential Provider Filters\{guid}  
are created  
dll loaded in LogonUI.exe (system context) or to any app which call CredUIPromptForWindowsCredentials ( usually user context)  
dll inject self to lsass after this  
implement ICredentialProviderFilter is optional  
install (and load) regsvr32 <name>.dll  
uninstall and unload from lsass regsvr32 /u <name>.dll  
log in \systemroot\temp\CDABA566C6BB44b7BFF0BF8D47553C1F  
required admin/elevated run  
example src+x64 binary - https://github.com/rbmm/MISC/tree/master/Credential%20Provider%20Filter

### References: <!-- use <...> or [abc](https://...) syntax. Prepend with "- " when more than one -->
<[Credential Provider Technical Reference]((https://www.microsoft.com/en-us/download/details.aspx?id=53556))>


### Credits: <!-- use [abc](https://...) syntax. Prepend with "- " when more than one. -->


### See also: <!-- if refering to the same repo, use [Name](file.md) syntax. -->
<!-- prepend with "- " if more than one -->


### Remarks: <!-- see the usage in the "classification" section. Use only 1:1 references i.e. not refering to the same footnote from two different places -->

