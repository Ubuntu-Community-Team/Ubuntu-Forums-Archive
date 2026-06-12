---
title: "Jaunty network hangs every 1 or 2 days"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Chaconne on 2009-09-21
Hello, gurus,

I have a problem that I'd like to get some help from you.

I recently upgraded my machine from Hardy to Jaunty(through Intrepid of course) and I notice that the network hangs every 1 or 2 days. It seems only port 80 is still accessible so I can still browse a little internet when the network hangs, while all services that I checked using other ports are not functioning anymore.

I have tried to ifdown/ifup the network interface or even cut off the network cable for a while, without positive outcome. The only way to solve the problem so far is to reboot the machine.

The programs that I run on the machine are normally MLDonkey, IPblock, terminal, Nautilus, Firefox, Totem or VLC, Audacious. However, the network often hangs when I'm away from the machine so at that moment, most programs except MLDonkey and IPblock are inactive. I have suspected the problem is caused by MLDonkey, but closing mlnet and restarting does not solve it. I sometimes notice however the mlnet still has upload/download traffic(monitored from my conky display) when the problem occurs(because I can not access MLDonkey's web interface using port 4080 at that moment) but after some time, the traffic will go down to none.

I noticed this problem in Hardy as well but happened less frequently than that in Jaunty now. At that time, I though it was caused by unofficially compiled MLdonkey version. The official MLdonkey on Hardy 64bit has a compling bug that will close itself every now and then.

I'm just a user that is interested in free software and trying to do all home stuffs on Ubuntu and I don't work in software area, so I don't have any clue to debug this problem. Any hints will be highly appreciated. Thanks in advance.

OS: Ubuntu Jaunty 9.04
kernel: 2.6.28-15 x86_64
MLDonkey version: 2.9.5
Router: Buffalo WHR-G125 with Tomato firmware v1.2.5

---

### Post by Chaconne on 2009-09-22
Bump. Can anyone give some little hints to start with? I really have no idea on where to begin to track down the root cause. It's quite easy to reproduce though.

---

