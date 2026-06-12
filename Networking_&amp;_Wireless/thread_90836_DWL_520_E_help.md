---
title: "DWL 520 E help"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by gexla on 2005-11-15
:confused: It seems one of the big sticking points of Linux today is wireless networking.  I have had a wireless connection ever since I went broadband like 5 years ago.  Every so often I give Linux a shot but I am never able to get connected, so I give up and go away.

The first time I tried Ubuntu, to my utter amazement, I was able to get connected to my wireless network right after installation.  I went into networking in the control panel, activated my connection, and then I was connected.  

Now that I was jazzed to give Linux a serious shot I wiped it and  I am now dual booting on my bigger hard drive with XP.  Back at a desktop I was no longer able to get connected.  I can go back into networking and activate my card, but activation takes forever.   Once activated I hit OK and the networking screen takes forever to close.  At this point I am unable to connect, ifconfig only brings up the lo interface, and when I go back into networking the card is unactivated.  Actually in the networking screen I have Wlan0 and Wifi0, both do the same thing.  I think before when it was working I was using Wlan0, but neither work this time.  

Too bad... I had my hopes up there.  Just in case I thought I would ask to see if anyone had any good advice.  I know there are lots of threads that go over this but if you ask ten people you get ten different answers.  I have read the page on connecting a DWL 520 E1 but that is way too many steps.  I am thinking that wireless networking is only for the advanced users... which is too bad because without my wireless connection my computer is worthless to me.  In any case, thanks in advance for any help you guys might throw my way... otherwise maybe I will see you in another year.  :D 

I have a Dlink DWL 520 Rev E wireless card running Ubuntu 5.10

---

### Post by Stereotypical Rage on 2005-11-15
Warty (5.04) read my DWL 520 fine. When I got to Breezy it choked. I still don't know why this is. I hope they will fix this in Dapper. Else, I am just going to get a new card that's on the wiki as supported WiFi.

---

### Post by gexla on 2005-11-15
Yeah, it is very strange.  Another item to note is that I had a WUSB11 USB wireless adapter plugged in at the time that my wireless worked.  The WUSB11 did not work, but the DWL 520 did.  I guess I felt that between the two maybe one of them would work.  That is the only thing I did different.  

I am a complete noob at this but I am wondering if it is possible something might have been loaded for the WUSB card that might have also been used by the DWL 520.

---

### Post by sedition on 2005-11-15
I'm having the same problems myself. I've tried the hostap wiki, ndiswrapper, etc. I did get it able to scan with iwlist at one point, but I never could get it to receive an IP from my WEP'd router. After a lot of research, I did find a couple of things:

teh card sux0rz. Apparently, it requires firmware to work (the hostap wiki can explain how and where to get it) since there is no permament firmware on the card

all of the tutorials/walk-throughs indicate that (for this card) your kernel must have "CONF_RADIO_ENABLED=y". I have no idea if this is enabled by default in the 5.10 "Breezy" install. A lsmod doesn't indicate this, but is does show that the hostap module is.

If you don't want to waste your time and/or patience, I'd recommend getting a cheaper and more compatible card. I've learned a lot about Ubuntu going throught this (*BSD man here), so it's been a good learning experience. I know that it's possible and I don't plan giving up until I've recompiled the kernel.

---

### Post by gexla on 2005-11-16
Or you could just get a wireless bridge.  Those things receive a wireless connection and plug into your computer via an ethernet cable.  The best part is they require no drivers, so you can use it on a gaming console or yes... even linux.

---

### Post by gexla on 2005-11-16
Heh... nevermind this problem.  My last post got me thinking and I decided to go for it.  I am getting a wireless bridge from Belkin (F5D7330).  It has great reviews from Amazon.  It is a little spendy at $99 but considering the time I would have to put into getting my wireless to work and then possibly buying another wireless card it is well worth it.

These bridges look pretty sweet.  As mentioned before it needs no drivers becuase it connects to your computer via ethernet.  This particular model also has WPA available through the firmware update which is something not all of these bridges have.  You can also connect it to a game console or another network device.  I am going to use it to plug into a switch to connect a home built server rack I am making out of old computers.  No more ICS!  Now I can have a persistant connection that does not rely on one computer to be booted at all times to have a connection.

Ok enough with the sales pitch, you would think I worked for Belkin :P

---

