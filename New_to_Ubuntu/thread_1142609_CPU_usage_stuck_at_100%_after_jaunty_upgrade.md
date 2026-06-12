---
title: "CPU usage stuck at 100% after jaunty upgrade"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by pognonec on 2009-04-29
[SOLVED]
I've been using Ubuntu for a while (but am still an absolute beginner in soul...), my PC has upgraded several times to new versions, without any major trouble. But this time, there is a major problem:
Every time I start my computer, the CPU usage is stuck to 100%, the 2 top processes being X.org (up to 46%) and gnome-system-monitor (up to 37% !!!). That does not seem normal. I uninstalled the tracker program, since I first thought that was the problem for the sluggishness (for some reason, my indexing was not valid anymore after jaunty upgrade). But I don't know what's going on...
Any idea?

PS: my PC is not a race horse, but it should be enough for normal Ubuntu usage: 
Ubuntu Release 9.04, kernel 2.6.28-11-generic Gnome 2.26.1
Hardware Memory 560.3 MiB Processor Intel Celeron CPU 2.66GHZ
System Status: Available disk space: 101.5 GiB

---

### Post by brunogirin on 2009-04-29
Do you use Netbook Remix and could it possibly be related to [this bug]("https://bugs.launchpad.net/netbook-remix-launcher/+bug/239943")? If it's not, maybe some of the advice in the bug's thread can be useful to you.

---

### Post by pognonec on 2009-04-29
> Do you use Netbook Remix?
Nope
> maybe some of the advice in the bug's thread can be useful to you.
Thanx. I've looked, and will look again, but haven't found the solution yet.

---

### Post by DavidTangye on 2009-05-01
There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

---

### Post by Scott O'Nanski on 2009-05-02
> **DavidTangye said:**
> There are many posts here all repeating your issue. For a solution see the launchpad bug reports, in this case [this one is good]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912") and there are many duplicate reports there too.
I can recommend you search before posting issues, especially [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu), as your answers are often already there, and it saves these forums being filled with 10,000 'me too' issues.

So, how do you fix it?

Those posts are Greek to most people...

---

### Post by Scott O'Nanski on 2009-05-02
For me the issue was npviewer, it showed 50% under system monitor but when I killed it everything was just butter. :)

[http://ubuntuforums.org/showthread.php?t=726383](http://ubuntuforums.org/showthread.php?t=726383)

---

### Post by pognonec on 2009-05-11
Sorry DavidTangye for filling the 10001 "me too" post. I did appreciate your help with the link though, which unfortunately was not the good one (I already uninstalled the tracker ap).
Scott O'Nanski, thank you for your input, but npviewer is not in cause here either (it is not in my running process list).
To me (sorry again, I can apparently only talk about "me", here), it looks more like whatever runs, the CPU gets stuck to 100%. And it becomes nerve crackingly slow... You guys that seem to count how many people like "me" are reporting this kind of CPU problems, did you notice whether there has been a steep increase since Jaunty arrived? That could indicate that there indeed is something behind the upgrade to Jaunty. Otherwise, it may indeed only be "my" problem. That I have not been able to fix yet :(

---

### Post by Peter09 on 2009-05-11
install htop and keep it running in a terminal, you can then see what is using CPU.

```
sudo apt-get install htop
```

then just type htop in a terminal.

---

### Post by pognonec on 2009-05-11
Thank you Peter09 for this usefull tip! I did it, and found that my CPU%, while stuck at 100%, is in reality 50% :confused:
(see attachment)

In addition, Firefox eats 30%!
Why is there such a discrepancy between CPU usages (50 seen with htop in list, but 100% seen in htop too, as CPU usage?). And isn't 30% a lot for firefox that is not actively being used?

---

### Post by Peter09 on 2009-05-11
I believe there is a mis-reporting issue in Jaunty for this. Still it helps identify who is using CPU.

---

### Post by woodamand on 2009-05-13
I have read thru all the posts on this, and my problem seems not to be related to anything I see here.
Before the upgrade to jaunty, my system used almost nothing of my dual core box, and afterward it has shot up to 90+%.
I am also using virtual box, and what seems quite strange to me is this:
before the upgrae, virtual box used up most of one core, and ubuntu was on the other core, with very little CPU usage.
Now, after a reboot, without anything, especially virtual box running, my unbuntu usage is across both cpus, and up in the 90% level.
Sorry if this is a me too thing but there really isn't anywhere else I know to ask about this.
thanks

---

### Post by Peter09 on 2009-05-13
Can you post the contents of /etc/X11/xorg.conf

and 

the output of

```
lshw -C video
```

---

### Post by woodamand on 2009-05-13
Here is the /etc/X11/xorg.conf
woodamand@bat2:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

and
lshw -C video gets me this:
*-display               
       description: VGA compatible controller
       product: GeForce 8400 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

thanks much for any help, much appreciated!

---

### Post by philinux on 2009-05-13
Have you install adobe acroread and using it's plugin. If so I got the same problem.

Some program ld-linux.so.2 sends cpu and memory sky high.

---

### Post by Peter09 on 2009-05-13
Hi,
as an experiment can you comment out the line with glx 

 in /etc/X11/xorg.conf just to see if it changes anything

---

### Post by woodamand on 2009-05-13
> **Peter09 said:**
> Hi,
as an experiment can you comment out the line with glx 

 in /etc/X11/xorg.conf just to see if it changes anything

good thought but that just killed my display in a pretty ugly way....note to self: backup conf files before changing them!

any other ideas most welcome.
thx

---

### Post by heatpumpcontrol on 2009-05-13
kill vinoserver........!!!!!!!

use x11vnc instead. Follow these instructions to add the password and add it to your startup file. You won't have the option to deny the connection but you can set up your screen to turn red to notify you the someone is connected. This is a temporary fix till they can fix vino.

[http://forums.opensuse.org/archives/sf-archives/archives-software/337668-quick-how-install-x11vnc-have-run-startup.html]("http://forums.opensuse.org/archives/sf-archives/archives-software/337668-quick-how-install-x11vnc-have-run-startup.html")

):P

---

### Post by woodamand on 2009-05-13
> **heatpumpcontrol said:**
> kill vinoserver........!!!!!!!

use x11vnc instead. Follow these instructions to add the password and add it to your startup file. You won't have the option to deny the connection but you can set up your screen to turn red to notify you the someone is connected. This is a temporary fix till they can fix vino.

[http://forums.opensuse.org/archives/sf-archives/archives-software/337668-quick-how-install-x11vnc-have-run-startup.html]("http://forums.opensuse.org/archives/sf-archives/archives-software/337668-quick-how-install-x11vnc-have-run-startup.html")

):P
Whoo-hoo! That did the trick. What I did was simply go to System/Preferences/Remote Desktop and unchecked Allow other users to view your desktop.
Excellent! THANKS SO MUCH!

---

### Post by krunge on 2009-05-13
> **heatpumpcontrol said:**
> use x11vnc instead. You won't have the option to deny the connection but you can set up your screen to turn red to notify you the someone is connected.

One can use the x11vnc option "-accept popup" to be prompted whether or not to allow the incoming VNC connection.

---

### Post by pognonec on 2009-05-14
"System/Preferences/Remote Desktop and unchecking Allow other users to view your desktop" did also solve my 100% CPU usage problem. I am back to a normal working Ubuntu. Except that I cannot use it remotely as simply as I did before. I will have to follow your alternative procedure, that I haven't tried yet.
I will thus mark this thread as "solved".

Thanks to all of you for finding a solution to this "me too" problem...

---

