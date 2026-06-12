---
title: "After upgrade  from 17.10 to 18.4 static IP addres not assigned to WIFI interface"
date: 2018-04-28
forum: Networking &amp; Wireless
---

### Post by bern1 on 2018-04-28
Hi, 
I have an issue with assigning static IP address to wifi network interface. 
Below netplan configuration file which works fine in the  previous Ubuntu version (17.10). 
```
network:
  version: 2
  renderer: networkd
  ethernets:
    wlp4s0:
      addresses:
       - 10.10.11.1/24
      dhcp4: no
```
But when I upgraded Ubuntu server to 18.4 my firewall (Shorewall) stop working with message:
```
Apr 28 20:40:07 akacja shorewall[1425]: Starting Shorewall....
Apr 28 20:40:07 akacja shorewall[1425]:    ERROR: Unable to determine the IP address(es) of wlp4s0:
Apr 28 20:40:07 akacja root[2800]: ERROR:Shorewall start failed:Firewall state not changed
Apr 28 20:40:07 akacja shorewall[1425]: Terminated
Apr 28 20:40:07 akacja systemd[1]: shorewall.service: Main process exited, code=exited, status=143/n
Apr 28 20:40:07 akacja systemd[1]: shorewall.service: Failed with result 'exit-code'.
Apr 28 20:40:07 akacja systemd[1]: Failed to start Shorewall IPv4 firewall.
```

How could I fix this?

See my network configuration details:
[http://paste.ubuntu.com/p/pYgDZ3MSgy/](http://paste.ubuntu.com/p/pYgDZ3MSgy/)

---

