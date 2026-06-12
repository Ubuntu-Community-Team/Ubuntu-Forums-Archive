---
title: "Wireless network keeps connecting/disconnecting after automatic update"
date: 2014-03-05
forum: Networking &amp; Wireless
---

### Post by Martin7182 on 2014-03-05
Hi all,

Since a few days my wireless connection doesn't work properly any more. It keeps connecting and disconnecting after a few minutes. It could have to do with automatic updates because only my two Ubuntu pc's suffer from this problem. My other wireless devices are just fine.

Some details:

OS: Ubuntu Lucid 10.04, kernel 2.6.32-57-generic

```
lspci
...
07:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
...

```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tun0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"my connection"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:11:50:5A:C2:D7   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've manually installed the "linux-firmware-nonfree" package and reloaded the b43 driver, but that didn't help.
```

sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43

```

Thanks for any suggestions,
Martin

---

### Post by varunendra on 2014-03-06
Let's take a look at other settings then. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

By the way, do you know that 10.04 desktop is no more supported? Can you upgrade to 12.04? (I recommend a fresh installation if you can).

---

### Post by Martin7182 on 2014-03-08
Thanks Varun, the issue solved itself in the meantime by automatic updates.
I'll upgrade to 12.04 asap, thanks for the hint.

Martin

---

### Post by varunendra on 2014-03-09
Glad it sorted out by itself. :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

**PS:**
For downloading 12.04, I highly recommend using torrents for higher download speeds and guaranty of the integrity of downloaded ISO.
Official torrent links : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Create a Live DVD or USB, and test it in Live mode first to make sure it works nicely with your system. Install only if satisfied with the performance. If the system specs are low, Xubuntu may be a better alternative.

---

