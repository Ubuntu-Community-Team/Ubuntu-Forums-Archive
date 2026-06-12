---
title: "booting with no operating system"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by taylorwoods on 2009-01-22
I managed to erase windows from my laptop and want to install Ubuntu.  How do I boot up so that I can install Ubuntu?

---

### Post by taurus on 2009-01-22
Go into the BIOS and make sure CD-ROM is the first bootable device.  Then, insert Ubuntu LiveCD and off you go.

---

### Post by Michael.Godawski on 2009-01-22
hi,

have also a look at some useful sites for beginners:


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[*][http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[*][http://godawski.oxyhost.com/ubuntu.html](http://godawski.oxyhost.com/ubuntu.html)
[/LIST]

---

### Post by lkraemer on 2009-01-22
Most likely you will need to have access to at least the Wifi
Driver that was being used with your Wifi card on Windows.
I hope you have a copy of it available, if you need it.

I'd start by getting a LiveCD of Gparted, and then remove all
existing partitions from your Windows Hard Drive and start fresh.

After Removing all Windows Partitions:
Create the Partitions you will use with Ubuntu as ext3 and Format.
Also create a Linux-Swap partition twice the size of your RAM and format.
REMEMBER: There is a MAXIMUM of FOUR Primary Partitions on your Hard Drive.

You can use just two Partitions (/ and Linux-Swap or add another Distro as
you desire.)  Just limit the total to four...unless you decide to use
extended partitions.

Then, insert the Ubuntu LiveCD and install Ubuntu.

Then use the Windows Wifi Driver to make your Wifi work with Ndiswrapper.
OR use the instructions from this forum by searching for your Wifi
Card's HOWTO: with SEARCH.

Good Luck.

lkraemer

---

