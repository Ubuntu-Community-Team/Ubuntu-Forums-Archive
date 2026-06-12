---
title: "wlan0 working, but not connecting."
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by npodges on 2006-08-17
I've got an Inspiron e1705, with the Broadcom 4311 wireless card..

I have the drivers correctly installed, and using network-manager, it even finds all wireless networks available.

Two problems:

1) when booting up, at the setting up network step, it sits there for about 30-60 seconds. Also everytime i change a wireless setting in network-admin, it takes quite a bit of time. Is this normal?

2) Although network-manager applet finds all local wireless networks, I cannot connect to any of them. They are unprotected, and should work fine.

Thanks,

Nick

---

### Post by npodges on 2006-08-17
Oh and, if it helps, iwconfig gives:

```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by bjorn 33 on 2006-08-17
I'm having the same trouble, but with my wireless device assigned to ra0.  Any thoughts?  Thanks!

---

### Post by ComplexNumber on 2006-08-17
> **bjorn 33 said:**
> I'm having the same trouble, but with my wireless device assigned to ra0.  Any thoughts?  Thanks!
apparently, its meant to in ubuntu.

---

### Post by npodges on 2006-08-18
I might just be an idiot, but i got it working... When i was setting it up, in network-admin, I had to click the drop down menu and select the network there.

If i didn't chose a network, network-manager wasn't finding any.. I'm not sure if it's right now, but it's working now.

---

### Post by ComplexNumber on 2006-08-18
> **npodges said:**
> I might just be an idiot, but i got it working... When i was setting it up, in network-admin, I had to click the drop down menu and select the network there.

If i didn't chose a network, network-manager wasn't finding any.. I'm not sure if it's right now, but it's working now.
install wifi-radar, then reboot, and see if that makes any difference. on fedora, i didn't have to put any settings in whatsoever because it detected everything perfectly.....even down to knowing that i'm attached to a router etc. all thats necesary is to install the ndiswrapper, then the windows drivers, and...............voila! an internet connection

---

### Post by bjorn 33 on 2006-08-20
I also have my wireless working now.  I made the embarrassing mistake of using a ASCII WEP key instead of hex.  Thanks to the Ubuntu forum and especially to Zotova on the thread [http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500](http://www.ubuntuforums.org/showthread.php?t=188192&page=2&highlight=rt2500).

---

