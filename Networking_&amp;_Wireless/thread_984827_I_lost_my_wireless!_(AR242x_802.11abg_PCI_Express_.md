---
title: "I lost my wireless! (AR242x 802.11abg PCI Express Adapter (rev 01)"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by uhappo on 2008-11-17
Suddenly I lost my wireless, it just went down. I'm using the latest snapshot from madwifi. Previously it has worked beautifully.

08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

dmesg | grep ath0```

[  112.628633] ath0: no IPv6 routers present

```

Whats going on?

---

### Post by jnorthr on 2008-11-17
not familiar with madwifi, but your output shows that there is no access-point your system can connect to. The ESSID is empty and this is the name many routers need to identify a 'client' so if you can get the ESSID set, you may be back in business.

---

### Post by jnorthr on 2008-11-17
just did a 'man iwconfig' to view the manual for the iwconfig command. It shows an example like:
[COLOR="Red"]sudo iwconfig ath0 essid any[/COLOR]
to reset your wireless to look for any available network to connect to.

---

### Post by uhappo on 2008-11-17
> **jnorthr said:**
> just did a 'man iwconfig' to view the manual for the iwconfig command. It shows an example like:
[COLOR="Red"]sudo iwconfig ath0 essid any[/COLOR]
to reset your wireless to look for any available network to connect to.

Didn't work

---

### Post by maestrobwh1 on 2008-11-18
Same problem here.  Using AR5001X+ and had madwifi compiled and it was working well.  It also just stopped working yesterday.  I reinstalled madwifi and I can see athO and wifi0... I can scan and see my router.  It just refuses to connect.

added the linux-restricted blah blah-intrepid... ath5k "works" in the sense that I see ath0 and wmaster00, it scans and sees my router, but just will not connect.  

I have an eee-pc that uses an atheros card running hardy and it still works.  I also have a the AR5001X+ in my on desktop running hardy, it still works.  I have an eee-box with a ralink wireless and it works.  

My acer laptop running intrepid with manually compiled madwifi worked great and now I absoultely cannot get it to work.  It is there... just not usable.

I stuck an Airlink USB in the same laptop and it immediately configured and connected.

There are several posts to this so I am wondering what upgrade did this to people and how to undo it.

The hardware manager is completely confusing... showing things that either are not on the machine, can't be enabled, shouldn't be enabled...

WTF?

---

### Post by dataflowcrescendo on 2008-11-23
HP Compaq Presario c700
Wifi worked... I think after a kernel update something mysterious happened. Or maybe it was kismet. We need a solid c700 bugs list.

---

### Post by uhappo on 2008-11-29
> **dataflowcrescendo said:**
> HP Compaq Presario c700
Wifi worked... I think after a kernel update something mysterious happened. Or maybe it was kismet. We need a solid c700 bugs list.

After kernel update you have to recompile the installer, or whatever is the word for Make -> sudo make install..

---

