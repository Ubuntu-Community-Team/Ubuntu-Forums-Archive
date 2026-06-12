---
title: "Configuring VPN on Ubuntu 13.10 with L2TP IPSec"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by theronmuller on 2013-12-14
I've followed the tutorials here: [http://bailey.st/blog/2011/07/14/connecting-to-a-l2tpipsec-vpn-from-ubuntu-desktop/](http://bailey.st/blog/2011/07/14/connecting-to-a-l2tpipsec-vpn-from-ubuntu-desktop/) and here: [http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page](http://wiki.l2tpipsecvpn.tuxfamily.org/wiki/index.php?title=Main_Page) with some reference to the how-to here: [https://strongvpn.com/setup_ubuntu_11.10_l2tp.shtml](https://strongvpn.com/setup_ubuntu_11.10_l2tp.shtml) to get a VPN connection to my university up and running. Unfortunately I'm up against a dead end. The output I'm getting when trying to connect is as follows:
```
12&#26376; 14 13:50:18.524 Stopping xl2tpd: xl2tpd.
12&#26376; 14 13:50:18.524 xl2tpd[20424]: death_handler: Fatal signal 15 received
12&#26376; 14 13:50:18.535 recvref[30]: Protocol not available
12&#26376; 14 13:50:18.535 xl2tpd[20573]: This binary does not support kernel L2TP.
12&#26376; 14 13:50:18.536 xl2tpd[20574]: xl2tpd version xl2tpd-1.3.1 started on ubuntu-hp-muller PID:20574
12&#26376; 14 13:50:18.536 xl2tpd[20574]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
12&#26376; 14 13:50:18.537 xl2tpd[20574]: Forked by Scott Balmos and David Stipp, (C) 2001
12&#26376; 14 13:50:18.537 xl2tpd[20574]: Inherited by Jeff McAdams, (C) 2002
12&#26376; 14 13:50:18.537 xl2tpd[20574]: Forked again by Xelerance (www.xelerance.com) (C) 2006
12&#26376; 14 13:50:18.538 xl2tpd[20574]: Listening on IP address 0.0.0.0, port 1701
12&#26376; 14 13:50:18.539 Starting xl2tpd: xl2tpd.
12&#26376; 14 13:50:19.540 xl2tpd[20574]: Connecting to host x.x.x.x, port 1701
12&#26376; 14 13:50:19.577 xl2tpd[20574]: Connection established to x.x.x.x, 1701.  Local: 22761, Remote: 26374 (ref=0/0).
12&#26376; 14 13:50:19.578 xl2tpd[20574]: Calling on tunnel 22761
12&#26376; 14 13:50:19.611 xl2tpd[20574]: Call established with x.x.x.x, Local: 30997, Remote: 15166, Serial: 1 (ref=0/0)
12&#26376; 14 13:50:19.619 xl2tpd[20574]: start_pppd: I'm running: 
12&#26376; 14 13:50:19.620 xl2tpd[20574]: "/usr/sbin/pppd" 
12&#26376; 14 13:50:19.620 xl2tpd[20574]: "passive" 
12&#26376; 14 13:50:19.621 xl2tpd[20574]: "nodetach" 
12&#26376; 14 13:50:19.621 xl2tpd[20574]: ":" 
12&#26376; 14 13:50:19.622 xl2tpd[20574]: "file" 
12&#26376; 14 13:50:19.622 xl2tpd[20574]: "/etc/ppp/U-of-T-VPN.options.xl2tpd" 
12&#26376; 14 13:50:19.622 xl2tpd[20574]: "ipparam" 
12&#26376; 14 13:50:19.623 xl2tpd[20574]: "x.x.x.x" 
12&#26376; 14 13:50:19.623 xl2tpd[20574]: "/dev/pts/1" 
12&#26376; 14 13:50:19.624 pppd[20575]: Plugin passprompt.so loaded.
12&#26376; 14 13:50:19.624 pppd[20575]: pppd 2.4.5 started by root, uid 0
12&#26376; 14 13:50:19.625 pppd[20575]: Using interface ppp0
12&#26376; 14 13:50:19.625 pppd[20575]: Connect: ppp0 <--> /dev/pts/1
12&#26376; 14 13:50:20.024 xl2tpd[20574]: handle_avps:  don't know how to handle atribute 46.
12&#26376; 14 13:50:20.025 xl2tpd[20574]: handle_avps:  don't know how to handle atribute 104.
12&#26376; 14 13:50:20.025 xl2tpd[20574]: control_finish: Connection closed to x.x.x.x, serial 1 (Locally generated disconnect)
12&#26376; 14 13:50:20.026 xl2tpd[20574]: Terminating pppd: sending TERM signal to pid 20575
12&#26376; 14 13:50:20.026 pppd[20575]: Modem hangup
12&#26376; 14 13:50:20.027 pppd[20575]: Connection terminated.
12&#26376; 14 13:50:20.050 pppd[20575]: Exit.
12&#26376; 14 13:50:35.027 xl2tpd[20574]: control_finish: Connection closed to x.x.x.x, port 1701 (No application/session timer expired), Local: 22761, Remote: 26374

```

What I'm not sure about is whether my problem is at the beginning:
```
12&#26376; 14 13:50:18.535 xl2tpd[20573]: This binary does not support kernel L2TP.
```

Or at the end:```

12&#26376; 14 13:50:20.024 xl2tpd[20574]: handle_avps:  don't know how to handle atribute 46.
12&#26376; 14 13:50:20.025 xl2tpd[20574]: handle_avps:  don't know how to handle atribute 104.
```

If the problem is with the attributes, where do I find out what the numbers mean so that I can make the necessary adjustments?

Any replies or help is most welcome. Getting a VPN to my university working with Ubuntu would be great.

Thanks in advance for your time and consideration.

---

### Post by csredrat on 2014-01-28
Use [https://launchpad.net/~seriy-pr/+archive/network-manager-l2tp](https://launchpad.net/~seriy-pr/+archive/network-manager-l2tp)


sudo apt-add-repository ppa:seriy-pr/network-manager-l2tp
sudo apt-get update
sudo apt-get install network-manager-l2tp-gnome


sudo service xl2tpd stop
sudo update-rc.d xl2tpd disable

---

### Post by theronmuller on 2014-01-28
Thanks for the tip. The softward installs fine, but I'm still getting the connection error. This time it's 'no shared secrets'. I'm not sure where the networking debug information is stored to get a closer look at the errors being generated. Any additional advice welcome.

---

