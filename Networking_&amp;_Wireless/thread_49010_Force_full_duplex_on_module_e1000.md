---
title: "Force full duplex on module e1000"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by olat on 2005-07-14
HI All!
I'm new to Ubuntu. I wonder howto make my network card go full duplex. In windows it runs with full duplex so why not i linux? It works with the module e1000. But i cant find where to edit any options for it. It is not listed i /etc/modules (maybe compiled into the kernel?).

- Ola

---

### Post by alastair on 2005-07-14
ethtool eth0

will report details.

And see : man ethtool

for possible ways to set duplex mode. It will depend on the other end of the link ofcourse. This is usually auto-negotiated.

Install via : apt-get install ethtool

From the e1000.txt file in the linux kernel Documentation :

```

Speed and Duplex Configuration
==============================

Three keywords are used to control the speed and duplex configuration. These 
keywords are Speed, Duplex, and AutoNeg.

If the board uses a fiber interface, these keywords are ignored, and the 
fiber interface board only links at 1000 Mbps full-duplex.

For copper-based boards, the keywords interact as follows:

  The default operation is auto-negotiate. The board advertises all supported
  speed and duplex combinations, and it links at the highest common speed and
  duplex mode IF the link partner is set to auto-negotiate.

  If Speed = 1000, limited auto-negotiation is enabled and only 1000 Mbps is
  advertised (The 1000BaseT spec requires auto-negotiation.)

  If Speed = 10 or 100, then both Speed and Duplex should be set. Auto-
  negotiation is disabled, and the AutoNeg parameter is ignored. Partner SHOULD
  also be forced.

The AutoNeg parameter is used when more control is required over the auto-
negotiation process.  When this parameter is used, Speed and Duplex must not 
be specified.  This parameter is a bitmap that specifies which speed and 
duplex settings are advertised to the link partner.

Bit            7      6      5       4       3      2      1       0
Speed (Mbps)   N/A    N/A    1000    N/A     100    100    10      10
Duplex                       Full            Full   Half   Full    Half

For example to limit the negotiated speed/duplex on the interface to 10 Mbps 
Half or Full duplex, set AutoNeg to 0x02: 
    insmod e1000 AutoNeg=0x02

Note that setting AutoNeg does not guarantee that the board will link at the 
highest specified speed or duplex mode, but the board will link at the 
highest possible speed/duplex of the link partner IF the link partner is also
set to auto-negotiate. If the link partner is forced speed/duplex, the 
adapter MUST be forced to the same speed/duplex.

```

---

### Post by olat on 2005-07-14
Thanks for the quick reply.! I have tryed ethtool, but no success  ](*,)  . I checked some readme about e1000 and ethtool is not supported. Ethtool can only read infomation from e1000, not change  :? 
My problem is that I cant find where the modules is loaded (which file, I've checked /etc/modules). Then I can add the correct options to the e1000 module.

Any ideas?

-ola

---

### Post by olat on 2005-07-15
I've got it to work with:
sudo ethtool -s eth0 speed 10 duplex full autoneg off  \\:D/ 

The only problem is to load the options at boot. 

Thanks
- Ola

---

### Post by alastair on 2005-07-15
It is unfortunately not obvious how to do the "load on boot" thing.

It looks like you /might/ be able to add a file :

/etc/modprobe.d/e1000

and add a line to this :

options e1000 <option list>

But perhaps this line should go in "/etc/modprobe.d/aliases".

Perhaps you could do some digging and find out. Let us know.

---

