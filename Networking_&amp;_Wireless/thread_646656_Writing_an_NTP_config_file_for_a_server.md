---
title: "Writing an NTP config file for a server"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by bluedalmatian on 2007-12-21
I've got a small self contained network for testing VoIP.

Every machine has a static IP in the range 192.168.254.x

I've assigned the machine with address 192.168.254.200 to be the NTP server. NTPD is installed and starts fine, but if I ask another machine to sync with it using ntpdate I get the following error:

no servers suitable for synchronisation.

This happens on both the other Linux servers I've setup and on my Mac if I plug it into the network and give it a suitable static IP so the problem appears to be in the config of the NTP server rather than the clients.

I've also got some CIsco IP phones which use Simple NTP rather than full NTP (no idea what the difference is?) and they will pick the time up off the server no problem.


NTP configuration seems to be very poorly documented there are no books and the websites dont seem to explain it well.

The ntp.conf file on the server contains the following (bearing in mind I just want any machine on the network to be able to get the time)

restrict 192.168.254.0 mask 255.255.255.0 nomodify notrap

As I understand it that will allow any machine with an IP in the range 192.168.254.x to get the time off the server for itself but not to modify the time on the server.

At one time I also had in there

driftfile /path/to/driftfile
broadcastdealy 0.008

If anyone reading this understands NTP configuration files couid you please try to explain them for the benefit of all Linux users everywhere ](*,)

Thanks v much.

---

