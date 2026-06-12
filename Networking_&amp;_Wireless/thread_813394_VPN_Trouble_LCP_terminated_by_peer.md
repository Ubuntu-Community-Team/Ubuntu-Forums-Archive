---
title: "VPN Trouble: LCP terminated by peer"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by giesen2 on 2008-05-30
I'm trying to connect to my VPN (Windows, I believe). I can connect without issue when I boot into Windows. Here are the log messages:

May 30 18:40:04 heron-sys pppd[5993]: pppd 2.4.4 started by root, uid 0
May 30 18:40:04 heron-sys pppd[5993]: Using interface ppp0
May 30 18:40:04 heron-sys pppd[5993]: Connect: ppp0 <--> /dev/pts/1
May 30 18:40:05 heron-sys pppd[5993]: nm-pppd-plugin: CHAP check hook.
May 30 18:40:05 heron-sys pppd[5993]: LCP terminated by peer (xH^HM-V^@<M-Mt^@^@^BM-3)
May 30 18:40:08 heron-sys pppd[5993]: Connection terminated.
May 30 18:40:08 heron-sys pppd[5993]: Modem hangup
May 30 18:40:08 heron-sys pppd[5993]: Exit.

Any ideas?

I'm running Ubuntu 8.04 x86 32-bit.

---

### Post by bilbometal on 2008-06-01
I have the same trouble, but I'm on ubuntu 7.10.

Jun  1 09:58:51 andre-desktop pppd[7508]: Plugin rp-pppoe.so loaded.
Jun  1 09:58:51 andre-desktop pppd[7510]: pppd 2.4.4 started by root, uid 0
Jun  1 09:58:51 andre-desktop pppd[7510]: PPP session is 42
Jun  1 09:58:51 andre-desktop pppd[7510]: Using interface ppp0
Jun  1 09:58:51 andre-desktop pppd[7510]: Connect: ppp0 <--> wlan0
Jun  1 09:59:21 andre-desktop pppd[7510]: LCP terminated by peer (Authentication failed)
Jun  1 09:59:24 andre-desktop pppd[7510]: Connection terminated.
Jun  1 09:59:24 andre-desktop pppd[7510]: Modem hangup

The secrets file are with the user and pass. The user and pass are correct.

My ISP is wireless and requires an authentication by a VPN. I'm already connected in a essid but the VPN doesn't works.

---

### Post by _zax_ on 2008-06-01
I guess that your network manager does not have the vpn option, so type:

sudo apt-get network-manager-pptp

---

### Post by bilbometal on 2008-06-01
Thanks for your reply.
But how do I do the download if a haven't internet connection?
I'll try to download the packet through windows (hope don't have depedencies) and see what happens.

---

### Post by bilbometal on 2008-06-01
I've installed the network-manager-packet. It required the ubuntu CD.
But nothing changed.
Here's the results of dmesg:
[  996.200880] wlan0: Initial auth_alg=0
[  996.200884] wlan0: authenticate with AP 00:02:6f:48:3f:f1
[  996.210674] wlan0: RX authentication from 00:02:6f:48:3f:f1 (alg=0 transaction=2 status=0)
[  996.210677] wlan0: authenticated
[  996.210679] wlan0: associate with AP 00:02:6f:48:3f:f1
[  996.219500] wlan0: RX AssocResp from 00:02:6f:48:3f:f1 (capab=0x1 status=0 aid=8)
[  996.219503] wlan0: associated
[  996.221800] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1006.211602] wlan0: no IPv6 routers present

It seems to all be ok except the last line where it says that the ISP doesnt have IPv6 routers. Am I right?
If so, how do I disable the IPv6 remaining only the IPv4 packets?

---

### Post by bilbometal on 2008-06-01
Ok, I disabled the IPv6 doing:

1. sudo gedit /etc/modprobe.d/aliases
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

This eliminated the problem in dmesg.
But I'm still with the same trouble:
Jun 1 09:58:51 andre-desktop pppd[7508]: Plugin rp-pppoe.so loaded.
Jun 1 09:58:51 andre-desktop pppd[7510]: pppd 2.4.4 started by root, uid 0
Jun 1 09:58:51 andre-desktop pppd[7510]: PPP session is 42
Jun 1 09:58:51 andre-desktop pppd[7510]: Using interface ppp0
Jun 1 09:58:51 andre-desktop pppd[7510]: Connect: ppp0 <--> wlan0
Jun 1 09:59:21 andre-desktop pppd[7510]: LCP terminated by peer (Authentication failed)
Jun 1 09:59:24 andre-desktop pppd[7510]: Connection terminated.
Jun 1 09:59:24 andre-desktop pppd[7510]: Modem hangup

What can I do?

---

### Post by cmsimike on 2008-11-16
bilometal, are you trying to connect to a Windows-based VPN? If so, try appending the domain name to your user name. That's what worked for me (got passed the authentication failing part, anyway).

Assume the domain name is XX and your username is example, while editing your vpn your username should be XX\example, leaving the NT Domain field blank.

---

### Post by cmsimike on 2008-11-16
sorry, double reply

---

