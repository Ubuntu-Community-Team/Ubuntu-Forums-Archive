---
title: "Installing Maple"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Blueball32 on 2009-01-17
Hey again everyone

I got a CD from my University with Maple for Linux. It contains the license file and the installer Maple12Linux32Installer.bin. How do I run this .bin file in order to install the app...?

THX :)

---

### Post by taurus on 2009-01-17
Open a terminal and change to the directory where that file is on the CD.

Applications -> Accessories -> Terminal
```
cd /media/cdrom0
sudo ./Maple12Linux32Installer.bin
```

---

### Post by Blueball32 on 2009-01-17
> **taurus said:**
> Open a terminal and change to the directory where that file is on the CD.

Applications -> Accessories -> Terminal
```
cd /media/cdrom0
sudo ./Maple12Linux32Installer.bin
```

hmmm...the command doesn't work...the terminal says: "command not found" :confused:

---

### Post by taurus on 2009-01-17
I assume you mean the second command.  What's the output of this command from a terminal?

```
ls -la /media/cdrom0
```
I assume your CD is mounted to /media/cdrom0.

```
df -h
```

---

### Post by Blueball32 on 2009-01-17
I changed the directory correctly, so the Installer.bin is there and nothing else except the license...

---

### Post by Blueball32 on 2009-01-18
Hey, I've managed to install Maple with chmod. The Installer came up and everything processed as it should, but how do I run maple now. I can't find it in the app-manager or in the app-menu...?? :(

---

### Post by txcrackers on 2009-01-18
Usually when you install "third-party" applications using an installer, they won't have the correct files to automagically show up in the menus. You will either need to run from a command-line or create the menu entry yourself. 

Prior to that, of course, you'll need to find where it installed and locate the actual executable program...

---

### Post by Nepherte on 2009-01-18
First find out what location it is installed in. You were prompted for the installation path during the installation. Maple also created a menu entry for me, you really should have installed it as root instead of chmodding around.

---

### Post by Blueball32 on 2009-01-18
> **Nepherte said:**
> First find out what location it is installed in. You were prompted for the installation path during the installation. Maple also created a menu entry for me, you really should have installed it as root instead of chmodding around.

Well I got the installation directory, but how should I know how to install this file/app correctly if nobody can help me here. I tried a solution I found with google -> chmod... :(

Whats the name of your executeable, so I can search for it...?

---

### Post by Nepherte on 2009-01-18
The executable resides in <installation path>/bin/xmaple for the graphical version.

---

### Post by Blueball32 on 2009-01-19
> **Nepherte said:**
> The executable resides in <installation path>/bin/xmaple for the graphical version.

Hey thats fine. Maple starts when I execute that file, but after I run it Maple starts up, the startup dialog appears and the I got a blank screen with nothing on it...really nothing... :(

---

