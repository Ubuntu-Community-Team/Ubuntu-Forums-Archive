---
title: "cant install dotnet20"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by cybuss on 2011-01-06
basil@basil-desktop:~$ winetricks dotnet20
------------------------------------------------------
Instaling .net 2.0 runtime.  Can take several minutes.  See [http://wiki.winehq.org/MicrosoftDotNet](http://wiki.winehq.org/MicrosoftDotNet) for tips.
------------------------------------------------------
prerequisite gecko already installed, skipping
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing cp -f /home/basil/.winetrickscache/dotnet20/l_intl.nls /home/basil/.wine/dosdevices/c:/windows/system32
DELETE - HKLM\Software\Microsoft\.NETFramework\policy\v2.0 (null) 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\.NETFramework InstallRoot 0 0 1
Error: The system was unable to find the specified registry key or value
Executing wine /home/basil/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\users\\shane\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"basil" (nil) 0x7cde2c (nil) 0x7cde30 0x7cde24 - stub
fixme:advapi:LookupAccountNameW (null) L"basil" 0x159978 0x7cde2c 0x158dd8 0x7cde30 0x7cde24 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
err:rpc:I_RpcGetBuffer no binding
err:msi:ITERATE_Actions Execution halted, action L"MsiPublishAssemblies" returned 1627
fixme:imm:ImmDisableIME (-1): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize
------------------------------------------------------
Note: command 'wine /home/basil/.winetrickscache/dotnet20/dotnetfx.exe' returned status 91.  Aborting.
------------------------------------------------------
basil@basil-desktop:~$ 

can anyone make sense of this?

---

