---
title: "First time ubuntu, and get this on reboot"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by horgh64 on 2011-03-10
Wat do, gents? In the plainest language possible, if you can. As I said, first time user.

[IMG]http://img691.imageshack.us/img691/7483/ubuntud.jpg[/IMG]

---

### Post by Jeanke on 2011-03-10
Hi,

Can you give some more info?
Do you get this message when you try to install Ubuntu with live cd?
Which version of Ubuntu are you trying to install?
Can you still boot into Windows?
If so, did you try to run chkdsk /f and reboot twice as instructed in the message?

Welcome btw ;)

---

### Post by |{urse on 2011-03-10
Lucky \\:D/

I'd say something most likely went wrong during install. You might want to re-install.

---

### Post by deeZee on 2011-03-10
I've never seen that error before, but it's telling you to:

Restart your computer and select Windows.

After you login, run the following command 'chkdsk /r' (without quotes) from a command prompt.

Restart your computer and select Windows again.

After windows has loaded, restart your computer again, and select Ubuntu.  From there your installation should resume.

---

### Post by horgh64 on 2011-03-10
> **Jeanke said:**
> Hi,

Can you give some more info?
Do you get this message when you try to install Ubuntu with live cd?
Which version of Ubuntu are you trying to install?
Can you still boot into Windows?
If so, did you try to run chkdsk /f and reboot twice as instructed in the message?

Welcome btw ;)

Right, so I install it as a dual boot with win7. As soon as the setup is done in windows, it asks to boot in ubuntu to finish installation. I boot it up, and unfortunately that's all I get. You can see the purple ubuntu background, it loads something and goes black screen with that.

Yeah, installing it on this computer, so I can boot back into windows no problem, but as soon as I try ubuntu again it's a no go.

And cheers! Hope I'll learn a lot from here.

---

### Post by |{urse on 2011-03-10
Also, I'm not even sure if this method still works but it might be worth a try.

[http://ubuntuforums.org/showpost.php?p=1731880&postcount=3](http://ubuntuforums.org/showpost.php?p=1731880&postcount=3)

Definitely do a chkdsk /r first.

---

### Post by grahammechanical on 2011-03-10
What do you mean when you say:

> As soon as the setup is done in windows, it asks to boot in ubuntu to finish installation.

Are you using Wubi? This is not the same a dual booting. If you are installing Ubuntu as a program inside windows, then that would explain the instruction to simply reboot into Windows.

The installation procedure cannot find the Ubuntu image (files if you like) to install from. How did you create the Ubuntu install CD or USB stick?

Regards.

---

### Post by horgh64 on 2011-03-11
> **grahammechanical said:**
> What do you mean when you say:



Are you using Wubi? This is not the same a dual booting. If you are installing Ubuntu as a program inside windows, then that would explain the instruction to simply reboot into Windows.

The installation procedure cannot find the Ubuntu image (files if you like) to install from. How did you create the Ubuntu install CD or USB stick?

Regards.
Yeah, installing into windows. Sorry I understood it was similar if not the same. I burnt the iso to a cd, and the installer could be read on it when in windows (installed it from there first) but not in ubuntu.

---

### Post by fabricator4 on 2011-03-11
> **horgh64 said:**
> Yeah, installing into windows. Sorry I understood it was similar if not the same. I burnt the iso to a cd, and the installer could be read on it when in windows (installed it from there first) but not in ubuntu.

You're doing a Wubi install into Windows.  It's telling you that there was a problem with the windows filesystem.  You need to run the chkdsk /r as it says to do. Reboot and run chkdisk /r again.  Once you run chkdsk /r and get no errors/fixes, you can be sure the filesystem is OK

You can then do a Wubi install of Ubuntu by inserting the CD while Windows it booted - the installer should autostart.  I would first check to see if Ubuntu is already installed in 'add or update programs' and delete it if it is.  You can then insert the CD and let it start the install again.

Chris.

---

### Post by bcbc on 2011-03-11
> **horgh64 said:**
> Yeah, installing into windows. Sorry I understood it was similar if not the same. I burnt the iso to a cd, and the installer could be read on it when in windows (installed it from there first) but not in ubuntu.

It is similar... the difference is 1) how you install and 2) the fact that it uses a virtual disk (so you don't need to partition your computer) and 3) the way it boots.

Wubi is useful to try out Ubuntu. It runs the same as a dualboot except for the virtual disk.

PS that message to run chkdsk is pretty generic. While it's a good idea, and won't hurt, it's probably not going to fix the issue.

If you can post the log file ( in the %temp% folder, called wubi-xx.xx-rxxx.log) that might show some clues.

---

### Post by horgh64 on 2011-03-11
> **bcbc said:**
> It is similar... the difference is 1) how you install and 2) the fact that it uses a virtual disk (so you don't need to partition your computer) and 3) the way it boots.

Wubi is useful to try out Ubuntu. It runs the same as a dualboot except for the virtual disk.

PS that message to run chkdsk is pretty generic. While it's a good idea, and won't hurt, it's probably not going to fix the issue.

If you can post the log file ( in the %temp% folder, called wubi-xx.xx-rxxx.log) that might show some clues.

You're right. Ran it, took a while, no fix. Would you suggest installing it on a partition?

---

### Post by bcbc on 2011-03-11
> **horgh64 said:**
> Would you suggest installing it on a partition?
If you are comfortable with partitioning, are able to (in the sense that you don't already have 4 primary partitions) and you are planning to use Ubuntu long-term - then it's always better to partition.

If you're just trying it out and might want to remove it, then I'd recommend Wubi.

Note: partitioning is generally safe, but there is always a small risk of data loss. So backup anything important. Also make sure you have your OS rescue disks beforehand.

---

