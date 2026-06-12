---
title: "[SOLVED] Avahi/NetworkManager keeps dropping my DHCP address"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by aaamr on 2008-11-21
Hi all - 

Having a hard time getting wireless going on my Ubuntu 8.04.1 (Dell Mini) distribution.

Intially, I thought it was due to the WPA or WEP security (tried them both), but the problem also manifests when using an unsecured wireless network.

Below are relevant excerpts from the syslog... as you can see, I successfully get an IP address from DHCP, and then it is immediately dropped and released.  Interfaces is the default:

# cat /etc/network/interfaces
auto 
iface lo inet loopback


Any ideas would be much appreciated!

Thanks,

-Adam

----------------------------------------

Nov 21 10:07:43 aronthal dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov 21 10:07:45 aronthal dhclient: DHCPOFFER of 192.168.7.109 from 192.168.7.1
Nov 21 10:07:45 aronthal dhclient: DHCPREQUEST of 192.168.7.109 on eth1 to 255.255.255.255 port 67
Nov 21 10:07:45 aronthal dhclient: DHCPACK of 192.168.7.109 from 192.168.7.1
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.7.109.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: New relevant interface eth1.IPv4 for mDNS.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Registering new address record for 192.168.7.109 on eth1.IPv4.
Nov 21 10:07:45 aronthal dhclient: bound to 192.168.7.109 -- renewal in 40228 seconds.
Nov 21 10:07:45 aronthal NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Nov 21 10:07:45 aronthal NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 21 10:07:45 aronthal NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov 21 10:07:45 aronthal dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Nov 21 10:07:45 aronthal dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Nov 21 10:07:45 aronthal dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Nov 21 10:07:45 aronthal NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov 21 10:07:45 aronthal NetworkManager: <info>    address 192.168.7.109 
Nov 21 10:07:45 aronthal NetworkManager: <info>    netmask 255.255.255.0 
Nov 21 10:07:45 aronthal NetworkManager: <info>    broadcast 192.168.7.255 
Nov 21 10:07:45 aronthal NetworkManager: <info>    gateway 192.168.7.1 
Nov 21 10:07:45 aronthal NetworkManager: <info>    nameserver 192.168.7.1 
Nov 21 10:07:45 aronthal NetworkManager: <info>    domain name 'lan' 
Nov 21 10:07:45 aronthal dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Nov 21 10:07:45 aronthal NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 21 10:07:45 aronthal NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov 21 10:07:45 aronthal NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Withdrawing address record for 192.168.7.109 on eth1.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.7.109.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Withdrawing address record for fe80::223:8ff:fe18:ef11 on eth1.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.7.109.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: New relevant interface eth1.IPv4 for mDNS.
Nov 21 10:07:45 aronthal avahi-daemon[8049]: Registering new address record for 192.168.7.109 on eth1.IPv4.
Nov 21 10:07:46 aronthal NetworkManager: <info>  Clearing nscd hosts cache. 
Nov 21 10:07:46 aronthal NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process.
 (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 21 10:07:46 aronthal NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Nov 21 10:07:46 aronthal NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 21 10:07:46 aronthal NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov 21 10:07:46 aronthal NetworkManager: <info>  SWITCH: terminating current connection 'eth1' because it's no longer valid. 
Nov 21 10:07:46 aronthal NetworkManager: <info>  Deactivating device eth1. 
Nov 21 10:07:46 aronthal dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 14100
Nov 21 10:07:46 aronthal dhclient: killed old client process, removed PID file
Nov 21 10:07:46 aronthal ntpd[13507]: ntpd exiting on signal 15
Nov 21 10:07:46 aronthal dhclient: DHCPRELEASE on eth1 to 192.168.7.1 port 67
Nov 21 10:07:46 aronthal avahi-daemon[8049]: Withdrawing address record for 192.168.7.109 on eth1.
Nov 21 10:07:46 aronthal avahi-daemon[8049]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.7.109.
Nov 21 10:07:46 aronthal avahi-daemon[8049]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov 21 10:07:47 aronthal NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid a
rgument 
Nov 21 10:07:47 aronthal NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Nov 21 10:07:47 aronthal NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed

---

### Post by aaamr on 2008-11-21
Ok... I appear to have solved the first issue by removing the wireless network from NetworkManager and rebooting, and then reconfiguring.

Now I am back to the initial problem which is that when I use WPA security on my access point, I can not seem to connect to certain sites.

Ping times are fine with no packet loss:
root@aronthal:~# ping dell-mini.archive.canonical.com
PING dell-mini.archive.canonical.com (91.189.90.29) 56(84) bytes of data.
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=1 ttl=53 time=139 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=2 ttl=53 time=137 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=3 ttl=53 time=138 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=4 ttl=53 time=137 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=5 ttl=53 time=138 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=6 ttl=53 time=138 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=7 ttl=53 time=138 ms
64 bytes from byrd.canonical.com (91.189.90.29): icmp_seq=8 ttl=53 time=137 ms

--- dell-mini.archive.canonical.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6997ms
rtt min/avg/max/mdev = 137.257/138.190/139.250/0.767 ms


But, a simple wget to the site fails:

root@aronthal:~# wget [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini)
--11:00:46--  [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini)
           => `hardy-dell-mini'
Resolving dell-mini.archive.canonical.com... 91.189.90.29
Connecting to dell-mini.archive.canonical.com|91.189.90.29|:80... 


This works find when using an unsecured network.

Any ideas on this one?

Thanks!

-Adam

---

### Post by aaamr on 2008-11-21
Well, I solved my issue.  For some reason, it wasn't liking TKIP as an encryption method on the Linksys wireless access point.  When I changed it to AES, everything started working.

-Adam

---

### Post by Iowan on 2008-11-21
Glad you got it working!!! Three posts, 48 views, and no replies could be a bit discouraging.  Hopefully, if you have other problems, the response will be better.  *Ordinarily*, _someone_ will offer some advice.

---

