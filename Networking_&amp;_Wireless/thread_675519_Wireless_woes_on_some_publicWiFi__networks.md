---
title: "Wireless woes on some publicWiFi  networks"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by bimargulies on 2008-01-22
Gutsy Gibbon. Dell m1330. 

At Dulles Airport, and at a coffee shop in Tyson's Corner, I can't connect to the public WiFi.

Syslog suggests that DHCP is upset, maybe, I'm not following it very well.

Jan 16 16:12:11 bim-1330 gnome-power-manager: (benson) Power Manager is already running in this session.
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Jan 16 16:12:17 bim-1330 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Will activate connection 'eth1/Washington Dulles WiFi'. 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Device eth1 activation scheduled... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) started... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 16 16:12:17 bim-1330 NetworkManager: <info>  Activation (eth1/wireless): access point 'Washington Dulles WiFi' is unencrypted, no key needed. 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Jan 16 16:12:18 bim-1330 kernel: [   65.260000] NET: Registered protocol family 17
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was '0' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 57617368696e67746f6e2044756c6c65732057694669' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 16:12:18 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 16 16:12:24 bim-1330 NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan 16 16:12:27 bim-1330 kernel: [   74.276000] SoftMAC: Open Authentication completed with 00:19:07:96:05:40
Jan 16 16:12:34 bim-1330 NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan 16 16:12:40 bim-1330 kernel: [   86.968000] SoftMAC: Open Authentication completed with 00:19:07:96:05:40
Jan 16 16:12:44 bim-1330 NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan 16 16:12:50 bim-1330 kernel: [   97.528000] SoftMAC: Open Authentication completed with 00:19:07:96:05:40
Jan 16 16:12:50 bim-1330 kernel: [   97.548000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 16 16:12:50 bim-1330 NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Washington Dulles WiFi'. 
Jan 16 16:12:50 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 16 16:12:50 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan 16 16:12:51 bim-1330 NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan 16 16:12:51 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 16 16:12:51 bim-1330 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan 16 16:12:52 bim-1330 avahi-daemon[5484]: Registering new address record for fe80::21e:4cff:fe15:6af on eth1.*.
Jan 16 16:12:55 bim-1330 NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jan 16 16:12:55 bim-1330 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jan 16 16:12:55 bim-1330 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 16 16:13:00 bim-1330 dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 16 16:13:01 bim-1330 kernel: [  108.036000] eth1: no IPv6 routers present
Jan 16 16:13:09 bim-1330 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jan 16 16:13:13 bim-1330 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jan 16 16:13:18 bim-1330 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jan 16 16:13:29 bim-1330 dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jan 16 16:13:40 bim-1330 dhclient: No DHCPOFFERS received.
Jan 16 16:13:40 bim-1330 dhclient: Trying recorded lease 10.71.1.8
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.71.1.8.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: New relevant interface eth1.IPv4 for mDNS.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Registering new address record for 10.71.1.8 on eth1.IPv4.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Withdrawing address record for 10.71.1.8 on eth1.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.71.1.8.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.71.1.8.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: New relevant interface eth1.IPv4 for mDNS.
Jan 16 16:13:40 bim-1330 avahi-daemon[5484]: Registering new address record for 10.71.1.8 on eth1.IPv4.
Jan 16 16:13:45 bim-1330 avahi-daemon[5484]: Withdrawing address record for 10.71.1.8 on eth1.
Jan 16 16:13:45 bim-1330 avahi-daemon[5484]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.71.1.8.
Jan 16 16:13:45 bim-1330 avahi-daemon[5484]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 16 16:13:45 bim-1330 avahi-autoipd(eth1)[6916]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jan 16 16:13:45 bim-1330 avahi-autoipd(eth1)[6916]: Successfully called chroot().
Jan 16 16:13:45 bim-1330 avahi-autoipd(eth1)[6916]: Successfully dropped root privileges.
Jan 16 16:13:45 bim-1330 avahi-autoipd(eth1)[6916]: Starting with address 169.254.4.121
Jan 16 16:13:51 bim-1330 avahi-autoipd(eth1)[6916]: Callout BIND, address 169.254.4.121 on interface eth1
Jan 16 16:13:51 bim-1330 avahi-daemon[5484]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.121.
Jan 16 16:13:51 bim-1330 avahi-daemon[5484]: New relevant interface eth1.IPv4 for mDNS.
Jan 16 16:13:51 bim-1330 avahi-daemon[5484]: Registering new address record for 169.254.4.121 on eth1.IPv4.
Jan 16 16:13:55 bim-1330 avahi-autoipd(eth1)[6916]: Successfully claimed IP address 169.254.4.121
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Jan 16 16:13:55 bim-1330 dhcdbd: Unrequested down ?:3
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) failed for access point (Washington Dulles WiFi) 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Activation (eth1) failed. 
Jan 16 16:13:55 bim-1330 NetworkManager: <info>  Deactivating device eth1.

---

### Post by xtuner on 2008-02-14
I've been having exactly the same problem for some time now.  I can connect to certain open wifi points, but not others.  I've confirmed they're open by connecting to them with my windows PC.  

My syslog looks very similar to yours: everything seems to be going along great until I get the "DHCP daemon state is now 9 (fail) for interface eth1 " message.

Does anyone else know why this is happening?  In particular, why we might be shut out of certain wifi networks but not others?

Thank you!

---

### Post by dca on 2008-02-14
Are these WEP protected networks?

---

### Post by xtuner on 2008-02-14
Nope.  They are open, and require no key to connect.  

A little more info: I'm running Gutsy 7.10 on a Thinkpad T42.  My Thinkpad T30 running Windows XP connects fine.

---

### Post by dca on 2008-02-14
What happens if you go to 'System -> Administration -> Network' on the panel menu, set the network cards to roaming enabled, click on the DNS tab and clear anything you see in them.  Restart the laptop, click on the nm and try connecting to wireless network?

---

### Post by xtuner on 2008-02-14
I followed your advice, but I still have the same problem, and the same messages in the syslog.

Is there a general reason for why a machine would connect to some open access points and not others?

---

### Post by dca on 2008-02-14
....that's the odd thing, normally I'm a little better w/ just getting the wireless cards to work in general, when they work but then down the road act flaky it kind of sounds like a bug.  If nobody else is able to help you can file a bug report or wait and see if others latch on to the thread that have had similar issues, I can't find anything helpful searching the ubuntu forum...
 

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
and click on the bug report button...

---

### Post by dca on 2008-02-14
...as an option, you can try controlling your NIC(s) using WICD and see if that solves the issue...  I feel bad because not being able to confirm if it's a bug w/ NM or not.  Hopefully someone can validate my suggestion of using WICD...
 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by xtuner on 2008-02-14
Thank you for your help nonetheless!

---

### Post by bimargulies on 2008-03-11
I just discovered that KDE works much better on one example of a network that causes NetworkManager to screw up in a number of ways including the way originally reported here.

---

### Post by xtuner on 2008-03-11
Hmm.  I'll try a KDE session and see if that solves the problem.  Thanks!

---

### Post by bimargulies on 2008-03-12
Looking around this morning, it seems to me that it might be manual configuration, not KDE, that made things work. That's not too bad for an extended stay at one endpoint.

---

### Post by xtuner on 2008-03-21
You were right.  I selected "Connect to Other Wireless Network" from the network manager dropdown, put in the SSID, and it connected just fine.  I wonder why that is?

---

### Post by bimargulies on 2008-03-23
I filed a bug report. The Gnome network manager does not deal well with access point roaming, at very least. When you go to manual config, the network manager is cut out of the loop, and can no longer mess things up.

I recommend wicd at this point.

---

### Post by xtuner on 2008-03-25
Thanks, bimargulies!  Would you mind telling me where to find that bug report?  I'd like to look it over to get a sense for how to submit bugs in the future.

---

### Post by bimargulies on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/201202](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/201202) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/201202](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/201202)

Sadly, it still remains 'incomplete' in spite of the log traffic I posted.

---

