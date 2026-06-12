---
title: "Mad wifi suddenly stopped working?!?!?"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by penguins916 on 2008-08-23
I have been using mad wifi with my aspire 5570z acer laptop, then suddenly it stopped working. 
I have uninstalled and reinstalled it like 10 times and restarted my computer even more.
Any Ideas anybody, my life, and internet depends on it.

---

### Post by penguins916 on 2008-08-24
in the 3rd page so bump...

I am REALLY desperate guys. :-({|=

---

### Post by wannadumpwindows on 2008-08-24
Did you install it manually?

---

### Post by penguins916 on 2008-08-24
yes, I did the sudo make clean, sudo make, sudo make install.
Home that helps.
The card shows up in a iwconfig and ifconfig, but it will not find any networks.

---

### Post by wannadumpwindows on 2008-08-24
Have you downloaded and used the newest version? I had some similar problems a while back, but I can't remember what I had to do to fix it.

Have you checked the restricted drivers manager to make sure the madwifi that comes with ubuntu is disabled?

Also, I noticed with mine last time I installed, that I had to manually add the "ath_pci" module to my /etc/modules file. It wasn't getting loaded on boot like it was supposed to be.

---

### Post by penguins916 on 2008-08-24
I will download the newest now, as for the restricted drivers:

atheros Hardware Access Layer(Hal)     enabled:no    status: in use
support for atheros 802.11 wireless lan cards. enabled:yes status in use.

I have been playing around with these settings as well.
Thanks for the help. I hope the new install will work.

---

### Post by wannadumpwindows on 2008-08-24
No problem. Sorry I can't offer more hhelp at them moment. I'll do a little digging around for you and see what I can come up with.

Good luck in the mean time . . .

---

### Post by penguins916 on 2008-08-24
I reinstalled madwifi with this guide from [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) and now the card doesn't even show up. I added ath_pci to etc/modules manually and still nothing, rebooting a few times in between.

I am going try to dissable the restricted drivers now, if anybody has any idea it would be nice.

---

### Post by wannadumpwindows on 2008-08-24
The restricted drivers are probably part of your problem. I've always had to disable them in order for the "normal" madwifi to work.

Did you try a reboot after you reinstalled? Once in a while it helps. 

And that how-to is the exact same steps that I use to install every time I need to, so you might have something else going on.

There could still be other modules being loaded that are interfering.

---

### Post by wannadumpwindows on 2008-08-24
Do you know exactly which chipset your wireless adapter uses?

I had a few issues getting the card in my Eeepc to work right. Seemed like some of the releases supported it just fine, while other newer ones didn't work at all.

It didn't make any sense to me.

---

### Post by penguins916 on 2008-08-24
I have been restarting my computer in the last 30mins about 7 times, so thats not the problem. My card is a AR5007EG. 
Once more thanks for the help, I will write if I make progress.

---

### Post by wannadumpwindows on 2008-08-24
Good to know. I have the same chipset in two laptops, and it's also the one that gave me issues. I wish I could remember what I did to fix it. LoL.

Both of them say they're Atheros AR5007EG, but they are not the same chips. One worked with one revision, the other worked with a different one.

---

### Post by penguins916 on 2008-08-24
Ok I got the card to show up in Iwconfig, here is the results:

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

STILL no working internet though.

I had a previous problem like this, and I solved it by reinstalling madwifi. 
I had a previous post about wifi, not the same problem, here and I got a different version of madwifi that was working, not now.

[http://ubuntuforums.org/showthread.php?t=806083](http://ubuntuforums.org/showthread.php?t=806083)

Hope that helps.

---

### Post by penguins916 on 2008-08-24
on to install the svn version now...

---

### Post by penguins916 on 2008-08-24
ok the svn didn't work. I am about ready just to format my drive and reinstall every thing. 

Any other ideas, anybody?????

Thanks again

---

### Post by penguins916 on 2008-08-24
dropped to page 3 bump...
really desperate you guys. school starts soon and I really need this to work, else, its back to the dual boot of vista, gasp.

---

### Post by penguins916 on 2008-08-24
SOLVED.
I have no idea how, booted to vista to check if the card worked, and then booted back and it worked.
????
no clue, but it works:lolflag:

---

