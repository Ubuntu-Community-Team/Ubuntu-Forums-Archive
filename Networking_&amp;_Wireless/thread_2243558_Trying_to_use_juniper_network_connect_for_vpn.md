---
title: "Trying to use juniper network connect for vpn"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by nikhil6 on 2014-09-09
Hi guys,

I'm trying to use network connect to set up a vpn connection to my university. THey tech support there say they do not support linux. Im trying to use the command line ncsvc tool to set up the vpn. So far, what I have done is download the "ncLinuxapp.jar" from the vpn server. Unzipped it to ~/.juniper_networks/network_connect. I downloaded the libraries "libc6-i386 lib32z1 lib32nss-mdns", used "getx509certificate.sh" to get the certificate. I then do ```
./ncsvc -h sslvpn.uc.edu -u username -f sslvpn.uc.edu.der
``` The output is ```
nikhil@deep-blue:~/.juniper_networks/network_connect$ ./ncsvc -h sslvpn.uc.edu -u gohilnn -f sslvpn.uc.edu.der
Password: 
Connecting to sslvpn.uc.edu : 443
nikhil@deep-blue:~/.juniper_networks/network_connect$ 

```

Still, It doesnt seem to be connected to my university, as I cant access on campus only features. "route -n" gives me ```
nikhil@deep-blue:~/.juniper_networks/network_connect$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.200.1   0.0.0.0         UG    0      0        0 wlan0
192.168.200.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0


```

Am I doing something wrong? Thanks for the help!

---

