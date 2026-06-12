---
title: "vpnc / network settings"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by nadjavox on 2008-05-20
I have vpnc installed with a custom configuration file. It works fine, and I can connect to the VPN with no trouble. After I disconnect from vpnc though, my network settings get hosed. 

I'm running Hardy Heron. I have a static IP address (setup through System | Administration | Network | Connections | Wired Connection). 

Unfortunately, my DNS server entries are erased from Network Settings after I disconnect from vpnc. 

Manually entering a DNS server gets me on the internet, but I am wondering if anyone knows how to prevent the DNS entries from being erased when I disconnect from the VPN?

It might be worth mentioning too, that I cannot run vpnc with my own user name. I have to sudo or vpnc will respond with an error:

vpnc: Error binding to source port. Try '--local-port 0'
Failed to bind to 0.0.0.0:500: Permission denied

Any help would be appreciated.

---

### Post by nadjavox on 2008-05-21
I tried editing /etc/dhcp3/dhclient.conf as recommended by this post:

[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

Still no luck. DNS was erased again after connecting to the VPN. Any ideas?

---

### Post by rapidwiz on 2008-05-21
Yep this happens to me too, I use a dirty work around, I am sure there is something better if you have time. I just have a script on my desktop which copies and original config back in place and hoses or the vpnc processes.

#!/bin/bash -x
sudo cp /etc/resolv.conf.orig /etc/resolv.conf
ps -ef  | grep vpnc | grep -v grep | awk {'print $2'} | while read a
do
echo "Kill Process ID:<$a>"
sudo kill -9 $a
done
echo "Press ENTER to continue"
#read junk

---

### Post by nadjavox on 2008-05-23
Oh, good idea!

---

