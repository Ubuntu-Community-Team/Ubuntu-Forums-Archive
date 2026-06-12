---
title: "Don't even know where to start. (strange problems)"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-12-14
For almost a week, my computer has been acting funny. At first I was paranoid and thought I'm being hacked, so started [this]("http://ubuntuforums.org/showthread.php?t=1349477") thread.

I don't know what to think now, but will tell the issue as best I can.

All of a sudden out the blue, my screen flashed black kinda like when you reboot, then it came back. It's happened a few times now and seems to get a bit worse. The last few days, my computer really slows down, to the point I have no choice but to reboot. The computer clock goes all screwy, either gaining or losing about 13hrs. And today after the last episode, and reboot, my Karmic looks like a very old version. I attached a screenshot. It now beeps, when I click certain icons too.

Does anyone know or can guess what is going on? My machine is only 6mths old, if that.

Also while I am at it, at start up I get this message. ```
One or more of the mounts listed in /etc/fstab cannot yet be mounted.
Swap: waiting for UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50.
Press ESC to enter recovery shell.
``` This didn't used to be a problem, but lately it sticks at that message and won't budge til I hit ESC, then it takes me to the normal login screen.

Help much appreciated, thanks in advance.

---

### Post by oldos2er on 2009-12-14
What are your system specs?

If I were you, I'd run memtest (from the grub menu), maybe let it run overnight; and also run fsck on your unmounted partitions. If you have an Ubuntu LiveCD, you can boot from it to run fsck your root partition.

---

### Post by hotstovejer on 2009-12-14
Can you please post the entire contents of /etc/fstab?

In a terminal window, type 

```
gedit /etc/fstab
```

Thanks!

---

### Post by Penguin Guy on 2009-12-14
```
One or more of the mounts listed in /etc/fstab cannot yet be mounted.
Swap: waiting for UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50.
```
This means your swap cannot be mounted, so if your computer doesn't have much physical memory the computer will crash - perhaps this is what is happening.

I can help you get it working again but I will need some information. Please [open a terminal]("http://www.psychocats.net/ubuntu/terminal") and run the following two commands and post their output back here: [COLOR="Green"]blkid[/COLOR] and [COLOR="Green"]cat /etc/fstab[/COLOR].

Also follow [oldos2er's advice]("http://ubuntuforums.org/showpost.php?p=8498164"), he has made two very good points and is obviously very experienced.

---

### Post by T4K3Z0U on 2009-12-14
> **oldos2er said:**
> What are your system specs?

If I were you, I'd run memtest (from the grub menu), maybe let it run overnight; and also run fsck on your unmounted partitions. If you have an Ubuntu LiveCD, you can boot from it to run fsck your root partition.

How do I run memtest from grub? Do I use the live CD? I only have 9.04 on cd. Also what is fsck?

This is embarrasing, but I can't find the place in Ubuntu to find my sys specs. I only remember RAM and HDD size. 4GB and 400GB respectively.


> **Penguin Guy said:**
> ```
One or more of the mounts listed in /etc/fstab cannot yet be mounted.
Swap: waiting for UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50.
```
This means your swap cannot be mounted, so if your computer doesn't have much physical memory the computer will crash - perhaps this is what is happening.

I can help you get it working again but I will need some information. Please [open a terminal]("http://www.psychocats.net/ubuntu/terminal") and run the following two commands and post their output back here: [COLOR="Green"]blkid[/COLOR] and [COLOR="Green"]cat /etc/fstab[/COLOR].

Also follow [oldos2er's advice]("http://ubuntuforums.org/showpost.php?p=8498164"), he has made two very good points and is obviously very experienced.

```
~$ blkid
/dev/sda1: UUID="388A35028A34BDE6" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="D0AC5FB4AC5F9436" TYPE="ntfs" 
/dev/sda5: UUID="f17d068f-b1cd-4864-87bf-dcc87924a63f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="32ff26f8-f948-4e09-b297-6eda46b51d37" TYPE="swap" 
```
```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I also forgot to mention, my little Num Lk light keeps turning on and off on it's own, and quite often firefox crashes. I presume that's to do with the swap thing.

---

### Post by wojox on 2009-12-14
You're UUID for Swap are out of whack. 

It's looking for this:

```
UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50
```

But needs this:

```
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37
```

Just edit fstab and it should load Swap.

```
gksudo gedit /etc/fstab
```

Change the swap UUID to the second one.

---

### Post by T4K3Z0U on 2009-12-14
> **wojox said:**
> You're UUID for Swap are out of whack. 


Just edit fstab and it should load Swap.

How and why did it get out of whack? How do I edit fstab?

ETA: Are all UUID meant to be the same?

---

### Post by NewbuntuUser777 on 2009-12-14
It seems to be common problem related to recent updates (or switching to 9.10 itself).  I had the problem.

In terminal, type
sudo nano /etc/fstab


And edit it so that the uuid for the swap is the same as for the ext3 partition (assuming you don't have more than 1 *nix partition).

It's linux so exceedingly unlikely that you've been hacked.  Even new 
computers have hardware problems, and ram problems are very common.

To run a memtest use the live CD.  One of the options on the main menu 
will be memtest.  Run it over night to see if you've got bad ram.  I 
think you probably do, but there may be other hardware problems.

---

### Post by T4K3Z0U on 2009-12-14
> **NewbuntuUser777 said:**
> It seems to be common problem related to recent updates (or switching to 9.10 itself).  I had the problem.

In terminal, type
sudo nano /etc/fstab


And edit it so that the uuid for the swap is the same as for the ext3 partition (assuming you don't have more than 1 *nix partition).

It's linux so exceedingly unlikely that you've been hacked.  Even new 
computers have hardware problems, and ram problems are very common.

To run a memtest use the live CD.  One of the options on the main menu 
will be memtest.  Run it over night to see if you've got bad ram.  I 
think you probably do, but there may be other hardware problems.

Using that terminal code, the UUID for ext3 is different than the UUID Wojox said to use, so which is correct? 

How could I have bad ram after only 6mths or less?

---

### Post by wojox on 2009-12-14
Okay what the number you see when using the terminal code?

---

### Post by T4K3Z0U on 2009-12-14
> **wojox said:**
> Okay what the number you see when using the terminal code?

UUID=f17d068f-b1cd-4864-87bf-dcc87924a63f.

But I just remembered, I went to the kernel before the very latest one. Perhaps that has something to do with it?

---

### Post by wojox on 2009-12-14
That's not your swap UUID that's you're ext filesystem UUID. Close nano and open with 

```
gksudo gedit /etc/fstab
```

Then look for this line

```
# swap was on /dev/sda8 during installation
```

It should have this number:

```
UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50
```

But needs to be this number:

```
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37
```

---

### Post by T4K3Z0U on 2009-12-14
> **wojox said:**
> That's not your swap UUID that's you're ext filesystem UUID. Close nano and open with 

```
gksudo gedit /etc/fstab
```

Then look for this line

```
# swap was on /dev/sda8 during installation
```

It should have this number:

```
UUID=058c89ba-d1e6-40cb-a981-c767fc15fc50
```

But needs to be this number:

```
UUID=32ff26f8-f948-4e09-b297-6eda46b51d37
```

OK I must have misread.

Here is what I got using the code you offered.

```
:~$ gksudo gedit /etc/fstab
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

(gksudo:6960): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

```

But using the sudo nano code, I can change it I think.

---

### Post by T4K3Z0U on 2009-12-14
I just want to be sure I get this right. Will try changing it now.

---

### Post by T4K3Z0U on 2009-12-14
Is there a way to save the UUID once I type in the new one? I don't see a save option.

---

### Post by oldos2er on 2009-12-14
If you don't have memtest in your grub menu, you can run it from the LiveCD, as was suggested.

 fsck = file system check. More info here: [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by T4K3Z0U on 2009-12-14
> **oldos2er said:**
> If you don't have memtest in your grub menu, you can run it from the LiveCD, as was suggested.

 fsck = file system check. More info here: [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Cool. And how do I save the UUID when I change it? The code given edits through terminal, and I can't work out how to save it, or does it do so automatically?

ETA. Or am I getting this wrong, I should first do the fsck, before worrying about changing things in terminal?

---

### Post by spiderbatdad on 2009-12-14
when using nano the options should be shown at the bottom of the window.
To save ctrl-o then enter to confirm. ctrl-x to exit.

---

### Post by T4K3Z0U on 2009-12-14
> **spiderbatdad said:**
> when using nano the options should be shown at the bottom of the window.
To save ctrl-o then enter to confirm. ctrl-x to exit.

Ah, so "write out" means save?

---

### Post by T4K3Z0U on 2009-12-14
> **oldos2er said:**
> If you don't have memtest in your grub menu, you can run it from the LiveCD, as was suggested.

 fsck = file system check. More info here: [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

It was a very long day yesterday. Now that I am refreshed.....

So far, memtest has done 4 passes all clean, still running. This doesn't stop automatically does it? How many passes should I let it do? 

As for fsck, I didn't realise, that's the ever 21 mount, forced check. That had actually run, around the same time this problems start occurring. I will run the check, once I know when to stop memtest.

I'm still waiting for a reply to my last post/question. Does "write out" mean save?

Thanks all.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
I don't know the official answer on memtest, but for checking stability when overclocking, 24 hrs is recommended.

---

### Post by T4K3Z0U on 2009-12-15
> **ST3ALTHPSYCH0 said:**
> I don't know the official answer on memtest, but for checking stability when overclocking, 24 hrs is recommended.

Overclocking?

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
The process of increasing multipliers and voltage to increase the speed of your hardware (for instance, my 2.5 GHz CPU is running at 3.0 GHz). Thus can cause instabilities in the processor and memory, so those components need to be stability tested. Memtest is used for the RAM in that instance as well, and 24 hrs is considered stable. If 24 hrs is sufficient to prove such a high demand application stable, then it should be definitive for standard setup equipment.

---

### Post by T4K3Z0U on 2009-12-15
OK. 24hrs without my computer will be hard, but if that's what I gotta do...

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
I would recommend it because when I had RAM failures it was in the 18-20 hr mark.

---

### Post by EssexEagle on 2009-12-15
> **T4K3Z0U said:**
> I'm still waiting for a reply to my last post/question. Does "write out" mean save?

Yes, it does.

---

### Post by T4K3Z0U on 2009-12-16
I let it run for a little more than 10hrs, which made 11 passes. I then forced the fsck, and the problem seemed resolved. HOWEVER, once I shut my machine down for the day and rebooted it, the same problem of stalling at startup happened.

I now need to try changing the swap code thing, and see what happens. I am really worried, though, coz what if that doesn't resolve the issue?

---

### Post by Roger Allott on 2009-12-16
> **T4K3Z0U said:**
> I let it run for a little more than 10hrs, which made 11 passes. I then forced the fsck, and the problem seemed resolved. HOWEVER, once I shut my machine down for the day and rebooted it, the same problem of stalling at startup happened.

I now need to try changing the swap code thing, and see what happens. I am really worried, though, coz what if that doesn't resolve the issue?

The "swap code thing" seems to be the most obvious problem you've got and resolving it is simple, as has been explained by others on this thread.

I'd like to know from one of the experts how such a problem of UUID identification can go so wrong on an install.

---

### Post by T4K3Z0U on 2009-12-17
I changed the UUID, then rebooted, this seems to have worked, but I haven't rebooted again to check, coz I'm a bit worried it may only be temporary.

---

### Post by John Bean on 2009-12-17
> **Roger Allott said:**
> I'd like to know from one of the experts how such a problem of UUID identification can go so wrong on an install.

It didn't happen at install. Note that the install-time partition numbers in the comments in fstab are different from those in the current blkid output. The partition table has been changed since installation and how that occurred is anybody's guess.

---

### Post by T4K3Z0U on 2009-12-18
Everything is still working OK at this point.

Thanks to all for your help.

---

