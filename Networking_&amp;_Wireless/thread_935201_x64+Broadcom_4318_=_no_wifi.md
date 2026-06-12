---
title: "x64+Broadcom 4318 = no wifi"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by oraldlight on 2008-10-01
Any one have luck getting this combo to work? Various threads/methods have gotten me nowhere. More irritating is that it works under Gutsyi386.

Even the supported cards list is wishy-washy about success.
Gateway gx7410

     Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by kestal on 2008-10-01
Yeah, I hear that! I have Ubuntu 64 and it took me a while to get it working 'properly'. I used the 32bit solutions for my Ubuntu 32 and it worked great too, then I tried the same approach for 64 and it didn't work out the way I hoped. Lost connections here and there, had lag bursts, my downloads were at about 1000-2000kbps and now its back up to my original speedtest results at over 6500, so I am happy. I found a relatively easy solution which worked for my B43xx.

1) from whatever computer, grab: [http://www.omattos.com/broadcom/b43-all-fw.tar.gz](http://www.omattos.com/broadcom/b43-all-fw.tar.gz)

2) get it over to your Ubuntu partition. Make a folder on your desktop (or wherever you are comfortable getting it from) and extract the contents from all.tar (inside b43-all-fw.tar.gz) into the folder. You'd probably only need the b43 folder, and not b43 legacy.

3) Open up *2* Terminals, do a  *[COLOR="DimGray"]sudo nautilus[/COLOR]*  for both of them. In one, go to your b43 folder. In the other, go to /lib/firmware/******-generic. Copy Paste all the contents from the folder to the generic folder. Then copy paste the folder itself, into the folder.

You could also just sudo cp in terminal to the right directory and that would work too, I just like working with nautilus and visually seeing it.

Either wait a few minutes for it to kick in, or restart your laptop.

Anyway, if it doesn't work, just reply back.

---

### Post by oraldlight on 2008-10-01
> **kestal said:**
> 

3) Open up *2* Terminals, do a  *[COLOR="DimGray"]sudo nautilus[/COLOR]*  for both of them. In one, go to your b43 folder. In the other, go to /lib/firmware/******-generic. Copy Paste all the contents from the folder to the generic folder. Then copy paste the folder itself, into the folder.

whoa there:
1) copy the "b43" contents to /lib/firmware/2.6.24-21-generic?? 
2) AND the b43 folder?? - the one I just copied from, to the same /lib/firmware/2.6.24-21-generic?

Seems redundant. Strangely I already ahve a b43 (and b43-legacy) folders in /lib/firmware. Although that could be from prior efforts to make this blessed card work.

---

### Post by alyoshablue on 2009-03-23
I struggled all day to get my wifi working and after all the information out there, this is the only solution that worked.  My wifi is now working.  Thanks for the easy solution.

Note:  I could not get nautilis to work, so, I just downloaded from an XP machine, copied (the whole b43 directory) onto a thumbdrive, and then copied that onto the desktop - then into the lib/firmware.  I did the reboot and it worked right away.

Thanks again.

---

