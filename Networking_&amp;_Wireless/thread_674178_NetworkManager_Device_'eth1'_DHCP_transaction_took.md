---
title: "NetworkManager: Device 'eth1' DHCP transaction took too long (&gt;99s), stopping it..."
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by motin on 2008-01-21
When trying to connect to my wireless network, I get this at first:

```
Jan  8 08:55:28 laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  8 08:55:28 laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'ebba'. 
Jan  8 08:55:28 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  8 08:55:28 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan  8 08:55:28 laptop kernel: [ 7145.183000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan  8 08:55:29 laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan  8 08:55:29 laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan  8 08:55:29 laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan  8 08:55:29 laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan  8 08:55:30 laptop avahi-daemon[5911]: Registering new address record for fe80::215:ff:fe24:684f on eth1.*.
Jan  8 08:55:30 laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jan  8 08:55:30 laptop dhclient: DHCPOFFER from 192.168.0.1
Jan  8 08:55:30 laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan  8 08:55:31 laptop dhclient: DHCPACK from 192.168.0.1
Jan  8 08:55:31 laptop avahi-daemon[5911]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.101.
Jan  8 08:55:31 laptop avahi-daemon[5911]: New relevant interface eth1.IPv4 for mDNS.
Jan  8 08:55:31 laptop avahi-daemon[5911]: Registering new address record for 192.168.0.101 on eth1.IPv4.
Jan  8 08:55:31 laptop dhclient: bound to 192.168.0.101 -- renewal in 275800 seconds.
Jan  8 08:55:39 laptop kernel: [ 7155.955000] eth1: no IPv6 routers present

```

HERE I AM CONNETED TO THE INTERNET and all is fine except that the nm-applit icon still only has one green ball lit as if it was still connecting. 

Then after about a minute or two - NetworkManager will disconnect from it all leaving this in syslog:

```
Jan  8 08:57:08 laptop NetworkManager: <info>  Device 'eth1' DHCP transaction took too long (>99s), stopping it. 
Jan  8 08:57:08 laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 11371
Jan  8 08:57:08 laptop dhclient: killed old client process, removed PID file
Jan  8 08:57:08 laptop dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Jan  8 08:57:08 laptop avahi-daemon[5911]: Withdrawing address record for 192.168.0.101 on eth1.
Jan  8 08:57:08 laptop avahi-daemon[5911]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.101.
Jan  8 08:57:08 laptop avahi-daemon[5911]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  8 08:57:09 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan  8 08:57:09 laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jan  8 08:57:09 laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jan  8 08:57:09 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jan  8 08:57:09 laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jan  8 08:57:09 laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan  8 08:57:10 laptop NetworkManager: <info>  Activation (eth1) failed for access point (ebba) 
Jan  8 08:57:10 laptop NetworkManager: <info>  Activation (eth1) failed. 
Jan  8 08:57:10 laptop NetworkManager: <info>  Deactivating device eth1. 
Jan  8 08:57:10 laptop avahi-daemon[5911]: Withdrawing address record for fe80::215:ff:fe24:684f on eth1.
Jan  8 08:57:19 laptop kernel: [ 7256.340000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

Looks like dhclient doesn't understand that a dhcp transaction has been carried out...

I tried removing lm-sensors (yes - whack! but [worked for another network manager error victim]("http://ubuntuforums.org/showthread.php?t=635779&page=3")) and stopping the dhcp server service as well as restarting NM, rebooting and more to no avail.

Any ideas? Rather annoying having to re-connect every 99 seconds or so - and irc etc is a no-no...

---

### Post by motin on 2008-04-25
Am I the only one having this problem?

The strange thing is, removing (--purge) network-manager and re-installing did not help, and not even now after an upgrade to Hardy does network-manager allow me to be connected for more than appr 99s!

Luckli Wicd exists, but it would be great not to have to resort to alternatives...

---

### Post by klauskiwi on 2008-06-03
I'm having the exact same problem. Funny thing is that I *think* this started happening after installing dhcp3-server.

Tried uninstalling it (purging config) to no avail. 

Actually, I'm having dhcp problems only with my wireless connection (Atheros), whereas wired eth0 works fine with NM.

---

### Post by motin on 2008-06-03
> **klauskiwi said:**
> I'm having the exact same problem. Funny thing is that I *think* this started happening after installing dhcp3-server.

Tried uninstalling it (purging config) to no avail. 

Actually, I'm having dhcp problems only with my wireless connection (Atheros), whereas wired eth0 works fine with NM.

Same for me, this weirdness showed up after I had been trying to get dhcp3-server (tried a couple of others as well) working to no avail. These are now purged leaving but a broken network manager behind...

Seems to be a confirmed issue then at least. Can we find any bug report at launchpad or upstreams about this issue? I found but this one: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251) but it is reported as a duplicate of a bug that seem not to be related to our issue at all.

---

### Post by motin on 2008-06-16
Do you by any chance have firestarter and dnsmasq installed and active? Does it work without those installed?

One thing I'd like to try, but haven't found the time for, is to compare all network related files in /etc with the corresponding ones on a working installation. Have you attempted this?

---

### Post by scoobymad555 on 2008-06-18
hey guys is this at all similar you think? .... my setup also uses dhcp3.

(i know it refs to knetworkmanager but it seems to be cross-platform)

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812)

---

### Post by motin on 2008-06-27
> **scoobymad555 said:**
> hey guys is this at all similar you think? .... my setup also uses dhcp3.

(i know it refs to knetworkmanager but it seems to be cross-platform)

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/139812)

Thanks, but it doesn't look related, as the connection is not established then withdrawn after around 99s.

---

### Post by motin on 2008-06-28
We finally have an official bug report for this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251)

Note once again, however, that the bug is not evident on a freshly installed system.

We ought to be able to inspect the differences in /etc between working and non-working systems to able to fix it without reinstalling Ubuntu...

Then, we will be able to make a qualified guess at whatever it is that messes up Network Managers configuration/ability to recognize dhcp leases.

---

### Post by motin on 2008-07-15
Very interesting blog post about this issue, which seems to be related to dhclient, dnsmasq and dbus messages: [http://debian-user-news.blogspot.com/2008/06/networkmanager-and-dhcp-issue-work.html](http://debian-user-news.blogspot.com/2008/06/networkmanager-and-dhcp-issue-work.html)

---

### Post by motin on 2008-07-15
Check [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105251) for fresh comments. 

A related but closed ubuntu forums thread btw: [http://ubuntuforums.org/showthread.php?t=145181](http://ubuntuforums.org/showthread.php?t=145181)

Some communication between dhclient and network manager is clearly not happening...

---

