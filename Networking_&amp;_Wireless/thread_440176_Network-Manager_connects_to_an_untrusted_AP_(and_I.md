---
title: "Network-Manager connects to an untrusted AP (and I would really like it to stop)"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by henrik_schmidt on 2007-05-11
Hi there,

This is my first post. Hopefully I'm in the correct category. Anyway, I've just installed Feisty Fawn on my laptop. The laptop has two network interfaces (eth0 - wired, eth1 - wireless). On bootup network-manager connects to a nearby AP and I'm given a lease on the remote DHCP-server. At some point, I might have accidently clicked on this network in nm-applet, making network-manager think that the network was trusted, but I'm not sure about that. If I pull out the wired LAN (or boot up without a wired connection), nm-applet tells me, that I'm not connected to any network. However, I can ping the remote network, browse the web etc., so it would seem nm-applet is lying.  I've tried removing all subdirectories in ~/.gconf/system/networking/wireless/networks and the offending dhcp.eth1.leases in/var/lib/dhcp3. That does not seem to have any effect. The remote router has the same IP (192.168.1.1) as the local router. I don't know if that adds to the confusion, but it really shouldn't. Below is the relevant part of my syslogd:

May 10 20:39:56 laptop ntpdate[5598]: the NTP socket is in use, exiting
May 10 20:39:58 laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
May 10 20:39:58 laptop NetworkManager: <information>^IUpdating VPN Connections... 
May 10 20:39:58 laptop NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
May 10 20:39:58 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 10 20:39:58 laptop NetworkManager: <information>^IWill activate connection 'eth1/NETGEAR'. 
May 10 20:39:58 laptop NetworkManager: <information>^IDevice eth1 activation scheduled... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) started... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
May 10 20:39:58 laptop NetworkManager: <information>^IActivation (eth1/wireless): access point 'NETGEAR' is unencrypted, no key needed. 
May 10 20:39:59 laptop avahi-autoipd(eth0)[5546]: Callout BIND, address 169.254.8.72 on interface eth0
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was 'OK' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was 'OK' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was '0' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 4e455447454152' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was 'OK' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was 'OK' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
May 10 20:39:59 laptop NetworkManager: <information>^ISUP: response was 'OK'

The solution I'm using right now is to switch off wireless altogether. If this isn't easily fixed, I'll put a rule in iptables banning the remote DHCP-server's MAC-address, once I get that up and running. This would solve my problem, I think, but if this is a wide-spread problem, it would seem to be fairly nasty security issue. Is there any way to tell NetworkManager, that this network is untrusted, or to even blacklist it? Any ideas?

---

### Post by rbhkamal on 2007-08-12
I'm suffering from the same problem, Network Manager keeps connecting to my neighbor's AP. I'm really concerned that he'll sue me or something, people have done that many times :(
Also his internet connection sucks

His router doesn't have the same network as mine; mine is 192.168.0.x and his is 192.168.1.x

Regards,
RK

---

