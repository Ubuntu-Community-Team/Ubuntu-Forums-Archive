---
title: "I want to make an old computer useful"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Noah0504 on 2007-04-21
I recently un-boxed our old Compaq Presario 5222 computer.  It has an a speedy 350MHz AMD processor, a ridiculous 64MB of RAM, and giant 10GB HDD.  (Ahh, I remember the day when those specs were top of the line.)

Anyway, I want to make this computer somewhat useful.  I currently have a console install of Debian Etch running smoothly, and I've been using it only for IRC using Irssi.  I'd like to maybe install Ubuntu on it and configure networking sharing.  Perhaps I could use it for simple backup, maybe a dedicated BitTorrent client, and a personal web server.  However, I really don't know where to start.  Do the alternate install CDs offer a console install?  Will Samba be setup automatically?

Thanks in advance for any information you can provide.

---

### Post by ner0tic on 2007-04-21
yes, teh alt cd has a text install.  No samba will not automatically install per say.  Once you get ubuntu up and running run ```
aptitude install samba
```and enter the needed information at the prompts and you should be good to go.  I had a machine close to the awesome power of yours and I decided to run xubuntu (ubuntu with xfc instead of gnome) which gave me a lighter weight gui that ran a little faster.

---

### Post by kerry_s on 2007-04-21
debian etch is a good system too. You can add to it for a custom build up from the console.-> apt-get install xorg gdm synaptic fluxbox <-then reboot, that's what i'm using for my debian etch install to start.

Anyways, ubuntu has a net installer that can install anything you want just like debian.-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

I forgot to mention, check out the tips & tricks here-> [http://forums.debian.net/index.php?sid=c8f6b95b9b3da77b611911f8d9aa2a06](http://forums.debian.net/index.php?sid=c8f6b95b9b3da77b611911f8d9aa2a06)

---

### Post by K.Mandla on 2007-04-21
I would suggest Arch, but I'd have to amend that to LowArch, since I'm guessing your AMD 350 is a K6-series, and it wouldn't run straight Arch. Be forewarned, if you want to use Arch, you'll need to know the guts of your system, but it will reward you with unprecedented performance. ... :)

---

