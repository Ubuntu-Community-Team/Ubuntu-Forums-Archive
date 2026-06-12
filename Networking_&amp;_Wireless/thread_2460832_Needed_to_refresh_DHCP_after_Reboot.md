---
title: "Needed to refresh DHCP after Reboot"
date: 2021-04-20
forum: Networking &amp; Wireless
---

### Post by ockenheimer85 on 2021-04-20
Hi Folks,

every time I reboot my server with Ubuntu 20.04 LTS, the Connection to the network wont work.
I need to release the dhcp-lease by ```
sudo dhclient -r enp0s25 && sudo dhclient
``` to access the machine via ssh.

I don't know why the dhcp-congif is suddenly broken, but I need a quickl way to set the system back to an functional state. (I'm currently writing my bacherlor thesis, and am a bit in a hurry :( )

Thanks in Advance
Markus

---

### Post by ockenheimer85 on 2021-04-20
Nevermind, fixed the problem

Netplan.io wasn't installed. The server reboots with functional network now.
Found the solution on [https://askubuntu.com/questions/1281516/cannot-connect-to-lan-internet-in-ubuntu-20-04](https://askubuntu.com/questions/1281516/cannot-connect-to-lan-internet-in-ubuntu-20-04)

Thanks to the readers.

---

