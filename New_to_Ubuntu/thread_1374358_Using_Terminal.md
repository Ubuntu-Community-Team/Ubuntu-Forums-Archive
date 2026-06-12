---
title: "Using Terminal"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Slayer. on 2010-01-06
I'm fairly new to Ubuntu. I've only been using it on and off for about two years. 

I'm trying to create a new partition, so I can install windows. (I didn't realize how much I'd miss mIRC and some other programs :P) I installed a few different partition managers, including KVPM, and KDE Partition Manager. However, I can't use either of them, because they have to be opened as root. I know the command for root is sudo, but I don't know how to use the terminal to actually OPEN the application as root. Help would be lovely.

---

### Post by tom.swartz07 on 2010-01-06
> **Slayer. said:**
> I'm fairly new to Ubuntu. I've only been using it on and off for about two years. 

I'm trying to create a new partition, so I can install windows. (I didn't realize how much I'd miss mIRC and some other programs :P) I installed a few different partition managers, including KVPM, and KDE Partition Manager. However, I can't use either of them, because they have to be opened as root. I know the command for root is sudo, but I don't know how to use the terminal to actually OPEN the application as root. Help would be lovely.

The problem is, you need to run the partition manager when you are not using your drive. Just like you cant work on a car engine when its running, You cant change anything with your hard drive until its off.

I would suggest using gParted. Burn it to a CD and boot to that, rather than your HardDrive. You could then make any changes.

BE SURE TO BACK UP YOUR DATA BEFORE YOU BEGIN!!!!!!!!!!!!!
The risks of losing your data accidentally increase 50 fold when you attempt to edit partitions.

Good luck!

---

### Post by bodhi.zazen on 2010-01-06
Boot a live CD and use gparted =)

---

### Post by mkoehler on 2010-01-06
FYI, there are some great substitutes for IRC clients - I'm not sure what else you're missing.  But yes, in order to edit hard drives, you will need to have your hard drive unmounted.  As bodhi.zazen said, boot into the live CD and use gparted.

To Tom: It's not really likely that you're going to lose data.  As long as you don't enable any of the changes you've made in gparted until they're right, you'll be fine.  Also, Linux automatically defrags the hard drive so you don't have to worry about running that operation before modifying the partition table. :)

---

### Post by tom.swartz07 on 2010-01-06
> **mkoehler said:**
> 
To Tom: It's not really likely that you're going to lose data.  As long as you don't enable any of the changes you've made in gparted until they're right, you'll be fine.  Also, Linux automatically defrags the hard drive so you don't have to worry about running that operation before modifying the partition table. :)

it never hurts to be safe! :D

Better to backup and have your stuff just in case, than to lose it and be out of luck

---

### Post by Slayer. on 2010-01-06
> **mkoehler said:**
> FYI, there are some great substitutes for IRC clients - I'm not sure what else you're missing.  But yes, in order to edit hard drives, you will need to have your hard drive unmounted.  As bodhi.zazen said, boot into the live CD and use gparted.

Right now, I'm just using ChatZilla. It works fine, but I miss the scripting feature, and the ability to easily customize colors and what-not. I tried running it in Wine, but it crashed whenever I opened the Script Editor. Oh well, I can live without it.

Anyways, thanks for the help everyone. :)

---

### Post by J V on 2010-01-06
Pretty much every big-time linux app has plugins, I'm sure you can get one that allows some sort of scripting...

---

### Post by -kg- on 2010-01-06
[LIST]
[/LIST]

I don't know about "script-ability," but you might also want to give XChat a try.  It's the closest thing to mIRC that I've found for Linux.

As far as partitioning operations...there is also the [GPartEd Live CD,]("http://gparted.sourceforge.net/") which is a Live CD dedicated just to editing hard drive partitions (and a relatively small download).  You can use the Ubuntu Live CD partition editor, but if you have problems editing partitions with it, make sure that the Swap partition is off.

Right click the swap partition, and if there is a menu selection that says, "Swapoff," click it.  If it says "Swapon," then obviously you're good to go.  The GPartEd Live CD doesn't mount any partition and doesn't use the swap partition.

---

