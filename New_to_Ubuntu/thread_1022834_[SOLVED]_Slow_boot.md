---
title: "[SOLVED] Slow boot"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by antony_css on 2008-12-27
I am using hardy LTS...
booting have been slow for months and i don't know why...
recently I installed bootchart and it generated this chart:

It takes 2min to boot!!!:(:(:(
Do I need to "trim" some sort of processes and services? And how?

P.S.: Sometimes it takes so slow that it affects loading of applets after log in, such as the "The panel encountered a problem while loading "OAFIID: GNOME_MultiLoadApplet" prompt. Is this because it exceeds the loading time limit?

---

### Post by antony_css on 2008-12-27
Here is the dmesg message during boot time:

---

### Post by namdung on 2008-12-27
There are many things that goes to improve ur boot performance.

*System-->Preferences-->Sessions*
Uncheck services not required.

```
sudo gedit /boot/grub/menu.lst
```
Then search for the line that reads timeout and change the value to read
either 1, for a one second countdown, or 0, to disable the boot menu
completely.

```
sudo gedit /etc/init.d/rc
```
Change ***CONCURRENCY=shell***. This will enable multicore processors to run startup scripts in parallel.

Reboot and see the difference.

BTW what is ur hardware specs?

---

### Post by Elfy on 2008-12-27
You have 2 things apparently taking a long time - readahead and linux-restricted.

From your dmesg you can see that there is a 70second lag between lines 363 and 364 - do you have a disc referenced in fstba not connected at boot? That would be a first guess from me

Have a look in you xorg log to see if there's anything in there as well.

---

### Post by antony_css on 2008-12-27
> Have a look in you xorg log to see if there's anything in there as well.
Could you tell me what is "xorg"? Is that a folder/file that I can browse in nautilus?
Or anything like a conf file?

Sorry I am just a newbie...

---

### Post by antony_css on 2008-12-27
> System-->Preferences-->Sessions
Uncheck services not required.

This was done well before the problem comes.
I unchecked following services:
Bluetooth manager
Evolution Alarm Notifier

> 
Code:

sudo gedit /boot/grub/menu.lst

Then search for the line that reads timeout and change the value to read
either 1, for a one second countdown, or 0, to disable the boot menu
completely.

Sorry, I am using Ubuntu-XP dual and I just need that.

> 
Code:

sudo gedit /etc/init.d/rc

Change CONCURRENCY=shell. This will enable multicore processors to run startup scripts in parallel.

Reboot and see the difference.
I will do this but I don't think this will work.
According to the bootchart, most of the boot time is wasted on delay on I/O wait and reading hard disk, so parallel running may not work...

> what is ur hardware specs?
Well, I don't know how to show these... Which command should be run on the console?

---

### Post by antony_css on 2008-12-27
I looked into the /var/log folder and I found the file Xorg.0.log
It is a bit messy...:confused:

Besides, I ran "locate fstba" in the terminal and it returns nothing.

mine is a hp box with 4 card readers...
I think this is the "SCSI removable disk" that is listed in dmesg.

---

### Post by Elfy on 2008-12-27
Your issues are nothing to do with your menu list.

Run this from a terminal - run it twice - replace EE with WW the second time - post both results here please

```
cat /var/log/Xorg.0.log |grep EE
```

Those 2 commands will give you any errors or warnings xorg gives during start.

Run this command - it will show your hardware 

```
sudo lshw -short
```

xorg - deals with your x window - it's afaik the basis for what you see and underlies your desktop manager

---

### Post by antony_css on 2008-12-27
all done.

---

### Post by antony_css on 2008-12-27
Sorry I have to go to bed now... I am in +8 time zone.
I will read your reply tomorrow...
thank you.

---

### Post by Elfy on 2008-12-27
Look ok to me, I assume that you don't have any other problems.

Can you post the result of this here please

```
cat /etc/fstab
```

---

### Post by antony_css on 2008-12-27
fstab text:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=0b82d154-2059-40fd-a66d-ea45d3fe50c5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1421c02d-075c-447d-be08-b09c6d026c75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

BTW what is "readahead-list" that is shown in the bootchart? Is it required? How can I trim it?

---

### Post by antony_css on 2008-12-27
I found this thread by searching "readahead-list":
[http://ubuntuforums.org/showthread.php?t=254263&highlight=readahead-list]("http://ubuntuforums.org/showthread.php?t=254263&highlight=readahead-list")

This is pretty old... Should I have a try?

---

### Post by antony_css on 2008-12-27
Done it. It saves 1:23.

"readahead-list" takes most of the boot time.:(


BTW firestarter was run unsuccessfully for three times, until it finally detected the device ppp0. Is the slow booting related to this?

---

### Post by namdung on 2008-12-27
> **antony_css said:**
> I found this thread by searching "readahead-list":
[http://ubuntuforums.org/showthread.php?t=254263&highlight=readahead-list]("http://ubuntuforums.org/showthread.php?t=254263&highlight=readahead-list")

This is pretty old... Should I have a try?

Yes, pls try. The method is tried and tested.

---

### Post by Elfy on 2008-12-28
> **namdung said:**
> Yes, pls try. The method is tried and tested.

+1

jdong is an admin - I can't see him leaving a dodgy tutorial about

I doubt if firestarter is causing the issue - you might like to know that UFW is much easier to use than firestarter

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by konsultor on 2008-12-30
In the string
cat /var/log/Xorg.0.log |grep EE

the .o. in Xorg.o.log should be a zero:  Xort.0.log
at least on my machine with U 8.10.

ADDENDUM:
After posting, it seems the message I was responding to was removed.

---

