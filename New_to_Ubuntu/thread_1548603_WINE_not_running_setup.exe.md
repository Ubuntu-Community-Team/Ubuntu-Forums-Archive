---
title: "WINE not running setup.exe"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by corncob on 2010-08-08
I've been using Print Shop Ensemble III since 1997, running it in WINE in Linux.  However, on this fresh installation of 10.04 I just get this message when I try to open setup.exe with wine installer:
> The file '/media/990502_0129/SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
Its running on 10.04 on my other computer but I had installed it in 9.10 and then upgraded. I did download wine1.2-gecko this time and also playonlinux out of curiosity.  I didn't try anything else as that's the only windows program I use anymore but I might do so to see what happens.

---

### Post by howefield on 2010-08-08
Right click the file and select properties > permissions and ensure that mark as executable is checked off.

---

### Post by 0004tom on 2010-08-08
> **howefield said:**
> Right click the file and select properties > permissions and ensure that mark as executable is checked off.

bugger you beat me lol or you can do this in a terminal.

```
chmod +x /media/990502_0129/SETUP.EXE

wine /media/990502_0129/SETUP.EXE
```

you need to give it execute permissions..

---

### Post by corncob on 2010-08-08
Thanks Guys, I meant to say I was trying to install it from a read only CD and it won't let me change permissions.  A thought would be to copy it to a CD-RW but I don't have one.  Anyway, here's what I got:
```
corncob@hp-laptop:~$ chmod +x /media/990502_0129/SETUP.EXE
chmod: changing permissions of `/media/990502_0129/SETUP.EXE': Read-only file system
corncob@hp-laptop:~$ 
corncob@hp-laptop:~$ wine /media/990502_0129/SETUP.EXE
wine: created the configuration directory '/home/corncob/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfd4
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x196e1c (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa60e8d8, overlapped 0xa60e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1cb6b94 (nil)
wine: configuration in '/home/corncob/.wine' has been updated.
corncob@hp-laptop:~$ 


```
If it tells you anything, please let me know.  Meanwhile I tried to install another old Windows program (Family Tree Maker 10) with the same result although it installed on my other computer, so its just the wine installation on this computer.  I'll try re-doing it.

---

### Post by corncob on 2010-08-08
I purged WINE and reinstalled it.  It installed wine1.2-gecko but not playonlinux.  Same thing.  I tried to fool it by copying the CD to a file on the HD, and made SETUP.EXE executable.  The mouse pointer turns into a clock for a couple seconds as if its going to do something but then it doesn't.  Running it from the Terminal gives no errors but doesn't do anything either:
```
corncob@hp-laptop:~$ wine Desktop/ensemble/SETUP.EXE
corncob@hp-laptop:~$ 
corncob@hp-laptop:~$ echo $?
0
corncob@hp-laptop:~$ 
```

---

### Post by akand074 on 2010-08-08
Maybe check the version of WINE your using on your other computer that was using 9.10 originally. There have been cases were some applications worked in older versions and not newer versions, for whatever reason. If you are already using the same version on both computers than it beats me..

---

### Post by 45acp on 2010-08-08
I had the same problem of no being able to install off a cd in wine. Found the answer in the thread "Can't execute in wine"

You need to edit /usr/share/applications/wine.desktop and change the line that begins with "Exec=" to "Exec=wine start /unix %f"

It worked for me.

---

### Post by nerdy_kid on 2010-08-08
yeah this "feature" is just stupid.  what you have to do is open a terminal and do 
```

wine start /unix FILE

```
and edit the menu file like 45acp said if you dont want to have to use the terminal every time you try installing something off a cd.

---

### Post by Lance7_q on 2010-08-08
Hi,
Here take an eye on these.It says:
Before using Wine, it is necessary to create the fake  C: drive where your Windows applications will be installed.  To do  this, enter the following command into the terminal: You may find the  terminal by going to Applications -> Accessories -> Terminal  
winecfgYou also have the option of configuring Wine via the Configure Wine option in the Applications-> Wine menu. 
This  will create a hidden folder (.wine) in your home directory containing  the fake C: drive as well as registry files similar to those used in  Windows.  Once this directory is created, the **Wine Configuration Window**  will appear.  This window will allow you to customize a variety of  settings for Wine, including which Windows Version that is emulated,  drive mappings, DLL overrides, as well as application specific settings.   Click the **Ok** button to close the window.

---

### Post by corncob on 2010-08-10
> **45acp said:**
> I had the same problem of no being able to install off a cd in wine. Found the answer in the thread "Can't execute in wine"

You need to edit /usr/share/applications/wine.desktop and change the line that begins with "Exec=" to "Exec=wine start /unix %f"

It worked for me.

This did change things but I still didn't get anything installed.  A blank window popped up for a split second and closed but nothing happened.
I had the bright idea of copying the .wine folder from the computer that was working but the pen drive, SD card, and USB drive all reported that their format (FAT32) didn't support symbolic links.

---

### Post by salmander on 2011-04-24
> **45acp said:**
> I had the same problem of no being able to install off a cd in wine. Found the answer in the thread "Can't execute in wine"

You need to edit /usr/share/applications/wine.desktop and change the line that begins with "Exec=" to "Exec=wine start /unix %f"

It worked for me.
thanks...worked for me...all i did was
in terminal type
sudo gedit /usr/share/applications/wine.desktop
then enter your password
then edit the line that begins with "Exec=" to "Exec=wine start /unix %f"

save and exit...
tadaaa...

---

