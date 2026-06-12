---
title: "Sporadic network connection - bcm4306 card"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Goombie on 2008-01-03
Ok, I'm getting fed up with this. :(
I have a Dell wireless card with a Broadcom 4306 chipset running under ndiswrapper. Every so often, maybe once every 2 hours, I lose my internet connection. It still shows as being connected to the router, but I can't get on the internet. Also, I can disconnect from the network, but I can't reconnect - the network manager applet just twirls and twirls and times out. The only way I can fix the problem -  to suspend my laptop and resume it again, or reboot Ubuntu, neither of which are much fun to do 10 times a day! My computer didn't always have this problem, it just started showing up a few days ago, when I switched from using Wicd to using NetworkManager. I switched back to Wicd, but the problem persisted, so now I'm back to using network manager. Help!:confused:

Oh, I don't think the network is the problem - I can connect on another computer without any problems. The router is a Linksys WRT54G, connected to a modem from Clearwire.

---

### Post by florus on 2008-01-03
Sounds very similar to the problems I have (see 'wireless problems' thread). My machine is a Dell Vostro 1400 with Intel 4965 AGN card. The network is always there when I boot into Vista, but only sporadic when I use Ubuntu.

---

### Post by Goombie on 2008-01-05
That does sound similar to my problem, but on a different machine and different card. Do you use NetworkManager to manage your connection?

Here's part of my daemon.log file; this is when the computer loses my network connection and tries to reconnect. The reconnection is unsuccessful:

```

Jan  5 19:41:06 goombie-laptop NetworkManager: <info>  wlan0: link timed out. 
Jan  5 19:41:06 goombie-laptop NetworkManager: <info>  SWITCH: found better connection 'wlan0/Atlantis' than current connection 'wlan0/Atlantis'.  same_ssid=1, have_link=0 
Jan  5 19:41:06 goombie-laptop NetworkManager: <info>  Will activate connection 'wlan0/Atlantis'. 
Jan  5 19:41:06 goombie-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Jan  5 19:41:06 goombie-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jan  5 19:41:06 goombie-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 19934
Jan  5 19:41:06 goombie-laptop dhclient: killed old client process, removed PID file
Jan  5 19:41:06 goombie-laptop dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Jan  5 19:41:06 goombie-laptop avahi-daemon[5627]: Withdrawing address record for 192.168.1.100 on wlan0.
Jan  5 19:41:06 goombie-laptop avahi-daemon[5627]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jan  5 19:41:06 goombie-laptop avahi-daemon[5627]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  5 19:41:07 goombie-laptop avahi-daemon[5627]: Withdrawing address record for fe80::290:96ff:feb5:6e9b on wlan0.
Jan  5 19:41:07 goombie-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) started... 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Atlantis' is encrypted, and a key exists.  No new key needed. 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan0 
Jan  5 19:41:07 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant4^I' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was '0' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 41746c616e746973' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 19:41:08 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  5 19:41:13 goombie-laptop avahi-daemon[5627]: Registering new address record for fe80::290:96ff:feb5:6e9b on wlan0.*.
Jan  5 19:42:08 goombie-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Jan  5 19:42:08 goombie-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Jan  5 19:42:08 goombie-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (Atlantis) 
Jan  5 19:42:08 goombie-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Jan  5 19:42:08 goombie-laptop NetworkManager: <info>  Deactivating device wlan0. 
Jan  5 19:42:08 goombie-laptop avahi-daemon[5627]: Withdrawing address record for fe80::290:96ff:feb5:6e9b on wlan0.
Jan  5 19:42:08 goombie-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Jan  5 19:42:18 goombie-laptop ntpd[5769]: Deleting interface #6 wlan0, fe80::290:96ff:feb5:6e9b#123, interface stats: received=0, sent=0, dropped=0, active_time=25500 secs
Jan  5 19:42:18 goombie-laptop ntpd[5769]: Deleting interface #7 wlan0, 192.168.1.100#123, interface stats: received=0, sent=0, dropped=0, active_time=25500 secs

```

And THIS section from daemon.log is when my computer connects successfully:
```

Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) started... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Atlantis' is encrypted, but NO valid key exists.  New key needed. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Atlantis'. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Atlantis' received. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  5 20:07:22 goombie-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Atlantis' is encrypted, and a key exists.  No new key needed. 
Jan  5 20:07:23 goombie-laptop ntpd[5769]: Deleting interface #8 wlan0, fe80::290:96ff:feb5:6e9b#123, interface stats: received=0, sent=0, dropped=0, active_time=300 secs
Jan  5 20:07:23 goombie-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant4^I' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was '0' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 41746c616e746973' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan  5 20:07:24 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  5 20:07:28 goombie-laptop avahi-daemon[5627]: Registering new address record for fe80::290:96ff:feb5:6e9b on wlan0.*.
Jan  5 20:07:29 goombie-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jan  5 20:07:31 goombie-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Atlantis'. 
Jan  5 20:07:31 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  5 20:07:31 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Jan  5 20:07:32 goombie-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Jan  5 20:07:32 goombie-laptop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Jan  5 20:07:32 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Jan  5 20:07:32 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Jan  5 20:07:33 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Jan  5 20:07:34 goombie-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  5 20:07:35 goombie-laptop dhclient: DHCPOFFER from 192.168.1.1
Jan  5 20:07:35 goombie-laptop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Jan  5 20:07:35 goombie-laptop dhclient: DHCPACK from 192.168.1.1
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: New relevant interface wlan0.IPv4 for mDNS.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Registering new address record for 192.168.1.100 on wlan0.IPv4.
Jan  5 20:07:35 goombie-laptop dhclient: bound to 192.168.1.100 -- renewal in 32793 seconds.
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    address 192.168.1.100 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    netmask 255.255.255.0 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    gateway 192.168.1.1 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    nameserver 208.67.222.222 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    nameserver 208.67.220.220 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    nameserver 64.13.48.12 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>    hostname 'goombie-laptop' 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Jan  5 20:07:35 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Withdrawing address record for 192.168.1.100 on wlan0.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Withdrawing address record for fe80::290:96ff:feb5:6e9b on wlan0.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: New relevant interface wlan0.IPv4 for mDNS.
Jan  5 20:07:35 goombie-laptop avahi-daemon[5627]: Registering new address record for 192.168.1.100 on wlan0.IPv4.
Jan  5 20:07:36 goombie-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Jan  5 20:07:36 goombie-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan  5 20:07:36 goombie-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jan  5 20:07:36 goombie-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Jan  5 20:07:36 goombie-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  5 20:07:36 goombie-laptop NetworkManager: <debug> [1199592456.131006] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Atlantis' 
Jan  5 20:07:36 goombie-laptop ntpdate[23606]: the NTP socket is in use, exiting
Jan  5 20:07:37 goombie-laptop avahi-daemon[5627]: Registering new address record for fe80::290:96ff:feb5:6e9b on wlan0.*.
Jan  5 20:12:23 goombie-laptop ntpd[5769]: Listening on interface #9 wlan0, fe80::290:96ff:feb5:6e9b#123 Enabled
Jan  5 20:12:23 goombie-laptop ntpd[5769]: Listening on interface #10 wlan0, 192.168.1.100#123 Enabled

```
I don't know what it all means, but does anyone else?

---

### Post by kevdog on 2008-01-06
Turn off or disable IPV6 -- do some research.  It  sounds like you are using wpa.  Does this do the same with an unencrypted wireless network or even a WEP network.

---

### Post by Goombie on 2008-01-06
In my neighborhood, everyone encrypts their networks. :| However, I was connected to an unsecured network yesterday, and I didn't notice any problems. I'll give disabling ipv6 a try and see what happens. *Crosses fingers*

---

### Post by daleus on 2008-01-06
In reply to the OP, I have a similar broadcom card in my dell 1501 laptop.

Try use the windows drivers manually in ndiswrapper, rather than using the restricted-manager.

This cleared up all trouble with protected networks and range issues. (before wireless would just twirl and twirl if signal was <70%, now it works right down to 4% at a friends house, beating windows ffs..)

---

### Post by Goombie on 2008-01-06
I already use the Windows drivers through ndiswrapper - I should have mentioned that in the first place. :)
And to follow up, disabling ipv6 didn't make any difference - I still lost the connection after a little while when I tried today. :|

---

