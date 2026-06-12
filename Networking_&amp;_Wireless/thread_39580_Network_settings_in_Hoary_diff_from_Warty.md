---
title: "Network settings in Hoary diff from Warty"
date: 2005-06-05
forum: Networking &amp; Wireless
---

### Post by grakhul on 2005-06-05
when I had Warty on my laptop I bought an AT&T6700G wireless Network card, popped it into my laptop, went into **Networking(Network Settings)** and was able to ADD my network card.  It worked flawlessly.

Now I have installed Hoary and **Networking(Network Settings)** does not have the option to ADD network configurations or cards.  What gives?  I can't connect wirelessly because their isn't a little icon in my network config that will allow me to add networking devices.  I have to be hardwired to my router, which bites.

---

### Post by spd106 on 2005-06-06
Hi, this sounds strange. I'm sure that the hotplug system should identify that you have plugged a network card in and automatically set up an entry in the networking  gui.

Does **$lspci** show that it has been found?

Also **$ifconfig** should show any configured network connections.

You might want to look in /etc/network/interfaces as this is where the gui will put any of it's settings.

Good luck

---

### Post by grakhul on 2005-06-06
This is what **lspci** shows:

> 0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01) 

This is what **ifconfig** shows:
> eth0      Link encap:Ethernet  HWaddr 00:0F:1F:BB:1B:B1
          inet addr:192.168.10.2  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:febb:1bb1/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:270681 (264.3 KiB)  TX bytes:86560 (84.5 KiB)
          Interrupt:19 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1100 (1.0 KiB)  TX bytes:1100 (1.0 KiB) 

Below you will find the output of ifup eth1
>  sudo ifup eth1
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
Failed to bring up eth1. 

The ifconfig shows me that my ethernet connections (hardwired) has been found.  Though when I go into network config, I only see the two connections listed above by ifconfig. 

I do not have the option of adding my wireless card to the network settings.  I have tried editing the /etc/network/interfaces file by adding my wireless config with no luck.

---

### Post by spd106 on 2005-06-07
I can't help you with this as i don't have that card, but this thread seems to have relevent information
[http://www.ubuntuforums.org/showthread.php?t=38972](http://www.ubuntuforums.org/showthread.php?t=38972)

Hope this helps

---

### Post by grakhul on 2005-06-07
I tried this and received lots of error messages from "make".  All in all the instructions did not work for me as posted.

---

