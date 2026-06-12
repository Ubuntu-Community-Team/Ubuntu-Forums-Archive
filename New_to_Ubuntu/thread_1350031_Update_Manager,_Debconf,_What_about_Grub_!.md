---
title: "Update Manager, Debconf, What about Grub ?!"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Ronok on 2009-12-08
Hi,
Just Now when I started my computer:
100% ubuntu 9.1 
the following happened:

1) automatic **Update Manager** started
2) then a window poped up called "**Debconf on (**[SIZE="1"]your computer name here[/SIZE]**)**"
---it says "**Configuring Grub-pc**"
------and it asks: "What would you like to do about Grub?"

( [SIZE="1"]there is a drop down menu with:[/SIZE] )

-->  install the package maintainer's version
-->  keep the local version currently installed
-->  show the differences between the versions
-->  show a side-by-side difference between the versions
-->  show a 3-way difference between available versions
-->  do a 3-way merge between available versions (experimental)
-->  start a new shell to examine the situation

(help button) = "A new version of configuration file /etc/default/grub
is available, but the version installed currently has been locally modified."

(Cancel button),  (Forward button)
__________________________________

I have **No Clue** what to choose, unclear what _Repercussions_ and 
_the Update Manager is waiting !_
I am an Ubuntu _Fan_, and _Advocate_, But
This Window, Update & Language is **NOT clear** to:
the _non_ programmer, that is 99% the human population, that is the grater public market

...I think I want the _newest_ & _best_ Ubuntu has... so ?
[SIZE="1"]this Laptop was a "New instal from downloaded .iso/CD on Nov 2009
Ubuntu 9.10 (karmic)
GNOME: 2.28.1
Kernel: 2.6.31-16-generic
Intel(R) Atom(TM) CPU N280 @ 1.66GHz[/SIZE]


not sure what is the next step
Thanks for your Help
Ronok     
[[SIZE="1"]http://www.gongkuo.com/index.htm[/SIZE]]("http://www.gongkuo.com/index.htm")

---

### Post by mikewhatever on 2009-12-08
This is a very odd message I've been getting with Jaunty on every kernel upgrade or GRUB upgrade. Basically, the system is asking whether or not to modify GRUB's configuration file, /etc/default/grub. I think it's best to select the second option, which will leave the configuration file unmodified.

---

### Post by Ronok on 2009-12-09
Hi mikewhatever
[SIZE="1"](note this Computer's OS was a "New install" from a downloaded .iso/CD on Nov 1st 2009, before was blank, Never Jaunty)[/SIZE]

ok I:
1) selected the second option: "keep the local version currently installed"
2) the updater finished without without any issues
3) I Restarted the computer...
4) it got to, and **completely stopped** at somthing like:
Fsck from Util-linux-NG 2.16
/dev/SDa1: clea, 275635/9584640 files 625646/38327065 Blocks

5) I pressed "**Ctrl+Alt+Del**" and got GNU Grub Version 1.97~Beta4
6) choose the top choice: "2.6.31-6-Generic"
7) got the desktop ok,then,
8) I rebooted again, OK ! 

Thanks mikewhatever
I will mark it as Fixed [SIZE="4"]**. . .**[/SIZE]
would be Great to address the language in Updater, for all useres
Thanks again 
Ronok
[[SIZE="1"]http://www.gongkuo.com/index.htm[/SIZE]]("http://www.gongkuo.com/index.htm")

---

### Post by kalwisti on 2009-12-11
I realize that this has been marked as "Solved," but I thought it might be useful to point out another forum thread where this is discussed:

[http://bit.ly/5ZIM8t](http://bit.ly/5ZIM8t)
"*what would you like to do about grub" window?*

It provides some additional information/opinions.

I encountered this for the first time last night on my Hardy partition, when the Update Manager proposed installing a new kernel. (*Note*: I've had several kernel updates since I've been running Hardy, and all of them went smoothly. The process also automatically added a new stanza to my /boot/grub/menu.lst). So the pop-up dialog box that appeared as the update was finalizing took me by surprise. The options listed were not very clear.

I'm still researching this issue and trying to understand why it's happening and what to do when it occurs again.

P.S. 
In the meantime, I fixed the problem by manually adding a new stanza in my menu.lst. Took a couple of tries, as I didn't know how to generate/calculate a UUID for the kernel location -- instead, I simply used /dev/sda1. (This worked, although it's probably incorrect from a technical standpoint).

---

### Post by prenoob on 2009-12-11
> **kalwisti said:**
> I realize that this has been marked as "Solved," but I thought it might be useful to point out another forum thread where this is discussed:

[http://bit.ly/5ZIM8t](http://bit.ly/5ZIM8t)
"*what would you like to do about grub" window?*

It provides some additional information/opinions.

I encountered this for the first time last night on my Hardy partition, when the Update Manager proposed installing a new kernel. (*Note*: I've had several kernel updates since I've been running Hardy, and all of them went smoothly. The process also automatically added a new stanza to my /boot/grub/menu.lst). So the pop-up dialog box that appeared as the update was finalizing took me by surprise. The options listed were not very clear.

I'm still researching this issue and trying to understand why it's happening and what to do when it occurs again.

P.S. 
In the meantime, I fixed the problem by manually adding a new stanza in my menu.lst. Took a couple of tries, as I didn't know how to generate/calculate a UUID for the kernel location -- instead, I simply used /dev/sda1. (This worked, although it's probably incorrect from a technical standpoint).If you find out what it means, can you let new boys like me on this forum know?  Another point - how does one tell those who produce these messages to write in such a way that a normal user can understand what he/she should do?  I notice that the other correspondence to which you referred did not exactly come to a useful conclusion!

Trevor

---

### Post by kalwisti on 2009-12-11
Hi, Trevor,

I'm still not understanding the cause of the problem, but I've continued searching and come across two other threads discussing this:

[http://bit.ly/5BELxg](http://bit.ly/5BELxg)
*What to do about menu.lst*. 16 Oct. 2008.
(See esp. reply # 7 from caljohnsmith)

[http://bit.ly/62UzCi](http://bit.ly/62UzCi)
*[SOLVED] boot failure after update - debconf?* 23 Oct. 2008.

In the way of help, the thread below points out that Ubuntu's Start-Up Manager can be a useful tool in this situation:

[http://bit.ly/8PHkYs](http://bit.ly/8PHkYs)
*GRUB, menu.lst, number of kernel entries*.

(I confess I didn't even know the Start-Up Manager existed, so I must read more about it). I'm not clear whether this might somehow be a GRUB2 issue ... although I'm not currently using GRUB2. :o This isn't a huge deal but I would like to figure it out.

HTH,
=david

---

### Post by kalwisti on 2009-12-11
My searching turns up reports of this behavior dating back to 2008, so I'm still puzzled why I haven't encountered this problem sooner ... At any rate, I feel like I've searched enough and would like to summarize what I've found, for the benefit of future forum readers.

My best guess is this has something to do with the update-grub script (maybe a bug?), which is described here:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
(These directions don't apply to Karmic, which uses GRUB2)

> Automagic Kernels List

* Ubuntu uses a script called update-grub to modify menu.lst. Whenever you install kernel updates from the repositories, update-grub is run to update the grub settings. It automatically detects all of the kernels you have in the /boot directory, and applies various global settings to each one.

There is related info at [https://wiki.ubuntu.com/GrubConflictDetection](https://wiki.ubuntu.com/GrubConflictDetection).

How to Solve The Issue?

It looks like we have several options:

1. Choose the option "Install the package maintainer's version." This may -- or may not -- overwrite any custom changes you have made. (There is conflicting evidence as to what happens with this option).

2. Choose the option "Keep the local version currently installed." Then you can manually add the necessary stanza to your menu.lst. If you need to figure out how to find the UUID (instead of the traditional "/dev/sda1" etc.), look at 
[http://bit.ly/7TBSZ8](http://bit.ly/7TBSZ8).

3. Follow the advice in the GrubHowto (linked above) to add some global options to your menu.lst to make sure your new kernel is automatically included in the menu.lst. User caljohnsmith offers similar advice here (in reply # 7):
[http://bit.ly/5BELxg](http://bit.ly/5BELxg)

4. If you don't wish to manually edit menu.lst, there are two GUI utilities to help you: Start-Up Manager and QGRUBEditor. (I haven't tried these, so use them at your own risk). Additional info on them:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

[http://bit.ly/4KmYEs](http://bit.ly/4KmYEs)
"*Ubuntu tip: Use Startup Manager to edit your boot menu*."

[http://bit.ly/qyz5v](http://bit.ly/qyz5v)
"*QGRUBEditor - A visual GRUB configuration editor*."

If any Ubuntu gurus see this and can clarify what's happening and offer recommendations on the best way to fix things, I'd appreciate it. I don't want to mislead anyone by providing inaccurate information.

---

### Post by prenoob on 2009-12-14
[SIZE=2][FONT=Verdana]Many thanks for all that information, Kalwisti.  You have really done your best for us new boys (and girls)[/FONT][/SIZE].

[FONT=Verdana][SIZE=2]I shall look into the various links today and see what pearls of wisdom can be harvested from this forum[/SIZE][/FONT][SIZE=2][FONT=Verdana]!  By the way, I discovered the existence of Start Up Manager but have not been able to make it do anything very useful, I'm afraid.[/FONT][/SIZE]

[FONT=Verdana][SIZE=2]Trevor[/SIZE][/FONT][FONT=Verdana][SIZE=2] (UK)[/SIZE][/FONT]

---

### Post by kalwisti on 2009-12-14
Hi, Trevor,

You're very welcome. Even though I don't have a definitive answer, at least I have a better idea of the available options -- and I won't panic the next time I see this dialog box. :)

One thing I'd like to point out: I noticed in your signature box that you're currently running Karmic Koala, which uses Grub 2 (i.e., the newer version of Grub) as its default. Grub 2 works differently than Grub Legacy (the older version), so any manual editing you do of your menu.lst must be done in a different way also.

I've read a tiny bit about Grub 2. Here's a few good starting points:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
"*Grub2*." [Ubuntu Community Documentation]

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
drs305. "*Grub 2 Basics*." 23 June 2009.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
"*GRUB 2 bootloader - Full tutorial*." Updated Dec. 2009.

I have a vague memory of reading something about Start-Up Manager not supporting/understanding Grub 2. You might want to confirm that. Maybe that's why it's not working properly for you ...

With best wishes,
=david

---

