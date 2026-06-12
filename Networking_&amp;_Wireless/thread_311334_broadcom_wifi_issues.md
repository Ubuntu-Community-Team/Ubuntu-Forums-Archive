---
title: "broadcom wifi issues"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by icky on 2006-12-02
i've followed [bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) to the teeth, up until performing iwlist... here's what i've got...

```
0000:06:02.0 Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1358
        Flags: bus master, fast devsel, latency 64, IRQ 233
        Memory at b0204000 (32-bit, non-prefetchable) [size=8K]

$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device
```

also, when i went to use bcm43xx-fwcutter on my driver from windows, i got:

```
Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum 114234fafec7060392195170e1c4d45e :(
```


also, after assigning eth1 an ssid, i tried dhclient. it sent discover to 255.255.255.255, i'm guessing i'm just screwed?

so am i screwed or can someone offer some insight?

---

### Post by icky on 2006-12-02
ok i understand i'm screwed thanks anyway

---

### Post by FrodoB on 2006-12-02
Have you done a search for your device on the forum and Google? I don't  have this device, but someone has surely documented it.

---

### Post by FrodoB on 2006-12-02
Note all of the entries for 4319 on the ndiswrapper wiki list:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Be sure to look at all of them. The are recommended NDIS drivers for 32bit and 64bit Linux.

I am not a big ndiswrapper user, but that is one possibility. 

The other is to get bcm43xx and fw-cutter working.

---

### Post by icky on 2006-12-02
> **FrodoB said:**
> Note all of the entries for 4319 on the ndiswrapper wiki list:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Be sure to look at all of them. The are recommended NDIS drivers for 32bit and 64bit Linux.

I am not a big ndiswrapper user, but that is one possibility. 

The other is to get bcm43xx and fw-cutter working.

[http://ubuntuforums.org/showpost.php?p=1656821&postcount=3](http://ubuntuforums.org/showpost.php?p=1656821&postcount=3) , however i will look into it...

and [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

---

### Post by FrodoB on 2006-12-02
Good luck. The key to get either one to work is finding a set of NDIS drivers that work well to cut the firmware from or install ndiswrapper.

---

### Post by icky on 2006-12-02
> **FrodoB said:**
> Good luck. The key to get either one to work is finding a set of NDIS drivers that **work well** to cut the firmware from or install ndiswrapper.

thanks, i'll need it

---

