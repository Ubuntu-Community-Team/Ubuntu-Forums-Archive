---
title: "Network-manager-openvpn VPN failed to start"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2008-11-11
Intrepid Ibex 8.10 clean install (not upgrade) with openvpn; openvpn-blacklist; network-manager; network-manager-openvpn packages.

Manual openvpn startup from shell works fine (using it now to write this post).

Created an openvpn connection in netmanager. Set to Certificates (TLS) mode, specified keys and certs, added TLS auth key and LZO comp.

Attempting to start this configuration from netmanager returns "The VPN "..." failed because the VPN service failed to start."

Previously, under 8.04 LTS, netmanager / openVPN worked just fine, with the same certs and keys.

What's changed here, and how to make it work?

--DJ

---

### Post by stromdal on 2008-11-12
I too have the same problem.

```

**VPN Connection Failed**

The VPN connection 'VPN1' failed because the VPN service failed to start, 

Failed to start child process "/usr/bin/nm-ppp-starter" (no such file or directory)

```

My machine is a 8.10 (upgrade from 8.04) on an wired connection to the router.

---

### Post by stromdal on 2008-11-13
Bump!

---

### Post by defishguy on 2008-11-13
OpenVPN worked for me using Intrepid until yesterday and then began to exhibit the same symptom as above.  

A bug has been filed [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/jaunty/+source/network-manager/+bug/290468")

We'll have to wait I suppose.

---

### Post by lordfoul on 2008-11-14
I hope they get this figured out soon, kind of drag.  Using [kvpnc]("http://home.gna.org/kvpnc/en/index.html") works flawlessly.

---

### Post by stromdal on 2008-11-17
Is it possible for me to install and use kvpnc on my (g)Ubuntu Intrepid box instead of the default VPN client?

---

### Post by lordfoul on 2008-11-17
Yes of course, there won't be any conflict.  Kvpnc is in the Add/Remove ubuntu maintained repositories.

---

### Post by stromdal on 2008-11-18
Thanx, I'll try that instead!

---

### Post by kgeekworking on 2008-12-16
I too had the same problem.  Worked fine for a long time until the last network-manager update.

I solved by removing & reinstalling the network-manager-openvpn package

---

### Post by Kamilion on 2008-12-17
Ran into the same problem myself with a fresh install of network-manager-openvpn. Checked the logs in /var/log/daemon.log which told me that the 'tun0' interface was having a problem provisioning it's IP.

```

Dec 17 12:50:05 bloodline NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Dec 17 12:50:05 bloodline NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 5713 
Dec 17 12:50:06 bloodline NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Dec 17 12:50:06 bloodline NetworkManager: <info>  VPN plugin state changed: 1 
Dec 17 12:50:06 bloodline NetworkManager: <info>  VPN plugin state changed: 3 
Dec 17 12:50:06 bloodline NetworkManager: <info>  VPN connection 'Intrinsyx' (Connect) reply received. 
Dec 17 12:50:06 bloodline nm-openvpn[5722]: OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Dec 17 12:50:06 bloodline nm-openvpn[5722]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 17 12:50:06 bloodline nm-openvpn[5722]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 17 12:50:06 bloodline nm-openvpn[5722]: LZO compression initialized
Dec 17 12:50:06 bloodline nm-openvpn[5722]: UDPv4 link local: [undef]
Dec 17 12:50:06 bloodline nm-openvpn[5722]: UDPv4 link remote: 204.16.153.84:1194
Dec 17 12:50:06 bloodline nm-openvpn[5722]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Dec 17 12:50:07 bloodline nm-openvpn[5722]: WARNING: 'dev-type' is used inconsistently, local='dev-type tun', remote='dev-type tap'
Dec 17 12:50:07 bloodline nm-openvpn[5722]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1542', remote='link-mtu 1574'
Dec 17 12:50:07 bloodline nm-openvpn[5722]: WARNING: 'tun-mtu' is used inconsistently, local='tun-mtu 1500', remote='tun-mtu 1532'
Dec 17 12:50:07 bloodline nm-openvpn[5722]: [127.0.0.1] Peer Connection Initiated with 204.16.153.84:1194
Dec 17 12:50:08 bloodline nm-openvpn[5722]: WARNING: Since you are using --dev tun with a point-to-point topology, the second argument to --ifconfig must be an IP address.  You are using something (255.255.0.0) that looks more like a netmask. (silence this warning with --ifconfig-nowarn)
Dec 17 12:50:08 bloodline nm-openvpn[5722]: TUN/TAP device tun0 opened
Dec 17 12:50:08 bloodline nm-openvpn[5722]: /sbin/ifconfig tun0 10.10.10.120 pointopoint 255.255.0.0 mtu 1500
Dec 17 12:50:08 bloodline nm-openvpn[5722]: Linux ifconfig failed: external program exited with error status: 1
Dec 17 12:50:08 bloodline nm-openvpn[5722]: Exiting
Dec 17 12:50:08 bloodline NetworkManager: <info>  VPN plugin failed: 1 
Dec 17 12:50:08 bloodline NetworkManager: <info>  VPN plugin state changed: 6 
Dec 17 12:50:08 bloodline NetworkManager: <info>  VPN plugin state change reason: 0 
Dec 17 12:50:08 bloodline NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Dec 17 12:50:08 bloodline NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Dec 17 12:50:08 bloodline NetworkManager: <info>  Policy set 'Auto Intrinsyx2028-N' (wlan0) as default for routing and DNS. 
Dec 17 12:50:20 bloodline NetworkManager: <debug> [1229547020.378783] ensure_killed(): waiting for vpn service pid 5713 to exit 
Dec 17 12:50:20 bloodline NetworkManager: <debug> [1229547020.379088] ensure_killed(): vpn service pid 5713 cleaned up 

```

Switching on the 'tap' option instead of 'tun' made OpenVPN work.

```

Dec 17 12:53:07 bloodline avahi-daemon[4632]: Registering new address record for 2002:4b3d:6283:0:202:72ff:fe74:28d3 on wlan0.*.
Dec 17 12:53:07 bloodline avahi-daemon[4632]: Withdrawing address record for fe80::202:72ff:fe74:28d3 on wlan0.
Dec 17 12:53:22 bloodline NetworkManager: <info>  Stanetwork manager log ubunturting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Dec 17 12:53:22 bloodline NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 5834 
Dec 17 12:53:22 bloodline NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Dec 17 12:53:22 bloodline NetworkManager: <info>  VPN plugin state changed: 1 
Dec 17 12:53:22 bloodline NetworkManager: <info>  VPN plugin state changed: 3 
Dec 17 12:53:22 bloodline NetworkManager: <info>  VPN connection 'Intrinsyx' (Connect) reply received. 
Dec 17 12:53:22 bloodline nm-openvpn[5839]: OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Dec 17 12:53:22 bloodline nm-openvpn[5839]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 17 12:53:22 bloodline nm-openvpn[5839]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 17 12:53:22 bloodline nm-openvpn[5839]: LZO compression initialized
Dec 17 12:53:22 bloodline nm-openvpn[5839]: UDPv4 link local: [undef]
Dec 17 12:53:22 bloodline nm-openvpn[5839]: UDPv4 link remote: 204.16.153.84:1194
Dec 17 12:53:22 bloodline nm-openvpn[5839]: WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Dec 17 12:53:23 bloodline nm-openvpn[5839]: [127.0.0.1] Peer Connection Initiated with 204.16.153.84:1194
Dec 17 12:53:24 bloodline nm-openvpn[5839]: TUN/TAP device tap0 opened
Dec 17 12:53:24 bloodline nm-openvpn[5839]: /sbin/ifconfig tap0 10.10.10.120 netmask 255.255.0.0 mtu 1500 broadcast 10.10.255.255
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Joining mDNS multicast group on interface tap0.IPv4 with address 10.10.10.120.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: New relevant interface tap0.IPv4 for mDNS.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Registering new address record for 10.10.10.120 on tap0.IPv4.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Withdrawing address record for 10.10.10.120 on tap0.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Leaving mDNS multicast group on interface tap0.IPv4 with address 10.10.10.120.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Interface tap0.IPv4 no longer relevant for mDNS.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Joining mDNS multicast group on interface tap0.IPv4 with address 10.10.10.120.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: New relevant interface tap0.IPv4 for mDNS.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Registering new address record for 10.10.10.120 on tap0.IPv4.
Dec 17 12:53:24 bloodline nm-openvpn[5839]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tap0 1500 1574 10.10.10.120 255.255.0.0 init
Dec 17 12:53:24 bloodline NetworkManager: <info>  VPN connection 'Intrinsyx' (IP Config Get) reply received. 
Dec 17 12:53:24 bloodline NetworkManager: <info>  VPNnetwork manager log ubuntu Gateway: 204.16.153.84 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Tunnel Device: tap0 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Internal IP4 Address: 10.10.10.120 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Internal IP4 Prefix: 24 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Internal IP4 Point-to-Point Address: 0.0.0.0 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Maximum Segment Size (MSS): 0 
Dec 17 12:53:24 bloodline NetworkManager: <info>  DNS Domain: '(none)' 
Dec 17 12:53:24 bloodline NetworkManager: <info>  Login Banner: 
Dec 17 12:53:24 bloodline NetworkManager: <info>  ----------------------------------------- 
Dec 17 12:53:24 bloodline NetworkManager: <info>  (null) 
Dec 17 12:53:24 bloodline NetworkManager: <info>  ----------------------------------------- 
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Withdrawing address record for 10.10.10.120 on tap0.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Leaving mDNS multicast group on interface tap0.IPv4 with address 10.10.10.120.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Interface tap0.IPv4 no longer relevant for mDNS.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Joining mDNS multicast group on interface tap0.IPv4 with address 10.10.10.120.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: New relevant interface tap0.IPv4 for mDNS.
Dec 17 12:53:24 bloodline avahi-daemon[4632]: Registering new address record for 10.10.10.120 on tap0.IPv4.
Dec 17 12:53:24 bloodline nm-openvpn[5839]: Initialization Sequence Completed
Dec 17 12:53:25 bloodline NetworkManager: <info>  (tap0): writing resolv.conf to /sbin/resolvconf 
Dec 17 12:53:25 bloodline NetworkManager: <info>  VPN connection 'Intrinsyx' (IP Config Get) complete. 
Dec 17 12:53:25 bloodline NetworkManager: <info>  (tap0): writing resolv.conf to /sbin/resolvconf 
Dec 17 12:53:25 bloodline NetworkManager: <info>  Policy set 'Intrinsyx' (tap0) as default for routing and DNS. 
Dec 17 12:53:25 bloodline NetworkManager: <info>  VPN plugin state changed: 4 
Dec 17 12:53:25 bloodline nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Dec 17 12:53:26 bloodline avahi-daemon[4632]: Registering new address record for fe80::1c71:41ff:fef9:26ad on tap0.*.

```

The problem seems to lie in this log clipping:
```

WARNING: Since you are using --dev tun with a point-to-point topology, the second argument to --ifconfig must be an IP address.
You are using something (255.255.0.0) that looks more like a netmask. 
(silence this warning with --ifconfig-nowarn)
TUN/TAP device tun0 opened
/sbin/ifconfig tun0 10.10.10.120 pointopoint 255.255.0.0 mtu 1500
Linux ifconfig failed: external program exited with error status: 1

```

Apparently this should be '/sbin/ifconfig tun0 10.10.10.120 pointtopoint 10.10.10.254 netmask 255.255.0.0 mtu 1500' if I'm not mistaken.

Anyway, long post short, try editing the connection in Network Manager, click the advanced button on the VPN tab, and checkmark 'Use a TAP device'. The default is unchecked, and will use a TUN device by default.

---

### Post by levidos on 2008-12-20
network manager says that the vpn service failed to start when trying to connect to a pptp vpn server. i;m using intrepid x86. my sistem is up-to-date. i thought this bug was already solved. is there anything i can do?

---

### Post by Kamilion on 2008-12-21
> **levidos said:**
> network manager says that the vpn service failed to start when trying to connect to a pptp vpn server. i;m using intrepid x86. my sistem is up-to-date. i thought this bug was already solved. is there anything i can do?

network-manager-openvpn != network-manager-pptp.

---

### Post by TalynOne on 2008-12-26
The following method should work, and IMO works a lot better than using Network Manager:

[http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

---

### Post by dziamid on 2010-08-04
I just noticed that if i tick 'available to all users' in a vpn connection config that I get "vpn service failed to start". Untick it and you are fine. Hope that helps someone.

---

### Post by csimone on 2010-10-01
> **dziamid said:**
> I just noticed that if i tick 'available to all users' in a vpn connection config that I get "vpn service failed to start". Untick it and you are fine. Hope that helps someone.

unticking available to all, solved this issue for me too. testing out ipredator service.

---

### Post by equusaustralus on 2010-11-12
@dziamid Thanks, worked for me too on Maverick!

---

### Post by bchapman on 2010-12-01
> **dziamid said:**
> I just noticed that if i tick 'available to all users' in a vpn connection config that I get "vpn service failed to start". Untick it and you are fine. Hope that helps someone.

Excellent! Thanks for this - worked for me on 10.04.

---

### Post by mostaphaamini on 2011-06-23
Thanks, it worked.

---

### Post by warfie on 2013-02-15
> **Kamilion said:**
> network-manager-openvpn != network-manager-pptp.

sorry but, is that meant to be some kind of answer?

---

