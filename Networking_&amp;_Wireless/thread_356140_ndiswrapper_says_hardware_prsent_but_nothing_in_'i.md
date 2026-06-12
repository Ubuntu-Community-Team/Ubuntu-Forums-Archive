---
title: "ndiswrapper says hardware prsent but nothing in 'ifconfig'"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by manishk on 2007-02-08
I use a bcm4311 wireless card on my HP nx6325 laptop. I used NDISWrapper to 'load' the Windows driver, but I get the following:
[I]
**sudo ndiswrapper -l**
Installed drivers:
bcmwl5 driver installed, hardware present

**ifconfig**
eth0 Link encap:Ethernet HWaddr 00:15:60:C8:64:5F
inet addr:172.16.40.145 Bcast:172.16.40.255 Mask:255.255.255.0
inet6 addr: fe80::215:60ff:fec8:645f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4301 errors:0 dropped:0 overruns:0 frame:0
TX packets:3804 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0 MiB) TX bytes:0 (0 MiB)
Interrupt:233

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:700 (700.0 b) TX bytes:700 (700.0 b) [/I]

Any solutions??

Thanks in advance.

---

### Post by phossal on 2007-02-08
Try rebooting. If that doesn't work, it's possible that your wireless device is being loaded using the wrong drivers. It's often necessary to blacklist and/or remove drivers that come with Ubuntu by default.

---

### Post by manishk on 2007-02-08
I have done that too. 

P.S: earlier I had a working wireless card, through NDISWrapper but I lost it to a reinstall. Sadly I dont remember how exactly I had enabled it since I had tried almost every HowTo here!! :)

---

### Post by Corvo78 on 2007-02-08
Is your wireless listed in the /etc/iftab file?

---

### Post by bvmou on 2007-02-08
I have the same card, also an HP.  I got it working, oddly enough, with a Dell driver, available here:  ftp.us.dell.com/network/R115321.EXE

The download from the hp website didn't work, which I presume is the case with the OEM windows driver as well.  No real idea why the one and not the other, something about the 64-bit version loading when 32 was called for.  Could you post the output of the command: dmesg | grep ndiswrapper

---

### Post by manishk on 2007-02-09
Well, I got it working using fwcutter now but still would prefer NDISWrapper since it supports being switched on/off using the radio button on the keyboard.

@Crovo78
Will the /etc/iftab have any relevance with respect to NDISWrapper now??

@bvmou
Even I had that problem of a 64-bit driver being loaded on a 32-bit kernel, I had posted that in a different thread.
I'll try the Dell driver and get back.

Thanks

---

