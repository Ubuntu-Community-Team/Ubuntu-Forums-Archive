---
title: "Help wanted for wireless configuration on laptop"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by dumas on 2007-03-01
Hi,

I switched to ubuntu edgy and it was great. But I can't configure the wireless network.

My computer is a laptop, NEC Versa E6000. It uses Centrino and Atheros. As I understand, the drivers are working.

I am connected to the router, but don't have the ip. I tried the following, but doesn't work.

      sudo dhclient ath0:
          Internet Systems Consortium DHCP Client V3.0.4
          Copyright 2004-2006 Internet Systems Consortium.
          All rights reserved.
          For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

          wifi0: unknown hardware address type 801
          wifi0: unknown hardware address type 801
          Listening on LPF/ath0/00:90:96:b2:08:70
          Sending on   LPF/ath0/00:90:96:b2:08:70
          Sending on   Socket/fallback
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
          DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
          No DHCPOFFERS received.
          No working leases in persistent database - sleeping.

      sudo invoke-rc.d networking restart, then dhclient again

      sudo ifconfig <ath0> down
      sudo ifconfig ip addr 192.168.x.x netmask 255.255.255.0 broadcast 192.168.x.255 up
          addr: Unknown host
          ifconfig: `--help' gives usage information.

Please help me, otherwise I might have to switch back to windows again:( 

Thanks in advance.

---

### Post by devoncatt on 2007-03-01
I Have almost the same problem. The card is not actually talking to the DHCP server on the router. First question any keys? WEP or WPA or wide open router?Have you used anything like network manager or wifi-radaror command line tools to see if you can see the router? There seems to be something in ubuntu that is not seamless in wireless unlike the easy configuration in wired ethernet
Devoncatt

---

### Post by Kobalt on 2007-03-01
What is the output of *iwconfig* please ...

---

### Post by dumas on 2007-03-01
i am not with my computer at the moment, so i can't remember the output for iwconfig.

There is a key for the network, I guess it's WEP. I can see the router, in fact I am already associated with it.

The problem is I can't get an IP address.

Any help would be appreciated.

---

