---
title: "dotnet20 problem"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Dev'olution on 2009-07-21
shouldve expected this as its frigging *doze crap but anyways...

trying to install dotnet20 thru winetricks, it froze at 'initializing install'.

UPDATE: Now it's not even getting to that stage :( It's doing the prep for that... and comes up with 

```
kristian@kristian-desktop:~$ sh winetricks dotnet20
Setting Windows version to win2k
Executing wine regedit /home/kristian/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/kristian/.winetrickscache/dotnet20/l_intl.nls /home/kristian/.wine/drive_c/windows/system32/
Executing wine /home/kristian/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP007.TMP\\" 00000000
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -480, std (d/m/y): 29/03/2009, dlt (d/m/y): 31/12/2009
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -480, std (d/m/y): 29/03/2009, dlt (d/m/y): 31/12/2009
fixme:advapi:LsaOpenPolicy ((null),0x33f3c0,0x00000001,0x33f3e8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"kristian" (nil) 0x8de454 (nil) 0x8de458 0x8de44c - stub
fixme:advapi:LookupAccountNameW (null) L"kristian" 0x154668 0x8de454 0x15acd0 0x8de458 0x8de44c - stub
fixme:advapi:LookupAccountNameW (null) L"kristian" (nil) 0x8de424 (nil) 0x8de428 0x8de41c - stub
fixme:advapi:LookupAccountNameW (null) L"kristian" 0xcf2ca8 0x8de424 0xcf9310 0x8de428 0x8de41c - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 4 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 4 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 7 ignored L"DuplicateFile" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 16 ignored L"CreateFolder" table values
fixme:msi:msi_unimplemented_action_stub BindImage -> 8 ignored L"BindImage" table values
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:rpc:RpcAssoc_BindConnection receive failed with error 1726
Note: command 'wine /home/kristian/.winetrickscache/dotnet20/dotnetfx.exe' returned status 67.  Abortin
```

---

### Post by keplerspeed on 2009-07-24
Ensure you have the latest winetrick script from here: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

