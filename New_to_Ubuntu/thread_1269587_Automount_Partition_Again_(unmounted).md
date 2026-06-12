---
title: "Automount Partition Again (unmounted)"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-09-18
I was previously using NTFS Config Tool to automount my partitions when ubuntu loads. Today I mistakenly unmounted a partition which the software automounts. Now when I go to the software, it does not show the partition I unmounted ? I cannot mount it via double clicking either. What should I do ? :confused:

EDIT : When I double click, it says "You are not privileged to mount the disk" although I am the Administrator and I have all privileges enabled in my Users & Groups.:(

---

### Post by bumanie on 2009-09-18
Go to Places --> Computer and all the drives in the computer should be listed there. You can double click them and they will open - might ask for your password, depending on how the permissions are set. Otherwise go to terminal and type sudo mount /dev/xxxx (substituting xxxx for the name of the drive).

---

### Post by SriLankanBoy on 2009-09-19
> **bumanie said:**
> Go to Places --> Computer and all the drives in the computer should be listed there. You can double click them and they will open - might ask for your password, depending on how the permissions are set. Otherwise go to terminal and type sudo mount /dev/xxxx (substituting xxxx for the name of the drive).

When I double click, it says "You are not privileged to mount the disk" :(

How do I find the name of the disk when I type the sudo code ? Do I have to use the partition name like (Downloads) ? :confused:

---

### Post by gnudoc on 2009-09-19
I am not familiar with NTFS Config Tool but it sounds like your program has unmounted the drive in such a way that means only it can remount it.

Clearly the administrator ("root" in linux terms) can also remount it, as root can do anything. But when you are in the graphical interface in ubuntu, you will be acting as a normal user, not the administrator (unless you have made some changes that are extremely inadvisable to make).

So, you need to remount this drive from the command line, but this is not going to be straightforward because you don't seem to know its designation. Do you remember if the program mentioned a code for the partition? Something like hda1 or sdb6?

If not, go to the command line (Applications->Accessories->Terminal) and type ```
sudo fdisk -l
``` This should list all the hard drives in your system with all of their partitions, and some properties for each.

Post the output of this command, and tell us as much as you know of the setup of your missing partition (how big is it, if there is more than one harddrive in your system, what size is the harddrive that it lives on, etc)

If we don't manage to fix it this way, there is another method involving the GUI that we could use, but you'll probably learn more about your computer doing this, so let's try this first!

gnudoc

---

