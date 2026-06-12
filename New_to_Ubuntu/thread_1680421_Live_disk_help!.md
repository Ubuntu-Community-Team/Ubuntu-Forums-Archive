---
title: "Live disk help!"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Jayavfc on 2011-02-02
I've been trying to boot the Ubuntu live cd, i burn the iso image, but when come to booting the screen goes funny! I've burnt at the lowest speed i can did it 4x on nero 6 and 3.5 on infra. Have posted this on a linux forum but if anyone can give me a idea where i'm going wrong. The link is to what my screen looks likes when booting
[http://img41.imageshack.us/i/img00039201101312141.jpg/](http://img41.imageshack.us/i/img00039201101312141.jpg/)

---

### Post by uRock on 2011-02-02
Hello and welcome to the forums.

What are the hardware specs of your system? CPU GPU RAM

Regards,
uRock

---

### Post by Jayavfc on 2011-02-02
Just ran belarc

Windows XP Professional Service Pack 3 (build 2600)
Install Language: English (United States)
System Locale: English (United States)	 	IBM 8172W5K ThinkCentre S51
System Serial Number: LMPW9TX
Enclosure Type: Low Profile Desktop
Processor a	 	Main Circuit Board b
3.00 gigahertz Intel Pentium 4
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache
Hyper-threaded (2 total)	 	Board: IBM IBM 
Bus Clock: 200 megahertz
BIOS: IBM 2BKT48AUS 11/02/2005
Drives	 	Memory Modules c,d
496.24 Gigabytes Usable Hard Drive Capacity
435.84 Gigabytes Hard Drive Free Space

TSSTcorp CDDVDW SH-S222A [Optical drive]
3.5" format removeable media [Floppy drive]

ST3500418AS [Hard drive] (500.11 GB) -- drive 0, s/n 5VML6H83, rev CC46, SMART Status: Healthy	 	2040 Megabytes Usable Installed Memory

Slot 'J9' has 1024 MB
Slot 'J10' is Empty
Slot 'J3' has 1024 MB
Slot 'J4' is Empty

---

### Post by switch10 on 2011-02-02
boot your live cd, switch to a tty (ctrl+alt+f1) and post the output (at least the "product" line)of:

```
sudo lshw -C video
```

we need to know what video card you are using.

---

### Post by Jayavfc on 2011-02-02
i did that but couldn't see nothing, dunno if it because of the screen cutting off, i did the diaxg check in windows and this my display name and model if it helps

Intel(r)82915g/gv/910gl express chipset family

---

### Post by quadproc on 2011-02-02
> **Jayavfc said:**
> I've been trying to boot the Ubuntu live cd, i burn the iso image, but when come to booting the screen goes funny! I've burnt at the lowest speed i can did it 4x on nero 6 and 3.5 on infra. 
Did you check the md5sum of your CDROM?  If there is any problem in the CDROM itself or in the CD reader then your md5sum will not agree.

You can find instructions on how to do the check at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And you can find the correct md5sum value at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If the md5sum is correct then the problem is not in the CDROM and I would suspect your hardware first.  You might try running any hardware diagnostics that you have for an existing and working operating system on that computer.

Just a wild thought - did you download the 32 or 64 bit version?  For a P4 you would need 32 bit.

quadproc

---

### Post by Jayavfc on 2011-02-02
ok the md5 sum seems to be wrong     3c522b01341cfd3d233c0866e10533fe  is the md5 which comes with the the iso download for the 32bit 10.10 desktop i3686 iso.

---

### Post by sandyd on 2011-02-02
> **Jayavfc said:**
> ok the md5 sum seems to be wrong     3c522b01341cfd3d233c0866e10533fe  is the md5 which comes with the the iso download for the 32bit 10.10 desktop i3686 iso.
torrenting it instead might help, because torrents check the md5 of each chunk

---

### Post by Jayavfc on 2011-02-02
> **sandyd said:**
> torrenting it instead might help, because torrents check the md5 of each chunk

Any links or a site with torrent links??

---

### Post by sandyd on 2011-02-02
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)
desktop-i386

---

### Post by Jayavfc on 2011-02-02
Ive made sure the mdsum is correct when downloaded from the torrent, when i burn to disc the md5sum changes, will this be causing the problem?

---

### Post by uRock on 2011-02-02
Are you burning it as a CD image or as a file on a CD?

---

### Post by Jayavfc on 2011-02-02
I'm burning as a image, i've done it with nero 6, infra and also magic iso to make sure, same problems happen when i boot up, its there but it keeps rolling off the screen

---

