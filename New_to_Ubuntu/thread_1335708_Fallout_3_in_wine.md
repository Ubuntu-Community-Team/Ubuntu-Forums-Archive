---
title: "Fallout 3 in wine"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by LostMagix on 2009-11-23
I have been dieing to play fallout 3 again but I cant get it working in wine, here is what I get after a fresh install


:~$ env WINEPREFIX="/home/l18nxboy/.wine" wine "C:\Program Files\Bethesda Softworks\Fallout 3\FalloutLauncher.exe" 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\MSVCP80.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\FalloutLauncher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\FalloutLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Fallout 3\\FalloutLauncher.exe" failed, status c0000135

google didnt turn much up for me

---

### Post by samigina on 2009-11-23
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322")

---

### Post by LostMagix on 2009-11-23
purged wine and reinstalled everything, its seems to be working now

---

### Post by gackt on 2009-11-24
Mind marking the treadh as solved?

Usually you just need to copy the dll to wine/windows/directory. Find the location of the dll on windowsxp and copy the dll to windows directory in wine. I always do that when something is missing.

---

### Post by LostMagix on 2009-11-24
I will as soon as I get it fully up and running, i can load the game but when i go to start a new game it freezes.

once I figure everything out I will post a full howto and mark as soulved

---

