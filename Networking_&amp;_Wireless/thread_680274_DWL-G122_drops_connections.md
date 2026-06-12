---
title: "DWL-G122 drops connections"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Tyr_7BE on 2008-01-27
Hi All

Very frustrating problem here.  Networking problems are always the worst.  I have a D-Link DWL-G122 wireless adapter here.  It's a usb wifi stick.  It seems to work fantastic under Windows, but in Linux I'm getting some weird behaviour.  It will work correctly for a while, and then all of a sudden it will just drop off.  It will cease to function, network manager shows the reception dropping to zero, and then it spends forever trying to get back on the wireless network.  If I unplug the card and plug it back in again, it will work again for however long it decides to work.  Sometimes it will be working for a few hours and then will cut out, sometimes I get 10 seconds out of it before I have to power cycle.  There are two lights on the front, "Act" and "Lnk".  When it's working fine, "Act" is flashing like crazy.  When it drops off, only "Lnk" is lit up.

When it drops off, I get the following in /var/log/syslog:

Jan 27 20:20:19 auto kernel: [ 6945.867764] phy6: unknown frame RXed (0xc9) 
Jan 27 20:20:23 auto kernel: [ 6950.451861] wlan0: No ProbeResp from current AP 00:13:10:9f:d7:2a - assume out of range 
Jan 27 20:20:24 auto kernel: [ 6951.239865] wlan0: No STA entry for own AP 00:13:10:9f:d7:2a 
Jan 27 20:20:30 auto kernel: [ 6956.931187] wlan0: No STA entry for own AP 00:13:10:9f:d7:2a 
Jan 27 20:20:35 auto kernel: [ 6962.622626] wlan0: No STA entry for own AP 00:13:10:9f:d7:2a 


Any ideas on how to get this card working reliably?

---

### Post by Tyr_7BE on 2008-01-27
Should also mention that this is a Rev A2

---

### Post by Tyr_7BE on 2008-01-28
Got it.  Probably should have read a little bit harder before posting.  For anyone experiencing this problem, it seems to be an issue with the open source prism 54 drivers that gutsy tries by default.  If you remove these drivers and instead use ndiswrapper, everything should work.

How to install ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Before you do, make sure you get the latest drivers for your card from [http://www.dlink.com](http://www.dlink.com) and store them in a place you can access without your wireless card working.

That's it.  Just follow those directions and you should be good to go after a reboot.  Just for the record, I had to blacklist the following modules to get it to work:

blacklist p54usb
blacklist p54common

---

### Post by tobyadams on 2008-04-23
I second that, im using it right now. It just drops every now and again, im a bit of a newbie to this Ubuntu thing. used it since 2004, but only for about a week on a spare machine for about a week after every new release. this one (8.04 RC) seems to be running to a level where i could start using it, but it seems to be just this one thing!!!!

---

