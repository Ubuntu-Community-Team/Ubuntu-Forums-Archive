---
title: "Slow internet with Rt2500 wireless card"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by fearevilleet on 2007-12-04
Hi,

 After upgrading to Gusty my internet is very slow. I have read every thread on how to try and resolve this issue but have been unsuccessful so far.  I have an RaLink RT2500 802.11g, using ndiswrapper, both  seemed to be installed and working correctly but download speed with not go over 200k. 


```
02:03.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
```

output for ndiswrapper

```
evil@box:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist line 29: ignoring bad line starting with 'blacklist-ipv6'
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500pci)

```

I have globally disabled ipv6 

```

evil@box:~$ lsmod | grep ipv6
evil@box:~$

```

I am also using opendns. Could anyone give me a hand with this?

Edit:

If anyone can help me solve this issue I will mail you $20 or make a donation to Ubuntu or something simular--- seriously. Having this prblem solved will be worth 20$.

---

### Post by fearevilleet on 2007-12-05
Please anyone, I even posted on somethingawful and know one knows.

---

### Post by hyp3R on 2007-12-05
I wrote some kind of guide how to configure RT2500 in let's say right way...
Try with it, not sure if it will help ...
Download attached file ... 
Hope it will help

---

### Post by fearevilleet on 2007-12-07
I actually tried the serial monkey drivers before I reinstalled Gusty, no luck. I think i am just going to have to buy a new wireless card. Cheap enough I guess

---

### Post by gark on 2008-05-21
The latest CVS version of the rt2500 driver from serialmonkey works like a charm.

The only problem is that it doesn't work with the gnome network manager, so you will have to use iwpriv to configure your connection.

I wrote some simple instructions on my webpage, mainly to help myself remember what I did, but I guess it could be useful for others as well: [http://blog.slettevoll.no/node/7]("http://blog.slettevoll.no/node/7")

---

### Post by arquio on 2008-06-02
I'm using RutilT, it is best that networ-manager for rt2500.

---

