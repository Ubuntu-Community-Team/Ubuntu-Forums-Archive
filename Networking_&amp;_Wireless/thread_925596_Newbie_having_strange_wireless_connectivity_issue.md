---
title: "Newbie having strange wireless connectivity issue"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by MrCashMan on 2008-09-20
Hello all,

I installed Ubuntu on my machine and have thus far been VERY pleased.  I am however having a strange problem with my wireless connection.  It detects my card just fine, and I am able to get on my wireless network no problem.  However, it seems that when I start downloading above a certain threshold of bandwidth, my wireless connection dies, and I'm unable to get it back unless I restart the computer.  A friend told me to try this command:

sudo /etc/init.d/networking restart

But it doesn't help.  Here is an output of something that I saw in another thread about someone else having problems, so I ran the same command to see if the info might be relevant to my problem.  

lloyd@lloyd-desktop:~$ sudo lshw -C network
[sudo] password for lloyd: 
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: wifi0
       version: 01
       serial: 00:06:25:a7:71:89
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.2 ip=192.168.1.3 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b

Any help would be greatly appreciated!  //EDIT: This is a DESKTOP system btw.

Regards,
Lloyd

---

### Post by alloftheabove on 2008-09-20
I don't really think I can help you, having my own problems lol.  However, I think that people might want to know whether you are using a laptop or a desktop.  Just thought it might help.

---

### Post by MrCashMan on 2008-09-22
Anyone have any ideas?  :(

---

### Post by MrCashMan on 2008-09-23
bump.

---

