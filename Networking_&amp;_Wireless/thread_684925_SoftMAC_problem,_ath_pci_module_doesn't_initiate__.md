---
title: "SoftMAC problem, ath_pci module doesn't initiate  ath0 device"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by ravitejac on 2008-02-01
I'm trying to install softmac over Linux laptop3 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux 

Softmac is an extention to madwifi driver. Please go through [https://systems.cs.colorado.edu/projects/softmac](https://systems.cs.colorado.edu/projects/softmac)

$ sudo make $ sudo make install
generated a lot of warnings.

$ sudo modprobe ath_pci 
generated no errors on command prompt however

$ dmesg 
yielded
 . . .
 [4312730.661000] softmac_core_init
[4312730.760000] ath_hal: module license 'Proprietary' taints kernel.
[4312730.762000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4312730.782000] wlan: 0.8.5.0-BSD (EXPERIMENTAL)
[4312730.785000] ath_rate_onoe: 1.0
[4312730.813000] ath_pci: no version for "cu_softmac_macinfo_get" found: kernel tainted.
[4312730.822000] ath_pci: 0.9.5.0-BSD (EXPERIMENTAL)
...

$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0B:5D:C5:D2:56
          inet addr:10.227.80.202  Bcast:10.227.80.255  Mask:255.255.255.128
          inet6 addr: fe80::20b:5dff:fec5:d256/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:676251 errors:2309 dropped:4109 overruns:2309 frame:0
          TX packets:34308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:114096111 (108.8 MiB)  TX bytes:3096321 (2.9 MiB)
          Interrupt:11 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7652359 (7.2 MiB)  TX bytes:7652359 (7.2 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



Can somebody help me to find what's going wrong? 

Thank you.

---

### Post by peabody on 2008-02-01
Don't know man...While I know you've tried modprobing the ath_pci module yourself and the ath0 interface doesn't seem to exist...have you tried running the script they recommend in the readme?

[https://systems.cs.colorado.edu/projects/softmac/browser/trunk/README](https://systems.cs.colorado.edu/projects/softmac/browser/trunk/README)

Maybe it does something they don't talk about.  Couldn't say.  Do they have a list of supported hardware?

---

### Post by ravitejac on 2008-02-02
The first line of the script is modprobing which I'm tying to do myself. And it doesn't work.

Do you know what could be the reason?  Can there be an error in making the module itself? 

What do you recommend?

---

### Post by peabody on 2008-02-02
Honestly, I've never worked with the software man.  I just don't know.

---

### Post by ravitejac on 2008-02-03
Ok, Thank you peabody.

---

### Post by ravitejac on 2008-02-03
Hey Peabody will any of your friends know about this?

---

