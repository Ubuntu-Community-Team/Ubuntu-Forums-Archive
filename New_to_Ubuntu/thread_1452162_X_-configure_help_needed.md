---
title: "X -configure help needed"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by HappinessNow on 2010-04-11
I am trying to install Ubuntu on an eMac

I need help with configuring X,  

I type in 

X -configure

and get

The '-configure' option can only be used by root.

How do I log in as root?

---

### Post by stilling on 2010-04-11
sudo su 

password

or sudo command password

---

### Post by lewyssmith on 2010-04-11
My guess is do
    sudo [command]
which seems to be the way for Ubuntu. Mind you, I would like to know how to at least 'su' to root to do file permission tweaking. How do you define the root password?

Lewis Smith

---

### Post by HappinessNow on 2010-04-11
> **stilling said:**
> sudo su 

password

or sudo command password

> **lewyssmith said:**
> My guess is do
    sudo [command]
which seems to be the way for Ubuntu. Mind you, I would like to know how to at least 'su' to root to do file permission tweaking. How do you define the root password?

Lewis Smith
I am in as root by doing 

sudo passwd

then entering new UNIX password twice

then su

put in password

I am now running as:

root@ubuntu:/home/ubuntu# 


but when I type in X -configure

I get:

Fatal server error:

server is already active for display 0

   if this server is no longer running, remove /tmp/.XO-lock
   and start again

Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help.

ddxSigGively: Closing log

...tried 

remove /tmp/.XO-lock but got
remove: command not found

I have never set up X.org and I have never installed Ubuntu on an eMac so I need some help

I am trying to follow directions found here:

[http://jeremy.visser.name/2009/02/20/how-to-get-xorg-working-on-an-apple-emac-ati-radeon-7500/](http://jeremy.visser.name/2009/02/20/how-to-get-xorg-working-on-an-apple-emac-ati-radeon-7500/)

and/or here:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9107903#post9107903](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9107903#post9107903)

---

### Post by mhgsys on 2010-04-11
For the command to work out you have to stop the currently loaded X first.

I'm guessing you want to generate a xorg.conf.new as thats what the command your trying to run does.

Anyway; you can stop X by entering

```
sudo service gdm stop
```

**Then switch to tty with Ctrl+alt+f1** (f2,f3, etc)
 
Login; and run Xorg -configure as root

After that you probably  want to copy the generated xorg.conf.new to /etcX11/xorg.conf so you can test it

```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

and start gdm again with 

```
sudo service gdm start
```

---

### Post by HappinessNow on 2010-04-11
> **mhgsys said:**
> For the command to work out you have to stop the currently loaded X first.

I'm guessing you want to generate a xorg.conf.new as thats what the command your trying to run does.

Anyway; you can stop X by entering

```
sudo service gdm stop
```

**Then switch to tty with Ctrl+alt+f1** (f2,f3, etc)
 
Login; and run Xorg -configure as rootran

Xorg -configure as root

```
Build Operating System: Linux 2.6.15.51-powerpc64-smp ppc Ubuntu
current Operating System: Linux ubuntu 2.6.31-14-powerpc #48-ubuntu Fri Oct 16 14:11:44 UTC 2009 ppc
Kernel command line: ro ramdisk_size=1048576 file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
build date: 26 October 2009 05:15:51pm
xorg-server 2:1.6.4-2ubuntu4 (build@)
     Before reporting problems, check http://wiki.x.org
     to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (??) unknown.
(==)Log File: "/var/log/Xorg.0.log", Time: Sun Apr 11 19:14:18 2010
List of video drivvers:
ati
chips
v41
mach64
mga
nv
r128
radeon
s3
s3virge
savage
sis
sisusb
tdfx
trident
fbdev
(++) Using config file: "/root/xorg/.conf.nex"

Backtrace:
0: Xorg(xorg_backtrace+0x50) [0x101075f0]
1: Xorg (xf86SigHandler+0x70) [0x1008d190]
2: [0x100364]
3: /usr/lib/xorg/modules//libint10.so(xf86ExtendedInitInt10+0x380) [0xf32a1e0]
4: /usr/lib/xorg/modules//libvbe.so(VBEExtendedInit+0x320) [0xf36f930]
5. /usr/lib/xorg/modules//libvbe.so(VBEInit+0x28) [0xf36fad8]
6. /usr/lib/xorg/modules/drivers//nv_drv.so [0xf7c7a50]
7. Xorg(DoConfigure+0xf24) [0x1007154]
8. Xorg(InitOutput+)x1bc) [0x1007154c]
9. Xorg(main+0x224) [0x10028344]
10. /lib/libc/so.6 [0xfa6c59c]
11. /lib/libc.so.6 [0xfa6c760]
Saw signal 7. Server aborting.
   ddxSigGiveUp: Closing Log
   ddxSigGiveUp: reraising 7
Bus error (core dump)
```

I have no idea what any of this means or what to do next.

Please help.

---

### Post by mhgsys on 2010-04-11
> **mhgsys said:**
> 




After that you probably  want to copy the generated xorg.conf.new to /etcX11/xorg.conf so you can test it

```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```

and start gdm again with 

```
sudo service gdm start
```

..:rolleyes:

---

### Post by stilling on 2010-04-11
sudo dpkg-reconfigure xserver-xorg

you'll be guided to several steps where you can reconfigure your keyboard, mouse, display driver and screen resolution my suggestion is to go through those steps and, if your keyboard and mouse are correctly set, just don't change them, just leave them as they are with the display driver you should look for one called «nv» or, if you don't see it, just pick the one called «vesa», it usually works for any display and for me, it's the one that get's me out of trouble after that you can choose what you'll find to be the correct screen resolution when all this is done just logout (you don't have to restart, I think!) and hit Ctrl+Alt+F7 to return to the GUI interface (not terminal) hopefully you can manage the installation of the correct driver for your graphics card within Ubuntu GUI.

---

### Post by ajgreeny on 2010-04-11
> **stilling said:**
> sudo dpkg-reconfigure xserver-xorg

you'll be guided to several steps where you can reconfigure your keyboard, mouse, display driver and screen resolution my suggestion is to go through those steps and, if your keyboard and mouse are correctly set, just don't change them, just leave them as they are with the display driver you should look for one called «nv» or, if you don't see it, just pick the one called «vesa», it usually works for any display and for me, it's the one that get's me out of trouble after that you can choose what you'll find to be the correct screen resolution when all this is done just logout (you don't have to restart, I think!) and hit Ctrl+Alt+F7 to return to the GUI interface (not terminal) hopefully you can manage the installation of the correct driver for your graphics card within Ubuntu GUI.
Not any use now, I'm afraid as it will do almost nothing.  That command has been deprecated for at least the last couple of versions of ubuntu.

---

### Post by stilling on 2010-04-11
i`m sorry i didn`t know 

that i was use and know that getit me out of shi. so sorry again

this replied to me 

Rather than communicating directly with the video hardware, the X server  &#9474; 
 &#9474; may be configured to perform some operations, such as video mode          &#9474; 
 &#9474; switching, via the kernel's framebuffer driver.                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; In theory, either approach should work, but in practice, sometimes one    &#9474; 
 &#9474; does and the other does not.  Enabling this option is the safe bet, but   &#9474; 
 &#9474; feel free to turn it off if it appears to cause problems.                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Use kernel framebuffer device interface?                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Yes>                       <No>                       &#9474; 
 &#9474;

---

