---
title: "Another Newbie Question"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Foreseer on 2009-02-24
Ok, I've installed ubuntu from my barely running windows XP.
I plan to leave windows in the background until I get my free cd.

My question being *complete newb* How do I install Adobe Flash Player into my Firefox. I've the amd64 version and when I try to install it:
Open with GDebi Package installer

I receive the following message:

Package: adobe-flashplugin
Status: Error: Wrong architecture 'i386'

---

### Post by llamabr on 2009-02-24
sudo apt-get install flashplugin-nonfree

---

### Post by Foreseer on 2009-02-24
How do I get into Terminal again... I'm a complete newb >.<

---

### Post by badmedic on 2009-02-24
It's under Applications > Accessories.

---

### Post by llamabr on 2009-02-24
For me, since I know that all the power of linux is in the command line, I right click on the terminal, and put it right on the task bar, so i have a short cut all the time.

Let us know if that doesn't work.

---

### Post by Foreseer on 2009-02-25
Well it seemed to isntall, but when I go to gaiaonline website that I'm trying to access it ask me to install flashplayer still.

This content requires the Adobe Flash Player.Get Flash

---

### Post by llamabr on 2009-02-25
Did you close firefox and open it back up?

Give us the exact url.

---

### Post by Foreseer on 2009-02-25
Aye, I tried. I'll try restarting my PC.

[http://www.gaiaonline.com/mygaia](http://www.gaiaonline.com/mygaia)

---

### Post by OU_Guy on 2009-02-25
i386 is typically an intel name. Are you sure you got the right driver?

Try this guys tutorial and link:
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

---

### Post by Foreseer on 2009-02-25
And now I'm on my mac.

I don't know what happened >.> I left my computer it auto booted into windows.
I went to shutdown, and had to do full power-down as my windows is fairly screwed...

Anyways when I rebooted into ubuntu I'm stuck in terminal again...
Second time I've been stuck here.. Anyways I tried to do as was suggested last time and type:
startx
Well to keep things short; it didn't work...
Could it be that it's because I'm using the amd64 version? Or just that I just need to get rid of windows all together.... When I created a CD it ended up compacting the data into a zip. I fairly rarely create data disk, music disk, or even burn disks for that matter.... Not exactly sure how a live cd works... I feel so computer illiterate now...

My computer is:
amd athlon 64(tm) 64 x2 Duel Core Processor 4600+
2056mb Memory

---

### Post by Ripose on 2009-02-25
Are you using FF 3.06? Flash works properly in this version.

It should have this plugin: Shockwave Flash 10.0 d21

---

### Post by Foreseer on 2009-02-25
Thanks for the info everyone I'll try again once I get a proper LiveCD to install it on my other blank harddrive; Think I've had all I can handle tonight getting tired.

---

### Post by gnoob on 2009-02-25
I would try the tutorial suggested by OU_Guy. make sure you go all the way to the part at the bottom and follow the 64 bit instructions.  I think your problem has to do with trying to install a version of flash made for i386 architecture and you want the one made for 64 bit architecture

---

### Post by Foreseer on 2009-02-25
I just got livecd, and formatted my windows with ubuntu. The suggested topic wasn't for me since I'm using 8.10

Am trying the:
sudo apt-get install flashplugin-nonfree

2009-02-25 04:25:39 (603 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3994294/3994294]

Download done.
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.

Setting up lib32nss-mdns (0.10-3ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
name@name-desktop:~$

---

### Post by Foreseer on 2009-02-25
Yay its working :3
The suggestion from Ou_guy did work.
I am just illiterate.

> Thanks to Alejandro for this nice script.

First you need to Download shell script from here
Using the following command
wget [http://queleimporta.com/downloads/flash10_en.sh](http://queleimporta.com/downloads/flash10_en.sh)

Now you need to give execute permissions using the following command
sudo chmod +x flash10_en.sh

Run the script now
sudo sh ./flash10_en.sh


I take it the other attempts I did that failed were not installed?
Im hoping I won't have any issues with wasting space.

---

### Post by llamabr on 2009-02-25
You're running this only on a livecd?

Rebooting your machine won't work, then, as all of your settings will be lost each time you reboot.

---

