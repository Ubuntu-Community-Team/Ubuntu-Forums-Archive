---
title: "[SOLVED] syncing an iPod in minimal Ubuntu 7.10 install"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rockerphil on 2009-01-05
ok, it's pretty simple, my computer is so old (128 MB of pc133 SD RAM and a 500 MHz Intel Celeron processor) that it won't run any standard *buntu distro as effeciantly as i'd like, so i used this tutorial:

[http://www.psychocats.net/ubuntu/minimalold](http://www.psychocats.net/ubuntu/minimalold)

to install a minimal Ubuntu 7.10 OS using Fluxbox as my WM, rox-filer for my file manager, Firefox as my browser and several other light weight apps to round off the OS. now, down to business, a friend brought me his iPod (don't know exactly the model, it's the huge palm sized one that you can rotate 90 degrees and it rotates the screen accordingly) and wanted me to sync it up for him since he's not all that technically inclined. this is where it gets fun, it doesn't show up on my partition table when connected, i can't find it when i run ```
cat /etc/mtab
``` but it shows up when i run ```
lsusb
``` any suggestions? any help is much appreciated, and thanx in advance,

Phil

---

### Post by shifty_powers on 2009-01-05
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

will be a good place to start...

---

### Post by jimmy the saint on 2009-01-05
First understand that it sounds like he has an ipod touch.  The problem that you will run into is that, even if you get it recognized, you won't be able to do much with it.  Everything has to go through the itunesdb file.  The only program that can interface with the itunesdb file at this time is itunes, which does not run properly on linux, especially not without wine.  Until the hashing mechanism that the ipod touches and iphones  currently use is reversed, they will be pretty useless with linux.  If you have an older ipod you can use it just fine with many programs like rythmbox or amarok.

---

### Post by rockerphil on 2009-01-05
thanx for the quick response, but it's not the iPhone, it's just the REALLY BIG version of the iPod that can connect to the web & all that jazz, but it's not a phone, no phone capabilities what so ever

---

### Post by rockerphil on 2009-01-05
ah, thanx Jimmy, then on my computer it sounds like he's pretty SOL on my computer, cus i've tried syncing older iPods on my Windows install on the same machine (Windows 2k) with no luck. much thanx anyways, and thanx for the info on the iPod touch

---

### Post by shifty_powers on 2009-01-05
ipod touch, which is what you have, and iphone are the same for this discussion, as they use the same software on the phone....

chances are that jimmy is right and you won't be able to sych it in ubuntu...

---

