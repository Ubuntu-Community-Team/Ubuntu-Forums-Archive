---
title: "Reestablishing a connection with openvpn"
date: 2017-03-26
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2017-03-26
I have been using openvpn for about 8 months on a laptop & 2 desktops without a problem, until a couple of days ago.
Packages installed
openvpn ver 2.3.10-1ubuntu2, network-manager-openvpn-gnome, network-manager-openvpn-gnome vers 1.1.93-ubuntu1.1 

Problem is like this: When I connect to a vpn server, Internet is available.  If I disconnect from that server, and reconnect there is no Internet access. I have to reboot before the service is available again
There is a notice that there is a connection with the vpn server. Connection information indicates that a tunnel is established tun0: ip Address 10.11.139.137, default route 10.11.139.137. vpn connection: 10.11.139.137 Primary DNS 8.8.8.8
Can anyone help):P

---

### Post by raybb on 2017-03-27
Hello,

I am currently experiencing the same issue. It was also happening on Linux mint over a pptp connection.
The only temporary fix I could find was to run the following command:
sudo service network-manager restart

After restarting the network manager you can connect again and internet will work. I hope that that someone can help find a more permanent fix.

Thanks,

Edit: I've also tried downgrading network-manager to 1.2.4 but that didn't seem to help.

Edit 2:
I think I've narrowed down the bug to be the network-manager-openvpn program. 
The bug seems to be having an impact on Version 1.2.6-2ubuntu1 and Version 1.1.93-1ubuntu1.1 (on Linux mint).
On Linux mint when I downgrade to a lower version and (and then restart the manger) I no longer have problems disconnecting and reconnecting.

There's a ticket open for the issue here. I'm not sure what at temporary fix might be for ubuntu since I don't see a way to downgrade (at least not on a fresh install of the latest iso).
[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1675199](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/1675199)

---

### Post by raybb on 2017-03-28
After doing more research it seems that the bub is probably in network-manager.
There's a ticket about it here [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1671606](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1671606)

If you downgrade it should fix the issue.
You can downgrade by running these commands.
```
sudo apt install network-manager=1.2.2-0ubuntu0.16.04.4
sudo service network-manager restart
```

Hope this helps!

---

### Post by uwe-bungto on 2017-03-28
After I posted my entire network went down. The cable modem locked up, I had an internal network; but couldn't even ping the modem. Got a replacement installed Saturday morning from the cable company. Really good service on their part.

I down graded network-manager as suggested, seems to work now. I tried to down grade network-manager-gnome also; but that didn't work to well. I kept getting a broken package warning.
I locked the whole network-manager group where it works and waiting for a fix.

Thanks everyone for the help

---

