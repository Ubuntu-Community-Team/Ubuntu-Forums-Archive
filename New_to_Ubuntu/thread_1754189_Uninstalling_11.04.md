---
title: "Uninstalling 11.04"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-09
Howdy folks.  I  installed what was the Ubuntu 11.04, and should not have.  Is there anyway to uninstall it?  I did say install it aside from windows.  Any Idea?

---

### Post by Dreigo42 on 2011-05-09
Not sure I understand. Did you install it inside of windows and now want it next to it as a second operating system?

---

### Post by TAspr on 2011-05-09
Well, yes, ultimately I do, but I should have not installed Ubuntu on this box at all. How do you get rid of it?

---

### Post by wilee-nilee on 2011-05-09
> **TAspr said:**
> Well, yes, ultimately I do, but I should have not installed Ubuntu on this box at all. How do you get rid of it?

If inside Windows as it sounds, go to the admin account then to the control panel-add remove packages click on it and it will be wiped.
[http://gizmodo.com/?_escaped_fragment_=5138189/win-7-tip-where-the-hell-is-addremove-programs#!5138189/win-7-tip-where-the-hell-is-addremove-programs](http://gizmodo.com/?_escaped_fragment_=5138189/win-7-tip-where-the-hell-is-addremove-programs#!5138189/win-7-tip-where-the-hell-is-addremove-programs)

---

### Post by lng on 2011-05-09
[SIZE=2]If you have Installed UBUNTU inside Windows, it can be Uninstalled as any other programs in WINDOWS.
Just Go to Control Panel.

- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - - [/SIZE][SIZE=2]- - - - - -[/SIZE][SIZE=2] - - - - - -[/SIZE]
[SIZE=2]Why to peep through [/SIZE]**[SIZE=2][COLOR=DarkOrange]WINDOWS[/COLOR][/SIZE]**[SIZE=2], When doors are [/SIZE]**[SIZE=2][COLOR=DarkOrange]OPEN[/COLOR][/SIZE]** !!  :D
[SIZE=2][FONT=Book Antiqua][COLOR=Blue]<<!ng>>[/COLOR][/FONT][/SIZE]

---

### Post by 3rdalbum on 2011-05-09
If you installed Ubuntu from within Windows, using the Windows program that comes on the Ubuntu CD, then you can remove it using the Add/Remove Programs function in Windows.

If you booted your computer from the Ubuntu CD and ran the Ubuntu-based installer, then it's not as easy as "uninstalling". You need to use a partitioning tool such as Gparted (which you can run from the Ubuntu live CD) to remove the Ubuntu partitions, resize your Windows partition upwards to fill the disk, and then boot up your Windows CD and run the 'fixmbr' command.

If this seems like gobbldigook to you, then you might want to do a search on Google for some more hand-holding instructions; I can't be of more help to you because I've never actually done this.

---

### Post by Hedgehog1 on 2011-05-10
If the install was done 'along side' windows (not a WUBI install) , then here are the instructions for removing it from the system it is on:


Fix MBR

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-10
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

