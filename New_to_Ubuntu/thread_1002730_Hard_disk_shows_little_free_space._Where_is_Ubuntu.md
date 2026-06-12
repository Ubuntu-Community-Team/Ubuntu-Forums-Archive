---
title: "Hard disk shows little free space. Where is Ubuntu stored?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by itsols on 2008-12-05
I installed Ubuntu 7.10 on my laptop to dual boot with Windows XP (which I already had). I'm sure I partitioned my laptop with 25GB EACH, and Windows was on my C drive.

Lately I've been sticking more onto Ubuntu and I'm trying to stop using XP altogether. So I've been busy setting up different packages and testing them. Now I have a problem. Strangely I find that I have something like 700 MB left as free space.

But I've only installed a few programs AFTER the Ubuntu CD and I'm CERTAIN that the HDD should have more space.

The bottom line:

1. How do I know where my Ubuntu is installed?
2. Is there a way of increasing the partition size without affecting anything?
3. I discovered the problem when I tried to upgrade to 8.04 and it reported that my drive had no space. How bad is this?

I hope someone out there can explain this issue easily and resolve it.

Many thanks.
Khalid

---

### Post by taurus on 2008-12-05
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by drs305 on 2008-12-05
You may have a lot of deleted files still taking up space on your ubuntu partition. The link below is to a tutorial that addresses how to find and eliminate all your trash files, as well as a few other things to take a look at to free up space:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by miniyak on 2008-12-05
that simple code works a lot better than the disc usage analyzer, i have a 30gb hard drive an the disc usage analyzer tells me its a 50. typing "df -h" into the terminal yielded the right results though

---

### Post by itsols on 2008-12-05
Oh Noooo!! I see that the disk shows as a 4 GB drive. Now, here's the result of the df command as pointed out by taurus...

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.1G  3.6G  290M  93% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  100K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-16-generic/volatile

And when I open the File Browser, I see these on the left panel, among other things:

File System
26.4 GB Volume
KLAP2

Explanation:
File System is where my Windows XP sits.
26.4 GB Volume is WHERE I THOUGHT the dual boot Ubuntu was installed.
KLAP2 is apparently a crazy partition I don't know how this tiny thing ever got here. Also it seems like my Ubuntu OS is on KLAP2.

Is there something I could do to fix this?
Thanks again!

---

### Post by bodhi.zazen on 2008-12-05
Looks like your partition for Ubuntu is quite small (4.1G).

Boot the desktop CD and from there you can manage (resize) your partitions from there.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by itsols on 2008-12-05
> **bodhi.zazen said:**
> 
Boot the desktop CD and from there you can manage (resize) your partitions from there.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

I appreciate the info above. I'd like to know if resizing the hard drive will cause any data/program loss.

Many thanks.

---

### Post by bodhi.zazen on 2008-12-05
> **itsols said:**
> I appreciate the info above. I'd like to know if resizing the hard drive will cause any data/program loss.

Many thanks.

Normally no it does not. 99.99% of the time your partitions will be resized without any problem. 

Because of the occasional problem, back up any mission critical data.

Windows partitions (ntfs or fat (vfat)) need to be defragmented first.

---

