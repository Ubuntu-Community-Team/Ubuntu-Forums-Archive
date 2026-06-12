---
title: "Ethernet Disconnects Randomly"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by falt004 on 2007-05-24
Hi,

I have two machines both running Kubuntu 7.04 on the same network (consisting of a bunch of other machines running Windows, Mac OS and other Linux Distros). Both machines are identical, with the network card being a Broadcom BCM5751 (tg3).

Anyway, every three to four days, these two machines get disconnected from the network at exactly the same time - and only these two while the other machines are still working fine. Doing an ifconfig down and up solves the problem, but it is kind of a hassle - especially since I often need to access them during the weekends from home - and it's kind of a hassle to do that if the network goes down during the weekend since I'm not there to bring it back up.

As I mentioned, none of the other machines are affected - moreover, I was running Debian before on these machines and they weren't disconnecting.

I have disabled IP6, which turned out to be a problem before, but looking at the logs it's not the problem now.

Below is the contents of the log when they disconnect (both have pretty much identical log entries). Any help would be appreciated :)

Notes:
- I've replaced the IP address of the DNS server with <Secondary DNS server>
- I've replaced the hostname's ip address with <hostname's IP address>

Cheers,
/Fuad

---------------------
/var/log/syslog
---------------------

[FONT="Courier New"]May 24 11:12:36 hostname kernel: [662203.914395] tg3: eth0: Link is down.
May 24 11:12:36 hostname NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid.
May 24 11:12:36 hostname NetworkManager: <information>^IDeactivating device eth0.
May 24 11:12:36 hostname dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5204
May 24 11:12:36 hostname dhclient: killed old client process, removed PID file
May 24 11:12:36 hostname dhclient: DHCPRELEASE on eth0 to <Secondary DNS server> port 67
May 24 11:12:36 hostname avahi-daemon[4993]: Withdrawing address record for <hostname's IP address> on eth0.
May 24 11:12:36 hostname avahi-daemon[4993]: Leaving mDNS multicast group on interface eth0.IPv4 with address <hostname's IP address>.
May 24 11:12:36 hostname avahi-daemon[4993]: Interface eth0.IPv4 no longer relevant for mDNS.
May 24 11:12:36 hostname avahi-autoipd(eth0)[23084]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
May 24 11:12:36 hostname avahi-autoipd(eth0)[23084]: Successfully called chroot().
May 24 11:12:36 hostname avahi-autoipd(eth0)[23084]: Successfully dropped root privileges.
May 24 11:12:36 hostname avahi-autoipd(eth0)[23084]: fopen() failed: Permission denied
May 24 11:12:36 hostname avahi-autoipd(eth0)[23084]: Starting with address 169.254.7.249
May 24 11:12:37 hostname NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
May 24 11:12:37 hostname NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
May 24 11:12:40 hostname kernel: [662208.721335] tg3: eth0: Link is up at 100 Mbps, full duplex.
May 24 11:12:40 hostname kernel: [662208.721341] tg3: eth0: Flow control is off for TX and off for RX.
May 24 11:12:40 hostname NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
May 24 11:12:40 hostname NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
May 24 11:12:40 hostname NetworkManager: <information>^IWill activate connection 'eth0'.
May 24 11:12:40 hostname NetworkManager: <information>^IDevice eth0 activation scheduled...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) started...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
May 24 11:12:40 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 24 11:12:41 hostname avahi-autoipd(eth0)[23084]: Callout BIND, address 169.254.7.249 on interface eth0
May 24 11:12:41 hostname avahi-daemon[4993]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.249.
May 24 11:12:41 hostname avahi-daemon[4993]: New relevant interface eth0.IPv4 for mDNS.
May 24 11:12:41 hostname avahi-daemon[4993]: Registering new address record for 169.254.7.249 on eth0.IPv4.
May 24 11:12:42 hostname NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
May 24 11:12:42 hostname NetworkManager: <information>^ICouldn't send DHCP 'up' message because: name 'com.redhat.dhcp.OperationInProgress', message 'int
erface eth0 is being released. Please try again later.'.
May 24 11:12:42 hostname NetworkManager: <information>^IActivation (eth0) failure scheduled...
May 24 11:12:42 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 24 11:12:42 hostname NetworkManager: <information>^IActivation (eth0) failed.
May 24 11:12:42 hostname NetworkManager: <information>^IDeactivating device eth0.
May 24 11:12:44 hostname avahi-daemon[4993]: Withdrawing address record for 169.254.7.249 on eth0.
May 24 11:12:44 hostname avahi-daemon[4993]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.7.249.
May 24 11:12:44 hostname avahi-daemon[4993]: Interface eth0.IPv4 no longer relevant for mDNS.
May 24 11:12:44 hostname NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
May 24 11:12:44 hostname NetworkManager: <information>^IWill activate connection 'eth0'.
May 24 11:12:44 hostname NetworkManager: <information>^IDevice eth0 activation scheduled...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) started...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
May 24 11:12:44 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 24 11:12:45 hostname avahi-autoipd(eth0)[23084]: Successfully claimed IP address 169.254.7.249
May 24 11:12:45 hostname avahi-autoipd(eth0)[23084]: fopen() failed: Permission denied
May 24 11:12:45 hostname NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface eth0
May 24 11:12:45 hostname NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
May 24 11:12:46 hostname NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
May 24 11:12:46 hostname dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
May 24 11:12:46 hostname NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 24 11:12:46 hostname NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
May 24 11:12:46 hostname avahi-autoipd(eth0)[23084]: Got SIGTERM, quitting.
May 24 11:12:46 hostname avahi-autoipd(eth0)[23084]: Callout STOP, address 169.254.7.249 on interface eth0
May 24 11:12:46 hostname avahi-autoipd(eth0)[23085]: client: RTNETLINK answers: No such device
May 24 11:12:46 hostname avahi-autoipd(eth0)[23085]: Script execution failed with return value 2
May 24 11:12:47 hostname NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0
May 24 11:12:51 hostname dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
May 24 11:12:55 hostname dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
May 24 11:13:01 hostname dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 24 11:13:15 hostname dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 24 11:13:18 hostname kernel: [662246.397189] tg3: eth0: Link is down.
May 24 11:13:18 hostname NetworkManager: <information>^IOld device 'eth0' activating, won't change.
May 24 11:13:20 hostname kernel: [662248.026165] tg3: eth0: Link is up at 100 Mbps, full duplex.
May 24 11:13:20 hostname kernel: [662248.026171] tg3: eth0: Flow control is off for TX and off for RX.
May 24 11:13:20 hostname NetworkManager: <information>^IOld device 'eth0' activating, won't change.
May 24 11:13:22 hostname dhclient: No DHCPOFFERS received.
May 24 11:13:22 hostname avahi-autoipd(eth0)[23155]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
May 24 11:13:22 hostname avahi-autoipd(eth0)[23155]: Successfully called chroot().
May 24 11:13:22 hostname avahi-autoipd(eth0)[23155]: Successfully dropped root privileges.
May 24 11:13:22 hostname avahi-autoipd(eth0)[23155]: fopen() failed: Permission denied
May 24 11:13:22 hostname avahi-autoipd(eth0)[23155]: Starting with address 169.254.7.249
May 24 11:13:27 hostname avahi-autoipd(eth0)[23155]: Callout BIND, address 169.254.7.249 on interface eth0
May 24 11:13:27 hostname avahi-daemon[4993]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.249.
May 24 11:13:27 hostname avahi-daemon[4993]: New relevant interface eth0.IPv4 for mDNS.
May 24 11:13:27 hostname avahi-daemon[4993]: Registering new address record for 169.254.7.249 on eth0.IPv4.
May 24 11:13:31 hostname avahi-autoipd(eth0)[23155]: Successfully claimed IP address 169.254.7.249
May 24 11:13:31 hostname avahi-autoipd(eth0)[23155]: fopen() failed: Permission denied
May 24 11:13:31 hostname NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth0
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled...
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) started...
May 24 11:13:31 hostname NetworkManager: <information>^INo DHCP reply received.  Automatically obtaining IP via Zeroconf.
May 24 11:13:31 hostname NetworkManager: <information>^Iavahi-autoipd running on eth0, assuming IPv4LL address
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Timeout) complete.
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
May 24 11:13:31 hostname NetworkManager: <information>^Inot touching eth0 configuration, was configured externally
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Finish handler scheduled.
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
May 24 11:13:31 hostname NetworkManager: <information>^IActivation (eth0) successful, device activated.
May 24 11:13:31 hostname dhcdbd: Unrequested down ?:3
May 24 11:13:31 hostname NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface eth0
May 24 11:13:31 hostname modprobe: WARNING: Not loading blacklisted module ipv6
May 24 11:14:17 hostname last message repeated 4 times
May 24 11:14:23 hostname ntpdate[23185]: can't find host ntp.ubuntu.com
May 24 11:14:23 hostname ntpdate[23185]: no servers can be used, exiting
May 24 11:15:07 hostname modprobe: WARNING: Not loading blacklisted module ipv6
May 24 11:15:57 hostname last message repeated 2 times
May 24 11:15:57 hostname modprobe: WARNING: Not loading blacklisted module ipv6
May 24 11:17:01 hostname /USR/SBIN/CRON[23234]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)[/FONT]

---

### Post by falt004 on 2007-05-28
Any ideas? :)

---

### Post by falt004 on 2007-05-30
I figured out what the problem was (with help from the people at Auckland lug). Will post it here in case someone else encounters the same problem and finds this post by searching.

The problem turned out to be that Avahi, which I don't really need on this network, was somehow interfering with it causing it to disconnect. What I needed to do was disable Avahi, which can be done by editing /etc/default/avahi-daemon and changing ```
AVAHI_DAEMON_START=1
```  to ```
AVAHI_DAEMON_START=0
```

Cheers,
/Fuad

---

