---
title: "Bad ending to &quot;upgrade&quot; from 8.04 to 8.10"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by harelb on 2009-12-21
my home machine, formerly running 8.04 ubuntu with gnome, is unusablee since  last night when I followed

[http://www.ubuntugeek.com/upgrade-ub...epid-ibix.html](http://www.ubuntugeek.com/upgrade-ub...epid-ibix.html)

Everything worked fine, until the reboot. Even the reboot works fine until the login screen. It even makes, half the time I re-boot it, that little "ubuntu drums" sound it makes normally. Except what happens is

1. the screen gets that orange colored background as normal right before the login screen -- as it always has

2. a circular rotating "please wait" (what used to be called hourglass) icon -- as it always has

3. rectangular area created where the login will be typed -- as it always has

4. then the background turns white instead of organge, the recnagular text box is still visible (but not a real tex box, just a rectangular area of a different color) and the rotating "please wait" icon freezes.

Did this reboot after reboot. Tried safe mode style reboot, and all the features there that I could try, none helped.

I had hoped by now this would be ironed out it having been 14 months...I usually rave to people about linux but feel really burned by this experience (yes I tried to use a backup utility, first, but that failed after my trying 2 or 3 different things, so I gave up on doing a backup before doing this) I just ordered an install CD which should arrive in a week or less.

..but I'm hoping the above details are specific enough that someone out there knows and can be a huge hero by telling me how to fix this install that's left my computer nearly dead and useless since..? Thanks in advance,

Harel

---

### Post by hugmenot on 2009-12-21
Difficult to say.

What you can try is to get more information. Try extracting some useful error messages You could boot from a Live CD and read the GDM log files. GDM is the screen with the login window that doesn't properly show up.

The logs are under /var/log/

---

### Post by harelb on 2009-12-21
New information. Previously having none of the recovery mode attempts worked: I would reboot and ask for recovery mode (I tried both the Ibex most recent (second from the top option, the top option being non-recovery mode Ibex) and the oldest one - they would just go through recovery, say no problems found, ask if I wanted to finish login, I said yes, and then I got the same message.

I am typing this from home, not work, becauase I tried yet again, only did another verion's recovery mode, and got an error,then hit "Exit" and to my shock got an actual working login screen (it reverted to the old password which threw me off, but I eventually figured that out). I was initially too  dim to realize I was not in Ibex but by definition in an earlier version, I was so thrilled 1) to be able to boot and 2) to get rid of my screen problem (which I had only with 8.04 and no one on ubuntuforums was able to help me with..no need to get into what it was..) did "updates" and under a half hour later, it was done with updates and asked me to reboot...

..which got me back to square one: can't log in, same error. Tried again to find the right one to put into recovery mode..not sure if this is what worked last time, but this worked this time:

**2.6.15-26-386.recovery **(or something like that)
and that again stopped at a line, I wrote down it was something like
**IPvG over IP tunneling driver**
it looked like it was frozen but after minute or so I hit return and sure enough, got a prompt, type "exit" at the prompt, and was able to get that login screen. I'm at Dapper 6.06

Does any of this info help? As for,

> **hugmenot said:**
> Difficult to say.

What you can try is to get more information. Try extracting some useful error messages You could boot from a Live CD and read the GDM log files. GDM is the screen with the login window that doesn't properly show up.

The logs are under /var/log/

I can now look, now that I can log in again, I hope (noob question here) my being in Dapper rather than via a live CD, doesn't affect that. Ok, under /var/log/gdm/ there are five files: 0.log.4 which is dated 2008 and presumably not important, and 0.log.3  , 0.log.2 , 0.log.1  and 0.log

Here's 0.log.3

> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux hbhome 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 21 21:59:55 2009
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

0.log.2 is the same size (910bytes) and probably the same, let me see and paste:

> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux hbhome 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 21 22:01:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

0.log.1 is 965 bytes so not identical, it is:


> X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux hbhome 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 21 22:01:38 2009
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
SetGrabKeysState - disabled
SetGrabKeysState - enabled

Not sure if this has anything to do with my login problems.

Also a new question in this Dapper recovery-mode login which is the only one I have right now (something that will hopefully change with help from you all :-), it warned of low disk space..turned out it was 256MB..I emptied trash and deleted a bit more and have 635MB but that's no where near the gigabytes of free space I had before Sun night's attempt at 8.04-->8.10  and I'm not sure if this problem will automatically go away once I'm allowed back into being able to log into the newly installed 8.10 or whether it's some separate problem with the install. There are other issues with this login that I don't want to distract with...hopefully I can get logged into 8.10...I mentioned the disk space in case that spirals into trouble even being able to use this temporary login..

Again all this started after following
[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)
with everything appearing to work fine for the install up to and including the "now reboot your system" step and all the early re-boot working until that frozen login screen. Hope the above info helps?

Thanks in advance,
Harel

---

### Post by hugmenot on 2009-12-22
Okay that was actually useful:
```
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
```

This sounds like a botched install. Did you install an Nvidia driver perchance?

But now, would it be too much for you to wipe the system and install the most current release 9.10? It may be more work than running a dist-upgrade, but you will get clean slate and an actually current release, not one that is a year old.

If you want to try to repair your install you might try to reinstall the Nvidia driver from the most current kernel. The driver installation must match the kernel version.

---

### Post by kansasnoob on 2009-12-22
Just a thought here. Since you have a disc space problem I'd be tempted to at least try to mount and chroot the install from a live CD and try a few things.

Is the newest Live CD you have Dapper? It probably shouldn't matter but the oldest Live CD I've actually tried this with is Intrepid.

Anyway the first thing you'd need to do is determine the partition number of your installed Ubuntu, so from the Live CD run:

```
sudo fdisk -l
```

(BTW that's a lower case L.)

If it's a fairly simple partitioning arrangement it should be somewhat easy to determine which partition it is. If you need more help with that please ask before proceeding.

Please read more about my mount & chroot procedure here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

It's actually fairly simple, assuming that Ubuntu is on /dev/sda1:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

I always like to see if I am where I want to be with:

```
lsb_release -a
```

Then helpful informational commands:

```
df -H
```

(Provides info regarding disc usage)

```
cat /etc/apt/sources.list
```

(Might give us some idea where the upgrade stalled)

**The rest of this involves a lot of guess work without seeing the actual output of each command!**

I'd then try to free up some space:

```
apt-get autoclean
```

(Should clean up unused .debs)

```
apt-get clean
```

(Will also get rid of .debs for packages that are installed)

Then I'd see what this says:

```
apt-get -f install
```

(It may suggest you run "apt-get autoremove")

If that has freed up enough space I'd then run:

```
apt-get update && apt-get upgrade
```

**Actually you may also want to run "apt-get dist-upgrade" but without seeing the output I can only guess!**

I would not be at all surprised to see the output of one of those commands to recommend running "dpkg --configure -a". If so that should be perfectly safe.

Since X seems to be involved here I'd almost surely want to run:

```
dpkg-reconfigure xserver-xorg
```

**As I said most of this is guess work without seeing things myself!**

When done in the chroot just:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

```
sudo reboot
```

I hope this might be slightly helpful.

---

### Post by hugmenot on 2009-12-22
Ya, you can try that if you feel up to it. 

The space has most probably been gobbled up by the package cache, which you can clear with apt-get clean.

---

### Post by kansasnoob on 2009-12-22
> **hugmenot said:**
> Ya, you can try that if you feel up to it. 

The space has most probably been gobbled up by the package cache, which you can clear with apt-get clean.

That's what I'm thinking. Maybe the upgrade even "stalled" due to lack of space.

It's one of those things I could easily diagnose if I had the computer in front of me. Sadly, diagnosing can be painfully slow just going back-n-forth thru the forums.

Like "df -H" might tell me something so I'd change the plan. Or the sources.list might tell me something else, or maybe even need editing - then that gets a bit scary because it requires using nano thru a chroot and nano can seem quite odd unless someone has used it before.

It's always best to avoid breakage :)

---

### Post by hugmenot on 2009-12-22
Right, that is why I was asking if wiping that thing and starting from scratch wouldn&#8217;t be a relatively quicker solution.

---

### Post by harelb on 2009-12-22
Kansasnoob,
I appreciate your extended set of suggestions..keep in mind that you are not only not a "noob" but much of your post is way over my head. I know that a 'live cd' is one that is bootable with an OS, but not much beyond that..I don't even know what the difference between the live cd and the 'alternate install' CD are (I just ordered both last night since I've misplaced my other older ones - I can no doubt find out via google, so I don't need a detailed reply on that issue but shows how little practice I've had other than day to day linux usage of ssh and browser..)

I don't have a life CD right now that I can find..is it totally useless to type the command without a live CD just logged in right now under "2.6.15-52-386" recovery mode (that and 2.6.15-26 recovery mode work, not "2.6.27-16...etc" nor "2.6.24-26.....") 

> sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         943     7574616   83  Linux
/dev/hda2             944        4865    31503465    5  Extended
/dev/hda5            4779        4865      698796   82  Linux swap / Solaris
/dev/hda6             944        4691    30105747   83  Linux
/dev/hda7            4692        4778      698796   82  Linux swap / Solaris

Partition table entries are not in disk order

Is that of any use at all? Do I have an nvidia driver? I install major things (other than the regular automated ubuntu updates and firefox plug-ins) very very rarely so it would be many years ago. On a previous machine that had only a CD reader where I purchased separately a CDwriter I think some nvidia software came up--this would be 2005 or so. On this current machine? I'm not 100% sure but I certainly don't recall doing anything like that explicitly..Any commands for me to run hugmenot? It is a moot point either way?

To try to reduce my ignorance:

1. What exactly did the GDM output tell you? Botched install sounds pretty general.

2. Is that the only command that can get useful info without a live CD?

3. When my new live cd arrives (I paid for 2 day or expedited delivery and ordered last night but it's near Xmas so who knows) are my choices just (a) erase everything and lose everything and instal a clean latest ubuntu or (b) spend hours on forensic investigations or will there be a more powerful option (c) when that arrives, that you recommend?

4. is there anyway to recover my files from before the messed up 8.04-->8.10?  (I have on CD my files as of 12 months ago including someof the most important ones but not all..when using a backup utility failed I gave up and just crossed my fingers)

This is the second time I've been burned by upgrades. The last time was summer 2008 when I upgraded from Dapper to 8.04 Heron and burned a CD (I can't remember if the other ways failed to work for me, or whether I was warned that the burn-your-own-CD was safer..I think the former!) and from the burned CD I installed  hardy heron which almost worked but the screen resolution was permanently botched...usable for most but not all software..several ubuntuforum members looked at my posts and couldn't figure out how to fix. I can still recomment linux to friends but I don't see how I can ever again recommend to anyone to "upgrade". This brings up the question.Next time I can maybe just burn all desktop files to a CD, then install a new OS and lose all the other data, then save from the CD the files again..?

5. Meanwhile back to the present problem, in case I can save this install, is there no way to get around the login screen? When I'm in recovery mode I get a recovfery menu, that allows "resume" and allows other options, like testing the disk but none of the options let me log into some primite shell from which to try to run commands to detect what's wrong and fix them, before loging in the regular way. Is there anything like that? Probably with all the experience you have you would have mentioned if the answer is 'yes' but I had to ask.. and lastly, the screen I get when I rebooot (I don't even know its name...the one that says it will use the standard one in 8 seconds if I don't do anything else..) it has a lot of options...one of them being these recovery mode earlier versions of ubuntu (is that why I'm so low in space I wonder? suddenly it has 10 or so previous versions saved, or maybe it always did?) is any of these options an optionthat will let me, if I'm willing to let it sit for an hour or more, would let me just re-try the entire 8.04-->8.10 installation all over again without losing more files?

Sorry for so many questions but the posts are really ahead of where I am (sadly, I forget much of what I learned 12 or 24 months ago so even if I become only 90% noob rather than my current 98% noob, back then, by the time a new upgrade comes up I've forgotten what little new I've learned!) apt-get is basically a shell command to get packages, instead of using the pulldown menus (which get you to the synaptic package manager) is that correct? Let me know if it's important I apt-get this 'clean' package and run is first thing.. 
Thanks,
Harel

---

### Post by harelb on 2009-12-22
I took so long to type that, that I did not see the last two responses #7 and #8 until now.

"Maybe the upgrade even "stalled" due to lack of space."

I had many gigabytes of space when I started the 8.04-->8.10 upgrade. So if lack of space is the problem, it's a problem that was created during some malfunction of the upgrade process itself...

As for starting from scratch, that's Plan B. But evne if I go with Plan B, is there anyway to recover the files I had on my desktop folders on Monday night before the upgrade?

---

### Post by harelb on 2009-12-22
From where I am now (which again is not a live cd but logged in via the recovery mode for the 2.6.15-52-386 which apparently is 6.06LTS) I typed just this second:

```
 apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

```

tried again with sudo
```

harel@hbhome:~$ sudo apt-get clean
Password:

harel@hbhome:~$


``` so just got back to the shell prompt and nothing else obvious happened..

If you meant something else, I unfortunately need is spelled out more basically :confused:

---

### Post by houseworkshy on 2009-12-22
Just an idea on the off chance you only have one burning drive or a shortage of memory sticks.  Obviously you can get online as you are posting.  So.  Download an iso of Puppy linux and burn it to cd.  Then boot with that.  The thing about puppy is that it is small and can be loaded to ram after which you can take the cd out.  This frees up your cd drive and lets you use the burner to take copies of your work off the machine.  I'd make this an important first step as operating systems can easily be replaced whilst ones work can not. It's very basic compaired to Ubuntu but a handy system to have lying around for problems which have locked you out.  As to fixing Ubuntu you are being advised by people who are clearly better informed than I.  Good luck with it.

---

### Post by hugmenot on 2009-12-22
> **harelb said:**
> 
tried again with sudo
```

harel@hbhome:~$ sudo apt-get clean
Password:

harel@hbhome:~$


``` so just got back to the shell prompt and nothing else obvious happened..

If you meant something else, I unfortunately need is spelled out more basically :confused:

No, that was good. No output means it worked, did its thing, no errors, and it freed some space.


Now you can see how much space you have free with "df -h". 

Then you can try to follow the instructions that kansasnoob gave you. But honestly, this does not guarantee it will work properly. And you might waste more time than necessary fiddling on the command line.

If I were in your place I would wait for that Live CD (which version are they sending?).
Can you only back things up on CD, or do you have external drives, anything else?

---

### Post by hugmenot on 2009-12-22
> **harelb said:**
> 
To try to reduce my ignorance:

1. What exactly did the GDM output tell you? Botched install sounds pretty general.


It told me that the graphical desktop cannot start because there is a mismatch with some graphics libraries that weren&#8217;t installed properly. Something went wrong. No idea what exactly.

> 
2. Is that the only command that can get useful info without a live CD?


You can try the chroot method outlined above, but if that restores your Nvidia graphics is dubious. I can&#8217;t even remember how Nvidia drivers were installed back then in 8.04 and 8.10.

> 
3. When my new live cd arrives (I paid for 2 day or expedited delivery and ordered last night but it's near Xmas so who knows) are my choices just (a) erase everything and lose everything and instal a clean latest ubuntu or (b) spend hours on forensic investigations or will there be a more powerful option (c) when that arrives, that you recommend?


No you should back-up. It&#8217;s only that while the Live-CD is in the drive you cannot burn anything.

---

### Post by kansasnoob on 2009-12-22
If you possibly can thru a recovery CLI:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by harelb on 2009-12-23
> **kansasnoob said:**
> If you possibly can thru a recovery CLI:

```
dpkg-reconfigure xserver-xorg
```

What does CLI stand for? Also not sure what a recovery CLI is and what the line of code is supposed to accomplish? To fix the entire problem I posted about, or to accomplish something more narrow (if so, what?) I'm at the "absolute beginner" board for a reason :-) (I admit I'm as quick to use acronyms etc on others as soon as I learn them too, assuming everyone knows it as soon as I learn them :-)

P.S.Aside to houseworkshy: thanks..so far my hours away I've only managed to find puppy linux, remind self of directions how to burn an ISO Cd, and to scratch the surface of the how to use puppylinux...I hope it is not too much more time before it's clear how to use ..otherwise that CD in the mail looks tempting to use and kill everyhitn :-(

PPS: someone asked what versions or what exadtly I ordered online. It's from  OSDisc.com and I orderd two, being in too much of a hurry to even research what's the difference, figuring I'd research that later (which to use) so I ordered both of these, doing my part to support linux distributors ;-) so ordered:
> 
Ubuntu 9.10 - Alternate Install CD (PC) 1       1.95    1.95
Ubuntu 9.10 - Install/Live CD (PC)      1       1.95    1.95 

though hope I won't have to resort to these this time, and can heal my computer...giving myself another 4-7 days before giving up..thanks to everyone who's tried to help with this unexpected 'adventure' :-)

---

### Post by harelb on 2009-12-23
is there a way to turn off automatic smiley generation so I can use the old fashioned two-in-one of a the mouth of the smiley being the close-parenthesis too..

---

### Post by harelb on 2009-12-23
> No, that was good. No output means it worked, did its thing, no errors, and it freed some space.

ok...and now I just type "clean" or "sudo clean" from shell to accomplish it? Must I be in / or other specific directory?

---

### Post by Sef on 2009-12-23
> What does CLI stand for?

Command Line Interface: it is called terminal in Ubuntu.  (Applications > Accessories > Terminal)

---

### Post by hugmenot on 2009-12-23
> **harelb said:**
> ok...and now I just type "clean" or "sudo clean" from shell to accomplish it? Must I be in / or other specific directory?

No no. It cleaned already.
[LIST]
[*]CLI is "command line interface", the black screen with white text you type commands in when you boot in Recovery Mode. The command line is what you can use to try to repair your system. You cannot start the GUI, so you have to use the CLI to fix it.
[*] We need to find out a few things: Is there enough space now? What is the state of the packages after you ran the upgrade? Is the system in a consistent state? Why is it crapping out complaining about libGL?
[/LIST]

Boot into Recovery Mode, and use the latest kernel in the Boot Menu. Please try these commands there, and report what happened.
[LIST=1]
[*]df -h        [COLOR="SlateGray"]#  "disk free", "human readable numbers in MB, GB"[/COLOR]
[*]sudo apt-get -f install        [COLOR="SlateGray"]# this is to reach consistent package state[/COLOR]
[*]sudo apt-get update        [COLOR="SlateGray"]# look for new packages[/COLOR]
[*]sudo apt-get dist-upgrade        [COLOR="SlateGray"]#  install updated packages trying to reach consistent up-to-date state.[/COLOR]
[*] dpkg -l | grep nvidia        [COLOR="SlateGray"]# show which Nvidia driver packages are installed[/COLOR]
[*] sudo dpkg-reconfigure xserver-xorg        [COLOR="SlateGray"]#  Detect graphics hardware and configure the GUI to try to make it start again.[/COLOR]
[/LIST]

Reboot after that and see if this made it work. If not:

[LIST][*]ls -lrt /var/log/gdm/
[/LIST]

The last file is relevant. Look for the (EE) error at the bottom of this file.

---

### Post by harelb on 2009-12-23
Hugmenot,
I appreciate the level of detail you have given. I have tried to be detailed below.

1a. I understand you to mean that unlike Sef, you mean by "CLI" to NOT refer to a terminal window running within GUIdesktop but always the primitive screen in recoery move that is a text-only

1b. I used the most recent recovery mode which was:

"ubuntu 8.10 kernel 2.6.27-16-generic (recovery mode)"

(I noticed there was also a 2.6.24-26-generic below it, which is puzzling, since I went from Hardy straightt o the Ibex...but I followed your instructions and used the most recent recovery (second line from the top) which is the above 2.6.27-16-generic)

1c. *Sometimes* when I choose a recovery mode it *automatically* stops and leaves me in "CLI" (allowing me to type command lines and NOT putting me back into "recovery menu") but *this* time, as sometimes happened depending on the boot (or maybe depending on which kernel's recovery mode I choose) it did *not* stop..it kept going and took me back to "Recovery Menu"

this had the options:
*resume normal boot
* clean (if I am reading my handwriting correctly)
* dpkg
*fsck file system check
*root- drop to root shell prompt
* xfix

I guessed that if I pick "root" to "drop to root shell prompt" then that is the same as being put into CLI by the computer. If I guessed wrong,  please tell me what to do instead...

If I guessed right and it is the same (choosing "root"from "recoery menu") as being put there directly (after computer is done 'talking to itself' after you choose recovery mode boot) then here is what I can report.

2. I typed "df -h" per your insturctions
a. I have to type by hand since I don't know how to print from there..so what I am reporting below should be 98%+ accurate but might not be 100% accurate
b. there is something wrong with the screen resolutions (maybe this is what bothered Hardy Heron but worked fine in Drake...my Insignia brand monitor) this means I do not see the first 1 or 2 characters in the left side so I have to guess what it says.

more or less it said (for example "?npfs" means I see "pfs" and it is hard to see what the 1 or 2 characters to the left of "pfs" are, and it looks like it might be "npfs") here it is from my hand-written transcription:

> 
filesystem   size      used      avail     use%     mounted
dev/sda6     26G        7.5G      20G       28%      /
?npfs        624M        0        624M      0%     /lib/init/var
?v?a?rrun     624M      12k       624M      1%     /var/run
?v?arlock     624M      0         624M     0%       /var/lock
?dev         624M      2.7M      621M      1%      /dev     
?npfs        624M       0        624M      0%      /dev/shm (?my handwriting unclear) 
?m           624M      2.7M      621M      1%    /lib/modules/2.6.2716-genetic/volat

but it probably said "volatile" or "voaltive" or something similar,I can see on the next line at the left, what looks like the right-half of the letter "e"


NOTE: when I am where I am now typing to you (which is the boot from 2.6.15-52-386 either recovery or without recovery works, I have discovered)   and if I right-click on a folder I will be told folder contains something (96Kb or something) and then "location: /home/harel/Desktop" and then "volume: /" and "free space: 474.4MB" -- this **same** right-click-on-folder-at-desktop **method** before my system crash (when I was on Hardy Heron on Sunday night) told me I had several gigabytes left!

..so, even if it is counting something a little different than "df" this is where I have seen the dramatic change from before the crash, to the post-crash older (meaning 2.6.15-52-386) boots that are now the only ones that work.

If I guessed correctly in the 1c above and no other problems arise, I can proceed to try the next one "sudo apt-get -f install" per your directions (I printed out your directions from notepad which prints right away but in this boot firefox does not, even though pointing at same printer name..at least I managed with the trick of copy/pasting your directions to notepad, one less sub-sub-problem!)  :-)

---

### Post by harelb on 2009-12-23
Hugmenot, instead of waiting longer I decided to 'cross my fingers' that I am in the correct CLI (as explained in 1c above) and to cross my fingers that I will not do any damage if I am in the wrong one..so just now I tried your steps 2 and 3.

step 2 "sudo apt-get -f"
yielded > "....upgrade 0 newly installed , 0 [can't read my handwriting, I was in a rush to report the error back to you!] 0 not upgraded" and ... at the beginning is probably a 0 but as noted in my previous post my screen in text only mode does not show the left-most 1 or 2 characters.

Not giving up, I tried step 3

step 3: "sudo apt-get update" and got:
> 
.....r [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Could not resolve 'security.ubuntu.com'

[several similar lines not being able to resolve others like 'us.archive.ubuntu.com]

[several 'failed to fetch' lines on the domain names listed]

Some index files failed todownload and have been ignored orold ones used instead

You may want to run apt-get update to correct the problem"

Wow..I typed "sudo apt-get update" and the error message gives me the 'suggestions' that I should run the same command...going in circles..!

I hope again that I am in the correct CLI..as I said in 1c above, sometimes when I boot in safe mode the computer just stops (after "talking to itself" ) and leaves me in the text-only white characters on black screen...and I just hit return and I have the prompt...at other times, like with this second-from-the-top boot option (meaning, the most recent system but in recovery mode) it does not leave me there but instead takes me to a "Recovery Menu" and I chose "*root- drop to root shell prompt" I hope that's the same effect, exactly, a completely identical CLI, I hope? If so, then you can see the errors/problems I got in trying your steps 2 and 3..I hope this is useful information..?

-Harel

P.S. On a side note, when I boot successfully in this old verion (clicking down from boot menu down to 2.6.15-52-386") and it is loading and talking to itself and saying "ok" in the right side, there is one lien that does not say ok, but says "fail" or something, that line looks something like "PCMCIA"...but keep in mind this is with the boot (old old verion, 6.06) that *does* work...

---

### Post by hugmenot on 2009-12-24
Sorry, I spent the whole day yesterday traveling.

> **harelb said:**
> 
this had the options:
*resume normal boot
* clean (if I am reading my handwriting correctly)
* dpkg
*fsck file system check
*root- drop to root shell prompt
* xfix


Actually you could have try some of these. I suspect that they do some of the same things that we told you to do, in much the same order. E.g. "clean" and "dpkg" is probably the apt-get lines we gave you, and "xfix" ist the reconfigure command.
> 
```
filesystem size used avail use% mounted
/dev/sda6 26G 7.5G 20G 28% /
```

This simply means your root partition (called "/") has 20GB free and 7.5G used, i.e., plenty of space.

> 
NOTE: when I am where I am now typing to you (which is the boot from 2.6.15-52-386 either recovery or without recovery works, I have discovered)   and if I right-click on a folder I will be told folder contains something (96Kb or something) and then "location: /home/harel/Desktop" and then "volume: /" and "free space: 474.4MB" -- this **same** right-click-on-folder-at-desktop **method** before my system crash (when I was on Hardy Heron on Sunday night) told me I had several gigabytes left!


Ja, weird. I cannot figure out why. Do you perchance have several (virtually identical) home partitions?

---

### Post by hugmenot on 2009-12-24
> **harelb said:**
> Hugmenot, instead of waiting longer I decided to 'cross my fingers' that I am in the correct CLI (as explained in 1c above) and to cross my fingers that I will not do any damage if I am in the wrong one..so just now I tried your steps 2 and 3.


Yeah sure, since there was no lack of space.

> 
step 2 "sudo apt-get -f"
yielded and ... at the beginning is probably a 0 but as noted in my previous post my screen in text only mode does not show the left-most 1 or 2 characters.


That means there was no problem to fix, i.e., no inconsistency. All good.

> 
Not giving up, I tried step 3

step 3: "sudo apt-get update" and got:

[... apt-get not downloading sources ...]

Wow..I typed "sudo apt-get update" and the error message gives me the 'suggestions' that I should run the same command...going in circles..!


You are not connected to the net at that point. It cannot fetch the updated package list from the server.
> 

P.S. On a side note, when I boot successfully in this old verion (clicking down from boot menu down to 2.6.15-52-386") and it is loading and talking to itself and saying "ok" in the right side, there is one lien that does not say ok, but says "fail" or something, that line looks something like "PCMCIA"...but keep in mind this is with the boot (old old verion, 6.06) that *does* work...


By the way, when you are booting "the old version" you are only booting the old kernel, and not the old Ubuntu version. And since it works with the old kernel and not with the new one I suspect that you only need to fix the NVidia graphics driver.

Go back to the old post and continue from point 5 in that post. Remember to boot the newest Kernel in Recovery Mode.

I need to know what Nvidia driver is/was installed, and then we will proceed to try to re-install it. That should get your graphical desktop working again. While you're there you can try "xfix" menu item, and/or "sudo dpkg-reconfigure xserver-xorg".

---

### Post by harelb on 2009-12-24
I appreciate that you are trying to help me while on your (probably holiday) travels. I am trying to follow your directions. Everything is so slow since this is new but also so slow because I have to hand-write everything I see, and type it again for you to see, instead of copy/paste..how used we all are, to copy/paste! I will number (with primes, to avoid confusion with previous posts) my attempts to act per your directions, so it's easier to follow/reply later:

> You are not connected to the net at that point. It cannot fetch the updated package list from the server

1') That was indeed my conjecture, despite my lack of experience, that was what I assumed. Unfortunately, I have no idea how to fix this; the internet connection works fine otherwise, but when in CLI I have this problem, and therefore, I get the error messges instead of being able to make your step 3 accepted by my computer.

2') "[I have the] old kernel, but not the old ubuntu" I am not sure what exactly this means. I guess kernel is a subset "ubuntu" like  the integers are a subset of the real numbers, so you are saying only that subset is "still the old version" is that what you were saying? I'm not sure what to do with this knowlege but appreciate your information.

3') I do not know about home partitions state..I am not sure. Since memory seems (for now) to be ok, I will just move on to the next things you said

4') Now to the heart of things. I stupidly typed line 6 first...so to fix my mistake I then did step 5 and then did step 6 a second time.

5') for Step 5, "dpkg -l |grep nvidia" I wrote all of this down by hand and am going to try to reproduce it here for you, to the best of my ability without copy/paste..so the output was:
> 
nvidia-173-modaliases    173.14.12-1-0ubuntu5.1
Modaliases for the NVIDIA binary X.org drive

nvidia-177-modaliases    177.82-0ubuntu0.1
Modaliases for the NVIDIA binary X.org drive

nvidia-180-modaliases    180.11--0ubuntu~intrepid1
Modaliases for the NVIDIA binary X.org drive

nvidia-71-modaliases    71.86.04-Oubuntu.10
Modaliases for the NVIDIA binary X.org drive

nvidia-96-modaliases     96.43.09-0ubuntu1.1
Modaliases for the NVIDIA binary X.org drive

nvidia-comon   0.2.4.2
 Find obsolete NVIDIA drivers 
nvidia-kernel-common
NVIDIA binary kernel module  common files 20051028+1+nmu2ubuntu2

I hope that's helpful...this should be almost 100% accurate..given my handwriting and copying by hand there may be a few wrong characters,if you have a specific line, that you want re-checked, and tell me the exact line, I can re-check for 100% accuracy. Or maybe this is all you needed to know...if only there was copy/paste from CLI..!

6') Then I re-did  your step 6, "sudo dpkg-reconfigure  xserver-xorg"
I was as we say in the U.S. "flying blind"...I did not know it would ask me so many questions..I used the default answers and hope that is ok! 

I have so many notes I have lost track of the exact step but at one point in the process, *probably* at the end of 6')?? I got on my screen, and wrote down:

> 
server-xorg postint warning:overwriting possibly-customized  configuration file; backup in /etc/X11/xorg.conf20091224213723

(Please tell me if I have to access/use this back up file, either now, or at any future time later while we try to fix my PC...)

I rebooted to "see if that made it work" but it did not: **still the same error at login screen**. You then said to try "ls -lrt /var/log/gdm/"

Just to be sure: did you mean to go into most-recent-install's-recovery-mode and from there to CLI? That's what I did (I assumed you did not want me to type this  ls command from my "old kernel"which is the only way I am logged in now and the only way I can get my computer to work in graphical mode etc)

From the CLI in question I typed "ls -lrt /var/log/gdm"  and the most recent file was ":0.log" (I initially thought it was "0.log" but got nothing with "more 0.log" so I did "more :0.log" instead which got me some screenful) This screenful started possibly a blank line and then:

Org x server 1.5.2
lease Date: 10 October 2008   [I assume that is "Release Date" but again left most characters are gone]

then some lines I did not write all down, until it told me that (--) means probed and that (**) means from config file etc, so this is just "General information"so I assumed I don't need to write that down..

then near the end it said (maybe I should post this and re-check and then post again) but it said something like:

file /var/.log/xorg.0.log
[some characters on the left] config file /etc/X11/xorg.conf

Well there were no error lines and I thought, "maybe hugmenot does not  need the information in this ':0.log' file...maybe this ':0.log' file is telling me that I should look instead at the other file in the same directory, '/var/log/xorg.0.log' instead! So did a "more" command on this second file, and it was very very long, but I did not see ANY line that started with (EE) for error...only one line had (WW) for warning (I could only see "W)....." but I assume is started "(WW)....") and that line was

WW) CHROME(0): Unable to estimate virtual size

Again: no lines with "EE" found in the ":0.log"file which is the "most recent file that 'ls -lrt /var/log/gdm/' command shows you"

And: no EE lines but one WW line in the file that :0.log mentioned, namely in the /var/log/xorg.0.log file

How are things now? Is there a light at the end of the tunnel as we say in the U.S...an idea what to fix?

I have almost zero experience with this stuff..please keep in mind this is all completely new to me so as much as possible, step by step instructions like "after you use 'sudo dpkg-reconfigure xserver-xorg' it will ask you how to configure your keyboard; say yes to all the default options" is really helpful so I do not make things worse by accident by making mistakes while trying to follow your directions :-)

Thx,
Harel

---

### Post by harelb on 2009-12-24
The smiley was created by ubuntuforums because a : character was followed by an O character.Let me try again with CODE,

```
Server-xorg postint warning :Overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf20091224213723
```

---

### Post by harelb on 2009-12-24
Hi, I rebooted again into revoery mode of the most recent ubuntu and again entered shell/CLI from the "recovery menu" and from there again typed "ls -lrt /va/log/gdm/" and again saw ":0.log" as the most recent file.

Again using "more"on that file I saw the same until the line that explains what (WW) and (EE) mean and then the immediately next lines are:
> 
==) log file: "/var/log/Xorg.0.log" Time:..[I did not type in this detail]
==) using config file: "/etc/X11/xorg.conf"
lfilled via CRI at 7683200
eed 7683200 (post 2)


and that last line (probably "feed" is what the "eed" is) was the very last line ofthe file...

In summary: no EE lines here. Again I looked at /var/log/Xorg.0.log in case that is where I should look instead. Again no lines with "EE" error there. I did see two more WW (warning) lines for a total of three, not one. 

> WW) The Directory "/usr/share/fonts/X11/cyrillic" does not exist
WW) CHROME(0) unable to estimate virtual size
WW) CHROME(0) option "use FBDer" i snot used

the cyrillic is just a font so not important? The others I dont know. But to recap again: no EE lines in either  the file you mentioned, nor in the other file that *it* mentioned, and only WW lines in the second of these, as reproduced above.

Another half-day spent trying to figure out why the "upgrade" from 8.04 to 8.1 went wrong :-( I hope among all this information is enough to fix it. Hope your travels are safe and that all the holidays/traditions that you observe are enjoyable :)

---

### Post by hugmenot on 2009-12-25
> **harelb said:**
> I appreciate that you are trying to help me while on your (probably holiday) travels. I am trying to follow your directions. Everything is so slow since this is new but also so slow because I have to hand-write everything I see, and type it again for you to see, instead of copy/paste..how used we all are, to copy/paste! I will number (with primes, to avoid confusion with previous posts) my attempts to act per your directions, so it's easier to follow/reply later:

Ya, sorry for that. All this fiddling would be immensely easier if you had access to a full system by booting from the Live CD you are still waiting for. This is also why I suggested to make a clean install. And you know, I would say we stop wasting more time like this and focus on getting your files and stuff off the drive and then making a clean install. More on that later.

> 1') That was indeed my conjecture, despite my lack of experience, that was what I assumed. Unfortunately, I have no idea how to fix this; the internet connection works fine otherwise, but when in CLI I have this problem, and therefore, I get the error messges instead of being able to make your step 3 accepted by my computer.

Are you on a wired network connection or wireless? Modem or router?
> 
2') "[I have the] old kernel, but not the old ubuntu" I am not sure what exactly this means. I guess kernel is a subset "ubuntu" like  the integers are a subset of the real numbers, so you are saying only that subset is "still the old version" is that what you were saying? I'm not sure what to do with this knowlege but appreciate your information.

The Linux kernel is the core of the operating system. It manages the hardware, contains the drivers, and runs programs. You can have several versions of the kernel installed at the same time. Since the kernel contains the hardware drivers but not the apps this means that booting another kernel has no effect on the Ubuntu desktop itself, mostly just  on the hardware. But ...
> 
3') I do not know about home partitions state..I am not sure. Since memory seems (for now) to be ok, I will just move on to the next things you said

I have a strong suspicion that you have two separate Linux installs on your hard drive.
When you look at the fdisk output you pasted above you can see two Linux partitions and two Swap partitions. I don&#8217;t know what versions of Ubuntu they belong to, or if they are used at all, but you have two sets of partitions.

The free space quote you gave belongs to the partition number "hda6" or "sda6", but there is a small one at the beginning of the disk called "hda1" or "sda1".

It might be that when you boot the "old Ubuntu version" you /actually do boot/ an old version of Ubuntu, that resides in the smaller partition.

> 4') Now to the heart of things. I stupidly typed line 6 first...so to fix my mistake I then did step 5 and then did step 6 a second time.

5') for Step 5, "dpkg -l |grep nvidia" I wrote all of this down by hand and am going to try to reproduce it here for you, to the best of my ability without copy/paste..so the output was:


From there what you found out was not that helpful. It appears you have no Nvidia driver installed. You only had stubs for the different versions, which Ubuntu installs by default to be able to retrieve one of them later.

The digging in the log files didn&#8217;t reveal anything useful.

This is what you should do.
[LIST=1][*]Wait for the Live CD for Ubuntu 9.10.[*]Have an external USB drive ready that you can copy your stuff off to.[*]Boot from the Live CD[*]Secure your stuff before installing on the external drive[*]Use the "Install Ubuntu" icon and choose the "use entire drive" option





[/LIST]

---

### Post by hugmenot on 2009-12-25
> **harelb said:**
> Another half-day spent trying to figure out why the "upgrade" from 8.04 to 8.1 went wrong :-( I hope among all this information is enough to fix it. Hope your travels are safe and that all the holidays/traditions that you observe are enjoyable :)

The traditions are certainly very nourishing ... Unfortunately the weather is too bad to go on extended walks in the countryside, what I usually do.

Let&#8217;s just stop with the command line business. I&#8217;m sure you will find that a fresh install makes all good again, with minimal effort. Just make that beackup before you start.

---

### Post by harelb on 2009-12-25
I have DSL..a simple Westell 6100F modem with it. Even "puppy linux" (which I spent timejust to burn on disk and try for a half hour) audomatically detected my internet connection (and mouse..but keyboard has some letters not work) but CLI apparently can't find the connection? :-(

This is a computer I got at walmart.com which has Xandros installed on it by the manufacturer, but I really didn't like Xandros so eventually a friend put Unbutu on it for me (that must have been Drake..I was too new to it to be able to follow what steps they used or how..)

Then, in summer 2008 I upgraded from Drake to 8.04 Hardy but one thing didn't work as I describe before..that's all the history I know as far as disk goes.

I'll reply separately to the other parts.

---

### Post by harelb on 2009-12-25
That should say "**had** Xandros" not "has"...not after replacing it with Ubuntu in 2007 or so...

---

### Post by harelb on 2009-12-25
Sorry to hear about the bad weather, I hope it was not too bad. On the main points..

* I guess "clean install" means, according to one internet page, "(1) To install an upgrade of an operating system (OS) on a hard drive that already has an OS running off of it without carrying over any settings of the older OS, such as user preferences or information about the hardware and/or the software. (2) To install an OS on a hard drive that does not already have an OS installed on it or a newly formatted hard drive"

while,

* A "live CD" has an OS -- a bootable OS  on it 

I guess the two are connected because if you have an OS on your CD ("live CD") then you can "install an upgrade of an OS on a hard drive" The terminology seems less than ideal but I am getting used to it slowly. I have known the basics of what a linux for many years, so am a bit embarrassed to know so little here, but the truth is, I've been busy with work and personal life and my style has been "learn only what I need to learn" which has meant text-only emacs (more years than I want to admit) and a handful of shell commands, and maybe 3 ubuntu commands, like synaptic, and nothing else! In 12 or 24 months if another problem occurs, I will probably say "I think I remember what a live CD is, but let me re-check just to be 100% sure" because I'll think nothing about it in the meantime! On a serious issue, I have two CDs coming my way:
> 
*i.     Ubuntu 9.10 - Alternate Install CD (PC)
*ii.   Ubuntu 9.10 - Install/Live CD (PC)

I should use the second one? What is the first one for?

Now to my main quesetions while I wait for the CDs:

> 1 Wait for the Live CD for Ubuntu 9.10.
2 Have an external USB drive ready that you can copy your stuff off to.
3 Boot from the Live CD
4 Secure your stuff before installing on the external drive
5 Use the "Install Ubuntu" icon and choose the "use entire drive" option


Thanks for your explaining the choices for step 5. For step 4, my questions are: 

1. will I be able to find the files I had on my computer before Sunday night? I do not have anything valuable from Dec 20 to Dec 25. 

2. If I can "secure my stuff" from before Dec 20, how, where do I find those?

3.Instead of buying a flash drive I could ftp the files to my shell account I guess. I have a shell account with dreamhost.com -- and then ftp back to my desktop when I am done (some other time I can buy and learn to use flashdrive...I would really like to learn to use Puppy Linux which another person here said can fit into RAM..so I can take out the CD and burn on to disk, he said...I did install it and internet and mouse and browser work but the keyboard does't work... the "a" when pressed always creates "a-" instead and the backspace works only half the time..strange) I suppose I should not be 'lazy', and flash drives are supposed to be both cheap and easy to use..just "shove" it in the back of my computer I guess.. (although everything new that I have tried, this week,  has ended up having something fail) so I guess I may use *either* flash *or* the "ftp trick" above if you don't see any problem with it...the key thing is to know if I can find and where to find my before-December-20 files..the rest I can find a way to save copies..

Then I hope step 5 is also ok..IF you can let me know about the above two main questions, I will cross my fingers and hope that is enough until, and after, the CDs arrive in the mail, which should be soon. Thank,
Harel

---

### Post by hugmenot on 2009-12-26
> **harelb said:**
> * I guess "clean install" means, according to one internet page, "(1) To install an upgrade of an operating system (OS) on a hard drive that already has an OS running off of it without carrying over any settings of the older OS, such as user preferences or information about the hardware and/or the software. (2) To install an OS on a hard drive that does not already have an OS installed on it or a newly formatted hard drive"

1. Yes, 2. Yeah

You&#8217;ll just copy off your files beforehand and then copy them back afterwards.
> 

while,

* A "live CD" has an OS -- a bootable OS  on it 

I guess the two are connected because if you have an OS on your CD ("live CD") then you can "install an upgrade of an OS on a hard drive" The terminology seems less than ideal but I am getting used to it slowly

[...snip...]

 I have two CDs coming my way:
```
*i. Ubuntu 9.10 - Alternate Install CD (PC)
*ii. Ubuntu 9.10 - Install/Live CD (PC)
```
I should use the second one? What is the first one for?

The Alternate CD has only an installer on it and it has only a basically text-based, so-called &#8220;curses&#8221; GUI in it. For example the partitioning wizard [looks like this]("http://www.kabatology.com/wp-content/uploads/2009/04/partition_disk.png"). It also has some advanced options that the installer on the Live CD doesn&#8217;t offer, like advanced partitioning with LVM, or whole-disk encryption.

The Live CD boots a complete graphical Desktop from the CD, i.e., you get a live system, without writing anything to the hard drive. It just extracts itself into a ram-drive. When you switch the computer off, it leaves to traces. You can use this to test Ubuntu before installing, but also to repair your system. And finally it also has an installer, which [looks like this (here, partitioning)]("http://www.dedoimedo.com/images/computers_new_1/ubuntu-install-partitioning.jpg"). I suggest using the Live CD because you could use the booted desktop to backup your file before running the installer. But you can also do that via Puppy Linux. More on that below.
> 
1. will I be able to find the files I had on my computer before Sunday night? I do not have anything valuable from Dec 20 to Dec 25.

Yes, everything will be in your home directory. Even the newer files. I don&#8217;t know what is in the two partitions you have. Better check both. Theres sda1 and sda6.
> 
2. If I can "secure my stuff" from before Dec 20, how, where do I find those?

As long you only stored things inside your home directory it will be as easy as copying everything under [FONT="Monospace"]/home[/FONT]. All program settings and all files you created are in there. You have two Linux partitions, better look at both to see where your stuff is. If you made some customizations outside of your home folder, then try to remember which and copy those too.

Now, if you want to save to a CD it is necessary to make a .tar.gz archive and burning that to CD because the CD file system does not store permissions on the files. The .tar.gz is like a .zip, but it holds all file meta information.

To create a tarball of your old [FONT="monospace"]/home[/FONT], you can use this command when you have a booted system:
```
cd <your mounted drive>
sudo tar czf home-backup.tar.gz home
```

It is important to note that the path for [font="monospace"]home[/font] will be different when you boot from a CD. On Ubuntu it might be [FONT="monospace"]/media/disk/home or /media/many-alphanumeric-characters/home[/FONT]. I don&#8217;t know where Puppy will mount your drives when you boot it.

Alternatively you can also use the Archive Manager program for this. I just gave this one-liner because it is easier to describe.
> 
3.Instead of buying a flash drive I could ftp the files to my shell account I guess. I have a shell account with dreamhost.com -- and then ftp back to my desktop when I am done (some other time I can buy and learn to use flashdrive...I would really like to learn to use Puppy Linux which another person here said can fit into RAM..so I can take out the CD and burn on to disk, he said...I did install it and internet and mouse and browser work but the keyboard does't work... the "a" when pressed always creates "a-" instead and the backspace works only half the time..strange) I suppose I should not be 'lazy', and flash drives are supposed to be both cheap and easy to use..just "shove" it in the back of my computer I guess.. (although everything new that I have tried, this week,  has ended up having something fail) so I guess I may use *either* flash *or* the "ftp trick" above if you don't see any problem with it...the key thing is to know if I can find and where to find my before-December-20 files..the rest I can find a way to save copies..

You could FTP the tarball you made to your host, yes. But it depends on how big it is. Do you have a lot of stuff in there? Is it gigabytes worth? Before you make this tarball you can check how big your home directory is with this command from the top of the mounted hard drive partition.
```
du -sh home/*
```

Alternatively, use the Disk Usage Analyzer in the Applications &#8594; Accesories menu. If you have large files in your home folder, then uploading via FTP can take days.
> 
Then I hope step 5 is also ok..IF you can let me know about the above two main questions, I will cross my fingers and hope that is enough until, and after, the CDs arrive in the mail, which should be soon. Thank,
Harel

One last thing, I always do is keep my /home on a separate partition. That way you can clean install a new system without losing /home. It will just not be overwritten. You can do this with the manual option of the partitioning step of the Live CD installer.

---

### Post by harelb on 2009-12-26
Ok, I will use the live CD only (don't worry about Puppy Linux, I will not use it for this project).

> As long you only stored things inside your home directory it will be as easy as copying everything under /home.

99% or 100% of what I need were on the desktop (or in folders in folders on the desktop) so I only need items from /home/Desktop, yes. 

> It is important to note that the path for home will be different when you boot from a CD. On Ubuntu it might be /media/disk/home or /media/many-alphanumeric-characters/home. I don&#8217;t know where Puppy will mount your drives when you boot it.

Is your comment only about Puppy? If so I can ignore it since I will use the live CD which will arrive by mail(ubuntu9.10),and will not use the puppylinux-CD, at least not for this fix. 

If on the other hand your comment is more general, then I guess I should look in such directories even with the Ubuntu 9.10 live CD
> 
Yes, everything will be in your home directory. Even the newer files. I don&#8217;t know what is in the two partitions you have. Better check both. Theres sda1 and sda6.

This is the part I least understand, since I have no experience with partitions (except a few times watching someone work on them and not understanding/following/remembering what they did..) So you're saying I need to look at 

sda1---> and tfrom there, the "home" directory
and 
sda6 --->and from there, the "home" directory
and maybe any other ones. My question is how do I choose which partition? Or will the ubuntu9.10-live-CD be very very clear, saying something like (in addition to the "install ubuntu" icon) in another icon or choice, "explore the hard drive" or something, and then will it show me all partitions?and then I can choose the partition, and then, choose directory? If so, then I can copy a .tar.gz but if this is not exactly how it will be, then I'd appreciate any clarifications :-)

(Also to make my life simpler, I'll either get a flash or even simpler, I'll just NOT recover my legal music files (legal free from kahvi.org, mostly) this means I can worry only about the text files, which are the most important, and also are the very, very smallest, so that makes life much simpler and easier to grab and 'save' them before installing the new 9.10 ubuntu..) 

I appreciate also your last sentence/paragraph, which would be something to do instead of your earlier, "use entire drive" suggstion (if I followed you) but I think I will wait until I see the liveCD and decide if I am 100% sure of what I am doing (so I don't screw something up) before thinking about whether to do this.

So, consequently, the most important questions I have really are the above ones about how to find the partitions from which to find all my important (mostly text) files from my "old (before 12/20/09) desktop"..if I can have a clarification on that, and if my live CD arrives, then I am hopefully almost at the end of the journey.. :-) Thx
Harel

---

### Post by JKyleOKC on 2009-12-26
> **harelb said:**
> This is the part I least understand, since I have no experience with partitions (except a few times watching someone work on them and not understanding/following/remembering what they did..)Think of your hard drive as a big box that has a number of smaller boxes in it (the partitions). Its name is "sda" and the file system addresses it as "/dev/sda" without a number. The partitions are numbered: sda1 and so on, and addressed as "/dev/sda1" et cetera.

The letters (a, b, c, d) are assigned according to the connectors on the motherboard and the numbers according to the sequence of entries in the drive's partition table (an area at the start of the drive that tells where the data is located). This table has room for only four entries, which will be sda1 through sda4. To get more partitions, one of the four has to be an "extended" partition, which is another box full of partitions such as your sda5, 6, 7, and 8. You don't need to worry about these because the partition manager will take care of the details.

To access the contents of a partition, it has to be mounted. The file manager of the live CD normally does this for you, so that you can click on the partition's icon and see the list of directories it contains. One of them will be "home" and inside that directory will be at least one more, bearing your user name. That inner directory is the one you want to back up.

If the file manager does not show you icons for the partitions, you'll need to "mount" them to gain access. However let's not try to cross that bridge until it becomes necessary, since it can be a bit confusing at first! Tools are available to simplify it, fortunately.

With a little experience you'll find this stuff much easier to get along with; it's all pretty logical, just different from the systems that you're used to!

---

### Post by hugmenot on 2009-12-26
> **harelb said:**
> If on the other hand your comment is more general, then I guess I should look in such directories even with the Ubuntu 9.10 live CD

Just boot hte Live CD, and open the &#8221;Computer&#8220; thing in the &#8220;Places&#8221; menu. There will be drives listed. These are you partitions. Have a look around and inspect them for the &#8222;home&#8220; folder. I guess you can tell where your files are.

Then you proceed to make a tarball and put your home directory in it. If you have one system user, then &#8220;home&#8221; will contain one subfolder. 

> 
(Also to make my life simpler, I'll either get a flash or even simpler, I'll just NOT recover my legal music files (legal free from kahvi.org, mostly) this means I can worry only about the text files, which are the most important, and also are the very, very smallest, so that makes life much simpler and easier to grab and 'save' them before installing the new 9.10 ubuntu..) 


You can also put your home folder into a .tar.gz tarball and exclude the big files while compressing. This should fit onto a CD (perhaps you even burn a DVD-R? More capacity). Then you can put in another CD and just burn the MP3s off. Permissions are not that important on music files.

On the command line this could be achieved like this:
(the precise paths are just examples, you have to look and see)

Excluding by file extension
```
cd /media/disk/home
tar czf  home-backup.tar.gz --exclude="*.mp3"  "harel"
```
or by path
```
cd /media/disk/home
tar czf  home-backup.tar.gz --exclude="harel/Music"  --exclude="harel/Videos" "harel"
```

tar czf means, 

c = create
z = gzip compressed
f = in file xyz.tar.gz

> I appreciate also your last sentence/paragraph, which would be something to do instead of your earlier, "use entire drive" suggstion (if I followed you) but I think I will wait until I see the liveCD and decide if I am 100% sure of what I am doing (so I don't screw something up) before thinking about whether to do this.

So, consequently, the most important questions I have really are the above ones about how to find the partitions from which to find all my important (mostly text) files from my "old (before 12/20/09) desktop"..if I can have a clarification on that, and if my live CD arrives, then I am hopefully almost at the end of the journey.. :-) Thx
Harel

If you want to create a separate partition for /home then you should assign the largest space to it. For the system files under "/" (aka, the root directory) it suffices to assign about 10GB. The rest can go into /home, where the bulk of your files go.

---

### Post by harelb on 2010-01-02
Thanks for all the tips, everyone. I got my "live CD" today-- it took  OSDisc.com 7 business days to deliver this even though I paid extra for priority which they said would be, as I recall, "2 to 4 business days". Oh well.

I also got a flash drive 8GB and saved some files from the 2.6.15-52-386 desktop (which contains things from Summer 2008 and older), the one I'm logged in from...but the BIG test will be whether the live CD lets me get into the right area/partition to find the more recent files, and to save those.

If I can do that, I'll try to install the new OS with the Live CD (since I have the flash drive I will, probably, decide to skip the more complicated work to create separate partitions) let me see if I can do at least the finding and saving of the more recent files tonight and will report back here if I can...crossing my fingers.. :-)

---

### Post by harelb on 2010-01-02
By the way I am no so sure Hugmenot that the different "desktops" are all the same except for the kernel because, on this old "Desktop" (booting the "2.6.15-52-386") flash does not have the most recent edition and can't play videos..before my late december problem when trying to upgrade from 8.04 to 8.1 and having the mess happen, I was able to...so there is also different software..I suspect you knew this but I misunderstood what you mean by "only the kernel is different" to mean same things installed..obviously not the same desktop files (or I would not need the flash drive etc) but also not the same (e.g. Adobe) software either.ok time to try out the Live CD..

---

### Post by harelb on 2010-01-03
Update: it's mostly worked...and I've copied almost all the files to the flash drive...except during the copying there were a few errors..the main one: .pdf files..turns out (when you click on expanding to show 'details') that it was a permission problem. To properly copy these files into the flash drive, I need to solve two problems

1) to use chmod I need a terminal..actually this is one area I may know more from terminal than gui..I need to use a command I learned from someone:

find . -name "*pdf" -print

to find all the pdf files (which are all in one sub-folder's subfolers)

and then from terminal to use chmod..only problem is: when I go to "Application" and then "accessories" and then "Terminal" the terminal I get is not in the right area..there are three "areas" (partitions??) two of them correspond to the partitions; if I go to "places" and then "computer"  it shows:

40GB Hard Disk: 31 GB file system

and

40 GB hard disk: /

and

Filesystem

(There are two other icons, but they come from the flash drive being plugged in so I'll ignore them)

The third one is where you have the files for installing the 9.1 new ubuntu..the other two are my "old" and "newer" files...the "40GB Hard Disk: 31 GB file system"is where all my recent files were which I copied (except for some pdf files..silly PDF!)

but if I go "accessories" --> terminal as I said above, I get to the third place..but not the place I want..which is the partition with the newer files..how do I get a terminal to 'be' in that place? Once I know that, I will go there, then  I will "cd /home/Desktop/harel/" and from there to the subdirectory with the pdf files, and will change their permissions, and then (I hope) be able to copy to my flash drive...

2) 2nd question, just to be sure...the Live CD never asked me for a superuser password...I take it one of the two I've been using (each of the above partitions has one, it would seem) is the right one?

If I can figure out these steps my backing up of my recent (just before my mishap) to my flashdrive will be done at last, then I can install the new 9.1 ubuntu and have the troubles (for now anyway) behind me...I'll check tomorrow for these last clarifications..? Thanks,
Harel

---

### Post by hugmenot on 2010-01-03
harel, sorry for delay, I&#8217;m staying with friends for a couple of days.

Are you still just using the Live CD and are just exploring the hard disk and the old installation? I&#8217;m not sure I completely understand what you are looking at.

Two things,

when you are in the terminal while using the Live CD you cannot just cd into folders like
/home/harel/Desktop with a slash directly in front. The CD has it own file system and the slash in front refers to places on the Live system. For example /home contains only "ubuntu" (the live CD user) and not "harel".

What you need to do is to mount the internal partitions first. You can do it by double clicking them in the file manager&#8217;s »Computer« view. Take note of the path that the internal hard drives partitions are mounted to. The mount point names are more or less artbitrary. 

You should look at 

```
/media/*/home
```

after mounting all the internal drive&#8217;s partitions.

Second, you don&#8217;t need a superuser password while using the Live CD because there is no protection on your files against being used in another operating system. And the CD is another operating system in that sense.


Lastly, you can chmod all pdf files using the »find« utility itself. E.g., like this:

```
find /media/xyz/home/harel -iname *.pdf -exec chmod +r {} \;
```

[-iname is case insensitive. It may be that some files are called *.PDF]

Can you post a screenshot of the »Computer« view. And maybe also a screenshot of a gparted window?

---

### Post by harelb on 2010-01-03
> **hugmenot said:**
> harel, sorry for delay, I’m staying with friends for a couple of days.

Are you still just using the Live CD and are just exploring the hard disk and the old installation? 

yes

> when you are in the terminal while using the Live CD you cannot just cd into folders like
/home/harel/Desktop with a slash directly in front. The CD has it own file system and the slash in front refers to places on the Live system. For example /home contains only "ubuntu" (the live CD user) and not "harel".

That's what I discovered last night but was not sure how to get into the right partition

> What you need to do is to mount the internal partitions first. You can do it by double clicking them in the file manager’s »Computer« view. Take note of the path that the internal hard drives partitions are mounted to. The mount point names are more or less artbitrary. 

You should look at 

```
/media/*/home
```

after mounting all the internal drive’s partitions.

unfortunately when I went into filemanager's computer view everythign is in GUI so it did not give me the directory names.

Then I realized on my own to try to right-click on a file name and see "properties" and that worked!

the partition I want turned out to be

/media/[huge huge huge name]/

and the old partition with the older files was invisible (it looked like there was only ONE place under media) because "ls" by default does not show certain files with certain names like "_" but the other partition was at

/media/_/

also the chmod did not work:

"chmod: changing permissions of `ChinaStudy_Excerpt.pdf': Operation not permitted"

However I decided to try with "sudo" and did 

"sudo * g+r" after "cd" into the right area, and that WORKED without asking me for password (as "ls -l" revealed) so this seems to be working.

Unfortunately there are now I see 150 or so pdf files so I need to try a few more places visually to check which ones were copied and which one were not..but I think in 30 or 45 minutes I should be done and back here to report if/that it all worked (copying to my flash drive)

Luckily I was able to solve this part on my own so did not need to take a picture, but if you wish to tell me for future reference how to take pictures most easily from my setup, that would be good. Also thank you for info re "-iname" I will try to fix the rest of the
pdf files -----> flash drive after fixing permissions, next..

---

### Post by harelb on 2010-01-03
The directory btw, was

/media/ac15e899-08dc-4d1f-9221-1814ade4a2a8/home/

anyway, looks like I got the files copied over to the flash drive...so tomorrow (Monday) I will try to use the Live CD to install 9.1 and if that works, then copy the files from flash drive to my new and improved Ubuntu :-)

ACTUALLY LET ME try your:
```

This is what you should do.

   1. Wait for the Live CD for Ubuntu 9.10.
   2. Have an external USB drive ready that you can copy your stuff off to.
   3. Boot from the Live CD
   4. Secure your stuff before installing on the external drive
   5. Use the "Install Ubuntu" icon and choose the "use entire drive" option
``` tonight if it doesn't take too long :o)

---

### Post by harelb on 2010-01-04
Good news and bad/depressing news: the good news is I seem to have installed 9.1 successfully.

The bad/depressing news is that the MAIN reason for upgrading from 8.04 to 8.1 (and now to 9.1) was the screen resolution and I hoped this would be fixed but it is still here. (Ok, it was not the main long-term reason; I know there are other reasons to upgrade to 9.1 but it was the main immediate/short-term reason)

As you can see at

[http://ubuntuforums.org/showthread.php?t=856642](http://ubuntuforums.org/showthread.php?t=856642)

several pages of people trying to help fix my problem but without any success, back in July of 2008 when I upgraded from 6.06.1 (where my screen resolution worked *perfectly*) to 8.04 where the resolution didn't work...and none of the suggestions worked which I got at the above url...

I just tried system-->preferences-->display now and that did not seem to help; again only 800x600 and 640x480 are the only two options for my "unknow" type monitor; "detect monitors" does not do anything when clicked, etc.

I can try other methods but I would ask people to look at the above thread to see if those have not already been previously tried (of course, it is possible that what didn't work for 8.04 will work for 9.10..but it is alarming that the fresh-clean-install-from-Live-CD itself started on the 'wrong foot' yet again...this is from-scratch install of 9.1 and again same or similar problems...(I suspected this would happen since even the Dialog Boxes during the install, in the one about partitions, the dialoge box was so "big"that I could not see the bottom of it and needed to remember that the left button was Quit, then Back then Forward since I could only see the tops of those three buttons in the right-half of the bottom of the Dialog Box during the install)

Help..??   > :-(

---

### Post by CharlesA on 2010-01-04
Are you running an onboard intel card? If so what model.

---

### Post by hugmenot on 2010-01-04
Let&#8217;s take a minute, a deep breath, and celebrate our partial victory first.

Now, to make screenshots just press PrintScr on your keyboard for the whole desktop and Alt-PrintScr for a shot of the active window.

Next, forget the graphical display configurator. It operates on information it gets from the display. In the olden, *painful* days of XFree86 you had to manually calculate and figure out the modes that the monitor supports in terms of frequencies and resolutions. Later on manufacturers would encode this into the device and make it available to the computer via something called DDC or EDID.

Your monitor seems to be crap, so from what I gather you have to somehow try to find the magical working modeline.

I remember when I did that on a lab machine in 2003 to get a CRT to run at 1400x1050. It took a while to get it to work. Back then there also was a [semi-graphical tool]("http://tuxicity.files.wordpress.com/2006/12/screenshot-terminal-5.png") called by dpkg-reconfigure -plow xserver-xorg. It seems to not be available anymore.

I pretty much used the method that [Pettman in the other thread proposed]("http://ubuntuforums.org/showpost.php?p=5405663&postcount=28"), just all inside xorg.conf. His method allows you to play in the running X server without restarting X all the time. 

So, I would continue like this. Try the things Pettman mentioned, maybe search Google, post your results.

Also definitely post your /var/log/Xorg.0.log as an attachment below. We need to establish what goes on, and what your exact hardware is.

---

### Post by hugmenot on 2010-01-04
Here&#8217;s another, similar walk-through from Ubuntu wiki:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by hugmenot on 2010-01-04
Here&#8217;s an interesting bug report in Launchpad:
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/471180](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/471180)

Try and post the information that Bryce asks for in comment #2


Here&#8217;s another similar wiki link :
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)


Finally, we can post a bug of our own if all fails by using this terminal command

```
  ubuntu-bug xorg
```

This will gather important info from the system and submit it all to a new bug. What you have is a regression, since it used to work. This is unfortunate and regressions usually receive more attention.

---

### Post by harelb on 2010-01-04
Charles - I have no idea what an 'onboard intel card' is.

Hugmenot - I appreciate all your help, and am trying to keep a 'celebrate the partial victory' in mind, but it is very frustrating; it's hard to celebrate since I fear things will be worse under 9.1 than they were under 8.04; after all, Ubuntu 6 understood my monitor perfectly, and when I "upgraded" to 8.04 in summer 08 suddenly my monitor didn't work correctly, so badly that for some software (like the LeechBlock plug in) the dialog boxes are so 'big' that I cannot see or press buttons) (here in Firefox  I can get around it so long as I don't have dialog boxes, by using control-(minus-sign) )

I do not believe that my monitor is "crap"

I purchased it at the beginning of 2007 at Best Buy and it is not a CRT.  It is an Insignia  15" LCD TV that again, worked perfecly for Ubuntu 6

Before trying to understand all your links, let me share with you in case it is helpful, the Specifications since I have the manual for the Insignia in front of me: Display type: "Color TFT LCD" pixel type "RGB stripe" Active screen size "15 inches dianogal" Maximum resolutoin "1024x768" (recall that ubuntu 9.0 it will not let me use any larger than 600 by 800 at the moment from the place I tried) 

So this is a relatively up-to-date monitor, not crap/obsolete, as far as I can tell. I just learned how to attach here and just **attached Xorg.0.log below**

I'm not sure which of the several methods you listed I should try first. I have a hard time understanding some of Pettman's suggestions, however, I did understand the beginning and typing "xrandr" from a terminal shell, I got the display below, which seems to say that X *thinks* that 600 by 800 is the max resolution which traces the root of the problem to X itself then? The code:

```
harel@harel-desktop:/var/log$ xrandr

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  

```

Of course I know that is not the real maximum screen resolution both because (a) of the manual in front of me stating 1024x768 and (b) that back when I used version 6 of Ubuntu (Drake, I think it was called) the resolution was perfect and allowed larger resolutions

As for Bryce's suggestions, when I type "xrandr --verbose > xrandr.txt" I get "bash: xrandr.txt: Permission denied" so things are still behaving strangely with needing sudo perhaps? No wait, I just needed to "cd" back into my home directory. Ok, I am now attaching "xrandr.txt" in case the above xrandr code isn't enough.Done. Except now I cannot see the first attachment file listed any more so let me post this and see if something happened to it.Wait, I see the problem, in the manage attachment dialog box under the top red font letters saying "Manage attachments" it says [b]"Upload errors" when it is done trying to upload  and says below that, ```
Xorg.0.log:
Invalid File 
``` It just did it again[/b] yet I can see it as a 46k file and even viewed it in gedit without any problems

Next, I tried "sudo ddcprobe > ddcprobe.txt" but got:"sudo: ddcprobe: command not found"

Finally,```
sudo get-edid|parse-edid > edid.txt
sudo: get-edid: command not found
The program 'parse-edid' is currently not installed.  You can install it by typing:
sudo apt-get install read-edid
parse-edid: command not found
```

I did "sudo apt-get install read-edid" and now trying again, got this complex answer:

```
harel@harel-desktop:~$ sudo get-edid|parse-edid > edid.txt
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0xc61a9 "VIA K8M800
"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
harel@harel-desktop:~$ 
```

I now finally tried to upload "edid.txt" but see it is listed as "0 bytes" so am not trying to upload that. Between all the above information and my manual "specifications" is this enough info?

[b]Added later in edit:```
harel@harel-desktop:~$ cd /var/log
harel@harel-desktop:/var/log$ ls -l *org*
-rw-r--r-- 1 root root 47141 2010-01-04 14:00 Xorg.0.log
-rw-r--r-- 1 root root 56851 2010-01-04 13:54 Xorg.0.log.old
```
is the file that gets error when I try to upload..it's not b/c of the root ownership is it? I thought root ownership is normal for such files[/b]

Also added in edit: since the upload to ubuntuforums.org for some reason keeps getting an error, I used ftp to put a copy of the file here:
 [http://barzilai.org/ubuntu/Xorg.0.log](http://barzilai.org/ubuntu/Xorg.0.log)
No idea why the uplaod error, but I hope the above helps so you can view this .log file. Hmmm, those lines starting with " CHROME(0): Not using default mode ....." seem to be part of the problem?

---

### Post by hugmenot on 2010-01-05
I like your &#8220;stream-of-consciousness&#8221; style post.

Harel, I said it is crap because of this

```

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
```

If they sell a monitor in 2007 that does not report the resolutions that it supports back to the computer, then it is crap because it makes you put up with the mess you are in now.

Nowadays monitors are supposed to be plug and play.

From you Xorg.log I can see that you have an integrated VIA graphics chip. Not a dedicated graphics card, a low-cost chip on the mainboard. And VIA is known for causing headaches in Linux

Then you can see this:
```
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
[...]
(II) CHROME(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
```

The monitor is not indentified, so Xorg uses a default config, i.e., 800x600.

Then you can see the VIA chip tries out all kinds of modes (or resolutions) and then we see this:

```
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
```

It doesn&#8217;t think it works using 1024x768. 

I offer you two options. You can read and try to understand the links I sent you above. Then proceed to try and find a modeline that works with your combination of VIA and BEst Buy monitor.

Or you open a bug in Launchpad as described above and point out that it used to work.

Since I&#8217;m not in front of your computer to do it for you and I have urgent things to do in the coming weeks I&#8217;ll have to leave you at that.

Good luck.

---

### Post by harelb on 2010-01-05
Hugmenot,
Firstly, I thank you and applaud you for taking all this time on this thread. You are my hero for all your efforts here.

Second, if I sounded too much "down" then please understand that it has been not only my own frustration, but also, secondly, that my long time support for linux has made this a heartbreaking episode..yes, really..I have recommended linux to others for years and I will still recommend it for the 98% of the time one is just using firefox, ssh, ftp, etc..for upgrades from a Live CD, it's hard to see how I can safely recommend it now, which is heartbreaking. If a friend asks me, I will have to say that with a 2007 monitor and a live CD, and even if the monitor worked perfectly with ubuntu 6, it may still not work with ubuntu 9.X...I know my friends would ask me, how could they not have it work in 9.X when it used to work in ubuntu 6 (in fact in my earlier posts on this thread, where I booted with this earlier version, the screen resolution was correct, and higher than 600x800..the screen resolution under Drake was *perfect* and a pleasure to use..maybe I should have stayed at version 6 of ubuntu and never upgraaed). I hope I am not considered less loyal to linux for saying this..those are the facts of my experience..and I consider myself a friend of linux both in spirit, and consider myself to be helping the linux cause for pointing out this discrepancy.

Also, I was confused and not sure if you were deliberately trying to give a stream of consciousness yourself, in posts 45, 46, 47, in other words, I wasn't sure if the latter posts were "in addition to" or "instead of" the preceding posts of yours, sorry for my confusion, I now undestand you better so I will indeed use "  ubuntu-bug xorg" and secondly, I will look at the launchpad and try to understand it as well how to "open a bug" on that site. The other urls you posted, I am afraid, are above my head and would require a second  10 hours on my part to try to understand. After the 10 hours so far I am going to try your two bug reports, and probably otherwise surrender (until I'm ready to buy a new monitor or switch to another distro...except other than this mess I love ubuntu too much) Thanks again for all  your time and effort, peace,
Harel

---

### Post by harelb on 2010-01-05
Charles, thanks to you too. I didn't mean to be short with you in my reply; I was not just exchausted, but a little bit overwhelmed, at the time, with the number of different directions being suggested for solving or investigating this..So thanks for your efforts too.

---

### Post by harelb on 2010-01-06
Reported it here:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/503674](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/503674)

which is now being autoforwarded to what I gather must be the bug report's more permanent home, here:

```
https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/503674
```
(used "code" to display this 2nd url since otherwise it wants to display it as identical to the first above)

---

### Post by harelb on 2010-01-14
The problem seems to be SOLVED as of and using the methods described in, item #19 here

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/503674](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/503674)

Unless I'm told there is a problem with the current fix, I'll stick with it (for my own case) and hope the folks behind the next update of Ubuntu will save someone else the trouble by having whatever it was that worked in Dapper, incorporated for Koala and future editions so that if a monitor was ok in Dapper, it will be ok for future editions without the fix I put in (they might have to do nothing other than automatically put in the xorg.conf with the line described in #19 in the link above)

After so many weeks and months I am crossing my fingers this latest doesn't blow up in my face either :-) But so far it's working...I'm back in 1024x768 resolution :-)

---

