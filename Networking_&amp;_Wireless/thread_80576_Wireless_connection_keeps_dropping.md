---
title: "Wireless connection keeps dropping"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by Rob2687 on 2005-10-22
I got an SMCWCB-G pcmcia card the other day. I think it has an atheros chip. 
I installed it in windows and it works fine but when in ubuntu, the connection keeps dropping after a minute or two and I have to reconnect in wifi-radar. Eventually if I do it too much the system will just freeze.
It's installed with ndiswrapper. I tried madwifi but it doesn't work fully. (Only works in b mode and doesn't always connect.)

Are there any settings I can play around with or anything?

---

### Post by bionnaki on 2005-10-22
did you enter the proper dns server info?

---

### Post by Rob2687 on 2005-10-22
I didn't enter any info. It's set up on DHCP.

It will connect and I can surf, download and everything. The connection just keeps dropping.

---

### Post by vimico on 2005-10-22
I have similar problems with madwifi / Atheros since updating to Breezy, but with another PCMCIA card.

Can you check the ARP cache of the other machines?

```
arp -a
```

You should see something like this:

```
10.0.0.1    EF-34-56-78-90-AB
```

The first value is an IP address, the second is a MAC address. (A MAC address is like an IP address on a lower level.  Without it, communication does not work either).

On the non-WIFI machines, the IP (and MAC) address of the WIFI machine should be listed. Could you please check this.

---

### Post by Rob2687 on 2005-10-23
? (192.168.1.1) at 00:0F:55:A9:42:AB [ether] on wlan0

---

### Post by mlambie on 2005-10-23
I found that my connection was dropping every few minutes for no good reason. I told NetworkManager to search "only when disconnected" and it seems to have stabilized. 

Good luck.

---

### Post by vimico on 2005-10-23
[quote=Rob2687]? (192.168.1.1) at 00:0F:55:A9:42:AB [ether] on wlan0[/quote]

Ok. ARP does work. It was just a hunch.

---

### Post by Rob2687 on 2005-10-23
[QUOTE=mlambie]I found that my connection was dropping every few minutes for no good reason. I told NetworkManager to search "only when disconnected" and it seems to have stabilized. 

Good luck.[/QUOTE]
Where is that option? I can't seem to find it.

Edit: Nevermind...I need an app that supports WPA. :(

---

### Post by gtrtoolman on 2006-11-12
I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman

---

### Post by headflux on 2007-11-24
> **gtrtoolman said:**
> I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman

Hi, I am having similar problems with Gutsy.  What do you mean by "remarked"
Thanks

---

### Post by ghostdog2402 on 2007-12-17
> Hi, I am having similar problems with Gutsy. What do you mean by "remarked"
Thanks

it means you put a ```
#
``` sign before the ```
iface eth0 inet dhcp
```

In the utc/network/interfaces

open the interfaces with Mousepad

---

