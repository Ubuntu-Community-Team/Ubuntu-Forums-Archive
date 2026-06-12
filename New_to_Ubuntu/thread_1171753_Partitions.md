---
title: "Partitions"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by hbe14 on 2009-05-27
Hi, I recently installed Ubuntu 9.04, choosing a side by side option to install alongside windows xp. Installation went fine, but now I don't any hard disk space to install any updates! Is there anyway to "repartition" the drive in order to make more space?

Thanks for the help!

---

### Post by blueridgedog on 2009-05-27
You can boot off of the live CD and resize the partitions using gparted (similar to what you did during the install).  

How much space did you give Ubuntu?

---

### Post by hbe14 on 2009-05-27
I gave it the default that it is given to it when you use the first option when installing ubuntu, im guessing it's very small because the updates the update manager is asking me to install are 44mb and they don't fit.

---

### Post by taurus on 2009-05-27
What are the outputs of these commands from a terminal, running one line at a time?

Applications -> Accessories -> Terminal
```
sudo fdisk -lu
df -h
```

---

### Post by hbe14 on 2009-05-27
[FONT=monospace]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde77f037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   307339514   153669726    7  HPFS/NTFS
/dev/sda2       307339515   312576704     2618595    5  Extended
/dev/sda5       307339578   312223274     2441848+  83  Linux
/dev/sda6       312223338   312576704      176683+  82  Linux swap / Solaris[/FONT]

---

### Post by taurus on 2009-05-27
> **hbe14 said:**
> [FONT=monospace]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde77f037

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   307339514   153669726    7  HPFS/NTFS
/dev/sda2       307339515   312576704     2618595    5  Extended
/dev/sda5       307339578   312223274     2441848+  83  Linux
/dev/sda6       312223338   312576704      176683+  82  Linux swap / Solaris[/FONT]

Looks like you have to shrink /dev/sda1 (windows) first.  Then, expand the extended partition, /dev/sda2, to take up that unallocated space.  Now, expand /dev/sda5 (Ubuntu) to take up the new space.

Of course, you have to use gparted from either Ubuntu LiveCD or GParted LiveCD and _ALWAYS_ back up your personal files first just in case.

---

### Post by hbe14 on 2009-05-27
Ok, will try this and will get back to you as soon as I can.

---

### Post by -kg- on 2009-05-27
> Device Boot Start End Blocks Id System
/dev/sda1 * 63 307339514 153669726 7 HPFS/NTFS
/dev/sda2 307339515 312576704 2618595 5 Extended
/dev/sda5 307339578 312223274 2441848+ 83 Linux
/dev/sda6 312223338 312576704 176683+ 82 Linux swap / Solaris

I'm wondering that the Guided Install only gave him that much hard drive space for Linux while leaving that much for XP.  It doesn't seem like a very equitable split, unless his XP partition is chock full.

He may end up having to transfer and/or delete some of the files in his XP partition before he's able to shrink the XP partition very much more.

---

### Post by hbe14 on 2009-05-27
> **taurus said:**
> Looks like you have to shrink /dev/sda1 (windows) first.  Then, expand the extended partition, /dev/sda2, to take up that unallocated space.  Now, expand /dev/sda5 (Ubuntu) to take up the new space.

Of course, you have to use gparted from either Ubuntu LiveCD or GParted LiveCD and _ALWAYS_ back up your personal files first just in case.

How do I expand /dev/sda2 to take up the unallocated space? I already shrunk /dev/sda1.

---

### Post by hbe14 on 2009-05-27
> **-kg- said:**
> I'm wondering that the Guided Install only gave him that much hard drive space for Linux while leaving that much for XP.  It doesn't seem like a very equitable split, unless his XP partition is chock full.

He may end up having to transfer and/or delete some of the files in his XP partition before he's able to shrink the XP partition very much more.

My xp partition is no where near full, only 36gb used out of 150.

---

### Post by Didius Falco on 2009-05-27
XP has a habit of sticking the Swap File and the System Volume stuff towards the back end of the partition. I've pretty much started recommending that people turn the Swap File in Windows off until after they've resized it - along with the obligatory 2x defragging... 

To resize your extended partition, just click on it in the Gparted screen, then right-click and choose Resize. It won't let you do it if it, or any of the partitions it holds, are mounted.

After you resize the Extended partition, you can the resize the Logical Drive inside it.

Regards,

Didius

---

### Post by hbe14 on 2009-05-27
How do I unmount it then? I'm new to linux.

---

### Post by Didius Falco on 2009-05-27
If you are doing it from the Live CD, it should be unmounted by default. Look to the left side of the screen in Gparted and see if there are any icons of a key. If so, that means that partition is mounted.

Highlight the partition on the screen, then Right-click it and select "unmount".

Again, if you are doing this from the Live CD (recommended way), the partitions should not be mounted.

Regards,

Didius

---

### Post by -kg- on 2009-05-27
When you do the resize operation, it won't let you do it unless unmounted (i.e., the options will be grayed out) but there will be an option that is not grayed out that says, "Unmount".  Because you are running from a Live CD, however, none of those partitions should be mounted.  If they are, just click on "Unmount" then go ahead with setting up the operations.

If you try to do this while running from the hard drive, however, they will be mounted and you can't unmount them, which is why you will definitely need to do this from the Live CD.

LOL!  You beat me to it, Didius!

---

### Post by hbe14 on 2009-05-27
I'm doing them from the live CD, and they are mounted. when I right click /dev/sda2, everything is greyed out except "manage flags" and "information".

---

### Post by Didius Falco on 2009-05-27
kg,

That'd be my one-time in a thousand then - I am a slowwwww typist.

Regards,

Didius

---

### Post by hbe14 on 2009-05-27
Can anyone help me with this? Unmount is greyed out on dev/sda2.

---

### Post by Didius Falco on 2009-05-27
When you say they are mounted - are you seeing the icons of keys on the screen? If you have a Linux Swap partition, that may be mounted - unmount that by highlighting and right-clicking, or highlight it and go to the Partition menu at the top of the screen.

Regards,

Didius

---

### Post by Paqman on 2009-05-27
> **hbe14 said:**
> I'm doing them from the live CD, and they are mounted. when I right click /dev/sda2, everything is greyed out except "manage flags" and "information".

What i'm guessing is that your swap inside your extended partition is stopping you from unmounting them. The LiveCD automatically looks for and mounts any existing swap partitions (to improve performance).

Bottom line: right click on your swap > swapoff. You should then be able to resize your other partitions.

The clue is the fact that your swap (and your extended) would have had a little key symbol on them, to say that they're locked as far as Gparted is concerned.

---

### Post by hbe14 on 2009-05-27
Yes! The swapoff worked like a charm, i was able to resize everything to the way I wanted. So much for my first adventure in Linux. Thanks for the help guys.

---

### Post by Didius Falco on 2009-05-27
Happy to help out!

---

