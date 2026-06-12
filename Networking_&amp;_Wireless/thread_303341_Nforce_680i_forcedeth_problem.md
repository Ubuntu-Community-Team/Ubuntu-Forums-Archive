---
title: "Nforce 680i forcedeth problem"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by wdiz on 2006-11-20
I have a evga mobo with Nforce 680i SLI and the LAN isn't working (MPC55 Ethernet controler)
I tried DHCP or static IP but no results, i tried with some options in /etc/modprobe.d/options (options forcedeth msi=0 msix=0) but no more results.
It works on other OS
Any help ?
Thx

PS : I am using Ubuntu Edgy

---

### Post by wdiz on 2006-11-22
up

---

### Post by davantalus on 2006-11-22
I've got the same problem. Let me know if you work anything out. I'll try to figure it out too.

---

### Post by wdiz on 2006-11-24
ok i'll repost here if i found a solution ;)

---

### Post by jeff47 on 2006-11-26
I've got the same problem with a Gigabyte GA-M55SLI-S4 board.  It's an AMD board, but still an nForce chipset.  I can't find any errors in the logs, but the driver just won't bring the nic online (link light stays off).

I've also tried the options you listed.  I've also found that some people have trouble when dual-booting to Windows, but I don't have windows.

Mostly, I'm writing this to bump your post.  :)

---

### Post by lazyd2 on 2006-12-03
Same here with Asus Striker Extreme and Edgy.

---

### Post by jaykup on 2006-12-03
I found this over on nvnews.net, it may work, one of the dev's had good luck with it.

[http://www.nvnews.net/vbulletin/showthread.php?t=79917&highlight=680i+ethernet](http://www.nvnews.net/vbulletin/showthread.php?t=79917&highlight=680i+ethernet)

---

### Post by cpk on 2006-12-14
Jaykup, 

I have a similar system as you (evga nForce 680i, e-GeForce 7600gt, 512mb RAM, dual boot sata HDs: indiv xp and edgy drives) and am also having problems getting ethernet working on this board in linux. Everything works fine when in XP but no connections when booted into Ubuntu. 

I have followed the instructions listed at the link you posted, setting options in modprobe but still no luck. Nvnews admin indicates that this problem is due to a bios bug and I have installed the latest bios update from evga (P21) - still no change in Ubuntu. 

Is there something unique about your installation or am I doing something wrong? If anyone else has a solution to getting ethernet on this mobo to work in Ubuntu, please post. 

thx,

cpk

---

### Post by hps on 2006-12-24
Since there does not seem to be any breakthrough on the 680i lan problem does anyone have a suggestion for another linux distro that does not have this problem.
Don't worry I'll be back when its fixed.

JP

---

### Post by wdiz on 2006-12-26
> **hps said:**
> Since there does not seem to be any breakthrough on the 680i lan problem does anyone have a suggestion for another linux distro that does not have this problem.
Don't worry I'll be back when its fixed.

JP

It is fixed with the P23 bios from EVGA

---

### Post by cpk on 2006-12-27
I have the P21 bios update installed and did an reinstall of Ubuntu using the amd64 alternate and all seemed to be fixed. 

cpk

---

### Post by Jim Rockford on 2007-01-08
I have an ASUS board (P5N32-E SLI) with the 680i nVidia chipset.  The EVGA bios update won't do anything for my board, and as of today (01/07/2006) I have the latest bios provided by ASUS (0602) and I still cannot get an ethernet connection with my Ubuntu 6.10 edgy install.  

Anyone else still having this problem with this particular board?

---

### Post by rnodal on 2007-01-23
Same problem here. :(

---

### Post by rnodal on 2007-02-03
this may help.
[http://ubuntuforums.org/showthread.php?t=352716]("http://ubuntuforums.org/showthread.php?t=352716")

---

### Post by ptzink on 2007-02-19
I have an Asus P5N32E-SLI Plus and am having the same problem as Rockford (and everyone). I have tried the msi=0 and msix=0 bit as well as upgrading the BIOS to 0602 and still no ethernet. I am running Edgy. Hope this gets worked out...

---

### Post by rnodal on 2007-02-20
> **ptzink said:**
> I have an Asus P5N32E-SLI Plus and am having the same problem as Rockford (and everyone). I have tried the msi=0 and msix=0 bit as well as upgrading the BIOS to 0602 and still no ethernet. I am running Edgy. Hope this gets worked out...

Did you try what I did?
[http://ubuntuforums.org/showthread.php?t=352716]("http://ubuntuforums.org/showthread.php?t=352716")

---

### Post by ptzink on 2007-02-20
Rnodal, which motherboard do you have? I tried going through the steps from that link and they did not work. Anyone with any other suggestions?:confused:

---

### Post by rnodal on 2007-02-20
I have an Asus P5N32-E SLI. Internet works just fine after I did those steps. 

-r

---

### Post by ptzink on 2007-02-23
Rondal,
I have tried that several times now to no avail. I have no idea why it is not working and I am pretty much so an Ubuntu newb, so my troubleshooting skills are limited. Anyone with any other suggestions as to what might be the problem?
Thanks,
pauL

---

### Post by rnodal on 2007-02-23
I'm using ubuntu 7.04 Herd 3 but I'm not sure if that's the reason. If you don't mind give it a try. Anyways sorry for not being of much help. Take care:


-r

---

### Post by ptzink on 2007-02-23
Rondal,
I downloaded Fiesty Fawn 7.04 Herd 4 the other night and burned it to a CD. I tried booting from the CD and it kept giving me a 'checksum error...sorry' message (as I recall). I tried burning the CD again and still got the same error. The data is all there, just something going on when I try to boot from it. So I was unable to upgrade. And I am such a Ubuntu newb, I don't know how to install 7.04 while in Ubuntu 6.10. Any hints? Thanks for all your help,
pauL

---

### Post by rnodal on 2007-02-23
Just because you are having difficulties installing 7.04 it does not mean that you are a noob. I took me a while for me to get it to work. Specially since the internet does not work until I did what did after install. Try downloading it from a different server. Anyways just don't give up because when you manage to do it you are going to love it. Take care.

-r

---

### Post by ptzink on 2007-02-26
I don't want to 'cloud' this thread with this discussion, but could some one point me in the right direction on how to upgrade from Ubuntu 6.10 to 7.04 Herd 4. I am hoping this will resolve my networking problems. When I try to boot from the Fiesty Fawn 7.04 CD, my home computer hangs. When I try it at work with the same CD, it boots right into Fiesty Fawn. Is there something with the GRUB boot loader that interferes with booting from the CD ROM? Anywho, maybe I will just wait until the official release of 7.04 and try Ubuntu again :(
Thanks.

---

### Post by rnodal on 2007-02-26
Which ISO are you using? The desktop version or the alternate one?


-r

---

### Post by ptzink on 2007-02-26
I am using the desktop ISO. I downloaded the PC (Intel x86) desktop CD from [http://cdimage.ubuntu.com/releases/feisty/herd-4/](http://cdimage.ubuntu.com/releases/feisty/herd-4/). Like I said, it boots from the CD-ROM fine on my work PC, but hangs on my home PC with 6.10 and GRUB installed. Don't know what's up...
pt :confused:

---

### Post by rnodal on 2007-02-26
If you don't mind try the alternate version. I believe that was the version that I used to install Herd 3 because any other method would fail. Take care:

-r

---

### Post by ptzink on 2007-02-26
Looks like the problem is with my DVD burner or my bios or something. It will not boot from any CD (including Windows XP CD). I have the 602 BIOS and downgraded back to the 402. That did not help any. I have no idea what's going on. It obviously booted fine from a CD when I installed Windows and Ubuntu 6.10. What gives now? Very frustrating...
:mad:

---

### Post by ptzink on 2007-02-27
Okay, after all that, I discovered that it was a PCI ATA RAID card that was causing the issue. Once I pulled that out and rebooted, it booted from the CD ROM no problem. I installed Fiesty Fawn Herd 4 and added the options forcedeth msi=0 msix=0 line to my modprobe.d file and it worked! I am typing this from Ubuntu! :)  Thanks for the help. Now on to the next issue - getting my nvidia graphics card to work.

---

### Post by rnodal on 2007-03-02
Good job and enjoy the ubuntu show ! :popcorn: 

-r

---

