---
title: "Can't Change Folder Permissions"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by noseshark on 2011-07-12
[FONT=Georgia][SIZE=2][COLOR=DarkGreen]My HTC cell phone is connected to my computer. The memory card is appearing on my desktop but I can't add or delete files from it. I've been on google all day and I still can't fix it someone please help. I just want some music on my phone :([/COLOR][/SIZE][/FONT]

[IMG]http://i982.photobucket.com/albums/ae305/noseshark/Screenshot-3.png[/IMG]

---

### Post by wildmanne39 on 2011-07-12
Hi, open nautilus by typing
```
gksu nautilus
```
after it opens right click on the folder go to properties click permissions and change them to give you read and write access.

---

### Post by mcduck on 2011-07-12
> **noseshark said:**
> [FONT=Georgia][SIZE=2][COLOR=DarkGreen]My HTC cell phone is connected to my computer. The memory card is appearing on my desktop but I can't add or delete files from it. I've been on google all day and I still can't fix it someone please help. I just want some music on my phone :([/COLOR][/SIZE][/FONT]

[IMG]http://i982.photobucket.com/albums/ae305/noseshark/Screenshot-3.png[/IMG]

The memory card is formatted in FAT, which doesn't support file and directory ownerships & permissions as they are used in Linux. You can't change permissions of single files or directories on FAT filesystems, the file system simply has no way to handle such things.

So, your problem lies somewhere else than in the file permissions. Besides, the memory card of your phone (or really, any removable FAT drive) should already be mounted with enough permissions to allow you to add or remove files from it. 

Actually, the error you got "read-only file system" would indicate that the drive was intentionally mounted as read-only, which usually happens in case there are any I/O errors or the file system is otherwise not seen as "clean".

One common thing that might cause this is pulling a memory card/removable drive out of a Windows machine without safely removing it first. If you might have done that, the solution is to plug it back to a Win system and remove it correctly this time. That should mark the file system clean and Ubuntu should mount it as read/write again.

Other than that, your best bet would be running "tail -f /var/log/syslog" in a terminal and then plugging in the phone, just to see how the system is detecting it and to catch any error messages.

---

### Post by noseshark on 2011-07-12
I don't own windows on my PC. The only thing running on windows is my cellphone. Before all this I even tryed formatting my card with the first option (works with all systems) due to my cell phone itself.

i typed in tail -f /var/log/syslog then plugged in my phone and this came up

Jul 12 10:33:24 noseshark kernel: [28124.772463] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jul 12 10:33:25 noseshark kernel: [28126.381614] FAT: Filesystem error (dev sdc1)
Jul 12 10:33:25 noseshark kernel: [28126.381626]     invalid access to FAT (entry 0xd606e550)
Jul 12 10:33:25 noseshark kernel: [28126.381636] FAT: Filesystem has been set read-only
Jul 12 10:36:21 noseshark kernel: [28302.088109] usb 1-4.1: reset high speed USB device using ehci_hcd and address 17


If I format my card with other options like (works only in linux) it wont work in my phone right?

---

### Post by noseshark on 2011-07-12
It does the same when I try to change permissions with nautilus as it did before :(

---

### Post by cmcanulty on 2011-07-12
Try this fix then you won't need a windows machine.

```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall
```

---

### Post by mcduck on 2011-07-12
> **noseshark said:**
> I don't own windows on my PC. The only thing running on windows is my cellphone. Before all this I even tryed formatting my card with the first option (works with all systems) due to my cell phone itself.

i typed in tail -f /var/log/syslog then plugged in my phone and this came up

Jul 12 10:33:24 noseshark kernel: [28124.772463] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jul 12 10:33:25 noseshark kernel: [28126.381614] FAT: Filesystem error (dev sdc1)
Jul 12 10:33:25 noseshark kernel: [28126.381626]     invalid access to FAT (entry 0xd606e550)
Jul 12 10:33:25 noseshark kernel: [28126.381636] FAT: Filesystem has been set read-only
Jul 12 10:36:21 noseshark kernel: [28302.088109] usb 1-4.1: reset high speed USB device using ehci_hcd and address 17


If I format my card with other options like (works only in linux) it wont work in my phone right?

Based on that, the filesystem on the card is broken, which is why it gets mounted read-only to prevent further damage.

Backup your files form the card, and try formatting it again. And yes, you'll have to use FAT, it's quite unlikely you phone would support anything else. But with a bit of luck formatting the card is enough to fix the problem.

In case that's not enough, you could try removing the partition from the card and creating a new one. And if even that's not enough, it's time to buy a new card...

(what comes to not being able to set the permissions, like I said, FAT doesn't support that. Even if the card was working correctly and was mounted as read/write, you *still* wouldn't be able to change any permissions on it. It's not a permission issue you are having, but a broken filesystem.)

---

### Post by noseshark on 2011-07-12
I guess that makes sence
Thanks anyway :)

---

