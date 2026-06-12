---
title: "Can't connect to University wireless network"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by sskye on 2007-11-07
Hey, I've been having a weird problem connecting to my University (University of Toronto) wireless network. I'm not quite sure what's wrong. It did used to work with 7.04 (last year) but stopped even before I upgraded to 7.10. Maybe they changed something, 

Here is the school's wireless information:
[http://wireless.utoronto.ca/]("http://wireless.utoronto.ca/")

I don't see anything bizarre there, and like I said, it used to work.

This is what happens. Seems to fail at "stage 4 of 5" and then just asks me for a new network key. The network key I enter is correct.:

```
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) New wireless user key for network 'UTORwin' received. 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: sending command 'TERMINATE' 
  16:40:15 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:15 GLaDOS NetworkManager: <info>  Activation (eth1/wireless): access point 'UTORwin' is encrypted, and a key exists.  No new key needed. 
  16:40:16 GLaDOS NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
  16:40:16 GLaDOS avahi-autoipd(eth1)[6325]: SIOCSIFFLAGS failed: Permission denied
  16:40:16 GLaDOS avahi-autoipd(eth1)[6325]: Callout STOP, address 169.254.10.74 on interface eth1
  16:40:16 GLaDOS avahi-daemon[5413]: Interface eth1.IPv4 no longer relevant for mDNS.
  16:40:16 GLaDOS avahi-daemon[5413]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.10.74.
  16:40:16 GLaDOS avahi-daemon[5413]: Withdrawing address record for fe80::219:7dff:feaf:93f9 on eth1.
  16:40:16 GLaDOS avahi-daemon[5413]: Withdrawing address record for 169.254.10.74 on eth1.
  16:40:16 GLaDOS avahi-autoipd(eth1)[6326]: client: RTNETLINK answers: No such process
  16:40:16 GLaDOS NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant6^I' 
  16:40:16 GLaDOS kernel: [  294.864000] ADDRCONF(NETDEV_UP): eth1: link is not ready
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was '0' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 55544f5277696e' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
  16:40:16 GLaDOS NetworkManager: <info>  SUP: response was 'OK' 
  16:40:16 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
  16:40:20 GLaDOS NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'UTORwin'. 
  16:40:20 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
  16:40:20 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
  16:40:20 GLaDOS kernel: [  298.576000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
  16:40:21 GLaDOS NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
  16:40:21 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
  16:40:21 GLaDOS NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
  16:40:21 GLaDOS avahi-daemon[5413]: Registering new address record for fe80::219:7dff:feaf:93f9 on eth1.*.
  16:40:22 GLaDOS NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
  16:40:23 GLaDOS dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
  16:40:30 GLaDOS dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
  16:40:30 GLaDOS kernel: [  308.936000] eth1: no IPv6 routers present
  16:40:37 GLaDOS dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
  16:40:45 GLaDOS dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
  16:41:06 GLaDOS dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
  16:41:08 GLaDOS dhclient: No DHCPOFFERS received.
  16:41:08 GLaDOS dhclient: Trying recorded lease 192.168.1.104
  16:41:08 GLaDOS avahi-daemon[5413]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.104.
  16:41:08 GLaDOS avahi-daemon[5413]: New relevant interface eth1.IPv4 for mDNS.
  16:41:08 GLaDOS avahi-daemon[5413]: Registering new address record for 192.168.1.104 on eth1.IPv4.
  16:41:11 GLaDOS avahi-daemon[5413]: Withdrawing address record for 192.168.1.104 on eth1.
  16:41:11 GLaDOS avahi-daemon[5413]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.104.
  16:41:11 GLaDOS avahi-daemon[5413]: Interface eth1.IPv4 no longer relevant for mDNS.
  16:41:11 GLaDOS avahi-autoipd(eth1)[6471]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
  16:41:11 GLaDOS avahi-autoipd(eth1)[6471]: Successfully called chroot().
  16:41:11 GLaDOS avahi-autoipd(eth1)[6471]: Successfully dropped root privileges.
  16:41:11 GLaDOS avahi-autoipd(eth1)[6471]: Starting with address 169.254.10.74
  16:41:16 GLaDOS avahi-autoipd(eth1)[6471]: Callout BIND, address 169.254.10.74 on interface eth1
  16:41:16 GLaDOS avahi-daemon[5413]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.10.74.
  16:41:16 GLaDOS avahi-daemon[5413]: New relevant interface eth1.IPv4 for mDNS.
  16:41:16 GLaDOS avahi-daemon[5413]: Registering new address record for 169.254.10.74 on eth1.IPv4.
  16:41:20 GLaDOS avahi-autoipd(eth1)[6471]: Successfully claimed IP address 169.254.10.74
  16:41:20 GLaDOS NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
  16:41:20 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
  16:41:20 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
  16:41:20 GLaDOS NetworkManager: <debug> [1194471680.178040] real_act_stage4_ip_config_timeout(): Activation (eth1/wireless): could not get IP configuration info for 'UTORwin', asking for new key. 
  16:41:20 GLaDOS NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'UTORwin'. 
  16:41:20 GLaDOS NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
  16:41:20 GLaDOS NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
  16:41:20 GLaDOS dhcdbd: Unrequested down ?:3,
```

---

### Post by pavicnat on 2008-01-18
I found this in another forum, and it might work:

```


sudo iwconfig wlan0 essid UTORwin key restricted s:UToronto1home
sudo ifconfig wlan0 up
iwconfig


```

with the exception that wlan0 might be different for you, just type iwconfig to see which connection is responsible for wirless. 

I am having the same problem, and I can't connect to UTORwin. I've tried this and it hasn't worked, tell me if it works for you.

---

### Post by pavicnat on 2008-01-18
Actually I just saw that this was posted in November 7th!! Has anyone been able to figure out how to fix the problem?

---

### Post by virtualcoder on 2008-03-23
Well this reply's a little late cause I just had this problem a few moments ago.
I'm writing for those who will encounter this in the future.

For me this worked:
-choose UTORwin from the list of networks.
-it will ask for the password, use 128/64 wep, something like that
-also choose ascii from the drop down menu.
well I cant remember exactly but its should be easy.

-Then use the password, its public so I'll post it here UToronto1home.
-Then load a web page, e.g. google.com, and you will be directed to another page
where you use your utor account id for logging in.

That should get you through as it worked for me as well :)

---

