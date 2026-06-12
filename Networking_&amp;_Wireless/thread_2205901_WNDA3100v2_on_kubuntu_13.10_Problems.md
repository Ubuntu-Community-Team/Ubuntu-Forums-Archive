---
title: "WNDA3100v2 on kubuntu 13.10 Problems"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by BrAjN on 2014-02-16
Hi everyone hope somebody can help me, as i mention in the title i got this usb wireless from netgear on kubuntu 13.10 64bit and this is what i have:

```

brajn@Laboratory:~/Templates/WNDA3100v2$ ndiswrapper -l
bcmn43xx32 : driver installed
        device (0846:9011) present

brajn@Laboratory:~/Templates/WNDA3100v2$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

brajn@Laboratory:~/Templates/WNDA3100v2$ lsusb
Bus 001 Device 005: ID 0424:2412 Standard Microsystems Corp. 
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04e8:3301 Samsung Electronics Co., Ltd 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```



so, i can see the device but i can't get installed thanks in advance for any advise.

---

### Post by varunendra on 2014-02-16
Welcome to the forums BrAjN !

Which version of windows driver did you install with ndiswrapper? Was it for Windows XP 64 bit?

What is the output of -
```
dmesg | grep ndis
```

---

### Post by BrAjN on 2014-02-17
> **varunendra said:**
> Welcome to the forums BrAjN !

Which version of windows driver did you install with ndiswrapper? Was it for Windows XP 64 bit?

What is the output of -
```
dmesg | grep ndis
```

I have try the inf file from windows 8 64 bit, then i found in this forum a link to this driver bcmn43xx64.inf, i even try with 32bit version but nothing...


dmesg | grep ndis has no output:

```

brajn@Laboratory:~$ dmesg | grep ndis
brajn@Laboratory:~$ 

```

---

### Post by varunendra on 2014-02-18
Please give me the link to the forum post that you tried. I don't personally have much experience or knowledge about ndiswrapper, I just hope I may be able to conjure some help from such links from Solved threads in this forum.

---

