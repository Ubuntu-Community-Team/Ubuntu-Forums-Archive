---
title: "WPA not an option on Xubuntu 8.04 ppc...ideas please?"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by stir-crazy on 2008-10-16
Hi there,

finally got Xubuntu 8.04 installed on an old iBook (G3 300mhz, 192mb ram) and everything works as good as could be hoped for, except the wireless doesn't give me the WPA security option, just:

WEP-128bit
WEP 64/128-bit Hex
WEP 64/128-bit ASCII
LEAP

Back when this ran OSX, there was no problem with WPA, so I know it isn't a limitation with the card.  [THIS]("http://ubuntuforums.org/showthread.php?t=263136") was the most promising info I think I could find here on the forums, but it doesn't seem to have worked for me.

At terminal "lshw -C Network" returns (hope this helps you help me):

```
  *-network               
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:20:0f.0
       logical name: eth0
       version: 00
       serial: 00:30:65:69:2e:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.4 latency=16 link=yes maxlatency=64 mingnt=64 module=sungem multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:27:92:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.70 link=yes multicast=yes wireless=IEEE 802.11b
```

I really would rather not downgrade from WPA to WEP encryption, and it would really be nice for when we grab coffee at our favorite place (which I think is also WPA) not to have to do all sorts of editing from terminal just to update the password weekly.

Sigh.  In advance, thanks so much for any help you may provide.

---

### Post by jimv on 2008-10-16
Use WICD for your network manager (works fine in Xubuntu), and then install the wpasupplicant package for the WPA support.

You can get WICD here:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by stir-crazy on 2008-10-16
Thanks for the fast reply, will give that a shot now; couldn't find it in the repositories from other threads.  Thanks again!

EDIT: Not sure what my issue continues to be here.  WICD installed, nice interface, allows me to select from WPA encryption.  But it doesn't connect.  Strangely enough, it detects my network, but diplays it as WEP, which it is absolutely not; it's WPA-PSK [TKIP] + WPA2-PSK [AES].

I'll try all the combinations I can think of on this, but if there are any other ideas anybody has out there, would love to hear them.

Also, despite being about 5 feet away from the wireless router, it registers a weak signal.  That signal disappears completely after about 10 feet...

Thanks again!

---

### Post by jimv on 2008-10-16
Ok, I did some research, and I think the driver that Ubuntu is using for your wireless doesn't support WPA...but the card does.

Here's a post about updating that driver so it will support WPA:

[http://ubuntuforums.org/showthread.php?p=5148420#post5148420](http://ubuntuforums.org/showthread.php?p=5148420#post5148420)

---

### Post by stir-crazy on 2008-10-16
Thanks again, but that didn't seem to do the trick.  I'll have to keep looking, but I think I'm halfway there now.

---

### Post by stir-crazy on 2008-10-17
Okay, been playing around with my router settings, turns out I can't use any encryption.  Arrrrr!  So I'm back to my old ways of security, no encryption, but MAC address must be recognized.  Probably should turn of SSID broadcast, but I'm still not comfortable with this.

Once (if) I get it figured out, I'll post back with what did the trick.  Or any of the many genius IQ people here who've already figured it out, please chime in!

---

