---
title: "Problem Dual-Booting Ubuntu/Vista"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-01-09
Hi. I got a new laptop the other day, and I've decided to replace the horror of Vista with the lovely ubuntu :P

It's my first real install, my only other attempt being a rather unsuccessful wubi install on my main computer, and I want to dual-boot vista alongside it, as I don't want to lose anything. (Eventually, if I can successfully migrate everything into ubuntu, I'll probably kick vista off if that's possible)

However, I'm experiencing a problem. I've been following a guide linked to from another post I found, and it says to shrink down the primary vista partition and then to install ubuntu onto the larger unpartitioned space. However, when I go into the disk managing option to do as it says, I have 3 partitions:
```

1.) Unlaballed. Layout: Simple, Type: Basic, No File System, Status: Healthy (EISA Configuration)

2.) Data (E:). Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy (Primary partition)

3.) Vista: (C:). Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy (System, Boot, Page File, Active, Primary Partition)

```

There's a few other bits of information listed, such as size and so on, but I'm guessing that's not needed? If I'm wrong, please tell me and I'll add them on.

Which of these should I shrink, and which should I install ubuntu on? I think I shrink C: and then Ubuntu will autoinstall itself onto E: as the largest partition, right? My USB memory stick (Which I'm also using to install ubuntu from, see below) shows up as drive E: if that's relevant.

Also, two other related questions.

1a.) The guide says it's written for Ubuntu 6 - I'm using 10 - will that effect anything?

2a.) I'm installing Ubuntu from a USB stick, courtesy of UNetbootin - will that effect anything? Mainly I'm wondering about the various menus and so forth that let me install it onto a seperate partition easily.

2b.) Does it matter if there are other files on the USB stick I'm installing Ubuntu from?

Thanks, and sorry for the disjointed post :)

---

### Post by nhasian on 2009-01-09
it would help to know how large those partitions are so we can decide which one to put ubuntu on.  also this updated guide may be helpful to you:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by -grubby on 2009-01-09
How big are the partitions? You may be able to install it on "unlabelled".

Also, there is no Ubuntu 6 or 10, the versioning is based on the date of release. Therefore, 6.06 was released in June 2006, and 8.10 was released in October 2008. The first 6 in 6.06 corresponds to the year, and the 06 is the month.

---

### Post by Azhtabak on 2009-01-09
```

1.) Unlaballed. Layout: Simple, Type: Basic, No File System, Status: Healthy (EISA Configuration) Capacity: 1.46, Free Space: 1.46, %Free: 100%, Fault Tolerance: No, Overhead: 0%

2.) Data (E:). Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy (Primary partition), Capacity: 73.21, Free Space: 69.29, %Free: 95%, Fault Tolerance: No, Overhead: 0%

3.) Vista: (C:). Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy (System, Boot, Page File, Active, Primary Partition), Capacity: 74.37, Space: 45.99, Free Space: 62%, Fault Tolerance: No, Overhead: 0%

```
Ok, there you go, hopefully that will help. Also, I've just had a thought:

Another guide I was reading in the documentation section here said that one of the ways to migrate files from windows to ubuntu is to copy them onto a third partition (and then presumably access that partition in ubuntu). Would I be able to do this, seeing as I think I have three partitions? Also, is it possible to simply access the vista stuff from ubuntu and just copy it over that way?

EDIT: Forgot to add in the extra info

---

### Post by caljohnsmith on 2009-01-09
It looks like what you would want to do is shrink down the main Vista partition, i.e. the "C" partition. If you have any problems with Vista not letting you shrink its partition, here are some tips that might help:
[LIST]
[*]**Disable the pagefile:**
Right-click "Computer" > Advanced System Settings > Advanced > Performance Settings > Advanced > Change Virtual Memory. Click on "No pagefiling" and then "Set." After reboot, delete C: pagefile.sys. To do that you might need to check "show hiddenfiles" and uncheck "hide system files" by doubling-clicking Computer > Organize > "Folder Options" > View.

[*]**Disable hibernation**:
Open a terminal as administrator: press the Windows key and "r" at the same time to get the run program/command dialog, then type "cmd", then press Ctrl-Shift-Enter, and finally type "powercfg -h off".

[*]**Disable "snapshots":**
Right-click Computer > Advanced System Settings > System Protection and uncheck all the drives.

[*]**Try shrinking the Vista partition more than once: **
After doing the above steps, if you can't shrink the Vista partition as much as you want, shrink it as much as Vista will let you, and then repeat the process again.
[/LIST]
Good luck and let us know how it goes. :)

---

### Post by Azhtabak on 2009-01-09
Ok, I'm doing that - where will ubuntu install to? E:, the third partition I can see, or the new one that's just appeared saying 'unallocated'? I'm guessing 'unallocated' and if so, should I shrink E: as well?

---

### Post by stchman on 2009-01-09
Best way to dual boot is to clear some free space on your hdd.  During the Ubuntu installation tell the installer to use the largest free space.

Problem with WUBI is that you are putting Ubuntu on the NTFS or FAT32 file system.  This means that performance can be decreased when the file system becomes fragmented.  Also you will have greater difficulty removing Windows if you decide to.

---

### Post by caljohnsmith on 2009-01-09
> **Azhtabak said:**
> Ok, I'm doing that - where will ubuntu install to? E:, the third partition I can see, or the new one that's just appeared saying 'unallocated'? I'm guessing 'unallocated' and if so, should I shrink E: as well?
I would recommend using the "manual" partition option when you go through the Ubuntu installer, and there you can create the partitions you will need for Ubuntu with the unallocated space on your HDD that will be freed when you shrink Vista. Also, I would recommend setting up an extended partition, and then inside of that create your Ubuntu partitions as logical partition; that way you won't have to worry about being limited by the maximum limit of having no more than 4 primary partitions.

---

### Post by Azhtabak on 2009-01-09
@stchman: I'm not using wubi for this one, just a normal install via UNetbootin. I'll probably try a normal install on my main computer again later, too.

@caljohnsmith: I'm sorry to sayI have no idea how to do that -_-

@in general: I'm having a few problems now with the shrinking - I've managed to shrink it down once, but when I try to remove pagefiles and the other things mentioned, I don't have 'advanced system settings' in computer, and also the command prompt given for hibernation tells me I don't have permission, though I'm logged on as an admin account (also the first account created for it) :confused:

Also, will other user accounts take up partition space?

EDIT: Also, I have an option to 'compress this drive to save disk space' - shall I do that as well?

---

### Post by Azhtabak on 2009-01-09
Ok, another interesting development - I shrank E: as well, and now I'm showing 2 unassigned partitions instead of 1? How do I combine them?

---

### Post by Azhtabak on 2009-01-09
Ok, a bit more progress - going through the livecd and then the installation, I can get to the partitioning bit, but when I go into 'manual' I am unable to use the two bits of open space, only one of them.

Also, within the livecd, ubuntu is refusing to pick up by wireless network automatically, and regrettably I haven't the slightest idea how to make it do so :(

Anyone got any ideas as to either?

---

### Post by babloo75 on 2009-01-10
another good guide for dual booting is here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

its a general help for the community, may not specifically apply to ur problem.

---

### Post by Azhtabak on 2009-01-11
Ok - my problem is moving the partitions around - unfortunately vista has given me 2 blocks of unused space instead of 1, and ubuntu seems to only want to install onto one of them. I'm downloading gparted now to try and sort it - will I be able to do that?

Also, is it worth deleting the E: partition? I don't think it's doing anything, and I could use the extra space - perhaps for a Fat32 partition to transfer files between vista and ubuntu, like some guides recommend?

---

### Post by tschluter on 2009-01-12
> **Azhtabak said:**
> Also, is it worth deleting the E: partition? I don't think it's doing anything, and I could use the extra space - perhaps for a Fat32 partition to transfer files between vista and ubuntu, like some guides recommend?

The E: partition may be a Rescue/Recovery Partition installed by the PC vendor. Verify by opening the Command Prompt window or typing "cmd" in the Run command line box. Then type "cd E:" then "dir" (without quotes).  Look for files named "Setup.exe" "Install.exe" etc.

If E: appears to be a Rescue/Recovery Partition you can re-install Vista if somehow Vista gets hosed.  Be advised that you may lose any data you have generated in Vista so you'll want to make a backup before you start.

---

