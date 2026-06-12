---
title: "Installing File/Printer Server"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by ptrnrs on 2010-12-09
As a distraction from other [adventures]("http://ubuntuforums.org/showthread.php?t=1640572") in Ubuntuland, I started trying to set up an old laptop as a server.  After the initial alarm that I only had a command prompt to look at, I took advice on how to set up (1) [a file server]("http://www.howtoforge.com/ubuntu-home-fileserver") & (2) [a printer server]("http://ubuntuforums.org/showthread.php?t=310450").  Neither really worked because I don't understand the *logic* of what's going on and therfore can't make simple adjustments to the instructions.

This leads me to several questions:-

[LIST=1]
[*]Can you configure an ordinary old laptop as a server (I'm not asking whether it's a good idea - I know it's not) or might there be hardware constraints that preclude it.
[*]Can you extend the standard (graphical) Ubuntu installation to provide server functionality?  If so, how?
[*]Can you use a graphical interface for the Ubuntu Server.  (Ideally I want to use the Ubuntu interface).  If so, how?
[*]Are the file & printer server instructions I used out of date?  With U 10.10, is there now an easier way to set up a file/print server?
[*]When installing Ubuntu Server, I selected both the Printer Server and the Samba File Server options.  What actually do they do?  Certainly it doesn't mean that it immediately starts working. :)
[/LIST]
And as always, a load of thanks to the Ubuntu experts who trawl this forum saving poor lost souls like me.

---

### Post by cariboo on 2010-12-10
> Can you configure an ordinary old laptop as a server (I'm not asking whether it's a good idea - I know it's not) or might there be hardware constraints that preclude it.

If you can install a Ubuntu CLI system on the laptop, you can use it for almost anything.

> Can you extend the standard (graphical) Ubuntu installation to provide server functionality? If so, how?

There are no gui server apps, but you can install any gui aplication you need and run it remotelly using ssh. You need to have openssh-server installed on the server, then log in to it:

```
ssh -X user@server
```

once at the prompt if for example you want to run the file manager type:

```
nautilus
```

> Are the file & printer server instructions I used out of date? With U 10.10, is there now an easier way to set up a file/print server?

You can use the cups web front end to set up a printer, and depending on how you want to share your files you can use Samba or NFS. I use both, Samba for sharing with the 3 Windows systems I have, and NFS for the 7 linux systems I run. 

If you follow the [server setup guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html"), you shouldn't have any problems with setting things up. It was originally written for 8.04, but it has been updated since, even though not much has changed as far as server setup goes since then. The only thing that has really changed is cloud serer setups, which I don't think you want to, or even can run on your laptop  

> When installing Ubuntu Server, I selected both the Printer Server and the Samba File Server options. What actually do they do? Certainly it doesn't mean that it immediately starts working. 

They can't do anything until you set the services up, like I said earlier, you can use the cups web frontend to setup your printer and share it. With Samba you need to setup your shares in /etc/samba/smb.conf, it's just a simple text file, and well commented so things shouldn't be to hard to understand.

---

### Post by ptrnrs on 2010-12-11
cariboo907: great, comprehensive response.  Thanks very much.  We'll see how I go with it now . . .

---

### Post by ptrnrs on 2010-12-12
I installed nautilus (apparently succesfully) with> sudo apt-get install nautilusWhen I type in "nautilus" or "sudo nautilus" to the CLI, I get:-> Could not parse arguments: Cannot open display:"nautilus --check", "nautilus --version", "nautilus --quit" etc. all give the same error.    Only 'nautilus --help" gives the expected response.


Don't know if it's relevant but "gedit" gives the error:-> (gedit:2468): Gtk-WARNING **: cannot open display:"sudo gedit" gives the error:-> (gedit:2469): Gtk-WARNING **: cannot open display:Any ideas?

---

### Post by tdapower on 2010-12-12
You can install ubunut on laptop, and also webmin, then you can manage your server from remote computer easily using webmin from web browser,
 
[http://www.unixmen.com/linux-distributions/4-ubuntu/1033-how-to-install-webmin-in-ubuntu-1004-lucid-lynx](http://www.unixmen.com/linux-distributions/4-ubuntu/1033-how-to-install-webmin-in-ubuntu-1004-lucid-lynx)
 
above link tells you well how to install webmin:P

---

### Post by ptrnrs on 2010-12-13
Thank you, tdapower.  I was really just hoping that I could get nautilus and gedit going on their own.

I know I can type . . .> sudo apt-get install ubuntu-desktop. . . and get everything I need.  Clearly webmin is another option.    But I'm still looking for a lightweight solution . . .

---

### Post by Locke_99GS on 2010-12-13
Those programs cannot find a display because there is no display. You have to install an X server if you want to run them on the laptop.

---

### Post by ptrnrs on 2010-12-13
I'm missing something.  I thought that "apt-get install . . . " would install *all *the prerequisites as well.

I don't understand the reference to X Server.  Is X Server the portion of Ubuntu that supports graphical display?  There seem to be several different flavours of X Server (xserver-xorg, xserver-xfree86, more?) - which one should I use?

---

### Post by drdos2006 on 2010-12-13
Install Webmin on the server and control the server from another computer through you browser.

Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by sandyd on 2010-12-13
> **ptrnrs said:**
> I'm missing something.  I thought that "apt-get install . . . " would install *all *the prerequisites as well.

I don't understand the reference to X Server.  Is X Server the portion of Ubuntu that supports graphical display?  There seem to be several different flavours of X Server (xserver-xorg, xserver-xfree86, more?) - which one should I use?

if you want minimal. run this.
```

sudo apt-get install openbox obconf xserver-xorg
sudo X -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
nano ~/.[xinitrc]("http://wiki.debian.org/xinitrc")

```stick this inside and press Control +x
```

exec openbox-session

```run
```

startx
```openbox window manager uses VERY little memory, and is good when you 
want a GUI only at a certain time.

After starting openbox, you can right click on the desktop to open a terminal and do whatever you want.

---

### Post by ptrnrs on 2010-12-13
Many thanks to drdos2006 & sandyd.

drdos2006, I don't think I'm competent enough to go into unchartered waters so I reckon I'll take the advice from [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin) and avoid WebMin.

sandyd, I followed your advice and got > E: Unable to locate package xorg-serverright at the kickoff.  I tried > sudo apt-get source xorg-serverand more successfully> sudo apt-get -b source xorg-serverDon't know if that was the right thing to do but it did load a bunch of stuff into xorg-server-1.9.0 in my personal folder (/home/ptrnrs/).  Still, though, the install fails with the same error.

So I've got xorg-server but apt-get doesn't know that I've got it.  Any ideas? If you're able to explain what each command actually does, that would be even better!

---

### Post by sandyd on 2010-12-13
> **ptrnrs said:**
> Many thanks to drdos2006 & sandyd.

drdos2006, I don't think I'm competent enough to go into unchartered waters so I reckon I'll take the advice from [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin) and avoid WebMin.

sandyd, I followed your advice and got right at the kickoff.  I tried and more successfullyDon't know if that was the right thing to do but it did load a bunch of stuff into xorg-server-1.9.0 in my personal folder (/home/ptrnrs/).  Still, though, the install fails with the same error.

So I've got xorg-server but apt-get doesn't know that I've got it.  Any ideas? If you're able to explain what each command actually does, that would be even better!
LOL.
typical me.
should be
```

sudo apt-get install xserver-xorg
```xorg-server is what its called in gentoo.....
should probably stop watching tv while posting....

---

### Post by ptrnrs on 2010-12-14
Thanks, sandyd.  We're still not there I'm afraid.  Here's what happened, my entries in [COLOR=Red]**red**[/COLOR] and my comments in [COLOR=Blue]**blue**[/COLOR] .  . . .```
=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2010.12.14 17:35:43 =~=~=~=~=~=~=~=~=~=~=~=
login as: ptrnrs
ptrnrs@192.168.0.5's password: 
Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Tue Dec 14 17:32:40 2010 from 192.168.0.2
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ ****sudo apt-get install openbox obconf xserver-xorg**[/COLOR]

Reading package lists... 0%
Reading package lists... 100%
Reading package lists... Done
Building dependency tree... 0%
Building dependency tree... 0%
Building dependency tree... 50%
Building dependency tree... 50%
Building dependency tree       
Reading state information... 0%
Reading state information... 0%
Reading state information... Done
xserver-xorg is already the newest version.
obconf is already the newest version.
openbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
[B][COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ [/COLOR][COLOR=Red]sudo X -configure[/COLOR]
[/B]
X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=af2d25a9-1382-4e14-930a-dde4c7d09ab0 ro quiet
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 14 17:36:14 2010
List of video drivers:
    radeon
    i128
    tseng
    voodoo
    r128
    apm
    ati
    sisusb
    nouveau
    chips
    openchrome
    mga
    vmwlegacy
    ark
    savage
    sis
    intel
    s3virge
    i740
    geode
    cirrus
    vmware
    nv
    ztv
    siliconmotion
    rendition
    mach64
    neomagic
    s3
    trident
    tdfx
    fbdev
    vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/ptrnrs/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**[/COLOR]
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ exec openbox-session**[/COLOR]
Openbox-Message: Failed to open the display from the DISPLAY environment variable.
**[COLOR=Blue]--ptrnrs: and then putty closed down--[/COLOR]**=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2010.12.14 17:37:18 =~=~=~=~=~=~=~=~=~=~=~=
login as: ptrnrs
ptrnrs@192.168.0.5's password: 
Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Tue Dec 14 17:35:57 2010 from 192.168.0.2

**[COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ startx[/COLOR]**

X: user not authorized to run the X server, aborting.
^Cgiving up.

xinit:  Connection refused (errno 111):  unable to connect to X server

xinit:  No such process (errno 3):  unexpected signal 2.
**[COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ su[/COLOR]**
Password: 
**[COLOR=Red]root@sammie-ubuntu: /home/ptrnrsroot@sammie-ubuntu:/home/ptrnrs# startx[/COLOR]**


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=af2d25a9-1382-4e14-930a-dde4c7d09ab0 ro quiet
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 14 17:38:00 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) AIGLX error: dlopen of /usr/lib/dri/nouveau_vieux_dri.so failed (/usr/lib/dri/nouveau_vieux_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
resize called 1280 1024
**[COLOR=Blue]--ptrnrs: and the screen locked up--[/COLOR]**
```So, the install works but the following commands seem to fail.

---

### Post by sandyd on 2010-12-14
> **ptrnrs said:**
> Thanks, sandyd.  We're still not there I'm afraid.  Here's what happened, my entries in [COLOR=Red]**red**[/COLOR] and my comments in [COLOR=Blue]**blue**[/COLOR] .  . . .```
=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2010.12.14 17:35:43 =~=~=~=~=~=~=~=~=~=~=~=
login as: ptrnrs
ptrnrs@192.168.0.5's password: 
Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Tue Dec 14 17:32:40 2010 from 192.168.0.2
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ ****sudo apt-get install openbox obconf xserver-xorg**[/COLOR]

Reading package lists... 0%
Reading package lists... 100%
Reading package lists... Done
Building dependency tree... 0%
Building dependency tree... 0%
Building dependency tree... 50%
Building dependency tree... 50%
Building dependency tree       
Reading state information... 0%
Reading state information... 0%
Reading state information... Done
xserver-xorg is already the newest version.
obconf is already the newest version.
openbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 73 not upgraded.
[B][COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ [/COLOR][COLOR=Red]sudo X -configure[/COLOR]
[/B]
X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=af2d25a9-1382-4e14-930a-dde4c7d09ab0 ro quiet
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 14 17:36:14 2010
List of video drivers:
    radeon
    i128
    tseng
    voodoo
    r128
    apm
    ati
    sisusb
    nouveau
    chips
    openchrome
    mga
    vmwlegacy
    ark
    savage
    sis
    intel
    s3virge
    i740
    geode
    cirrus
    vmware
    nv
    ztv
    siliconmotion
    rendition
    mach64
    neomagic
    s3
    trident
    tdfx
    fbdev
    vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/ptrnrs/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**[/COLOR]
[COLOR=Red]**ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ exec openbox-session**[/COLOR]
Openbox-Message: Failed to open the display from the DISPLAY environment variable.
**[COLOR=Blue]--ptrnrs: and then putty closed down--[/COLOR]**=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2010.12.14 17:37:18 =~=~=~=~=~=~=~=~=~=~=~=
login as: ptrnrs
ptrnrs@192.168.0.5's password: 
Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Tue Dec 14 17:35:57 2010 from 192.168.0.2

**[COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ startx[/COLOR]**

X: user not authorized to run the X server, aborting.
^Cgiving up.

xinit:  Connection refused (errno 111):  unable to connect to X server

xinit:  No such process (errno 3):  unexpected signal 2.
**[COLOR=Red]ptrnrs@sammie-ubuntu: ~ptrnrs@sammie-ubuntu:~$ su[/COLOR]**
Password: 
**[COLOR=Red]root@sammie-ubuntu: /home/ptrnrsroot@sammie-ubuntu:/home/ptrnrs# startx[/COLOR]**


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux sammie-ubuntu 2.6.35-22-generic-pae #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=af2d25a9-1382-4e14-930a-dde4c7d09ab0 ro quiet
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 14 17:38:00 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) AIGLX error: dlopen of /usr/lib/dri/nouveau_vieux_dri.so failed (/usr/lib/dri/nouveau_vieux_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
resize called 1280 1024
**[COLOR=Blue]--ptrnrs: and the screen locked up--[/COLOR]**
```So, the install works but the following commands seem to fail.
what graphics card are you using?

---

### Post by ptrnrs on 2010-12-15
Thanks very much, sandyd, for your continued assistance.

The video card is NVIDIA GeForce2 MX/MX 4000.  Don't how I would have found that out in Ubuntu CLI!  Luckily I still had Windows there.

A friendly tip if you're dealing with beginners like me - we'll *really *appreciated being told what to type into the CLI!  And what it does . . .

---

### Post by sandyd on 2010-12-15
> **ptrnrs said:**
> Thanks very much, sandyd, for your continued assistance.

The video card is NVIDIA GeForce2 MX/MX 4000.  Don't how I would have found that out in Ubuntu CLI!  Luckily I still had Windows there.

A friendly tip if you're dealing with beginners like me - we'll *really *appreciated being told what to type into the CLI!  And what it does . . .
have you tried booting with nomodeset?

cause on a fx 5500, it works fine.

---

### Post by ptrnrs on 2010-12-17
Thanks sandyd.  I'm away from my computer at the moment so I can't test out your idea.

I've found some info about booting with NOMODESET [here]("http://ubuntuforums.org/showthread.php?t=1613132").

---

### Post by ptrnrs on 2010-12-20
I tried booting with nomodeset and pretty much the same thing happened (but with a different screen resolution).

Unless you guys have any more ideas, I guess I'll just have to load the full Ubuntu - disappointing.  Thanks for your help anyway.

---

