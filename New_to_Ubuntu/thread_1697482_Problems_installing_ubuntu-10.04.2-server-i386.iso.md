---
title: "Problems installing ubuntu-10.04.2-server-i386.iso"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by MerlinCoder on 2011-02-28
Hey guys. 
 
I am having real problems trying to install the Ubuntu server edition. I have burned 5 different discs and downloaded the iso twice. Both times I checked the MD5 of the iso and got the same result: 9807160B8935289096DF8160832E358E *ubuntu-10.04.2-server-i386.iso 
 
It tells me that there was a problem reading data from the CD-ROM drive and when I do the disc scan it breaks in the same location each time: ./dists/lucid/main/binary-i386/Packages.gz 
 
The Ubuntu hashes webpage doesn't seem to match to this, although it is talking about version 10.04.1 which may be different to the one I downloaded. 
 
Any help is greatly appreciated and thanks for your time.

---

### Post by sandyd on 2011-02-28
> **MerlinCoder said:**
> Hey guys. 
 
I am having real problems trying to install the Ubuntu server edition. I have burned 5 different discs and downloaded the iso twice. Both times I checked the MD5 of the iso and got the same result: 9807160B8935289096DF8160832E358E *ubuntu-10.04.2-server-i386.iso 
 
It tells me that there was a problem reading data from the CD-ROM drive and when I do the disc scan it breaks in the same location each time: ./dists/lucid/main/binary-i386/Packages.gz 
 
The Ubuntu hashes webpage doesn't seem to match to this, although it is talking about version 10.04.1 which may be different to the one I downloaded. 
 
Any help is greatly appreciated and thanks for your time.
MD5s right [http://cdimage.ubuntu.com/ubuntu-server/lucid/daily/current/MD5SUMS](http://cdimage.ubuntu.com/ubuntu-server/lucid/daily/current/MD5SUMS)
Try using another cd drive, and burning slower.

---

### Post by MerlinCoder on 2011-02-28
Thanks for such a quick reply.

I have tried burning as slowly as possible but I havn't had any luck. Is there a way to check to see if my CD drive is running okay? I'll try burning one more disc but I'm running low so I don't want to waste too many more. I have Windows XP on it which I also installed today (my intention is to dual boot) and that installed fine.

---

### Post by robsoles on 2011-02-28
If the optical drive on the machine keeps failing you perhaps you can use unetbootin or similar to make yourself a bootable USB of the server edition ISO and install from that.

---

### Post by MerlinCoder on 2011-02-28
Thanks, USB is probably the way to go. I have managed to get it onto the USB stick using unetbootin and managed to get it to boot into the installation. I'm still having problems though as it is saying it can't find the CD in the driv., I'm sure theres a guide out there that I should be able to find...but I've been on this problem since 8PM and need to get what little sleep I can tonight and my tired eyes are probably missing something obvious.

---

### Post by MerlinCoder on 2011-03-01
I'm up and running now, thanks guys!

---

### Post by drdos2006 on 2011-03-01
Are you able to describe what you did to get you up and running ?
It would assist others.

Don't forget to mark your thread as solved when you are finished...

regards

---

### Post by MerlinCoder on 2011-03-01
Absolutely.

I'm hoping to eventually move over to cloud hosting, as such I wanted to set up a machine that has both a windows and linux environment to see which one I prefer and to get some (more) experience using applications such as putty. I have experience with the desktop edition of Ubuntu but felt it was a touch too bloated with unnecessary things for running a pure web server/mysql database.

As mentioned before, I burned several discs and tried to install the OS from them. It would get as far as checking the media, after asking me about my keyboard (I always choose the United Kingdom) before giving me the impassable MD5 error.
It really is bizarre to me that the discs I burned didn't work, especially since I had used the drive to install XP earlier onto another partition. But whatever, I'm never going to use that drive for the purposes of this server. (The drive in question is a: hl-dt-st dvdrrw gwa-4161b).

I followed robsoles advice and used unetbootin to transfer the iso onto a USB stick (choosing the Ubuntu 10.04 Live under distro) and loaded up the installation. The installation gave me options to install the server or the cloud host, but clicking either of them would eventually throw an error that it couldn't find the CD (as I wasn't using one). At this point I gave up and hit the hay, it had been a long night!

After a sleep I noticed that there was another option on the menu named "Install" and that seemed to put the operating system on fine (I assume its the server edition rather than the cloud). Installation went really well, easy to use and partition, nice and speedy with no problems, it was just getting it to accept the installation media.

Everything is running fine at the moment, LAMP has just been put on and tested! Looking foward to starting development on a new website project!

---

