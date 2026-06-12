---
title: "Networkmanager cannot obtain IP via DHCP"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by er4z0r on 2008-04-20
Hi there,

I am running Hardy Heron on a Macbook Pro here.
Wireless is setup with madwifi driver as described on macbook wiki-page.
When I setup up wireless with iwconfig and dhclient everything works well.

When I use knetworkmanager, it associates with the wireless network, but fails to obtain an IP-Address via dhcp. Please see syslog output below:

```
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) New wireless user key for network 'H0m3n3t' received.
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Apr 20 20:37:46 phrackbook NetworkManager: <info>  Activation (ath0/wireless): access point 'H0m3n3t' is encrypted, and a key exists.  No new key needed.
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was '0'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 48306d336e3374'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  SUP: response was 'OK'
Apr 20 20:37:48 phrackbook NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Apr 20 20:37:56 phrackbook NetworkManager: <info>  Supplicant state changed: 1
Apr 20 20:37:56 phrackbook NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'H0m3n3t'.
Apr 20 20:37:56 phrackbook NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 20 20:37:56 phrackbook NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started...
Apr 20 20:37:57 phrackbook NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction.
Apr 20 20:37:57 phrackbook NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete.
Apr 20 20:37:57 phrackbook NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0
Apr 20 20:37:57 phrackbook dhclient: wifi0: unknown hardware address type 801
Apr 20 20:37:57 phrackbook avahi-autoipd(ath0)[6543]: Got SIGTERM, quitting.
Apr 20 20:37:57 phrackbook avahi-autoipd(ath0)[6543]: Callout STOP, address 169.254.6.89 on interface ath0
Apr 20 20:37:57 phrackbook avahi-daemon[5232]: Withdrawing address record for 169.254.6.89 on ath0.
Apr 20 20:37:57 phrackbook avahi-daemon[5232]: Leaving mDNS multicast group on interface ath0.IPv4 with address 169.254.6.89.
Apr 20 20:37:57 phrackbook avahi-daemon[5232]: Interface ath0.IPv4 no longer relevant for mDNS.
Apr 20 20:37:57 phrackbook avahi-autoipd(ath0)[6544]: client: RTNETLINK answers: No such process
Apr 20 20:37:58 phrackbook dhclient: wifi0: unknown hardware address type 801
Apr 20 20:37:58 phrackbook NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0
Apr 20 20:37:58 phrackbook dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
Apr 20 20:38:01 phrackbook NetworkManager: <info>  Old device 'ath0' activating, won't change.
Apr 20 20:38:02 phrackbook dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Apr 20 20:38:08 phrackbook dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
Apr 20 20:38:10 phrackbook kernel: [  232.969218] applesmc: wait status failed: 5 != 4
Apr 20 20:38:10 phrackbook kernel: [  233.062600] applesmc: wait status failed: c != 8
Apr 20 20:38:13 phrackbook kernel: [  234.417975] applesmc: wait status failed: 5 != 4
Apr 20 20:38:14 phrackbook kernel: [  234.489840] applesmc: wait status failed: c != 8
Apr 20 20:38:22 phrackbook dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
Apr 20 20:38:29 phrackbook dhclient: No DHCPOFFERS received.
Apr 20 20:38:29 phrackbook avahi-autoipd(ath0)[6791]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 112).
Apr 20 20:38:29 phrackbook avahi-autoipd(ath0)[6791]: Successfully called chroot().
Apr 20 20:38:29 phrackbook avahi-autoipd(ath0)[6791]: Successfully dropped root privileges.
Apr 20 20:38:29 phrackbook avahi-autoipd(ath0)[6791]: Starting with address 169.254.6.89
Apr 20 20:38:35 phrackbook avahi-autoipd(ath0)[6791]: Callout BIND, address 169.254.6.89 on interface ath0
Apr 20 20:38:35 phrackbook avahi-daemon[5232]: Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.6.89.
Apr 20 20:38:35 phrackbook avahi-daemon[5232]: New relevant interface ath0.IPv4 for mDNS.
Apr 20 20:38:35 phrackbook avahi-daemon[5232]: Registering new address record for 169.254.6.89 on ath0.IPv4.
Apr 20 20:38:39 phrackbook avahi-autoipd(ath0)[6791]: Successfully claimed IP address 169.254.6.89
Apr 20 20:38:39 phrackbook NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface ath0
Apr 20 20:38:39 phrackbook NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Apr 20 20:38:39 phrackbook NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started...
Apr 20 20:38:39 phrackbook NetworkManager: <debug> [1208716719.180640] real_act_stage4_ip_config_timeout(): Activation (ath0/wireless): could not get IP configuration info for 'H0m3n3t', asking for new key.
Apr 20 20:38:39 phrackbook dhcdbd: Unrequested down ?:3
Apr 20 20:38:39 phrackbook NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface ath0
Apr 20 20:38:39 phrackbook NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'H0m3n3t'.
Apr 20 20:38:39 phrackbook NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete.
```

What could be the problem?
What more information do you need?

---

### Post by CrazyGuy123 on 2008-04-20
Usually thats caused by something being wrong with the encryption.  Does it work with encryption off?

---

### Post by er4z0r on 2008-04-21
> **CrazyGuy123 said:**
> Usually thats caused by something being wrong with the encryption.  Does it work with encryption off?

OK?! This is strange now. I switched from my old WEP128 to WPA.
Tada! Works now. But why the hell?

kind regards
er4z0r

---

