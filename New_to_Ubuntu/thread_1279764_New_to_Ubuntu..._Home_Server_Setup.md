---
title: "New to Ubuntu... Home Server Setup?"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by AccidentalGeek on 2009-10-01
I’m looking to setup an Ubuntu “WS / Home Server” for OS-X file sharing and my little home network backup (NAS) server. However, I don’t want Ubuntu to be running all the time, hence I would like for it to go to sleep and wake up only when needed (A wake on LAN sort of option or on a schedule) would this be possible?

I’m new to Ubuntu and Linux all together and I’m not sure Ubuntu is the best solution but I really would like to give it a shot and get away from using Windows Home Server (WHS) in this case. This would be on a custom built (old) workstation I have with about (3) 500gig drives in it (not sure how they will be setup yet).

I know I can accomplish this WHS (which I own already) but I would not be using any other Windows feature and wasting HD space this is why I ask if Ubuntu would be a good alternative.

---

### Post by 3rdalbum on 2009-10-01
Oh yeah, I use Ubuntu on a Mini-ITX computer as my home server. I do run mine all the time so I'm not sure how to do the Wake-On-Lan.

Basically, just install regular Ubuntu, put a big hard drive in the machine and mount the hard drive somewhere convenient (I have mine mounted at /terrabyte). Set up Samba (file sharing) using the "system-config-samba" program from the repositories; note that with this software, all the user accounts that you create for Samba will also need to be created in the Users and Groups program (basically, for every Samba user, you need to have a Linux user too; I just have the one user account so it's real simple).

When you've done that, then your share should be accessible from the network. Make sure you don't use the "Hidden share" option, because Mac OS X can't access hidden shares.

When everything's set up the way you want it, turn on Remote Desktop (System > Administration > Remote Desktop), enable SSH by installing the "openssh-server" package, and unplug the monitor, keyboard and mouse from the server. From then on, you'll be able to access the desktop from any other computer with a VNC remote desktop client. And for quick little command-line tasks you can log in using SSH and get a command-line.

You can remove any program you don't want to slim down the install as well, but you'll probably find you don't really need to. My home server runs off an 8 gig flash drive with lots of space to spare, and I haven't pared it down at all. I don't recommend running off a flash drive; I've got persistant filesystem corruption on mine, and I'm going to copy the system to a 2.5 inch HDD. The big terrabyte hard disk is fine, the problem is the flash drive.

I also download and seed torrents on mine using the Transmission web interface. The latest version of Transmission allows you to set up different speed limits for different times. My server runs an older version, so I have a Cron job (task scheduling) that runs the command "*transmission-remote --no-uplimit --no-downlimit*" when my ISP's off-peak time starts, and runs "*transmission-remote --uplimit 50 --downlimit 50*" when the off-peak time ends.

Ubuntu is a great choice for a home server; it does everything I ask of it, and a lot of people here run more sophisticated home servers than I.

---

### Post by ukripper on 2009-10-01
For wake on lan you can follow this howto - [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

All my machines are running wakeonlan at home. Works perfectly!!

---

### Post by AccidentalGeek on 2009-10-01
Wow OK, now I'm glad I posted my question. Thanks 3rdalbum and ukripper for the quick replies. I'm going to DL Ubuntu 8.04 LTS Desktop edition and see if I can get this RIG up and running. Already printed this thread for reference.  \\:D/
   
  On my way to see the other thread now...
  
[B]

[/B]

---

