---
title: "Ralink usb disabled problem"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by jairichard on 2008-02-20
I am very new to Linux but learning fast from the marvellous help here.
I installed Ubuntu 7.10 and am using a Sweex lw053 usb adaptor with a Raklink chipset. Device manager says it has rt2500 driver.  lshw -C network shows *-network  DISABLED for wlan0. The wired connection can be ticked on Networks and it works but ticking wireless instead gets no connection. dmesg | tail -n 30 after plugging in the device finishes with the line phy1 -> rt2500usb enable radio: Error - Register initialisation failed.  I am stuck now so if anyone can point me in the right direction I would be most grateful.
Thanks,
jairichard.

---

### Post by rustybronco on 2008-02-20
[http://www.spotonuk.com/info~Itemcd~1251109~Frm~S~MainCat~Networking~ItmDesc~Sweex+LW053+Wireless+LAN+USB+2.0+Adapter+54+Mbps~Make~Sweex~ModelNo~LW053.htm](http://www.spotonuk.com/info~Itemcd~1251109~Frm~S~MainCat~Networking~ItmDesc~Sweex+LW053+Wireless+LAN+USB+2.0+Adapter+54+Mbps~Make~Sweex~ModelNo~LW053.htm)
it should have a rt2571 chipset so the rt2500usb driver probably not work.
so with that said try this (wep encryption only! )  [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

---

### Post by jairichard on 2008-02-21
Thanks Rustybronco, I will have a good look at that. Surprisingly the Windows driver CD that came with the Sweex LW053  adapter has the rt2500usb.inf and rt73usb.inf in its XP folder. Ubuntu has used its own rt2500 driver and booting from the live CD the Live session connects via WEP64 just fine so I would be surprised if your suggested driver would improve matters on the installed Ubuntu.
Thanks,
jairichard.

---

### Post by rustybronco on 2008-02-21
The reason for the two .inf files is probably because of two different rt2571 chipsets.

Chipset: Ralink RT2571WF which maybe a  rt73 chipset. so maybe ndiswrapper+ the rt73 drivers or the same process as outlined above using the correct daily cvs for the rt73? or there is a thread on the rt73's.

---

### Post by jairichard on 2008-02-21
Hi Rustybronco,
I have just finished following Wiemann's excellent thread at [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547) and blacklisted the rt2500usb driver and adding the rt73 driver. Gave it a restart and  it WORKS!! had to go to mauual network selection and put in ssid and WEP settings and still have the blackdouble screen but after forcing it back to roaming and a further restart I have it all working with the blue signal strength icon.
many thanks for you help,
jairichard.:guitar:

---

### Post by rustybronco on 2008-02-21
Gotta love two rt2571 styles,
Glad you nailed it!

---

