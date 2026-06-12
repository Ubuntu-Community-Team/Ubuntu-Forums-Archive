---
title: "Wireless worked with liveCD, not working with HDD install?"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by ACMarina on 2007-07-28
Hi all,

Not new to linux or *ubuntu, but I am new to wireless, so bear with me a little bit ;)

I was given a laptop recently for home use.  After a lot of browsing and playing, I decided that Xubuntu would be best, as I don't have a lot of ram at my disposal.  Played with the liveCD and had no trouble so I decided to wipe the hard drive and install.  Only problem - I can't get the wireless internet working.  I've tried three different cards that I've verified in my work (read:w2k) laptop, so I know they're working.  I've browsed for anything I can find to no avail, worked my way through the wireless troubleshooter on the wiki and that didn't help either..

Laptop is a thinkpad - all the cards are one brand or another of the orinoco variety.  

I've since tried to run the Xubuntu, Ubuntu and Kubuntu LiveCDs, but they won't cooperate either.  The only success I have had was running D*** Small Linux, which worked while I ran the LiveCD.

Thanks in advance :)

---

### Post by ACMarina on 2007-07-28
I've dug a little deeper with my canarywireless meter and found that the channel isn't showing up properly in iwconfig - I tried to change it, but I get 

Error for wireless request "Set Frequency" (8b04) :
     SET failed on device eth2 ; Device or resource busy.

Shouldn't  it automatically pick up the right channel??

---

### Post by ACMarina on 2007-07-28
Well, now I'm utterly confused.

I took the computer to my office and tried to connect via wired connection and it still didn't work.  This bummed me out big time.  I placed the unit on a desk next to my wireless router and antenna, and it still wouldn't do anything.

Just brought it home and it's working now - I'm updating everything via apt-get right now.  Any idea what's going on now??

---

### Post by ACMarina on 2007-07-30
Hmmm, bump??

To add - I downloaded and installed Wicd, and while it shows that I am connected to my access point at the bottom of the window, it dows not show any wireless networks found..

---

