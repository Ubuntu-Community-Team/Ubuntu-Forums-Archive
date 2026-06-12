---
title: "NetworkManager, OpenVPN, and DHCP"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by freelock on 2006-10-14
Hi,

I just got a new Thinkpad, and am revisiting my OpenVPN system. I'm trying to configure NetworkManager to control the VPN connection, and have gotten it working except for DNS. I'm getting this in /var/log/daemon.log:

Oct 14 10:38:57 shasta NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification! 


This is in a brand new Edgy (Beta) install, with the network-manager-gnome packages installed, along with the network-manager-openvpn deb from here:
[http://news.u32.net/articles/2006/10/04/building-network-manager-openvpn-from-revu](http://news.u32.net/articles/2006/10/04/building-network-manager-openvpn-from-revu)

... following the basic OpenVPN settings described here:
[http://www.niemueller.de/wiki/?OpenVPNwithNetworkManager](http://www.niemueller.de/wiki/?OpenVPNwithNetworkManager)

My OpenVPN server is trying to push a DNS server setting via DHCP, but Network Manager is responding with the above message. I found a reference in the Network Manager list, [http://mail.gnome.org/archives/networkmanager-list/2006-September/msg00110.html](http://mail.gnome.org/archives/networkmanager-list/2006-September/msg00110.html) but Edgy apparently uses a different DHCP client.

Any hints?

Thanks,
John Locke
Freelock Computing
[http://www.freelock.com](http://www.freelock.com)

---

