---
title: "Help with Inventel UR054g (RO1) device with Ubuntu"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by rhyswynne on 2007-03-06
Hi everybody

I recently tried returning to my Ubuntu (Edgy Eft) setup now that Windows is once again misbehaving. I have previously tried to get my Inventel (Conexant) Wireless UR054g (R01) USB Dongle working with it (the one that is given away with Wanadoo/Orange broadband), but have had no such luck. I gave up, but after reading threads, people have been successful.

I have tried and followed as much as possible on this thread [http://www.ubuntuforums.org/showthread.php?t=280239&highlight=UR054g](http://www.ubuntuforums.org/showthread.php?t=280239&highlight=UR054g)

and used the drivers mentioned in the following thread
[http://www.ubuntuforums.org/showthread.php?t=157180&highlight=UR054g](http://www.ubuntuforums.org/showthread.php?t=157180&highlight=UR054g)

and when I carry out a ndiswrapper -l in terminal, it is reporting the prisma04 driver present and the hardware is also present. The light on the USB device is on, but I'm unable to detect any WAN networks.

My router is currently unprotected, so there's no issue regarding WEP/WPA.

Any ideas? Or what further information do you need, and I'll be happy to get it?

Thanks in advance, I really want to get Ubuntu working, as apart from this minor niggle, I love it :)

---

### Post by rhyswynne on 2007-03-07
Anybody? Surely somebody can help me? Or do you need more information?

---

### Post by rhyswynne on 2007-03-09
Bumpity bumpity!

---

### Post by chili555 on 2007-03-09
Could we please take a look at iwconfig as well as sudo iwlist <your_wireless_interface> scan?

We'll get you going.

---

### Post by rhyswynne on 2007-03-09
iwconfig

```
rhys@rhys-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

iwlist eth2 scan

```
rhys@rhys-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results
```

Hope this helps. I'm assuming eth2 was my wireless interface?

---

### Post by chili555 on 2007-03-09
eth2, it is! I would try sudo iwconfig eth2  mode managed followed by sudo iwconfig eth2 channel auto and see if you can sudo iwlist eth2 scan and produce a result, especially an ESSID we can specify in iwconfig.

Another option is to go into the administration page of your router to find the exact ESSID and then sudo iwconfig eth2 essid <essid_you_found>

---

### Post by rhyswynne on 2007-03-10
Trying the first method

```
rhys@rhys-desktop:~$ sudo iwconfig eth2 mode managed
Password:
rhys@rhys-desktop:~$ sudo iwconfig eth2 channel auto
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth2 ; Invalid argument.
rhys@rhys-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results

```

I then logged into my router. I couldn't find an ESSID, only an SSID. My router is a Netgear DG834G (if that is any use to you). Anyway, the SSID I found was "Wireless"

Trying the second method

```

rhys@rhys-desktop:~$ sudo iwconfig eth2 essid Wireless
rhys@rhys-desktop:~$ sudo iwlist eth2 scan
eth2      No scan results

```

Couldn't find anything via a scan, and I couldn't connect to the internet.

Any ideas?

---

### Post by chili555 on 2007-03-10
I have to think that the channel is the only roadblock left. Obviously, if your interface is listening on channel 1 and your router is broadcasting on channel 6, they will not connect. So, let's try sudo iwconfig eth2 channel 6 followed by sudo dhclient eth2.

I picked channel 6 because routers typically, but not always, ship transmitting on channel 6. If this doesn't work, you may have to go back into the router's administration pages, under wireless, to see what channel is being used.

Good luck and let us know.

---

