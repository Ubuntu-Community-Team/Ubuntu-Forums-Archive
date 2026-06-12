---
title: "Broadband at modem speed!"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by andy.t on 2009-01-14
Hi all,

Had one or 2 issues with ubuntu, wiping my xp disk was one... But anyway, I'm persevering!

I can connect to the internet fine, but my speed varies. I either get full broadband speed, or very slow modem speed. Currently networkmanager applet is reporting 1.0 mbs, but sometimes it's 40 mbs.

My machine is dual boot, and we have another Vista laptop. Only the ubuntu boot has slow broadband, so it's not the connection.

We connect wirelessly by the way.

Any suggestions would be welcomed!

TIA!

Andy...

---

### Post by ubrox on 2009-01-14
Reg wiping the xp disk, unless the person who is installing explicitly asks the installer to wipe the disk, the installer wont do it. So this maybe a PBKAC issue. :) 

Reg your internet connection, I guess the ubuntu system connecting to the internet using wireless. If so, what wireless card is your system using? 

Execute: sudo lshw -C network

Are you facing any signal issues for your wireless? You may also please post last few lines (maybe 20) from output of "dmesg"

---

