---
title: "installing on wine."
date: 2010-05-23
forum: New to Ubuntu
---

### Post by aprillia99 on 2010-05-23
ok i go to properties and click the execute box and tell it to open with wine. but when i double click to start the install all i get is the waiting sign then nothing, like i  never clicked it no error or anything am i missing something?

---

### Post by ShadowMage on 2010-05-23
Try running it from the terminal, chances are you'll see the error then.

For example,
```
wine path/to/my.exe
```

---

### Post by aprillia99 on 2010-05-23
this is what i get an sugestions? 

Asus:~$ wine /home/kyle/Desktop/GameRangerSetup.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\kyle\\Desktop\\GameRangerSetup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\kyle\\Desktop\\GameRangerSetup.exe" failed, status c0000135
kyle@kyle-laptop-Asus:~$

---

### Post by 3rdalbum on 2010-05-23
> **aprillia99 said:**
> this is what i get an sugestions? 

Asus:~$ wine /home/kyle/Desktop/GameRangerSetup.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\kyle\\Desktop\\GameRangerSetup.exe") not found

It needs MFC42.DLL. You may be able to find it online, and then put it into Wine's System32 (~/.wine/drive_c/WINDOWS) directory.

---

### Post by aprillia99 on 2010-05-23
ok TY i got the .DLL file i needed can anyone tell me why this program isnt running

THIS IS A DIFFERENT PROGRAM

******************
 wine /home/kyle/Desktop/LeagueOfLegendsDownloader04_27_2010.exe
err:seh:setup_exception_record stack overflow 1868 bytes in thread 0019 eip 7bc3f33e esp 00c80be4 stack 0xc80000-0xc81000-0xe80000
err:seh:setup_exception_record stack overflow 824 bytes in thread 0009 eip 7bc81c06 esp 00a80ff8 stack 0xa80000-0xa81000-0xc80000
kyle@kyle-laptop-Asus:~$ 
***************

Ty

EDIT

This is a installer for a game downloader, the game is league of legends if that matter at all.

---

