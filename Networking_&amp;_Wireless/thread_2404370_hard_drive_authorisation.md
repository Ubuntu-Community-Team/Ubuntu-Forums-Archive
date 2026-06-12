---
title: "hard drive authorisation"
date: 2018-10-23
forum: Networking &amp; Wireless
---

### Post by 0dy553u5 on 2018-10-23
Hey there,

I am setting up a NAS server on a raspberry pi 3 using samba, and therefore, I am using an external hard drive . It's a 2TB sata hard drive with a usb dock, which I have used before and works perfectly. The NAS itself works as well, but the access to the hard drive is denied no matter what I do (so I can read/write files on the sd card, and then I do find them when i log from another computer). The weird thing is that access to the hard drive is denied from any computer (I tried on windows and android), and even from the pi itself (when i go to the right folder and type "cd disk1" I get "-bash: cd: disk1 :  Permission denied") and apparently you're not allowed to do "sudo cd". Please does anyone have a clue of what's the problem? Thank you so much.

---

### Post by TheFu on 2018-10-23
How can I say this nicely.  Using a Raspberry Pi for a NAS is like using a tricycle powered by a 3 yr old for your 25 mile drive to work.  The Pi architecture uses a shared USB2 controller for everything, USB2, networking are the keys here.  Slow.  There are better solutions for not all that much more cash.  For $65, there are more powerful ARM SBCs that support real GigE networking and USB3 ports. An $80 used computer with GigE networking is faster.  A 5 yr old used chromebook with USB3 adaptor that has USB3 ports and a GigE adapter ($20) would be faster. The new r-pi v3+ claims to have a GigE network. It isn't.
Ok, I'm done with that.

On all Unix systems, the type of file system matters for storage.  Most USB drives will come pre-formatted with NTFS.  That is a poor choice for backups for many reasons.  There are a number of different ways you can setup a new disk.  Here's what I would do, knowing absolutely ZERO about your situation.

I would use gparted to perform most of these things using any Linux desktop.  I'd use an Intel computer with real USB3 just so it isn't slow. Steps:
* backup any data on the disk you can't loose. We will be totally wiping everything.
* Create a new, fresh, GPT partition table.
* Create a new, fresh, partition. I'd probably use the entire disk, so that would use total-1 MB of the storage.  The leading 1MB is there to force partition alignment on a sector boundary.  This is best for performance.  NOT doing it can make the drive 10-30% slower until fixed.  That might be 8+ yrs. gparted handles this for us, automatically.
* Format that new partition, /dev/sdZ1, with ext4.  There are many other choices, but ext4 is a good, general purpose, file system.
* Write everything and verify each step completes successfully.
* Eject the disk (some systems will automatic mount it).  Any GUI file manager will have an "eject" icon - unplug the USB from the computer.

Now move to the Raspberry pi and connect the USB disk to it, powered up.
* sudo mkdir /backup  # this will be the mount point for the new USB partition; there are many reasons NOT to use /mnt/ or /media/
* sudo mount /dev/sdZ1 /backup   # you'll need to figure out the actual device name.
* Fix the samba config to point at /backup  # I'll assume you can do that.
* Fix the permissions for /backup to be what you need.  The required permissions will totally depend on the userids that need to write to the storage.  If you are backing up different computers, I'd always use the {hostname} at the 2nd level to keep them separate.

Comments on cmds run above:   *cd disk1* isn't helpful without knowing the current directory and the permissions of the disk1 directory.  *sudo cd* is completely useless. sudo creates a subshell, runs the request, then exits, which returns to the current userid and PWD of that userid.

So, what userid(s) need to have write access to the storage from the r-pi side.  We can deal with Samba later.  If the client machines aren't Windows, I'd strongly suggest using the native file sharing protocol for Unix systems, NFS.  There are many reasons, not just because NFS is faster but it supports native permissions.

So, please gather some facts and post them.

For samba, run **testparm** and post that output using *code tags*.
For permissions, run **ls -al /path/to/mounted/top/level **and post that output using *code tags*.  Please.

---

