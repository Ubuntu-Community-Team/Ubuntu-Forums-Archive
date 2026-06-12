---
title: "Networking through a fast ethernet switch"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by DaveinSpain on 2008-04-30
This ought to be simple.  At the risk of being lynched I will say from the outset that Windows XP/Vista managed it in 3 or 4 mouse clicks.  My setup is a DHCP telephony modem connected to my ISP via a microwave link (no wires or cables here in Rural Spain).  That connects via a patch lead to fast ethernet switch, 8 ports with 4 currently connected via wired LAN, 1 to each computer, 1 to a spare socket for visiting laptops and the fourth is the modem patch lead.  The internet is instantly accessible from any machine.

I have torn my hair out trying to get my linux installations to talk to each other.  I want to use Guadalinex 4.2, as produced by the Government of Andalucia and based on Edgy Eft, but the latest version has the Gutsy kernel.

I have tried Ubuntu 7.04, Mandriva 2008, Fedora Core 6 and CentOS as well, in matching pairs and all possible combinations but the boxes are most reticent to make a connection, direct, VPN, ssh, pptp, Samba or otherwise.  I have follwed several sets of "Expert" instructions with no success.  All assume that when you do X, y will happen and it just doesn't.  For example:

From [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN), I found this.

$ echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

Returns 1 as expected, then 

$ sudo ssh -w 0:0 1.2.3.4

Should set up the tunnels but times out after a couple of minutes.  $ ssh -V confirmed I have v4.03 of ssh installed

$ ifconfig

then returns only the physical (eth0) interface with the dhcp assigned public IP data and the loopback (lo) interface.  ie no tunnel has been created and the Ubuntu documentation page gives no hel on what to do when things don't work.

I have also tried installing pptp, which finds the loacl machines but not the remote ones.

I have been struggling with this for 3 months.  Any help most gratefully received.

If I hadn't managed to set things up so easily under Windows I would have assumed that it was just not possible.  The Government of Andalucia uses this distribution in schools, libraries, old people's homes and much of it's support infrastructure, so it should be well enough tested.

---

