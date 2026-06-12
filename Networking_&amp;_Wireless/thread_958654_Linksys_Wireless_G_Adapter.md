---
title: "Linksys Wireless G Adapter"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by Sexraider on 2008-10-25
I had a thread in the beginner section, but No one provided help to get my adapter working.

I'm using a linksys Wireless G 2.4ghz 802.11g adapter.

I've done iwconfig this is what comes up
```
syrex@syrex-desktop:~$ iwconfig
lo   no wireless extensions

rausb0   rt2500usb wlan essid: ""
         mode: managed  frequency = 2.412 GHz
         RTS thr: off  fragment thr: off
         link quality= 0/70  signal level:- 120 dBm 
noise level:- 256 dBm
         Rx invalid nwid: 0 Rx invalid crypto: 0 Rx Invalid
frag: 0
         Tx excessive retries: 0 Invalid misc: 0 missed beacon: 0

eth0   No wireless extensions

sit0   No wireless extensions
```

I've done sudo ifup rausb0 and this came up
```
password:
ignoring unknown interface rausb0=rausb0
```

and when i did iwlist scan it said

```
lo Interface doesn't support scanning

rausb0 No scan results

eth0 Interface doesn't support scanning

sit0 Interface doesn't support scanning
```

Also, When I do ifconfig, Terminal prints this.
```
rausb0	Link encap:Ehternet	Hwaddr 00:12:17:67:38:49
	inet addr:192;168.1.103 Bcast:192.168.1.225 Mask: 255.255.255.0
	inet6 addr: fe80::212:17ff:fe67:3849/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MUTI:1500 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes 130717 (127.6KiB) TX bytes:1656 (1.6KiB)
```

I have my windows booted up posting this, so my internet is indeed working.

I don't know what I'm doing wrong =/

---

### Post by Sexraider on 2008-10-25
~Bump.

Sorry <___<

---

### Post by The Sunburned Surveyor on 2008-10-25
Sexraider,

(I won't ask questions about how you got that user name.) :]

I'm using the same Linksys wireless router as you, and I'm having the same problems.

What wireless network card are you using to connect to the router?

If your using a ralink wireless network card you might want to look at some of the sticky posts at the top of this forum.

The Sunburned Surveyor

---

### Post by Sexraider on 2008-10-25
> **The Sunburned Surveyor said:**
> Sexraider,

(I won't ask questions about how you got that user name.) :]

I'm using the same Linksys wireless router as you, and I'm having the same problems.

What wireless network card are you using to connect to the router?

If your using a ralink wireless network card you might want to look at some of the sticky posts at the top of this forum.

The Sunburned Surveyor

That's not my router. That's my Wireless box Adapter plugged into my computer.



[img]http://img508.imageshack.us/img508/448/68432367lx1.gif[/img]

---

