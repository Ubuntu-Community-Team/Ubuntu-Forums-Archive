---
title: "Can't Mount Western Digital My passport external Hard drive"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by HyyDeff on 2011-01-20
I have no idea how to get this thing running. Once I plug it in, the virtual CD pops up, but thats it. When I try to run the install software for the drive, it says the autorun program cannot be found. Can someone help out?

---

### Post by verymadpip on 2011-01-20
Some more info may be helpful.

I didn't have to install any software to get mine working, however, I am only using it to backup my data.

I cut all the 'stuff' that came on it & pasted it into another folder somewhere, just in case.  (Just in case of what, I don't know; just in case.......)

---

### Post by HyyDeff on 2011-01-20
What information is needed? I will provide as much as I can. I just didnt know what all to post on here.

Edit: The drive is configured in NFTS

---

### Post by Hatsune Miku on 2011-01-20
> **HyyDeff said:**
> What information is needed? I will provide as much as I can. I just didnt know what all to post on here.

Edit: The drive is configured in NFTS

Type this in the Terminal

```
df
```

and post what it said in a forum post.

---

### Post by HyyDeff on 2011-01-20
> **Hatsune Miku said:**
> Type this in the Terminal

```
df
```

and post what it said in a forum post.

My results


```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73719016   4895040  65079208   7% /
none                    991940       256    991684   1% /dev
none                    997540       588    996952   1% /dev/shm
none                    997540       100    997440   1% /var/run
none                    997540         0    997540   0% /var/lock
none                  73719016   4895040  65079208   7% /var/lib/ureadahead/debugfs
/dev/sr1                629128    629128         0 100% /media/WD SmartWare
```

---

### Post by Hatsune Miku on 2011-01-20
> **HyyDeff said:**
> My results


```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73719016   4895040  65079208   7% /
none                    991940       256    991684   1% /dev
none                    997540       588    996952   1% /dev/shm
none                    997540       100    997440   1% /var/run
none                    997540         0    997540   0% /var/lock
none                  73719016   4895040  65079208   7% /var/lib/ureadahead/debugfs
/dev/sr1                629128    629128         0 100% /media/WD SmartWare
```

Hmm... Try this

```
sudo mkdir /media/western
sudo mount ntfs /dev/sdb1 /media/western

```

---

### Post by wilee-nilee on 2011-01-20
> **HyyDeff said:**
> I have no idea how to get this thing running. Once I plug it in, the virtual CD pops up, but thats it. When I try to run the install software for the drive, it says the autorun program cannot be found. Can someone help out?

That install software is most likely for a Windows OS, do you see any .exe files, and is it a cd?

You may not have all the capability for encryption from WD, but there is a very good open source alternative called truecrypt. You might explain what the programs are for as well if needed.

The smartware has caused other Linux users problems, the fix I have seen is to upgrade that; it is firmware, and can't be removed. This has to be done on a MS OS then you can hide the smartware from that update program, in order for Ubuntu to see it

---

### Post by HyyDeff on 2011-01-20
> **Hatsune Miku said:**
> Hmm... Try this

```
sudo mkdir /media/western
sudo mount ntfs /dev/sdb1 /media/western

```

This is what i got from typing that in.

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount . 
```

> **wilee-nilee said:**
> That install software is most likely for a Windows OS, do you see any .exe files, and is it a cd?

You may not have all the capability for encryption from WD, but there is a very good open source alternative called truecrypt. You might explain what the programs are for as well if needed.

The smartware has caused other Linux users problems, the fix I have seen is to upgrade that; it is firmware, and can't be removed. This has to be done on a MS OS then you can hide the smartware from that update program, in order for Ubuntu to see it

I see .exe files. And the EHD creates a virtual CD. Used to install the software for the EHD. None of the .exe files will run though.

---

### Post by osb_tensor on 2011-01-20
i have no idea if this is relevant to this conversation, but i think it might be close.. and i was curious about my situation also. i bought a western digital external and hooked it up to my ubuntu box and got nothing. zip zero zilch. (no cd or software came with the hd) i then hooked it up to my xp box and it read it and stated i had new hardware installed. i then unplugged from xp and replugged into my ubuntu box and suddenly ubuntu recognised the hd. is there a first time setup that windows performs to make the hd readable? could i have done something such as a mount to make this readable in ubuntu the first time?

---

### Post by wilee-nilee on 2011-01-20
> **HyyDeff said:**
> 
I see .exe files. And the EHD creates a virtual CD. Used to install the software for the EHD. None of the .exe files will run though.

You can't run .exe in Linux, here is a link that explains the method I was alluding to in getting it readable by Ubuntu.
[http://superuser.com/questions/44318/how-do-i-remove-a-mybooks-wd-smartware-virtual-cd-from-my-desktop](http://superuser.com/questions/44318/how-do-i-remove-a-mybooks-wd-smartware-virtual-cd-from-my-desktop)

---

### Post by TechWiz2100 on 2011-01-20
WD Passports need to be "Unlocked" via Windows or Mac b4 they can be used in any way shape or form.

I don't have the foggiest idea as to why WD would include such a useless function in their firmware and then put the needed unlocking software in a constantly available read-only partition but yea...

Take the device to a Mac or PC and run the "Unlock" application or the WD Smartware Utilities to enable access to the writable partition then format that so that you may use it properly. You can also try WINE on the unlocking .exe

If the drive is missing the apps, you can download the software kit for Mac and PC from WD's support pages.

---

### Post by Layvian on 2011-01-20
If you want to get it to work, you can Unmount it, and Format it in either a Masterboot or a GUID, but that is up to you, it will delete EVERYTHING including the software.

---

### Post by HyyDeff on 2011-01-21
> **TechWiz2100 said:**
> WD Passports need to be "Unlocked" via Windows or Mac b4 they can be used in any way shape or form.

I don't have the foggiest idea as to why WD would include such a useless function in their firmware and then put the needed unlocking software in a constantly available read-only partition but yea...

Take the device to a Mac or PC and run the "Unlock" application or the WD Smartware Utilities to enable access to the writable partition then format that so that you may use it properly. You can also try WINE on the unlocking .exe

If the drive is missing the apps, you can download the software kit for Mac and PC from WD's support pages.

I think I'm just going to delete the password in the morning and see how that works. 

And to the poster who said to use WINE, I tried but it didn't work. I may be doing it wrong, but I'm pretty sure it doesn't work with the WD software.

---

### Post by [Snc] on 2011-01-21
> **HyyDeff said:**
> I think I'm just going to delete the password in the morning and see how that works. 

And to the poster who said to use WINE, I tried but it didn't work. I may be doing it wrong, but I'm pretty sure it doesn't work with the WD software.

wow, i haven't heard anything about unlocking WD passports yet :-k

anyhow, my experience is, that the passports come with a very short cable and cannot be connected to any longer ones then the ones, that are provided. also, mine has to be pluged into a USB port, that is directly on the motherboard 

so not an inch/cm more cable, or it will not work!

PS. i plugged mine first into Ubuntu and it just worked, no unlocking needed...

---

### Post by verymadpip on 2011-01-21
I didn't need to unlock mine either.

As I said before, I cut the WD stuff from the drive & pasted it to a folder elsewhere (just in case..........).

I then formatted the drive to ext4 & that was that.  I've only done one backup so far & it went smoothly.

Keep us posted HyyDeff

---

### Post by 3602 on 2011-01-21
Don't know whether this would help, but back when I was using Jaunty, I did something then nothing would mount. The solution was to install *pmount*.

---

### Post by psusi on 2011-01-21
> **3602 said:**
> Don't know whether this would help, but back when I was using Jaunty, I did something then nothing would mount. The solution was to install *pmount*.

pmount is what handled auto mounting in jaunty.  It has been replaced with udisks.

---

### Post by bollucks on 2012-02-04
So there is no answer for accessing the NTFS formatted My Passport without being able to run the unlock.exe?
I installed wine for ubuntu but it did not let me run any .exe files on the WD SmartWare CD.

---

### Post by bollucks on 2012-02-22
:When I try running the unlock.exe through wine I get the error/;
Unlock
The application has encountered an unexpected error and is now exiting.

I've tried running it from the virtual CD and by copying that file to my computer, get same error either way.

---

