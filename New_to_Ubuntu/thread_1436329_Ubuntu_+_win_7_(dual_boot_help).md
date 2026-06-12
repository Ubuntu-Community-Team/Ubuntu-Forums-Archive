---
title: "Ubuntu + win 7 (dual boot help)"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by r.sushant on 2010-03-22
hello friends, i am new user of ubuntu, currently i m using win 7 on my laptop, and i am interested in ubuntu (right now using through pen drive!), but without any changes in my win7 os. i have 2 partitions in hdd 150gb each, if i install ubuntu in 2nd drive, will i loose all data currently exist in that drive?
I bought laptop(dell studio 1450) 2 months ago, will this experimenting with OS affect on my warranty? please help!!

---

### Post by MrFaler on 2010-03-22
The best thing you can do to experiment more freely with Ubuntu is to install it with Wubi. With Wubi you can install Ubuntu as an application in Windows, and therefore you can uninstall it in the same way. 

Wubi installs Ubuntu on the same drive as Windows and in that way there is minimal danger to mess things up.

Wubi is officially supported by Carnocial (the makers of Ubuntu) and you can get it [here]("http://www.wubi-installer.org"): 
[HTML]http://www.wubi-installer.org[/HTML]I hope this helped.

EDIT: I forgot to mention that this isn't some virtualisation program, it really creates a dual boot with Windows. The only problem you might experience is that your screen resolution does not really work.

I don't know anything about the waranty voiding. You should ask your manufacturer.

And yeah if you install Ubuntu on the extra drive, the installer will format the partition, which causes you to loose all the data on it.

---

### Post by Hikayu on 2010-03-22
> **r.sushant said:**
> hello friends, i am new user of ubuntu, currently i m using win 7 on my laptop, and i am interested in ubuntu (right now using through pen drive!), but without any changes in my win7 os. i have 2 partitions in hdd 150gb each, if i install ubuntu in 2nd drive, will i loose all data currently exist in that drive?
I bought laptop(dell studio 1450) 2 months ago, will this experimenting with OS affect on my warranty? please help!!

To answer your *DIRECT* question, installing Ubuntu on *another* partition will not remove Windows/destroy data on your HD.

---

### Post by r.sushant on 2010-03-22
thanks....
i gave a try to it... but now it is downloading ubuntu-9.10-desktop-amd64.iso.torrent
but i am using intel arch and i have copy of ubuntu 9.10! still i have to download this again...?
n what about amd64?

---

### Post by linuxman94 on 2010-03-22
> **r.sushant said:**
> thanks....
i gave a try to it... but now it is downloading ubuntu-9.10-desktop-amd64.iso.torrent
but i am using intel arch and i have copy of ubuntu 9.10! still i have to download this again...?
n what about amd64?

amd64 just means that it is the 64 bit version of ubuntu.  No need to download it again, wubi will automatically chose the right architecture for your system.

---

### Post by gadolinio on 2010-03-22
When you install ubuntu to a partition, the installer formats it first, so all the data in THAT PARTITION will be gone.
Regarding warranty, all i've read about is that you might lose it if you quit Windows, but not if you add something else in another partition. Just make sure you don't format any partition that the computer originally came with.
I bought a laptop with win 7 installed, and 2 other partitions; just resized the biggest one, and installed ubuntu there. No original files were deleted.

What you say about the installer downloading an iso file happened to me but when installing from Wubi, inside windows. It worked okay when installed on a separate partition.

---

### Post by wilee-nilee on 2010-03-22
Are you sure you want to do a wubi install into windows, this is good for trying it out. The only thing is that there seems to be problems with wubi and updating or upgrading the Ubuntu OS.

A dual boot is a better way of going separate OS on separate partitions. It is easy to load the MBR for either system if needed if you have install discs for MS or recovery discs and install discs or thumb for Ubuntu.

---

### Post by Nidwow on 2010-03-22
Yeah, dual boots is easily done in Windows 7.  I just started to play with Linux last week and Ubuntu is the first distro I picked.
 

 Just use shrink feature of Windows 7 in disk management to shrink your 2nd partition. It can be done on the fly and it only take a few min to do.
 

 I made about 40GB to play with Ubuntu.  I know nothing about Linux at all until a few days ago but Ubuntu made installation and dual boots so easy.
 

 First make sure you have Windows 7 rescue disc. I made mine using Windows 7 backup and restore feature to creates Windows 7 repair disc.
 

 If you get rid of Ubuntu for some reason just got to disk management and delete the volume that you have Ubuntu installed. Reboot from Windows 7 with repair disc then drop to command prompt.
 

 Then just type:
 bootrec /fixmbr
 bootrec /fixboot
 

 Reboot, now your windows 7 will be back in full swing no more dual boots. Then you can go back to disk management and expand the partition back to it's original size if you want.
 

 I just did the same thing as my new laptop came in with Nvidia G210M which I have problem with it.  So I went back to full Windows 7 by doing above.
 

 Now I am running Ubuntu on my $50.00 laptop and it run better then my $800.00 laptop LOL

---

### Post by Mark Phelps on 2010-03-24
> **r.sushant said:**
> hello friends, i am new user of ubuntu, currently i m using win 7 on my laptop, and i am interested in ubuntu (right now using through pen drive!), but without any changes in my win7 os. i have 2 partitions in hdd 150gb each, if i install ubuntu in 2nd drive, will i loose all data currently exist in that drive?
Concern I have is that two partitions of exactly the same size implies that you have a RAID setup -- which requires you use the Alternate CD since the standard desktop CD can not work with RAID.
> I bought laptop(dell studio 1450) 2 months ago, will this experimenting with OS affect on my warranty? please help!!

If you ever need to send this back to Dell, or have Dell come out and service it, the minute they detect another OS on this machine, they will have the legal right to deny all warranty support.

Regardless of what other folks will tell you, the SELLER gets to decide what does and does not affect the warranty, not the BUYER. At least, that's what I learned in my Contract Law course.

BTW, I've seen an alarming number of reports from folks whose preinstalled Win7 machines started overheating after installing Ubuntu 9.10.  If yours does that, and you damage or burn out any hardware as a result, you can forget about any warranty support from Dell.

Just some things to think about when you start tinkering with your laptop.

---

### Post by r.sushant on 2010-03-24
thank a lot my friends for your kind help!
i decided to run it on pendrive itself! as its taking very less cpu (4%) n ram (7%) and i can work normally...
but again i met with a problem...
i cant play any song (MP3) n video(avi or wmv, mpeg, etc ) why so?
it can play only ogg but no sound at all...
what to do now?

---

### Post by Mark Phelps on 2010-03-24
> **r.sushant said:**
> thank a lot my friends for your kind help!
i decided to run it on pendrive itself! as its taking very less cpu (4%) n ram (7%) and i can work normally...
but again i met with a problem...
i cant play any song (MP3) n video(avi or wmv, mpeg, etc ) why so?
it can play only ogg but no sound at all...
what to do now?

IT's a bad idea to keep expanding a thread into offtopic areas because many of us respond to a thread based on it's title.

So, "what to do now" is to open a new thread ... for your new problem.

---

