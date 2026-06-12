---
title: "Uninstalling Ubuntu (grub)"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by therabidbadger on 2009-07-30
History:
I had my MSI Wind set up in a dual boot with windows and UNR. I had not used UNR in like a month so I attempted to format that part of the hard drive and use it for something else. 

My Attempts:
Using the hardy live CD and partition editor, I formatted that part of the hard drive into blank FAT32.

The Result:
When I rebooted the machine, grub (I think 1.5) came up with error 17 and it wouldn't let it go further. 

What I did:
I just installed hardy and was able to get to windows. 

My Problem:
How do I get Ubuntu and Grub off my system so that Windows will just boot up automatically.

---

### Post by wojox on 2009-07-30
[https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/1800](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/1800)

---

### Post by Het Irv on 2009-07-30
Stick in a Windows Boot CD, and pull up the Recovery Console.  Use the command "fixmbr" and it reinstall the Windows Boot Loader to your Master Boot Record.

---

### Post by egalvan on 2009-07-30
> **Het Irv said:**
> Stick in a Windows Boot CD, and pull up the Recovery Console.  

And if you don't have access to a Win Boot CD,
try SuperGRUB LiveCD

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

herman has some good instructions for this...

[http://members.iinet.net.au/~herman546/p18.html#Super_Grub_Disk](http://members.iinet.net.au/~herman546/p18.html#Super_Grub_Disk)


And this thread...

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

