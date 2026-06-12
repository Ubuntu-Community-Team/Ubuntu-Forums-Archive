---
title: "How to keep changes using USB stick LiveCD"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by donnybb on 2010-12-29
I am making headway.  I downloaded Ubuntu 10.10 ISO and then used Unetbootin to install onto my 4GB USB stick.  Everything boots up and works just fine.  I downloaded Adobe Flash for Linux and that worked well also.  When I rebooted, all the changes to wallpaper etc were gone and I had to download Flash again.  How can I make it so the changes are permanent?
Also - is there a way to lock it after I make the changes so there are no viruses that can attack my USB installation?  That is, something like write protecting the stick after changes are made permanent.

---

### Post by davidmohammed on 2010-12-29
You cant "save" changes using a LiveCD - 

If you want ubuntu permanently on a USB stick then follow instructions such as [these]("http://www.pendrivelinux.com/").

---

### Post by sml156 on 2010-12-29
Im not sure what the file size of flash is but it might be bigger than your persistence file

---

### Post by donnybb on 2010-12-29
I think I have plenty of disc space as the Flash for Linux is 4.66 MB and I am using a 4GB stick.  What is a persistence file and where is it located?  Can I just copy the Flash for Linux file there?

---

### Post by a quarter past seven on 2010-12-29
[QUOTE=donnybb;10294391]I think I have plenty of disc space as the Flash for Linux is 4.66 MB and I am using a 4GB stick.  What is a persistence file and where is it located?  Can I just copy the Flash for Linux file there?[/Q


when you install the live disk to a usb or cd it gives you the option to have a persistent cache up to 4gb which saves all youre changes and stuff if you didnt do that then i think you have to re burn the usb but this time make sure you select the persistent cache option when you do

---

### Post by donnybb on 2010-12-29
I used Unetbootin to create my LiveUSB stick.  It did not have an option to create a persistence partition.  I downloaded Universal USB Installer and it does have that option.  I tried using it (and the same Ubuntu ISO) and it did not work.  That is, I selected a 2GB persistent partition and it seemed to install without problems.  When i rebooted, it got to the screen where the word Ubuntu is and there are 5 dots below it.  It seems to be stuck there.  I repeated the process, except I did not specify a persistence partition this time.  I got the same thing: stuck during boot.  So, to summarize:
Unetbootin works perfectly, but does not have a persistence option.
Universal USB Installer has a persistence option, but does not make a usable USB stick.
The computer I use to create the USB stick is a Windows7 - 64 bit machine.  Could that be the problem with Uni-USB Installer?  I do have an XP Pro machine I could try it with.

---

### Post by C.S.Cameron on 2010-12-29
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by I2k4 on 2010-12-30
I'm running off a 4GB drive with 3GB of persistence to save changes - no problems.  I just used the official Ubuntu download and install instructions, but chose the "Persistence" option with the PenDrive installer at Step 2 - everything I do from one boot to the next is saved.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Seems to me your installer doesn't have the same functionality for persistence and you should use the recommended one.

---

