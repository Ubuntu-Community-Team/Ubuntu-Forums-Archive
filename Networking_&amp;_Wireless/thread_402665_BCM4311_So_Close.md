---
title: "BCM4311 So Close"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by equant on 2007-04-06
I´m using a Lenovo laptop with a Broadcom 4311 wireless card and a fresh install of Edgy (Xubuntu).  I´ve installed the bcm43xx driver following instructions found on the ubuntu wiki/forums (firmware stuff etc).  The wireless light on my laptop is now on, and blinks in response to certain actions (trying to ping, etc), but I can´t get any kind of network connection.

I can get a working network connection using an ethernet cable.

I read on the NDIS 43xx wiki page that a feature called ¨Afterburner¨ needs to be turned off on the Broadcom device in order for it to work with some Linksys access points.  I am using a Linksys wireless access point.  Is there a way for me to check if the afterburner feature is turned off with the bcm43xx driver?

The linksys access point works with other wireless laptops in the house (Mac and Linux).

Any ideas on how to move forward would be greatly appreciated.  After several days of reading forums and wiki pages (all of which have been a great help), I have come to a dead end.

Thanks,
Nathan
Tucson, AZ USA

---

### Post by evilghost on 2007-04-06
You could try using ndiswrapper instead of the firmware cut from fwcutter; I didn't have luck with anything but ndiswrapper on my wife's laptop which has a BCM4311.

---

### Post by equant on 2007-04-06
> **evilghost said:**
> You could try using ndiswrapper instead of the firmware cut from fwcutter

I´m holding the NDIS solution in my back pocket, but I was hoping to get the firmware/native driver working since it seems like I´m pretty much there.

It could be that I´ve got just one step screwed up or something, but I don´t know how to proceed in discovering where my problem is.  It could just be my network configuration or something.  Who knows?  Not me.

Nathan

---

### Post by evilghost on 2007-04-06
What does 'iwconfig' say?

---

### Post by equant on 2007-04-06
Here's my iwconfig output...

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"GSO"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

