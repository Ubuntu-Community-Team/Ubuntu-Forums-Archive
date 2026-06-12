---
title: "help uninstalling version 10.10 in stand alone install"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Hunter84 on 2011-05-06
yes i am a noob and screwed up. OK here is what happened i started to install Ubuntu 10.10 the very  first thing you see is install along windows or stand alone. so i choose  stand alone stated it going used a simple password to get it going   then was going to change it to a better one after it was  nice and  installed well went through the whole thing installed it on a separate  drive that i had freed up which was my E partition got all the way done  restarted and was waiting for the prompt to select windows or Ubuntu  well that never happened it just went straight to windows, its OK i  talked to a couple of people and i fixed my grub so now i have that  prompt to select  windows or Ubuntu and so on. now the bad news  the  password i put in before isn't working so MY first question is how do i  change a password that i don't know then how do i uninstall Ubuntu (dont  worry i still want Ubuntu just as a side by side with windows not a  stand alone, to many problems already) also on a side note the hard  drive/ partition i installed it on which i can still go into (Ubuntu i  mean) is still empty and shows the same amount of free space as before i  installed?:confused:?  if there is a way to uninstall it with out changing the password wont  need that problem fixed any help would be great please and a very big  thank you to who ever helps. :grin:

---

### Post by Hedgehog1 on 2011-05-07
First - How to change the password when you have forgotten (or mistyped it twice - ask me how I know):

Please use this handy web page to reset your root password: **_[resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")_**

If you still need to reinstall Ubuntu - there are two ways of doing it:

1) Overwrite the current Ubuntu install with the new one.

2) Do a FixMBR to boot into windows directly, then delete the Ubuntu partitions; then later reinstall Ubuntu when you are ready again.

The next two posts will how you how to fixMBR and uninstall Ubuntu on a 'typical' install - you may have to adjust to your hard drive layout.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-07
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

### Post by Hedgehog1 on 2011-05-07
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

### Post by Hunter84 on 2011-05-07
ok cool i was able to reset the password to something i like. now i am following you awesome little tutorial, which is greatly appreciated, and i am looking at the disk management in the storage section. there are 3 partitions with no drive letter is there a way to tell which one to delete? ok this one harddrive is suppose to be split into just 3 drives, but im seeing 6

 
its disk 1 i only thought i had the D E F. is the 27.66 GB free space apart of one of them or is it separate. then the right most two, im thinking one of them is the ubuntu install is there a way to tell like i dont think its in the 2.4 gb one but not sure. then next question is the first steps to get it to boot to windows. when it boots up it come to a screen were i can select ubuntu, an old version of windows which isnt even in stall anymore and windows 7. if i delete the ubuntu will it still show up like the old version of windows. ( it was an old version of xp that didnt work any of my new hardware )

---

