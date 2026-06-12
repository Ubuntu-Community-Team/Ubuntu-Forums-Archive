---
title: "ipw works, but drops connection every 10 seconds"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by siennalizard on 2005-11-25
Hello all,

I finally got my ipw2200 drivers to work with the 686 kernel that comes with breezy, and successfully made a connection with wpasupplicant to my wpa-psk protected network. Whether under load or not, however, the connection fails every few seconds. Checking the syslog with tail -f whilst flood pinging the router gave me several errors. The flood ping was just so that I could see when packets were being sent properly. These messages and errors occurred every time the flood ping stopped:

```

Nov 25 11:27:09 localhost kernel: [59481.995843] eth1: MSDU decryption/MIC verification failed (SA=00:11:50:24:6b:a3 keyidx=0)
Nov 25 11:27:14 localhost kernel: [59486.991695] TKIP: replay detected: STA=00:11:50:24:6b:a3 previous TSC 00000000000d received TSC 000000000002
Nov 25 11:27:17 localhost kernel: [59489.384448] eth1: no IPv6 routers present
Nov 25 11:27:23 localhost kernel: [59495.308273] N/A: Michael MIC verification failed for MSDU from 00:11:50:24:6b:a3 keyidx=0
Nov 25 11:27:23 localhost kernel: [59495.308280] eth1: MSDU decryption/MIC verification failed (SA=00:11:50:24:6b:a3 keyidx=0)
Nov 25 11:27:28 localhost kernel: [59500.298145] N/A: Michael MIC verification failed for MSDU from 00:11:50:24:6b:a3 keyidx=0
Nov 25 11:27:28 localhost kernel: [59500.298152] eth1: MSDU decryption/MIC verification failed (SA=00:11:50:24:6b:a3 keyidx=0)

```

So, whilst the connection comes up, I loose so many packets that it's hardly usable.

Any ideas? I'd be very grateful, as googling for these errors doesn't throw up any useful information.

J.

---

### Post by hoomanb on 2006-02-21
Have you found a solution? I'm having the same problem at work and if I don't manage to fix it soon they might make me use Windows! :evil:

---

### Post by drakeoutlaw on 2006-02-21
Check your range. Does the problem go away if you get close to the wireless router?

---

### Post by siennalizard on 2006-02-21
Hello there,
I don't mean to scare or upset you, but I'm quite an experienced Linux user, and it took me a _very_ long time to get this working smoothly (and I'm not even quite sure which of the many changes I made did the trick).

One thing I would check is that the router does not do 802.11e Quality of Service (QoS). It seems to mess up the 4-way handshake that is important with WPA. I've got a Belkin Pre-N router, and this (I think) solved the problem for me.

If that didn't work...

I'm assuming you've done a search on the forums and read all the ipw2200 stuff. If so, in brief:

- I fetched the latest stable linux kernel sources from [http://kernel.org](http://kernel.org), and compiled myself a new custom kernel using kpkg.

- I fetched the latest ieee80211 sources, and the sources and firmware from the ipw2200 project page on sourceforge, and compiled the modules.

- I then dumped the wpasupplicant package that comes with ubuntu, and fetched the latest version. I compiled it after creating a .config file in the source directory containing:
```

CONFIG_DRIVER_HOSTAP=y
CONFIG_DRIVER_WEXT=y
CONFIG_WIRELESS_EXTENSION=y
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
CONFIG_EAP_GTC=y
CONFIG_EAP_OTP=y
CONFIG_EAP_SIM=y
CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_CTRL_IFACE=y

```

I then symlinked to the new supplicant in /usr/bin and changed my /etc/default/wpasupplicant file to use -D wext, rather than -D ipw

If you do all of that, it will put your computer in pretty much the same state as mine re wireless networking. I'm assuming that, if your problem is the same as mine, that will solve it.

Good luck!
J.

---

### Post by hoomanb on 2006-02-21
I'm pretty close to the router (like 1-2 meters with nothing in between). 

I've learned this might have something to do with ieee80211 modules that ipw2200 uses. Maybe another version of 80211 will fix the problem but I could only get the card woking by combining a certain version of ieee80211 with a certain version of ipw2200 modules and I don't want to play around (the card works at home and for work I found a usb wifi that works fine :D ).

---

### Post by siennalizard on 2006-02-21
hoomanb, just out of interest, what is the usb id of that wireless usb adapter? (Just do "lsusb").

Cheers!
J.

---

### Post by hoomanb on 2006-02-21
Thanks for your help. I could get the latest version of ipw and latest version of ieee80211 compiled together, I am gonna try the latest wpa supplicant as well as -D wext as you suggested. 

BTW, that card isn't usb , I meant I'm using a usb card INSTEAD for the time being until I mess with this over the weekend again.

---

### Post by greenrenault on 2006-10-29
Just passing thru and saw via Google and noticed this thread didn't have the answer to the problem, which I've since found. See this URL below.

[http://www.tuxyturvy.com/blog/index.php?/archives/23-Using-the-IPW3945-with-Linux,-WPA,-and-the-SMP-Kernel.html](http://www.tuxyturvy.com/blog/index.php?/archives/23-Using-the-IPW3945-with-Linux,-WPA,-and-the-SMP-Kernel.html)

---

