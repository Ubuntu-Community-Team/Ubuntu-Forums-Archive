---
title: "[SOLVED] I can see but not connect to wireless networks with Madwifi and my Atheros c"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Coward on 2008-09-07
I can see but not connect to wireless networks with Madwifi and my Atheros AR5007eg chip. Madwifi used to work, but died hours after I fixed the CPU frequency scaling (this may be unrelated). I installed WICD and changed the WPA supplicant to madwifi but still no luck. I have 32bit Hardy on an hp dv5z laptop. I have disabled the HAL under hardware options which is how it was when my wireless was working. Ndiswrapper didn't work for me either, but this may be because I set it up wrong. I'd rather use madwifi anyway. Any suggestions?

---

### Post by d_singo69 on 2008-09-07
have you tried this ?
[http://ubuntuforums.org/showthread.php?t=865971&highlight=chili555](http://ubuntuforums.org/showthread.php?t=865971&highlight=chili555)

---

### Post by Coward on 2008-09-09
Just tried it. Thanks for the link but it didn't seem to change anything for me. I still see my network, but cannot connect. My system log says:

```

Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Device ath0 activation scheduled... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) started... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'POPPY' is encrypted, but NO valid key exists.  New key needed. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'POPPY'. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) New wireless user key for network 'POPPY' received. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Sep  8 20:52:40 jake-laptop NetworkManager: <info>  Activation (ath0/wireless): access point 'POPPY' is encrypted, and a key exists.  No new key needed. 
Sep  8 20:52:41 jake-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
Sep  8 20:52:42 jake-laptop kernel: [  118.152764] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Sep  8 20:52:42 jake-laptop kernel: [  118.197945] NET: Registered protocol family 17
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was '0' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 504f505059' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  8 20:52:42 jake-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Sep  8 20:52:43 jake-laptop avahi-daemon[5130]: Registering new address record for fe80::222:69ff:fe5b:9799 on ath0.*.
Sep  8 20:52:49 jake-laptop NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep  8 20:52:52 jake-laptop kernel: [  128.625653] ath0: no IPv6 routers present
Sep  8 20:53:02 jake-laptop NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Sep  8 20:53:39 jake-laptop last message repeated 3 times
Sep  8 20:53:42 jake-laptop NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation. 
Sep  8 20:53:42 jake-laptop NetworkManager: <info>  Activation (ath0) failure scheduled... 
Sep  8 20:53:42 jake-laptop NetworkManager: <info>  Activation (ath0) failed for access point (POPPY) 
Sep  8 20:53:42 jake-laptop NetworkManager: <info>  Activation (ath0) failed. 
Sep  8 20:53:42 jake-laptop NetworkManager: <info>  Deactivating device ath0. 
Sep  8 20:53:42 jake-laptop avahi-daemon[5130]: Withdrawing address record for fe80::222:69ff:fe5b:9799 on ath0.

```

All the messages seem good until it gets stuck on "NetworkManager: <info>  Old device 'ath0' activating, won't change." I'm not sure what this means.

I tried this post aswell [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780). Compiling madwifi does not seem to be the fix for this.
EDIT: Just looked at that link I posted and it was for 64bit ubuntu. Still didn't seem to change anything.

When trying to connect with WICD the syslog shows only what seems like good news, except WICD ends up saying "Not Connected".
```

Sep  9 10:06:52 jake-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Sep  9 10:06:52 jake-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Sep  9 10:06:52 jake-laptop dhclient: All rights reserved.
Sep  9 10:06:52 jake-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep  9 10:06:52 jake-laptop dhclient: 
Sep  9 10:06:52 jake-laptop dhclient: wifi0: unknown hardware address type 801
Sep  9 10:06:53 jake-laptop avahi-daemon[5164]: Registering new address record for fe80::222:69ff:fe5b:9799 on ath0.*.
Sep  9 10:06:54 jake-laptop dhclient: wifi0: unknown hardware address type 801
Sep  9 10:06:54 jake-laptop dhclient: Listening on LPF/ath0/00:22:69:5b:97:99
Sep  9 10:06:54 jake-laptop dhclient: Sending on   LPF/ath0/00:22:69:5b:97:99
Sep  9 10:06:54 jake-laptop dhclient: Sending on   Socket/fallback
Sep  9 10:06:58 jake-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Sep  9 10:07:02 jake-laptop kernel: [  884.115978] ath0: no IPv6 routers present
Sep  9 10:07:06 jake-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
Sep  9 10:07:23 jake-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Sep  9 10:07:29 jake-laptop dhclient: No DHCPOFFERS received.
Sep  9 10:07:29 jake-laptop dhclient: No working leases in persistent database - sleeping.
Sep  9 10:07:29 jake-laptop avahi-autoipd(ath0)[8517]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Sep  9 10:07:29 jake-laptop avahi-autoipd(ath0)[8517]: Successfully called chroot().
Sep  9 10:07:29 jake-laptop avahi-autoipd(ath0)[8517]: Successfully dropped root privileges.
Sep  9 10:07:29 jake-laptop avahi-autoipd(ath0)[8517]: Starting with address 169.254.7.95
Sep  9 10:07:34 jake-laptop avahi-autoipd(ath0)[8517]: Callout BIND, address 169.254.7.95 on interface ath0
Sep  9 10:07:34 jake-laptop avahi-daemon[5164]: Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.7.95.
Sep  9 10:07:34 jake-laptop avahi-daemon[5164]: New relevant interface ath0.IPv4 for mDNS.
Sep  9 10:07:34 jake-laptop avahi-daemon[5164]: Registering new address record for 169.254.7.95 on ath0.IPv4.
Sep  9 10:07:38 jake-laptop avahi-autoipd(ath0)[8517]: Successfully claimed IP address 169.254.7.95

```

---

### Post by Coward on 2008-09-11
Thanks for the help.

Solved, and I feel stupid. I had to use WICD. What I didn't notice was that you have to click the arrow next to the wireless network to get more options to show. Then the arrow next to advanced settings. Then you have to put the password where it asks about encryption. I had just assumed it would use the encryptions and keyrings that the network-manager program did.

For anyone else who has this chipset. Compile madwifi. Add ath_pci to the /etc/modules file. Have the restricted drivers enabled for wireless. Install wicd. Set madwifi in preferences as the WPA supplicant. Finally do what I described above to give it the password/key. Done!!!

---

