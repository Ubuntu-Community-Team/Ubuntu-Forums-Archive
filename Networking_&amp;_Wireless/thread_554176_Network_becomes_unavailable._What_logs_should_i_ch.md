---
title: "Network becomes unavailable. What logs should i check?"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by jalla2000 on 2007-09-18
OS: Ubuntu 7.04 desktop edition
Mainboard: MSI K9N SLI mainboard
LAN: Dual LAN 10/100/1000 Fast Ethernet by Vitesse VSC8601
Chipset: NVIDIA® nForce 570 SLI MCP Chipset

I used eth0 and in the middle of a big transfer, the interface suddenly died... Then i plugged my cable into eth1 and it worked fine for a while and then it died in the middle of a big file transfer too. Now it has no contact with anything and does not receive an IP from the DHCP.

I typed lsmod and found that my system was running the forcedeth driver. I tried to rmmod and modprobe it but it's still the same.

When I tried ```
sudo /etc/init.d/networking restart
```, I got a message saying that there is already a pid file /var/run/dhclient.ath.pid with pid 3298319 (not unusual this?) and then it says 

```
 SIOCSIFADDR: No such device 
```
and
```
 ath0: ERROR while getting interface flags: No such device 
Failed to bring up ath0
```

When I reboot, the interface are back up again for a while. Is this a bug in the foredeth driver? I am pretty noob and I dont know what this ath0 is...

---

### Post by noob12 on 2007-09-19
This just means you have some interfaces specfied in **/etc/network/interfaces** that you don't actually have on your system.  

By running **ifconfig -a** you can determine what interfaces you do have.

Remove the sections in **/etc/network/interfaces**  that are configuring interfaces that you don't actually have.  Those messages will go away.

Your problem with the network becoming unavailable needs some separate diagnosis.  Can you describe what happens when it becomes unavailable?  the next time it becomes unavailable, see if you can ping your router's ip address.

---

