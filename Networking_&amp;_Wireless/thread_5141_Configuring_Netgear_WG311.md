---
title: "Configuring Netgear WG311"
date: 2004-11-15
forum: Networking &amp; Wireless
---

### Post by kepardue on 2004-11-15
I'm setting up a computer for my wife on the other side of the house, but instead of running cables, I've decided to buy a wireless router (Netgear WGR614) and a wireless PCI card (Netgear WG311). I read that these cards were supported under Linux, and they seem to have been detected, hardware-wise, just fine.  I'll eventually be getting a laptop Ubuntu installed, and it'll be nice to have wireless already configured.  

However, when trying to configure the network, both through the initial setup and from Computer/System Configuration/Networking, I can't seem to get anywhere.  I walk through the wizard and select wlan0 as my device, and use the ESSID that I put into the router and the WEP key that I selected.  (Changing the security from Disabled to 128 bit WEP was the only non-factory default change that I've made).  On authentication type, I try Automatic (DHCP) since that's what I believe this router is set up to run on.

However, when trying to activate the connection, it only stays active for a moment, and never seems to connect.  Furthermore, when walking through the process on the Ubuntu install, I get a message saying that my connection configuration has failed, and that it can't configure DHCP, that it may not be running on my network or that it's running too slowly.

I've tried this on both my wife's system and my system.  My system is dual boot with Windows XP, and I'm able to connect to the wireless network just fine from there.

Any thoughts?  I'm not experienced with network administration, so be gentle...

Thanks.

---

### Post by FLeiXiuS on 2004-11-16
Have you installed the nsdiswrapper for your Wi-Fi NIC Card yet?

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.7773155363)

---

### Post by kepardue on 2004-11-16
Well, the problem here is that I can't get on the Internet to update the packages this article mentions.  The other computer does not have an ethernet card other than the wireless.  Although linux-image-2.6.8.1-3* shows up in Synaptic, ndiswrapper-utils doesn't appear to be on the CD.

Do you think it is a problem with the hardware not being recognized?  After all, this card shows up in System Configuration/Device Manager.  "ACX 111 54Mbps Wireless Interface".  Furthermore, it's listed as one of the supported cards at [http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php), which is where I was referred to ensure that this card would work under Linux.  Is there perhaps something that I need to install from that site to get it working?  I could burn it to CD and transfer it to the system in the other room.

Thanks in advance.
Kenneth

---

### Post by kepardue on 2004-11-16
Well, I've been trying to configure this on either my wife's system or my system all evening and I'm admittedly getting frustrated.  I followed the link above and installed these packages on my system (though I have no idea how I would install them on my wife's computer which has no internet at all).

I believe I've got the ndiswrapper-utils installed, and I did the instructions on installing the inf file.  I have no idea what version I was supposed to grab from the CD, Windows 2000, XP, 98, or ME, so I just grabbed XP.  Telling me to "edit the etc/network/interfaces" to my liking might as well be telling a road worker to build the space shuttle.  I have no idea what I'm looking at, what I should be doing, etc.  I did wind up getting an error that said, "Nobody Cares!" and disabled IRQ 22-something.

I also found this resource: [http://wiki.digital-scurf.org/PrismNotes](http://wiki.digital-scurf.org/PrismNotes) but can't get past the stage where I type "ifconfig ethX up".  Not a clue!

I'm beginning to think that I'm not cut out for Linux, at least for the time being.  I've been working with this for hours that I could be spending with my wife, and still haven't made any progress.  Sorry to rant, I'm just a bit on the frustrated side.

Does anyone know if support for this card would/could be included in the Hoary release?

Thanks,
Kenneth

---

### Post by kepardue on 2004-12-28
Bump.  Any other feedback on this?

Ken

---

### Post by fragmented_user on 2006-11-13
> **kepardue said:**
> Bump.  Any other feedback on this?

Ken

there is an alternative firmware included in the Linux driver. To activate it:

1. you need to add the following line to the file /etc/modprobe.d/options

```
options acx firmware_ver=1.2.1.34
```

2. Then restart the driver:

```
$ sudo rmmod acx

$ sudo modprobe acx firmware_ver=1.2.1.34

```

3. Then it is just a simple matter of configuring the interface

4. Finally, start the interface:
```

$ sudo ifup wlan0
```

If that does not work do the following:

1. add the following line to the file /etc/modprobe.d/options

```
options acx firmware_ver=1.2.0.30
```

2. Then restart the driver:

```
$ sudo rmmod acx

$ sudo modprobe acx firmware_ver=1.2.0.30

```

Complete Steps 3 and 4


[http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)

---

### Post by Sorcererbob on 2007-11-12
The one thing stopping me installing ubuntu on my gfs machine is the lack of support for her wireless card. It detects the wireless card, and when I click on the networking icon in the top right it even detects the network... tries to connect, has small heart attacks and eventually the networking gui bit dies and we're back to square one. Except that occasionally it will be impossible to pull up the network configuration screens after that (just the border loads, and eventually crashes.)

I'll be trying this method rather soon (with a live CD) to see if it works.

Thanks fragmented_user!

---

