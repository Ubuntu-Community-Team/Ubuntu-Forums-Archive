---
title: "Successfully installed wireless driver using ndiswrapper, but can't connect"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by kingleer on 2008-01-11
Okay, I just got a Dell Inspiron 1525, and installed Ubuntu 7.10 (the 64 bit edition) on it no problem. I installed my wireless driver using ndiswrapper without a problem. 

However, when I type iwconfig, I get 

lo             no wireless extensionsions
eth0        no wireless extensionsions 
eth1        IEEE 802.11b/g ESSID:"Kinglear" Nickname:"Broadcom 4311"
               Mode:Managed   Access Point: Invalid 
               RTS thr: off          Fragment thr: off 
               Encryption key: ****-****-****-****-****-****-** Security mode: open
                Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm 
                Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid frag:0 
               Tx excessive retries:0  Invalid misc:0  Missed beacon:0 

A little help would be greatly appreciated. Thanks in advance for any help.

---

### Post by murmel on 2008-01-11
Is roaming mode enabled?

---

### Post by kingleer on 2008-01-11
> 
Is roaming mode enabled?
 

Let me check (I don't think so). Checked. Nope.

---

### Post by kingleer on 2008-01-11
I still have not figured this out yet. Any help would be appreciated.

---

### Post by kingleer on 2008-01-11
I followed this procedure to install my wireless driver by the way...

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by kingleer on 2008-01-12
Okay, I'm trying to use madwifi. In specific I tried following the guide here - 

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

No luck. 

I'm getting desperate here.

---

