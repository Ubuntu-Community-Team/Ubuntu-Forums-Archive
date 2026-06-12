---
title: "Starts up to a MS-Dos mode after installed"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by KMSMD on 2009-04-02
Hey guys, I am new to Ubuntu but heard many great things about it.  I made the switch last night and had no big issues yet.  I started my PC back up this morning and instead of going to the desktop, it loaded to a MS_DOS prompt screen asking for login and password.  Once I have that info it was like a terminal which of course I have no clue what to do from there.  Any ideas on why this would happen?  P.S. it seems to happen everytime i start up now after the initial install.

---

### Post by roger_1960 on 2009-04-02
Hi

Not sure why it happens, but after you have entered your login and password, try entering > startx at the prompt.  Does it start the graphical interface?

---

### Post by tarps87 on 2009-04-02
Firstly we will need some more information.
What version did you install
Ubuntu, Kununtu, etc
8.04,8.10
Desktop, server
The most important being was it the server version if so there is no GUI.
Also has it ever loaded up into the GUI? If so do you know what change you have made?

p.s. The MS_DOS prompt is a Unix/Linux shell

---

### Post by KMSMD on 2009-04-02
Installed Ubuntu 8.10, got it from the pro magazine so I am guessing that it is not the server edition.

---

### Post by tarps87 on 2009-04-02
That is probably the desktop edition, after you installed it did it load up with a GUI or is this the first time you've tried?

---

### Post by brayden13 on 2009-04-02
It will say on the disk if it is desktop edition or not. Mine does. They might have even for some reason managed to mess up and burned a Server edition rather than desktop edition.

---

### Post by KMSMD on 2009-04-02
ok, it gives the message of "No resume image, doing normal boot" then asks for the login and password.  StartX did not work.

---

### Post by Sef on 2009-04-02
1) What are your system specs, especially your graphics card?

2) If you boot from the Live CD, do you still get the command line?

---

### Post by tarps87 on 2009-04-02
The "No resume image, doing normal boot" message is normal, this just mean that it has not been hibernated so it is doing a clean boot.
What happens when you try to run startx?

---

### Post by KMSMD on 2009-04-02
System Specs:
Intel Duo 2.13GHz, 1066 MHz
Video Cards: e-GeForce GTS (two, connected for SLi)
Motherboard: Nvidia 680i
Memory: 4 GB @800 or 1033 (can't remember exactly)

No I do not get the same problem using the Live Disk.

---

### Post by KMSMD on 2009-04-02
When i run 'startx' it runs through a couple of things, then states that it is 'giving up'.  I did notice something with PCI then (EE) which the commands say EE = error but doesn't really say what exactly.  I want to assume it something graphical.

---

### Post by tarps87 on 2009-04-02
That usually means there is something wrong with the the xorg.conf, if there is an error it will be listed at the end of the output, the line "EE = error" is probably part of the key.

Try mv the config file
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
```
Now try and startx, this should create a clean configuration, if it does not load try
```

sudo dpkg-reconfigure -phigh xserver-xorg
```
and startx again

---

### Post by KMSMD on 2009-04-02
ok, tried both commands and still nothing.  Here is what i get when i try 'startx'

xorg-server :2:1.5.2-2ubuntu3.1
Module Loader Present
(==) Logfile: "/var/log/xorg.o.log"
(==) Using config file: "/etc/x11/xorg.conf"
Primary is not PCI
(EE) No device detected
Fatal Server Error
No screens found
giving up
xinit: connection refused (errno111): unable to connect to x server
xinit: no such process (errno3): server error

---

### Post by tarps87 on 2009-04-02
Primary is not PCI
(EE) No device detected

It can not detect the graphics card/device, the only reports of this error I have seen are when there a two graphic cards involved.

I am going to assume have have at least one graphics device on the basis you have a monitor plugged in :)

First we need to find it/them

can you post the output of this command please
```
sudo lspci | grep VGA
```
It should look like this:
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
the bits we will need are:
01:00.0
the manufacture of the device e.g nVidia

---

### Post by KMSMD on 2009-04-02
i got, 
01:00.0 VGA compatible controller: nVidia Corporation [GeForce 8600 GTS] (rev a1)
03:00.0 VGA compatible controller: nVidia Corportaion [GeForce 8600 GTS] (rev a1)

---

### Post by tarps87 on 2009-04-02
You have two graphics cards [-X

This should fix your problem, take out one of the cards and send it to me.

or

type
```
sudo nano /etc/X11/xorg.conf
```
look for the section labelled device:
Section "Device"
Identifier "Configured Video Device"
EndSection

now add these two lines:
Busid "PCI:1:0:0"
Driver "nvidia"

It should now look like this:
Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
EndSection

Now:
ctrl+x
y
<enter>

now try the startx command, the next time you boot it should load into gdm, the graphical login.

This is due to the way xorg works being changed, Ubuntu 8.10 was the first release this effected. I believe this is fixed in an update but it being a fresh install won't have them.

Edit:
If you still have problem replace
Driver "nvidia"
with
Driver "vesa"

---

### Post by coffeecat on 2009-04-02
KMSMD, is that Ubuntu 8.10 (Intrepid) you're running? There's a problem on Intrepid that affects some people running two nvidia cards. Read all about it, plus a few fixes on this thread:

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

Alternatively, use Hardy (8.04) instead.

**Edit:**, aha I see tarps87 has posted one of the fixes a minute or two before I posted. But if you've got a couple of hours, you might find the thread interesting. :wink:

---

### Post by KMSMD on 2009-04-02
ok, I see no section labeled devices, matter of fact i see no sections at all.  I can type stuff but well, i get no where.  Starting to wonder if I should re-install or what?

---

### Post by coffeecat on 2009-04-02
> **KMSMD said:**
> matter of fact i see no sections at all.

That means you've mistyped the nano command. Nano will open a new empty file if you mistype.

You've possibly made the mistake with X11 - that's CAPITAL-X_eleven. And it's safer to use the -w flag with nano, so you're better off with:

```
sudo nano -w /etc/X11/xorg.conf
```Make sure you save with ctrl-O when you've finished.

---

### Post by KMSMD on 2009-04-02
yea, needed to put capital x when i did it, it worked this time with adding the lines.  Thank you for the patience and help guys.  Now if i can just get my world of warcraft to work...

---

### Post by tarps87 on 2009-04-02
Glad I could help, for wow you may want to try wine and have a look at this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)
I manage to install the demo version a while ago but there have been several updates since then so I'm afraid I can't be of much help.

---

### Post by KMSMD on 2009-04-02
I found the initial thread for how to copy WoW and BC from the disks to install and so far so good.  I am in the process of getting WotLK expansion from the WoW website, the disc will not let you copy for some reason.  I'll post and let you know how it goes.

---

### Post by jerome1232 on 2009-04-02
> **KMSMD said:**
> I found the initial thread for how to copy WoW and BC from the disks to install and so far so good.  I am in the process of getting WotLK expansion from the WoW website, the disc will not let you copy for some reason.  I'll post and let you know how it goes.

If you run into problems with accepting the eula (won't let you click accept) the workaround is to update to the newest beta release of wine, it's an issue with the current stable release of wine.

You can get the newest release here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by KMSMD on 2009-04-02
After the WoW website install of WotLK, it all works fine so far!  Thanks for the patience and help guys.

---

