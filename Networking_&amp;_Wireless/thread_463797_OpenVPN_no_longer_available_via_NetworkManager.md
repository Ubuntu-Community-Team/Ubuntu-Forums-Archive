---
title: "OpenVPN no longer available via NetworkManager"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by cyrilg on 2007-06-04
Hi,

Yesterday I succesfully installed OpenVPN so that it is accessible via the Gnome Network Manager. By using this command:

```
sudo apt-get install network-manager-openvpn
```

I used the VPN client successfully and even got some remote work done. I then proceeded to install a bunch of software (as my install is 3 days old).

When I restarted and came back to the computer today, I see that my NetworkManager only says "Manual Configuration" and the VPN submenus have dissapeared.

Any help would be greatly appreciated 	:idea:

Thanks!

Cyril

---

### Post by makan on 2007-11-08
i also have this issue on Gutsy...
i have installed network-manager-openvpn but there is no any menu to setup openvpn client...

:confused:

---

### Post by makan on 2007-11-08
i can run the network-manager-openvpn configuration from command line.

```
/usr/lib/network-manager/nm-vpn-properties --import-service org.freedesktop.NetworkManager.openvpn --import-file %f
```

but i don't know why it cannot running from "Applications -> Internet -> VPN Connection Manager"

and i don't know how to activate a profile from VPN Connection Manager

:confused:

---

### Post by sedeer on 2007-12-28
In order to get a menu to set up VPN connections, you also need to install network-manager-vpnc.  Once that's installed, quit and reload your network-manager and you should see a VPN menu there.

---

### Post by robmoore on 2008-04-27
I've followed sedeer's instructions but am still seeing the same issue. Anything else I can try?

---

### Post by robmoore on 2008-05-11
OK, finally figured this one out. On the [Ubuntu VPN]("https://help.ubuntu.com/community/VPNClient") page I found the solution. I had to edit the /etc/network/interfaces file down to the minimum per the instructions found on the VPN page. The relevant section:

> NetworkManager only allows VPN connections if it is currently managing a connection. If your network interface is manually configured (in the Network Administration Tool under System/Administration) or in /etc/network/interfaces), it is not managed by NetworkManager. If the option for VPN connections is greyed out, NetworkManager is not managing a connection. Remove the connections from the Network Administration Tool, or manually edit /etc/network/interfaces. For a general case, it is safe to backup the interfaces file, and reduce its to only contain

auto lo
iface lo inet loopback

---

### Post by Explodinglemur on 2008-05-27
> **robmoore said:**
> OK, finally figured this one out. On the [Ubuntu VPN]("https://help.ubuntu.com/community/VPNClient") page I found the solution. I had to edit the /etc/network/interfaces file down to the minimum per the instructions found on the VPN page. The relevant section:

Unfortunately this doesn't work for people (like me) that have their machines configured with a manually-set static IP address.  Does anyone know a way to set an IP address manually (no DHCP or autoconf in our environment) but still allow VPN connections to be managed through network-manager?

---

