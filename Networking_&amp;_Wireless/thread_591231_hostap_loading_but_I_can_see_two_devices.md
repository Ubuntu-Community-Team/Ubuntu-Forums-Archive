---
title: "hostap loading but I can see two devices?"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by echodep on 2007-10-25
Hi, I've pulled HostAP and utils from synaptic having recently upgraded to gutsy via synaptic too.  I blacklisted the orinoco drivers in /etc/modprobe.d and edited /etc/pcmcia/config so that the card would bind to the hostap_cs.  I also added host_cs in the device section and gave values """ class "network" module "hostap_cs" """.  When I insert the card I get two beeps but if I do an iwconifg I have two instances for the card eth3 and wlan0_rename.  

dmesg seems to show everything is ok.
[  896.796000] pccard: PCMCIA card inserted into slot 0
[  896.796000] pcmcia: registering new device pcmcia0.0
[  896.796000] hostap_cs: setting Vcc=33 (constant)
[  896.796000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[  896.796000] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[  896.796000] io->flags = 0x0046, io.base=0x0000, len=64
[  896.796000] hostap_cs: Registered netdevice wifi0
[  896.836000] hostap_cs: index 0x01: , irq 3, io 0xe100-0xe13f
[  897.028000] prism2_hw_init: initialized in 192 ms
[  897.028000] wifi0: NIC: id=0x800c v1.0.0
[  897.028000] wifi0: PRI: id=0x15 v1.1.0
[  897.028000] wifi0: STA: id=0x1f v1.8.4
[  897.032000] wifi0: registered netdevice wlan0


lshw -C network shows

  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0_rename
       serial: 00:02:6f:03:89:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.8.4 multicast=yes wireless=IEEE 802.11b

cardmgr says it is busy

I'm stuck and not sure where to look from here, please help!

thanks, echo.




 I'm using a Senao NL2511CD with firmware 1.8.4 which has a Prism2.5 chipset.

---

