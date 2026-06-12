---
title: "oi vey"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by protpisys on 2011-05-29
I posted about 2 weeks ago about problems I was having booting into 11.04...I've tried reinstalling over the current and got nothing; then a complete reinstall wasn't allowed due to partition issues. Now I'm just frustrated as hell.

I'm at the point now where I'm just going to start again from scratch. But before I erase and reinstall I want to save the data in my current home file. Booting live from the disc prohibits copying files, so my question is how can I salvage that stuff before I delete the partition to begin the process? Thanks

---

### Post by beringse on 2011-05-29
Have you given Deja Dup or some other kind of back up utility a try so you could save your home folder to an external or other type of media?

---

### Post by protpisys on 2011-05-29
no, I'm looking for suggestions how to do it, will this work even though I can't access Ubuntu at all?

---

### Post by dFlyer on 2011-05-29
First, we need a little information about your system:

Are you dual booting ubuntu and some other os?

Have you ever been able to boot into ubuntu?

What is the other OS?

When you say copy data in your home folder are you able to mount your hdd using ubuntu live cd?

---

### Post by protpisys on 2011-05-29
I just checked the site and it doesn't seem to help me here, I"m looking to salvage my home folder from an Ubuntu system that is no longer running. It's not a back up issue, at this point, I got to get to the stuff to save it elsewhere

---

### Post by protpisys on 2011-05-29
I dual booting w/Vista, I've been doing so since version 9.04 and was doing fine until about 2 weeks after using "update manager" to install 11.04, it's not the ability to mount a drive that's the issue, it's that the live disc doesn't allow me to copy and move files from the corrupted, I  assume, partition

---

### Post by dFlyer on 2011-05-29
Have you replaced your damage drive with a new one? or are you trying to copy the files back to the damage drive in another partition or folder?

---

### Post by KL_72_TR on 2011-05-29
I was thinking about using the command line and [cp] to Vista.

---

### Post by protpisys on 2011-05-29
It's not the drive, if anything it's the partition. It's the same harddrive I boot Vista from and that works, as well as one can expect it to. I originally posted this about 2 weeks ago and go no real help with it. When I turn my computer on I get to the screen where one chooses the os, at that point if I choose Ubuntu it goes to a blank screen and hangs, but if I choose Vitsa it works as usual.

---

### Post by dFlyer on 2011-05-29
I'm assuming you can mount the ubuntu /home partition. How much data are you talking about? If you have a drive failing copying data to another partition isn't going to help. Copying it to an external hard drive or usb may help.

---

### Post by protpisys on 2011-05-29
> **dFlyer said:**
> I'm assuming you can mount the ubuntu /home partition. How much data are you talking about? If you have a drive failing copying data to another partition isn't going to help. Copying it to an external hard drive or usb may help.

I cannot copy or save data from the corrupted version of Ubuntu using the live disc, it is not allowed...it isn't a matter of mounting media. The live disc will not allow me to copy and/or move the existing data as it, I assume, from a different user

---

### Post by coffeecat on 2011-05-29
> **protpisys said:**
> Booting live from the disc prohibits copying files, so my question is how can I salvage that stuff before I delete the partition to begin the process? Thanks

That's a common problem, but easily solved. The cause is that your UID in your permanent installation is 1000, but the UID of the live "ubuntu" account is 99. Linux permissions, quite rightly, deny you access, although it is frustrating when you want to backup your own files.

The workaround. First, in the live CD desktop session mount your Ubuntu partition by clicking on it in the Places left pane of a Nautilus window. Now close that window. Now open a root nautilus with 'gksudo nautilus' in the terminal. Click on "File system" in the left pane of the root nautilus window. That shows you the filesystem of the live session, not the filesystem of your Ubuntu system. Open the media folder and find the mountpoint of your Ubuntu system. Open that and you will see the filesystem of your Ubuntu system and you should be able to navigate to your home folder without any hindrance now.

---

### Post by protpisys on 2011-05-29
thanks I'll give it a shot

---

### Post by protpisys on 2011-06-06
> **coffeecat said:**
> That's a common problem, but easily solved. The cause is that your UID in your permanent installation is 1000, but the UID of the live "ubuntu" account is 99. Linux permissions, quite rightly, deny you access, although it is frustrating when you want to backup your own files.

The workaround. First, in the live CD desktop session mount your Ubuntu partition by clicking on it in the Places left pane of a Nautilus window. Now close that window. Now open a root nautilus with 'gksudo nautilus' in the terminal. Click on "File system" in the left pane of the root nautilus window. That shows you the filesystem of the live session, not the filesystem of your Ubuntu system. Open the media folder and find the mountpoint of your Ubuntu system. Open that and you will see the filesystem of your Ubuntu system and you should be able to navigate to your home folder without any hindrance now.

ok, I finally had some time and tried this...it still won't let me copy and move the file to another file system, this is what I really, really need to do. Move the contents of my home folder from the corrupted partition to a good one so I may erase the partition and start anew...I really need these files, and can't stand using windows. Thanks

---

### Post by coffeecat on 2011-06-06
> **protpisys said:**
> ok, I finally had some time and tried this...it still won't let me copy and move the file to another file system

The method I posted will certainly allow you to navigate into your home folder and copy the files. But what filesystem are you trying to copy to? That could be the problem. Is it FAT32, NTFS or a Linux filesystem? Is it on an internal partition or an external USB drive?

---

### Post by protpisys on 2011-06-06
It was to the windows partition on the same drive filesys = NTFS

---

### Post by coffeecat on 2011-06-06
Did you get an error message when you tried to copy? How did you mount it?

---

### Post by wolfen69 on 2011-06-06
Try it as root.
```
sudo su
```
then 
```
nautilus
```

It's also good to have a puppy linux cd handy. You are always root and will copy anything.

---

### Post by coffeecat on 2011-06-06
> **wolfen69 said:**
> Try it as root.

If the OP is following my suggestion of using 'gksudo nautilus' they will already have a root nautilus.

---

### Post by wolfen69 on 2011-06-06
> **coffeecat said:**
> If the OP is following my suggestion of using 'gksudo nautilus' they will already have a root nautilus.

I didn't see your post. Excuse me for trying to help.

---

### Post by coffeecat on 2011-06-06
> **wolfen69 said:**
> I didn't see your post. Excuse me for trying to help.

No please do. :) I'm puzzled as to why the OP is unable to copy to a NTFS filesystem. Any suggestions would be helpful.

---

### Post by protpisys on 2011-06-06
puppy linux cd? what's that

---

### Post by protpisys on 2011-06-06
could it be related to the the whole "not working at all" deal?

---

### Post by protpisys on 2011-06-06
I did a screen print so you could see the error message, it's on one of my posts here

---

### Post by jtarin on 2011-06-06
I suggest you CHROOT into your environment using the Live CD. This will allow you root access to that environment and give you the ability to move or copy.

---

### Post by protpisys on 2011-06-06
I noticed a slight discrepancy between the teminal commands suggested by Coffeecat and Wolfen69, so I went back in and tried again with Wolfen69"s code and got the same result  as seen in the screen print above, but it also produced this in the terminal itself:

(nautilus:12908): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:12908): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs



is this significant? and, can it be corrected? Thanks for all the effort folks.

---

### Post by protpisys on 2011-06-06
I have no idea why those happy faces are there, but in both cases they replace an "8" followed by a close parens ")"
ie: 12908) and 12908) respectively...thanks again

---

### Post by protpisys on 2011-06-06
CHROOT? how do I do that

---

### Post by jtarin on 2011-06-06
> **protpisys said:**
> CHROOT? how do I do that[URL="https://help.ubuntu.com/community/Grub2#ChRoot"]
Print these instructions on the CHROOT link out.
Go here[/URL] and follow the instructions, but when you come to _**steps 8,9 and 10 skip them**_ at that point proceed to your file copy operation. When finished exit by following the remaining steps to the end.

---

