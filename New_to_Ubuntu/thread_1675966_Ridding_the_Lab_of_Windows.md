---
title: "Ridding the Lab of Windows"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by dwdarkstar on 2011-01-26
[FONT=Arial][SIZE=2]Hello, i have been trying to install some software to control a programmable lab grade bench-top power supply on my computer via wine but i'm having trouble.  This power supply constitutes the last "reason for windows" in our research lab.  The software requires **microsoft .net framework 2.0** which i tried to install via [[COLOR=Blue]this thread[/COLOR]]("http://www.uluga.ubuntuforums.org/showthread.php?t=943298"), however there seemed to be issues with the **fakeie6** command as detailed below.  I have Wine 1.0.1 running on Ubuntu 9.10 and the output following the **fakeie6** command in the aforementioned guide is provided below.[/SIZE][/FONT]

```
Install of dotnet20 done
winetricks done.

farstar@go-bot-lab:~$ sh winetricks fakeie6

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000135
Unknown arg fakeie6
Usage: winetricks [options] package [package] ...
This script can help you prepare your system for Windows applications
that mistakenly assume all users' systems have all the needed
redistributable runtime libraries or fonts.
Some options require the Linux 'cabextract' program.

Options:
 -q         quiet.  You must have already agreed to the EULAs.
 -v         verbose
 -V         display Version
Packages:
 7zip          7-zip file archiver
 adobeair      Adobe AIR runtime
 amstream      MS amstream.dll
 art2kmin      MS Access 2007 runtime

```[SIZE=2]pressing on with the P/S software instillation despite the **fakeie6** trouble yields the following after installing the USB driver:[/SIZE]

```
farstar@go-bot-lab:~/Desktop$ wine USB_CP2102_XP_2000.exe 
fixme:advapi:LookupAccountNameW (null) L"farstar" (nil) 0x33f864 (nil) 0x33f868 0x33f85c - stub
fixme:advapi:LookupAccountNameW (null) L"farstar" 0x134e78 0x33f864 0x130db8 0x33f868 0x33f85c - stub
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:advapi:CheckTokenMembership ((nil) 0x1901e8 0x7ed194e0) stub!
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:crypt:CertAddEncodedCTLToStore (0x19f430, 00000001, 0x19f530, 9225, 00000004, 0x7ed19290): stub
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```[SIZE=3][SIZE=2]installing the actual software program yields:[/SIZE]
[/SIZE]
```
farstar@go-bot-lab:~/Desktop$ wine DPS_Setup.exe 
fixme:shell:IPersistFile_fnGetCurFile (0x169e88)
fixme:shell:IPersistFile_fnGetCurFile (0x16a710)
fixme:shell:IPersistFile_fnGetCurFile (0x16a710)
fixme:shell:IPersistFile_fnGetCurFile (0x16ad28)
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub

```[SIZE=2]finally, attempting to run the power supply control program from terminal results in:[/SIZE]

```
farstar@go-bot-lab:~/.wine/drive_c/Program Files/DPS/DPS 32V5A Software$ wine CAPDPScontrol.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorwks.dll") not found

```[SIZE=2]Along with this error box: **C:\windows\Microsoft.NET\Framework\v2.0.50727\mscorwks.dll could not be loaded**

[/SIZE]  [SIZE=2]any ideas...?  thanxs![/SIZE]

---

### Post by HermanAB on 2011-01-26
Howdy,

I would try Virtualbox or VMWare with Windows on a Linux Host.

---

### Post by beew on 2011-01-26
You don't really get rid of Windows with VM, if you want to be legit you still need to pay for your copy of Windows for one thing so M$ is still selling you a Windows license :)

---

### Post by Mark Phelps on 2011-01-26
The link below is to the WineHQ page for .Net framework, version 2.0:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754")

Maybe there's some info in the Testing Results that you can use...

---

### Post by anglican on 2011-01-27
> **dwdarkstar said:**
> [SIZE=2]  The software requires **microsoft .net framework 2.0** [/SIZE]Have you tried it using mono?

H

---

