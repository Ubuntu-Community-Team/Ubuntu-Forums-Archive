---
title: "How do I load Winmodem at startup?"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by jimw1956 on 2005-08-24
Hi, I'm a newbie to linux.  I am one of the fortunate few that have been able to download drivers for my Lucent modem, and get it to work with ubuntu.

I go to the terminal, dpkg the driver file, it installs sets up an /dev alias and all is fine...until I shut down and reboot...then I have to go back to square 1, dpkg the file again...etc.

My question is, how do I get the drivers to load at startup?

I also have a similar problem with my system at my office, also ubuntu.

We have had some problems lately with our primary dns server.  I can get around the problems by going to the network settings and changing the DNS address to the secondary server....works fine...once again, until I reboot and then it reverts to the primary server, which is offline.

How can I make these settings / drivers permanent?

Thanks,
Jim W.

---

### Post by s_p_a_r_k_y on 2005-08-24
if you know the name of the driver, stick that into /etc/modules and it should load that driver upon boot. As for the DNS server, i'm pretty sure it will get that from the DHCP server everytime it boots unless you have a static network, in that case /etc/resolv.conf is where to look

---

