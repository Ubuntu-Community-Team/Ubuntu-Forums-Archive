---
title: "AR5212 problem after upgrade"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by prefec2 on 2007-12-27
Hello folks,

I have a strange problem. After upgrading from feisty to gutsy, the wifi stopped to work. I started to dig into the problem and tried also some desperate measures, like trying different Live CDs even from different distributions, but nothing works.

My setup is:
IBM Thinkpad R51e with a Atheros AR5212/AR5213 card. I have a D-Link AirPlus G+ WLAN acess point.

syslog reports:
```
Dec 27 22:20:21 oslo NetworkManager: <info>  Deactivating device eth0.
Dec 27 22:20:21 oslo dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7399
Dec 27 22:20:21 oslo dhclient: killed old client process, removed PID file
Dec 27 22:20:21 oslo dhclient: wifi0: unknown hardware address type 801
Dec 27 22:20:21 oslo dhclient: wifi0: unknown hardware address type 801
Dec 27 22:20:21 oslo dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Dec 27 22:20:21 oslo avahi-daemon[6400]: Withdrawing address record for 192.168.0.105 on eth0.
Dec 27 22:20:21 oslo avahi-daemon[6400]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.105.
Dec 27 22:20:21 oslo avahi-daemon[6400]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) started...
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 27 22:20:22 oslo avahi-daemon[6400]: Withdrawing address record for fe80::20
a:e4ff:fe3e:30e on eth0.
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Dec 27 22:20:22 oslo NetworkManager: <info>  Activation (ath0/wireless): access point 'oma1' is unencrypted, no key needed.
Dec 27 22:20:23 oslo NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10).
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant3^I'
Dec 27 22:20:23 oslo kernel: [ 1332.704000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK' Dec 27 22:20:23 oslo NetworkManager: <info>  supplicant_init() - connect to devi
ce ctrl socket (1/10).

Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was '0'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0
 ssid 6f6d6131'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0
 scan_ssid 1'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0
 key_mgmt NONE'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: sending command 'ENABLE_NETWOR
K 0'
Dec 27 22:20:23 oslo NetworkManager: <info>  SUP: response was 'OK'
Dec 27 22:20:23 oslo NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete.
Dec 27 22:20:25 oslo avahi-daemon[6400]: Registering new address record for fe80::214:a4ff:fe74:42d2 on ath0.*.
Dec 27 22:20:31 oslo NetworkManager: <info>  Old device 'ath0' activating, won't change.
Dec 27 22:20:34 oslo kernel: [ 1343.384000] ath0: no IPv6 routers present
Dec 27 22:20:39 oslo NetworkManager: <info>  Old device 'ath0' activating, won't change.
Dec 27 22:21:11 oslo last message repeated 4 times
Dec 27 22:21:19 oslo NetworkManager: <info>  Old device 'ath0' activating, won't change.
Dec 27 22:21:23 oslo NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation.
Dec 27 22:21:23 oslo NetworkManager: <info>  Activation (ath0) failure scheduled ...
Dec 27 22:21:23 oslo NetworkManager: <info>  Activation (ath0) failed for access point (oma1)
Dec 27 22:21:23 oslo NetworkManager: <info>  Activation (ath0) failed.
Dec 27 22:21:23 oslo NetworkManager: <info>  Deactivating device ath0.
Dec 27 22:21:23 oslo NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Dec 27 22:21:23 oslo avahi-daemon[6400]: Withdrawing address record for fe80::214:a4ff:fe74:42d2 on ath0.

```

I configured my access point as open without any security settings, so any WPA or WEP problems will not appear. I also tried it with WPA. That didn't work too.

When I boot and sudo myself to become root, I can call iwconfig which tells me:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I can set the access point and essid by hand with:
```

iwconfig ath0 essid oma1
iwconfig ath0 ap XX:XX:XX:XX:XX:XX

```

But I still cannot get a connection.

I even tried to change the SSID of the access point. After a reboot, my laptop find the AP with the new SSID. When I change the SSID again, the networ kmanager doesn't get that change.

I have the feeling that the problem must be somewhere else, but a cannot find it.

Any suggestions or debug hints welcome
   Reiner

---

### Post by prefec2 on 2007-12-27
Hello,

I have fixed the problem somehow. I deactivated ACPI at boot time and now it works fine on my Thinpad R51e. However now both APM and ACPI are deactivated. And this is somewhat unpleasant on a laptop. So if anyone has some insights in this problem, please help

Thanks in advance
  Reiner

---

