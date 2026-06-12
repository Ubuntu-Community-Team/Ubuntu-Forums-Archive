---
title: "WINE: EQEMULATOR and .xml FIles"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Arsin on 2009-01-02
Trying to run EQemulator and this is what I get.

I opened the error log it says to check and it says it cannot find EQLSUI.xml but i found the file and its right where it said it should be.



[PHP]aaron@aaron-desktop:~$ wine "C:\Program Files\Sony\EverQuest\eqgame.exe" patchme-opengl
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec74,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
FINAL Couldn't open or read UIFiles\default\EQLSUI.xml
FINAL Couldn't open or read UIFiles\default\EQLSUI.xml
err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer format yet
err:d3d:IWineD3DDeviceImpl_Reset What do do about a changed auto depth stencil parameter?
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
[/PHP]

---

### Post by blueridgedog on 2009-01-02
Well, your request is pretty advanced, but here are some basic suggestions:

-is the file case exactly as it is looking for?
-is the file readable by the program?  Try setting it to globally read/write with:

chmod 777 ./EQLSUI.xml (from a terminal while in that directory)

Failing that, perhaps the wine forums will have someone who has tried this and overcame the issue.

---

### Post by joshuapurcell on 2009-02-19
I get the same issue. I've installed EQ Titanium and the install went great. Every time I try to run the game though it comes up with these errors in the log. This only happens when adding the patchme value to the end of the wine command. Here are the commands that don't work from the shortcut:```
exec "/opt/cxgames/bin/wine" --bottle "eq" --check --wait-children --start "C:/Program Files/Sony/EverQuest/eqgame.exe patchme" "$@"
exec "/opt/cxgames/bin/wine" --bottle "eq" --check --wait-children --start "C:/Program Files/Sony/EverQuest/eqgame.exe" "patchme" "$@"
exec "/opt/cxgames/bin/wine" --bottle "eq" --check --wait-children --start "C:/Program Files/Sony/EverQuest/eqgame.exe" "patchme"
```
Here is the command I've tried from the command line and it also doesn't work:```
/opt/cxgames/bin/wine --bottle "eq"--start "C:/Program Files/Sony/EverQuest/eqgame.exe" patchme
```
Here's a command that works (which is the default in the shortcut), but the problem is that it doesn't include the patchme option that is required to connect to a standalone server:```
exec "/opt/cxgames/bin/wine" --bottle "eq" --check --wait-children --start "C:/windows/profiles/All Users/Start Menu/EverQuest.lnk" "$@"
```
Not sure what else to try but still messing with it.

---

