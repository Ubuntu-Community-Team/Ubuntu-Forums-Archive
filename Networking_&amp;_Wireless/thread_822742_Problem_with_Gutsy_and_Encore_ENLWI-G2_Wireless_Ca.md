---
title: "Problem with Gutsy and Encore ENLWI-G2 Wireless Card"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by porcho on 2008-06-08
Hi there. I'm facing some problems with the above mentioned wireless card (a RTL8185L chipset card) and Ubuntu Gutsy, using Ndiswrapper. I'm able to connect with Network Manager but then, after 20-30 min of network activity, I get disconnected and I'm only able to reconnect when I restart the system, sometimes two or three times.
The content of some log files follows:

**daemon.log**
```
Jun  8 15:19:24 porchonew NetworkManager: <info>  wlan1: link timed out. 
Jun  8 15:19:24 porchonew NetworkManager: <info>  SWITCH: found better connection 'wlan1/PorchoDomain' than current connection 'wlan1/PorchoDomain'.  same_ssid=1, have_link=0 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Will activate connection 'wlan1/PorchoDomain'. 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Device wlan1 activation scheduled... 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Deactivating device wlan1. 
Jun  8 15:19:24 porchonew dhclient: There is already a pid file /var/run/dhclient.wlan1.pid with pid 6415
Jun  8 15:19:24 porchonew dhclient: killed old client process, removed PID file
Jun  8 15:19:24 porchonew dhclient: DHCPRELEASE on wlan1 to 192.168.1.1 port 67
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Withdrawing address record for 192.168.1.5 on wlan1.
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.5.
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jun  8 15:19:25 porchonew NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan1: Invalid argument 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) started... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1/wireless): access point 'PorchoDomain' is unencrypted, no key needed. 
Jun  8 15:19:25 porchonew avahi-daemon[5312]: Withdrawing address record for fe80::208:54ff:feae:49fe on wlan1.
Jun  8 15:19:26 porchonew NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jun  8 15:19:26 porchonew NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was '0' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 506f7263686f446f6d61696e' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1/wireless): association took too long (>60s), failing activation. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failure scheduled... 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failed for access point (PorchoDomain) 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failed. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Deactivating device wlan1. 
Jun  8 15:20:27 porchonew NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan1: Invalid argument 

```

**kern.log**
```
Jun  8 15:19:27 porchonew kernel: [ 2716.283853] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jun  8 15:20:40 porchonew kernel: [ 2789.439661] ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

**syslog**
```

Jun  8 14:41:25 porchonew syslogd 1.4.1#21ubuntu3: restart.
Jun  8 14:41:25 porchonew anacron[5896]: Job `cron.daily' terminated (mailing output)
Jun  8 14:41:25 porchonew anacron[5896]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Jun  8 14:45:01 porchonew anacron[5896]: Job `cron.weekly' started
Jun  8 14:45:01 porchonew anacron[6904]: Updated timestamp for job `cron.weekly' to 2008-06-08
Jun  8 14:45:02 porchonew syslogd 1.4.1#21ubuntu3: restart.
Jun  8 14:45:02 porchonew anacron[5896]: Job `cron.weekly' terminated
Jun  8 14:45:02 porchonew anacron[5896]: Normal exit (2 jobs run)
Jun  8 15:09:01 porchonew /USR/SBIN/CRON[7734]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jun  8 15:17:01 porchonew /USR/SBIN/CRON[8051]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  8 15:19:24 porchonew NetworkManager: <info>  wlan1: link timed out. 
Jun  8 15:19:24 porchonew NetworkManager: <info>  SWITCH: found better connection 'wlan1/PorchoDomain' than current connection 'wlan1/PorchoDomain'.  same_ssid=1, have_link=0 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Will activate connection 'wlan1/PorchoDomain'. 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Device wlan1 activation scheduled... 
Jun  8 15:19:24 porchonew NetworkManager: <info>  Deactivating device wlan1. 
Jun  8 15:19:24 porchonew dhclient: There is already a pid file /var/run/dhclient.wlan1.pid with pid 6415
Jun  8 15:19:24 porchonew dhclient: killed old client process, removed PID file
Jun  8 15:19:24 porchonew dhclient: DHCPRELEASE on wlan1 to 192.168.1.1 port 67
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Withdrawing address record for 192.168.1.5 on wlan1.
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.5.
Jun  8 15:19:24 porchonew avahi-daemon[5312]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jun  8 15:19:25 porchonew NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan1: Invalid argument 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) started... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan1 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Jun  8 15:19:25 porchonew NetworkManager: <info>  Activation (wlan1/wireless): access point 'PorchoDomain' is unencrypted, no key needed. 
Jun  8 15:19:25 porchonew avahi-daemon[5312]: Withdrawing address record for fe80::208:54ff:feae:49fe on wlan1.
Jun  8 15:19:26 porchonew NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jun  8 15:19:26 porchonew NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Jun  8 15:19:27 porchonew kernel: [ 2716.283853] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was '0' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 506f7263686f446f6d61696e' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  SUP: response was 'OK' 
Jun  8 15:19:27 porchonew NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1/wireless): association took too long (>60s), failing activation. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failure scheduled... 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failed for access point (PorchoDomain) 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Activation (wlan1) failed. 
Jun  8 15:20:27 porchonew NetworkManager: <info>  Deactivating device wlan1. 
Jun  8 15:20:27 porchonew NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan1: Invalid argument 

```

I've checked and it's not a problem with the Wifi card itself, as I tested it with other computer and it works allright.
A similar problem happens with Win XP, and I can read from the Event Viewer that "the system has detected that the wireless adapter has been disconnected and it's configuration was reset".

Could that be some sort of incompatibility between my Wifi card and my motherboard chipset, for example? Or am I using a broken driver, both in Ndiswrapper and Win XP? My computer configuration is:

Gigabyte P35-DS3 motherboard
Intel Core 2 Duo E6750 2.66Ghz 4MB FSB 1333MHz
2 x 1 GB 667 MHz DDR2 RAM
HDD Samsung 500 GB SATA II 16 MB cache
GeForce 8600GT 256 MB DDR3

Any help would be appreciated. Thanks in advance!

---

