---
title: "ktorrent+browsing = slow speed"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by porcellinux on 2007-10-04
Hi everyone!
I have a problem with ktorrent. It downloads at a max speed of 13kb/s. besides, when it's on going it slows/bloks the web browsing

How can I boost the download speed? (I already set right the router ports, and switched to opendsn)

How can my browser be fast while ktorrent is running? (I already tried to limit upload speed)

I also tried to pass to azureus, but risults are equal!!!!

This is really a problem 4 me!

Thank you!

---

### Post by wieman01 on 2007-10-04
First of all you need to open these ports to get maximum performance:

> Prior to version 3.2, BitTorrent by default uses ports in the range of 6881-6889. As of 3.2 and later, the range has been extended to 6881-6999. (These are all TCP ports, BitTorrent does not use UDP.) The client starts with the lowest port in the range and sequentially tries higher ports until it can find one to which it can bind. This means that the first client you open will bind to 6881, the next to 6882, etc. Therefore, you only really need to open as many ports as simultaneous BitTorrent clients you would ever have open. For most people it's sufficient to open 6881-6889.

The port range that BitTorrent uses is configurable, see the section on command line parameters, specifically the --minport and --maxport parameters.

The trackers to which BitTorrent must connect usually are on port 6969, so the client must have outbound access on this port. Some trackers are on other ports, however.

BitTorrent will usually work fine in a NAT (network address translation) environment, since it can function with only outbound connections. Such environments generally include all situations where multiple computers share one publicly-visible IP address, most commonly: computers on a home network sharing a cable or xDSL connection. If you are unsure of whether you have NAT or not, then try this link which will try to determine if you are behind a NAT gateway.

However, you will get better speeds if you can accept incoming connections as well. To do this you must use the "port forwarding" feature of whatever is performing the NAT/gateway task. For example, if you have a cable or DSL connection and a router/switch/gateway/firewall, you will need to go into the configuration of this device and forward ports 6881-6889 to the local machine that will be using BitTorrent. If your device makes it hard to enter a range of ports (if you must enter each one separately), then you can just do the first 10 or so ports, or however many simultaneous clients you plan to ever have open. If more than one person behind such a gateway wishes to use BitTorrent, then each machine should use a different port range, and the gateway should be configured to forward each port range to the corresponding local machine.
Source here: [http://www.dessent.net/btfaq/#ports]("http://www.dessent.net/btfaq/#ports")

Second you need QoS = "Quality of service" enabled on the router. That depends again on what brand you own. You need to give browsing (http) a higher priority than torrent download (BitTorrent). 

I use the DD-WRT firmware for my router and you can enable QoS easily there:

[http://www.dd-wrt.com/dd-wrtv2/index.php]("http://www.dd-wrt.com/dd-wrtv2/index.php")

---

### Post by porcellinux on 2007-10-04
well...I hate my router firmware...

I have a speedcom art25gsu...from the present firmware I cannot find a QoS config

Do you think I can upgrade it to the one you told me?

---

### Post by wieman01 on 2007-10-04
> **porcellinux said:**
> well...I hate my router firmware...

I have a speedcom art25gsu...from the present firmware I cannot find a QoS config

Do you think I can upgrade it to the one you told me?
Check their website. I don't know if your model is support or not. If it is, you will love DD-WRT.

---

