---
title: "sd card not showing up"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by ubunguy on 2010-07-04
Hello beginner here everything else i pretty much  setup but this one is really starting to bug me.

when i take any one of my sd cards and put it in a card reader /pen drive and insert it via usb i can see the folders the drive pops up etc.

but the problem is when i insert the actual sd card into the netbook it self ,i dont see nothing im using a acer 532 aspire.

i know the card reader works but when im out i may not have my card reader thats more stuff to carry.

so what would you suggest i do to fix this issue?:cry:

---

### Post by NUboon2Age on 2010-07-04
First thing, which version of Ubuntu are you using?

You might try going to the #ubuntu-beginners irc channel for troubleshooting help and maybe one of the volunteers there will know something about this.  If you are not set up with an irc client yet you could use [http://tinyurl.com/irc-ubuntu-beginners](http://tinyurl.com/irc-ubuntu-beginners)

---

### Post by warfacegod on 2010-07-04
The irc channels have a pretty bad reputation when it comes to newbs. They aren't well known for friendliness to say the least. I'm not saying you should stay away. Just that you may not get the kind of response you bargained for.

Here's an example: [http://ubuntuforums.org/showthread.php?t=1523377](http://ubuntuforums.org/showthread.php?t=1523377)

---

### Post by MooPi on 2010-07-04
After you have inserted your SD card into the slot open a terminal. Type ```
sudo fdisk -l
``` Hopefully your SD card should be listed as a drive and it should look something like this,   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3        2112     3860480    b  W95 FAT32

```
Now in terminal ```
sudo mkdir /media/usb1
``` ```
sudo mount /dev/sdb1 /media/usb1
``` the directory usb1 can be named whatever you'd like. This is just one option another could be editing /etc/fstab file to include your SD card reader.

---

### Post by hackerseraph on 2010-07-04
did you originally use the sd slot to install ubuntu?

I know for me and a few other users that when you install from usb, it might cause that port to lock up [thumbdrive, external optical drive, SD slot using usb interface on the mainboard, etc.], and you have to go and remove that entry from the fstab.

---

### Post by cavalier911 on 2010-07-04
Read here: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
Acer Aspire One 532h
Known Issues:
The (multifuntion) cardreader shows up in lsusb, but doesn´t work.

---

