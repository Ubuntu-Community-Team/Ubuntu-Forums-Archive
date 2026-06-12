---
title: "Mounting windows partition in ubuntu"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by pcsphinx on 2011-07-28
Hi I just installed ubuntu 11.04 and since it was a desktop installation, the first problem i faced was that i had to switch between windows and ubuntu or keep copies of files in both.

Though i found a solution: find the partition where windows is installed, in my case it was /dev/sda3, and mount the drive using:

$mount -t ntfs /dev/sda3 /mnt/windows -o "umask=022"

but every time i restart, i have to mount the drive! is it possible i could write a program and run it at startup every time so the drive could be mounted?

or better, is there a permanent solution for accessing windows files?

i have a single C: drive in my windows.

---

### Post by coffeecat on 2011-07-28
> **pcsphinx said:**
> $mount -t ntfs /dev/sda3 /mnt/windows -o "umask=022"

You don't need to do that. Simply open a Nautilus (file browser) window, find your Windows C: partition in the left pane and click on it. The system will automount it. Easy.

> **pcsphinx said:**
> but every time i restart, i have to mount the drive! is it possible i could write a program and run it at startup every time so the drive could be mounted?

You can add a line to the system file /etc/fstab and the partition will be mounted every time you boot up. But think twice before you do that. Permanently mounting a ntfs data partition is a good idea. Permanently mounting a Windows C: partition is **not** a good idea. It is all too easy to accidentally delete/modify a Windows system file.

If you need help with /etc/fstab, post back.

---

### Post by lordievader on 2011-07-28
This is possible.
How I always do it is with the utility called "Storage Device Manager". It is in the Ubuntu Software Center.
Run it, you get a list of your hard drives with their partitions, set the mount options and mount it.
This should be permanent.
-Lordievader.

---

### Post by pcsphinx on 2011-07-28
> **coffeecat said:**
> You don't need to do that. Simply open a Nautilus (file browser) window, find your Windows C: partition in the left pane and click on it. The system will automount it. Easy.



You can add a line to the system file /etc/fstab and the partition will be mounted every time you boot up. But think twice before you do that. Permanently mounting a ntfs data partition is a good idea. Permanently mounting a Windows C: partition is **not** a good idea. It is all too easy to accidentally delete/modify a Windows system file.

If you need help with /etc/fstab, post back.

if you say permanently mounting a data file folder is a good idea, i can just mount my user folder in the drive.
regarding the nautilus, i dont wish to install a separate file browser( which i am thinking it is!)

should i install nutilus or mount the folders i require?

---

### Post by pcsphinx on 2011-07-28
> **coffeecat said:**
> You don't need to do that. Simply open a Nautilus (file browser) window, find your Windows C: partition in the left pane and click on it. The system will automount it. Easy.



You can add a line to the system file /etc/fstab and the partition will be mounted every time you boot up. But think twice before you do that. Permanently mounting a ntfs data partition is a good idea. Permanently mounting a Windows C: partition is **not** a good idea. It is all too easy to accidentally delete/modify a Windows system file.

If you need help with /etc/fstab, post back.
and yes i also need help with /etc/fstab! :)

---

### Post by centaurusa on 2011-07-28
> **pcsphinx said:**
> and yes i also need help with /etc/fstab! :)

Information on how to mount Windows' partitions automatically (at boot time) can be found at:  [http://linuxnorth.wordpress.com/2011/02/20/mounting-disks-automatically/](http://linuxnorth.wordpress.com/2011/02/20/mounting-disks-automatically/)

The posting includes references to a couple of related web sites.

---

### Post by pcsphinx on 2011-07-28
thank you :)

---

### Post by coffeecat on 2011-07-28
> **pcsphinx said:**
> if you say permanently mounting a data file folder is a good idea, i can just mount my user folder in the drive.

No, that is not what I said. I said that permanently mounting a data **partition** is a good idea. A separate partition wuold appear as D: or E: in Windows, but from what you say, I don't think you have one.

> **pcsphinx said:**
> regarding the nautilus, i dont wish to install a separate file browser( which i am thinking it is!)

should i install nutilus or mount the folders i require?

If you are running Ubuntu, then Nautilus is the name of the default file browser - the Ubuntu equivalent to Windows' Explorer. What makes you think you have to install anything?

> **pcsphinx said:**
> and yes i also need help with /etc/fstab! :)

I think we need to clarify these basic points first.

---

### Post by Mark Phelps on 2011-07-28
> **pcsphinx said:**
> Though i found a solution: find the partition where windows is installed, in my case it was /dev/sda3, and mount the drive using...

Hey folks, we're all mixing different terms here -- need to pay closer attention!

OP wants to mount their OS partition in Ubuntu, not a "data folder" or "data partition".  This is a really BAD idea -- unless the mount or fstab entries are coded to mount read-only.  Mounting Vista/WIN7 OS partitions in Ubuntu read/write is a real easy way to get filesystem corruption and then -- Vista/Win7 won't boot anymore.

In stark contrast, mounting DATA partitions is OK.

And yes -- the detail differences DO matter.

---

### Post by coffeecat on 2011-07-28
> **Mark Phelps said:**
> Hey folks, we're all mixing different terms here -- need to pay closer attention!

OP wants to mount their OS partition in Ubuntu, not a "data folder" or "data partition".  This is a really BAD idea -- unless the mount or fstab entries are coded to mount read-only.  Mounting Vista/WIN7 OS partitions in Ubuntu read/write is a real easy way to get filesystem corruption and then -- Vista/Win7 won't boot anymore.

I thought we'd already established that.

> **coffeecat said:**
> You can add a line to the system file /etc/fstab and the partition will be mounted every time you boot up. But think twice before you do that. Permanently mounting a ntfs data partition is a good idea. [SIZE="3"]Permanently mounting a Windows C: partition is **not** a good idea. It is all too easy to accidentally delete/modify a Windows system file.[/SIZE]

---

### Post by Mark Phelps on 2011-07-29
> **coffeecat said:**
> I thought we'd already established that.

Sorry ... missed that.  My mistake!

---

### Post by coffeecat on 2011-07-29
> **Mark Phelps said:**
> Sorry ... missed that.  My mistake!

No problem. In fact, I'm glad you said it. It needs emphasising. :)

It's a pity the OP misunderstood what I said about clicking on the Windows partition in a Nautilus file browser window. Because this is so quick and easy, and because it avoids having the Windows C: partition permanently mounted, I don't understand why people feel they need to post fstab howto links for inexperienced users. At least not before they find out what the OP really needs.

---

