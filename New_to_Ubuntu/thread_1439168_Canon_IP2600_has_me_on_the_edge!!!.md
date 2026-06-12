---
title: "Canon IP2600 has me on the edge!!!"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by stw9495 on 2010-03-25
Well call me what you want but I'm a newbie to Ubuntu. I thought it frustrating at first as I could not install software easily until I found the option in the menu..."duh" moment. I got KDenlive, which looks to be very good for what I want to do. The only other pet peeve I have that is driving me up a wall is that I simply cannot for the life of me get my new Canon PIXMA IP2600 Printer to work. I have searched and found drivers but they never install correctly, I always get an error message. I got this printer at Wal-Mart for a low $32 and thought this will work great...but it just opened up a can of worms for me. I don't really want to take this thing back...because it was the cheapest one and the next cheapest was also a Canon I believe. So, if you guys can help me I would appreciate ever so much! 

Oh, and for good measure, here's a spec list of what I'm using currently.

Dell Dimension 4100
Intel Pentium 3 866MHZ
512 MB RAM
9.50GB Quantum Fireball HDD
CD-ROM 
LG Multi DVD Drive (I need an IDE to SATA adapter, if anyone can get me one cheap, I'd appreciate that as well)
MSI Turbo G Wireless PC Card
Ubuntu 9.10 (originally had Windows 98 SE)

I think I have like $68 in this, the PC came as a trade...after some experimenting with Puppy I burned a boot disc on Windows 98 (It burned the disc that ultimately ended it's time on the HDD, lol.) And installed Ubuntu...Works very well, aside from the PRINTING!

Thanks in advance for any help at all,
Tyler.

---

### Post by cariboo on 2010-03-25
Canon North America doesn't seem to want to support Linux, but I found a driver [here]("http://http://support-asia.canon-asia.com/P/search?category=Inkjet+Printers&series=PIXMA&model=PIXMA+iP2680&menu=download&filter=0") that may work. Just download the .deb file and double click it, gdebi should install it for you.

---

### Post by uRock on 2010-03-25
It has been my experience that Ubuntu doesn't get along well with Canon printers. There is a bug report on this problem for your model. I have a Canon printer that I haven't hooked up in 2 years(I think it is the same model) and I have a really old HP printer that I do use and it runs great with ubuntu. 

If you would like to add to the bug report it is at this link [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/444126](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/444126)

Cheers,
Ronnie

---

### Post by spartan_87 on 2010-03-25
I have a friend that has this same printer and I got it to work for him. Canon actually has linux divers for this printer, but there not on their North America site, I found them under the Asia site for some reason. You will need to download two packages from [here]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html") and [here]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html"). Make sure the printer is plug in and then install the packages. After you install those you should be able to unplug the printer and plug it back in and Ubuntu should see it, if it still doesn't try restarting.

---

### Post by stw9495 on 2010-03-26
Well guys I got it to work!!! Thanks to this forum and a very helpful member I was able to locate a set of rebuilt drivers that worked like a charm...it takes a bit for the printer to do what you ask, but it does it, which is fine by me. Now my next problem. My Ubuntu Software Center mysteriously stopped working...I open it and it closes before I can use it....I see this is a bug that hasn't been solved yet...but I 'd like to be able to install more software...any ideas?

---

### Post by halitech on 2010-03-26
try Synaptic instead and see if it works

---

### Post by flyfishingphil on 2010-03-29
Great to have a chance to share suggestions!

It costs about $40, but got to [www.turboprint.info]("http://www.turboprint.info")and see if your printer is listed. Their program provides the drivers needed for a large number of printers to work in Linux. My Canon M560 is listed there.

---

