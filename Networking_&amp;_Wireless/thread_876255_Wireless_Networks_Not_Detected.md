---
title: "Wireless Networks Not Detected"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by abelianjeff on 2008-07-31
Hi all,

I've just set up my uncle's laptop with Ubuntu Hardy. We have no wired internet access, so I had to download and install the b43xx firmware files on my computer, transfer them over to his computer, and install them. Under System --> Administration --> Hardware Drivers, the Broadcom B43 wireless driver is shown as both enabled and in use, and the wireless light on the laptop is lit. However, the computer is not picking up any wireless signals, and I am also unable to manually connect to the wireless network in the house. Any ideas?

-Jeff

---

### Post by abelianjeff on 2008-07-31
Solved. Thanks anyway!

---

### Post by calexbg on 2008-10-03
I'm having the same problem on my Compaq Presario m2000 (bcm4306 rev. 03).  I had ndiswrapper working with dapper onward until hardy, and I've been having an endless stream of trouble with the wireless setup.  Right now I have a fresh install of hardy, updated, enabled the bcm43xx hardware in Administration->Hardware Drivers, wireless light is on, but no wireless networks show up in network manager (though I have an unsecured, and a wpa network in range).  Here's the readout of iwconfig:

colin@colin-laptop:~$ sudo iwconfig
[sudo] password for colin: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks =]

---

