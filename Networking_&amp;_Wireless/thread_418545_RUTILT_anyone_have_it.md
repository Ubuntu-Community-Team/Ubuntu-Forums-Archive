---
title: "RUTILT anyone have it?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by 3mbc on 2007-04-22
Tried a fresh 7.04 install (after upgrade broke the wireless) to fix the wireless no luck -> Wicd can see the wireless but won't connect. I was using RutilT before but the site seems to be down.

---

### Post by AleXit on 2007-04-22
Yes, I use rutilt successfully and I have made also an Ubuntu .deb package, which should work also on Feisty:

[rutilt_0.14-0~3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb)

---

### Post by 3mbc on 2007-04-22
Thanks. Same issue won't even connect without encryption.

---

### Post by Boni2k on 2007-04-25
Thank you Alexis!

Actually, I can't connect to my Wifi with this. I think it's beause Rutilt configures the connection with iwconfig or ifconfig but for my network, I need to do this:

sudo iwpriv ra1 set NetworkType=Infra
sudo iwpriv ra1 set AuthMode=SHARED
sudo iwpriv ra1 set EncrypType=WEP
sudo iwpriv ra1 set DefaultKeyID=1
sudo iwpriv ra1 set Key1="****"
sudo iwpriv ra1 set SSID="****"
sudo dhclient ra1

Otherwise I don't receive DHCPOFFERS...

Anyway it's a very nice tool for monitoring

---

### Post by Gruelius on 2007-07-22
Why is the iwpriv part nessicary? i can manually run a script each boot however i would like Network manager to bbe able to run my wireless!

---

### Post by nickmcg on 2007-07-22
Latest rutilt from [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

---

### Post by imdano on 2007-07-22
Network Manager doesn't support ralink cards because they have to use the iwpriv method (instead of wpa_supplicant), which goes against the standard linux method.  The next release of wicd will have support for it, though.  If you head to our forums ([http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)) you can actually test the updates needed to add support for them now.

---

### Post by nickmcg on 2007-07-22
The latest rt2x00 drivers *SHOULD* work with network manager, although the legacy drivers don't.

Unfortunately, I don't seem to be able to build the latest rt2x00 sources.

Nick

---

### Post by imdano on 2007-07-22
Ah yeah, I should have added that. Serialmonkey's rt2x00 next-gen drivers use wpa_supplicant, so they should work like most drivers.  Eventually they're going to be included in the linux kernel by default (not sure when exactly, maybe in time for Gutsy?).

---

### Post by kevdog on 2007-07-22
Any knowledge of what happened with the ra drivers between edgy and feisty??  Im seeing a lot of people that state their card worked in Edgy, they upgraded, and no nothing works.  Usually if I walk them through compiling the cvs sources from serial monkey, everything works, although their are some definite conflicts with these new drivers and network manager.  The rutilt gui tool seems to work, and disabling network manager.  

Ive heard rumors about these new version being included in the Gusty release.  I think, although cant confirm they are in the beta versions already released.

---

