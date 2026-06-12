---
title: "64 bit WEP disabled by updates?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by surfcity_dad on 2008-05-08
I upgraded my Thinkpad X21 installing 8.06 today, keeping 7.04 and Win 2K.  Everything went smoothly installing from the CD. I have a 64 bit WEP LAN and it worked great with it.  I was prompted to install 50+ updates after completing the initial install, which I downloaded via my wireless LAN and installed.  After installation I was no longer able to connect to my LAN - did 64 bit WEP get removed in the updates? I'm able to connect to unsecured  hotspot, so I know the net works.  

I'm using 7.04 on the X21 for this post, no issue with 7.04 or Win 2K.  I realize this is not super secure, also use MAC address filtering.   I have a number of older devices, don't think they support 128 bit WEP.  Used mainly to keep casual users off my LAN.

Hardware  

Thinkpad X21
Orinoco Gold wireless card

Any info would be appreciated,

Mark

---

### Post by surfcity_dad on 2008-05-08
Just a further update for clarification, if I go to manual to configure my wireless card, and chose the key, with 64 / 128 bit WEB -the field for the key it doesn't accept my key, I need more characters.  Makes me think that its validating as if its a 128 bit key.  Seems like it could be something as simple as form validation for the field that's preventing my connection.

thanks in advance for any input,

Mark

---

### Post by chili555 on 2008-05-08
Did you try manual configuration:```
sudo iwconfig eth1 essid <ur_essid>
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
```64-bit WEP is 10 HEX characters. You do have 10, right?

---

### Post by surfcity_dad on 2008-05-08
Thanks, that was the problem, I had recorded the key incorrectly.  works great now - thanks!

---

### Post by trubshac on 2008-11-20
I too have this problem:

My wife has a lovely new Sony laptop which she has let me install Ubuntu on - everything works fine at home, but she needs to connect to the network at work too.  They (stupidly) use 64 bit WEP, but unfortunately, the "Network Connections" program no longer offers this as an option.  She is not (yet) up to the bash shell and vi, so I really need to have it available via a user-friendly menu.   

Is there a config file somewhere that I can edit which will enable 64 bit WEP as an option within the Network Connections program?

Thanks

---

