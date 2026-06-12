---
title: "Can wireless card be put into a state were a cold reboot will not bring it back?"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by odin1965 on 2007-08-20
My laptop wireless was working fine for a week after installing 7.04. Then it became flaky and finally stopped working. When it first started acting up, I tried a  PClinuxOS live CD and my wireless worked out of the box with that. Now even that will not connect. My wireless light flashes as if scanning for network, but will not connect. I have tried a fresh install of 7.04 and that no longer works either.

My wireless card is detected, driver loaded and everything seems normal there


```
lspci output;
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

lsmod output;
pw3945               118816  1 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ieee80211              34760  1 ipw3945
```



I can scan for SSID's in range and it finds them, see output from iwlist scan;

```
eth1      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"eascan1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-55 dBm  Noise level=-55 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 84ms ago

```

Though, at times, the scanning is inconsistent. Sometimes is says 'Interface doesn't support scanning' though that goes right away upon scanning again. Sometimes I get 'no scan results', but not very often.

```

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2228   Missed beacon:0
```

I have tried to connect with network manager, WiCD and wifi radar and they all see the ESSID's but timeout before connecting. Very rarely, I will get connected, but at 0% signal strength with both WiCD and Network Manager.

Will follow up with output from syslog.

---

### Post by odin1965 on 2007-08-20
Here is output from syslog, while booting with Network Manager.

```
Aug 17 06:47:07 delllap syslogd 1.4.1#20ubuntu4: restart.
Aug 17 06:47:07 delllap anacron[5326]: Job `cron.daily' terminated
Aug 17 06:47:07 delllap anacron[5326]: Normal exit (1 job run)
Aug 17 06:47:10 delllap dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 17 06:47:13 delllap kernel: [ 2266.088000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:17 delllap dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 17 06:47:21 delllap kernel: [ 2273.696000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:24 delllap dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 17 06:47:29 delllap kernel: [ 2281.204000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:32 delllap dhclient: No DHCPOFFERS received.
Aug 17 06:47:32 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 06:47:36 delllap kernel: [ 2288.816000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): lts: -1 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Failed to get scan results 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Failed to get scan results - try scanning again 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Setting scan request: 1 sec 0 usec 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Starting AP scan (broadcast SSID) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan timeout - try to get results 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Received 0 bytes of scan results (0 BSSes) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan results: 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Selecting BSS from priority group 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): No suitable AP found. 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Setting scan request: 5 sec 0 usec 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Starting AP scan (broadcast SSID) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan timeout - try to get results 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Received 0 bytes of scan results (0 BSSes) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan results: 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Selecting BSS from priority group 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): No suitable AP found. 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Setting scan request: 5 sec 0 usec 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Starting AP scan (broadcast SSID) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan timeout - try to get results 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Received 0 bytes of scan results (0 BSSes) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan results: 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Selecting BSS from priority group 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): No suitable AP found. 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Setting scan request: 5 sec 0 usec 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Starting AP scan (broadcast SSID) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan timeout - try to get results 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Received 0 bytes of scan results (0 BSSes) 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Scan results: 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Selecting BSS from priority group 0 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): No suitable AP found. 
Aug 17 06:47:38 delllap NetworkManager: <information>^Iwpa_supplicant(7162): Setting scan request: 5 sec 0 usec 
Aug 17 06:47:44 delllap NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_essid (): error getting ESSID for device eth1: Resource temporarily unavailable 
Aug 17 06:47:44 delllap kernel: [ 2296.432000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:51 delllap kernel: [ 2303.940000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:47:59 delllap kernel: [ 2311.552000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:48:04 delllap NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>120s), failing activation. 
Aug 17 06:48:04 delllap NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Aug 17 06:48:04 delllap NetworkManager: <information>^IActivation (eth1) failed for access point (leeman02) 
Aug 17 06:48:04 delllap NetworkManager: <information>^IActivation (eth1) failed. 
Aug 17 06:48:04 delllap NetworkManager: <information>^IDeactivating device eth1. 
Aug 17 06:48:07 delllap kernel: [ 2319.076000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:48:08 delllap kernel: [ 2320.336000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 17 06:48:15 delllap kernel: [ 2327.716000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:48:35 delllap kernel: [ 2347.980000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:48:56 delllap kernel: [ 2368.240000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:49:16 delllap kernel: [ 2388.504000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:49:36 delllap kernel: [ 2408.672000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:49:57 delllap kernel: [ 2428.832000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:51:57 delllap kernel: [ 2549.096000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:53:57 delllap kernel: [ 2669.360000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:54:04 delllap gconfd (root-7570): starting (version 2.18.0.1), pid 7570 user 'root'
Aug 17 06:54:04 delllap gconfd (root-7570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 06:54:04 delllap gconfd (root-7570): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 17 06:54:04 delllap gconfd (root-7570): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 17 06:54:04 delllap gconfd (root-7570): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 06:54:04 delllap gconfd (root-7570): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 06:54:24 delllap NetworkManager: <information>^IGoing to sleep. 
Aug 17 06:54:24 delllap avahi-autoipd(eth0)[5547]: SIOCSIFFLAGS failed: Permission denied
Aug 17 06:54:24 delllap avahi-autoipd(eth0)[5547]: Callout STOP, address 169.254.8.138 on interface eth0
Aug 17 06:54:24 delllap dhclient: receive_packet failed on eth0: Network is down
Aug 17 06:54:24 delllap NetworkManager: <information>^IWaking up from sleep. 
Aug 17 06:54:24 delllap NetworkManager: <information>^IDeactivating device eth0. 
Aug 17 06:54:24 delllap NetworkManager: <information>^IDeactivating device eth1. 
Aug 17 06:54:24 delllap avahi-autoipd(eth0)[5548]: client: RTNETLINK answers: No such process
Aug 17 06:54:24 delllap kernel: [ 2696.264000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 17 06:54:24 delllap kernel: [ 2696.284000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 17 06:54:24 delllap NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Aug 17 06:54:24 delllap NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Aug 17 06:54:24 delllap NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Aug 17 06:54:24 delllap NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Aug 17 06:54:24 delllap NetworkManager: <information>^IDeactivating device eth0. 
Aug 17 06:54:26 delllap dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5653
Aug 17 06:54:26 delllap dhclient: killed old client process, removed PID file
Aug 17 06:54:26 delllap dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 17 06:54:26 delllap dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 17 06:54:26 delllap dhclient: All rights reserved.
Aug 17 06:54:26 delllap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 17 06:54:26 delllap dhclient: 
Aug 17 06:54:26 delllap dhclient: Listening on LPF/eth0/00:19:b9:83:8f:a5
Aug 17 06:54:26 delllap dhclient: Sending on   LPF/eth0/00:19:b9:83:8f:a5
Aug 17 06:54:26 delllap dhclient: Sending on   Socket/fallback
Aug 17 06:54:26 delllap dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Aug 17 06:54:26 delllap dhclient: send_packet: Network is unreachable
Aug 17 06:54:26 delllap dhclient: send_packet: please consult README file regarding broadcast address.
Aug 17 06:54:26 delllap avahi-autoipd(eth0)[7668]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Aug 17 06:54:26 delllap avahi-autoipd(eth0)[7668]: Successfully called chroot().
Aug 17 06:54:27 delllap avahi-autoipd(eth0)[7668]: Successfully dropped root privileges.
Aug 17 06:54:27 delllap avahi-autoipd(eth0)[7668]: fopen() failed: Permission denied
Aug 17 06:54:27 delllap avahi-autoipd(eth0)[7668]: Starting with address 169.254.8.138
Aug 17 06:54:31 delllap kernel: [ 2703.636000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:54:32 delllap avahi-autoipd(eth0)[7668]: Callout BIND, address 169.254.8.138 on interface eth0
Aug 17 06:54:36 delllap avahi-autoipd(eth0)[7668]: Successfully claimed IP address 169.254.8.138
Aug 17 06:54:36 delllap avahi-autoipd(eth0)[7668]: fopen() failed: Permission denied
Aug 17 06:54:36 delllap avahi-autoipd(eth0)[7668]: SIOCSIFFLAGS failed: Permission denied
Aug 17 06:54:36 delllap avahi-autoipd(eth0)[7668]: Callout STOP, address 169.254.8.138 on interface eth0
Aug 17 06:54:36 delllap avahi-autoipd(eth0)[7669]: client: RTNETLINK answers: No such process
Aug 17 06:54:38 delllap NetworkManager: <information>^IGoing to sleep. 
Aug 17 06:54:38 delllap NetworkManager: <information>^IWaking up from sleep. 
Aug 17 06:54:38 delllap NetworkManager: <information>^IDeactivating device eth0. 
Aug 17 06:54:38 delllap kernel: [ 2710.580000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 17 06:54:46 delllap kernel: [ 2717.832000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 06:55:04 delllap gconfd (root-7570): GConf server is not in use, shutting down.
Aug 17 06:55:04 delllap gconfd (root-7570): Exiting
Aug 17 06:55:10 delllap NetworkManager: <information>^IGoing to sleep. 
Aug 17 06:55:13 delllap NetworkManager: <information>^IWaking up from sleep. 
Aug 17 06:55:20 delllap kernel: [ 2752.620000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)

```



Here is subsequent output from syslog, while trying to connect with Network Manager.
```

Aug 17 06:57:25 delllap gconfd (root-7842): starting (version 2.18.0.1), pid 7842 user 'root'
Aug 17 06:57:25 delllap gconfd (root-7842): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 06:57:25 delllap gconfd (root-7842): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 17 06:57:25 delllap gconfd (root-7842): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 17 06:57:25 delllap gconfd (root-7842): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 06:57:25 delllap gconfd (root-7842): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 06:57:55 delllap gconfd (root-7842): GConf server is not in use, shutting down.
Aug 17 06:57:55 delllap gconfd (root-7842): Exiting
Aug 17 06:58:16 delllap dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 17 06:58:16 delllap dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 17 06:58:16 delllap dhclient: All rights reserved.
Aug 17 06:58:16 delllap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 17 06:58:16 delllap dhclient: 
Aug 17 06:58:17 delllap dhclient: Listening on LPF/eth1/00:1b:77:5f:e5:23
Aug 17 06:58:17 delllap dhclient: Sending on   LPF/eth1/00:1b:77:5f:e5:23
Aug 17 06:58:17 delllap dhclient: Sending on   Socket/fallback
Aug 17 06:58:21 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 17 06:58:28 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Aug 17 06:58:39 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Aug 17 06:58:51 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Aug 17 06:58:52 delllap dhclient: No DHCPOFFERS received.
Aug 17 06:58:52 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 06:58:52 delllap avahi-autoipd(eth1)[7932]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Aug 17 06:58:52 delllap avahi-autoipd(eth1)[7932]: Successfully called chroot().
Aug 17 06:58:52 delllap avahi-autoipd(eth1)[7932]: Successfully dropped root privileges.
Aug 17 06:58:52 delllap avahi-autoipd(eth1)[7932]: fopen() failed: Permission denied
Aug 17 06:58:52 delllap avahi-autoipd(eth1)[7932]: Starting with address 169.254.6.106
Aug 17 06:58:57 delllap avahi-autoipd(eth1)[7932]: Callout BIND, address 169.254.6.106 on interface eth1
Aug 17 06:59:01 delllap avahi-autoipd(eth1)[7932]: Successfully claimed IP address 169.254.6.106
Aug 17 06:59:01 delllap avahi-autoipd(eth1)[7932]: fopen() failed: Permission denied
Aug 17 06:59:21 delllap ntpdate[7953]: can't find host ntp.ubuntu.com 
Aug 17 06:59:21 delllap ntpdate[7953]: no servers can be used, exiting
Aug 17 07:02:10 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Aug 17 07:02:14 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Aug 17 07:02:23 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Aug 17 07:02:33 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 17 07:02:41 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:02:41 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:05:56 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Aug 17 07:06:00 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 17 07:06:06 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Aug 17 07:06:20 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 17 07:06:27 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:06:27 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:09:04 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Aug 17 07:09:07 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 17 07:09:15 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 17 07:09:23 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Aug 17 07:09:32 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Aug 17 07:09:35 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:09:35 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:13:48 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 17 07:13:55 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Aug 17 07:14:11 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 17 07:14:19 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:14:19 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:17:01 delllap /USR/SBIN/CRON[8513]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 17 07:21:04 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 17 07:21:11 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Aug 17 07:21:21 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Aug 17 07:21:35 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:21:35 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:28:12 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Aug 17 07:28:16 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Aug 17 07:28:20 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 17 07:28:25 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 17 07:28:30 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Aug 17 07:28:36 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Aug 17 07:28:43 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:28:43 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:30:01 delllap /USR/SBIN/CRON[8923]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Aug 17 07:30:01 delllap anacron[8948]: Anacron 2.3 started on 2007-08-17
Aug 17 07:30:01 delllap anacron[8948]: Normal exit (0 jobs run)
Aug 17 07:34:59 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Aug 17 07:35:04 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Aug 17 07:35:15 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Aug 17 07:35:28 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Aug 17 07:35:30 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:35:30 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:42:07 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Aug 17 07:42:15 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Aug 17 07:42:25 delllap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Aug 17 07:42:38 delllap dhclient: No DHCPOFFERS received.
Aug 17 07:42:38 delllap dhclient: No working leases in persistent database - sleeping.
Aug 17 07:44:15 delllap gconfd (root-9375): starting (version 2.18.0.1), pid 9375 user 'root'
Aug 17 07:44:15 delllap gconfd (root-9375): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 07:44:15 delllap gconfd (root-9375): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 17 07:44:15 delllap gconfd (root-9375): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 17 07:44:15 delllap gconfd (root-9375): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 07:44:15 delllap gconfd (root-9375): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 07:44:41 delllap dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 7941
Aug 17 07:44:41 delllap dhclient: killed old client process, removed PID file
Aug 17 07:44:41 delllap dhclient: Internet Systems Consortium DHCP Client V3.0.4
Aug 17 07:44:41 delllap dhclient: Copyright 2004-2006 Internet Systems Consortium.
Aug 17 07:44:41 delllap dhclient: All rights reserved.
Aug 17 07:44:41 delllap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 17 07:44:41 delllap dhclient: 
Aug 17 07:44:41 delllap dhclient: Listening on LPF/eth1/00:1b:77:5f:e5:23
Aug 17 07:44:41 delllap dhclient: Sending on   LPF/eth1/00:1b:77:5f:e5:23
Aug 17 07:44:41 delllap dhclient: Sending on   Socket/fallback
Aug 17 07:44:41 delllap dhclient: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Aug 17 07:44:41 delllap avahi-autoipd(eth1)[7932]: SIOCSIFFLAGS failed: Permission denied
Aug 17 07:44:41 delllap avahi-autoipd(eth1)[7932]: Callout STOP, address 169.254.6.106 on interface eth1
Aug 17 07:44:41 delllap avahi-autoipd(eth1)[7933]: client: RTNETLINK answers: No such process
Aug 17 07:44:41 delllap kernel: [ 5713.180000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 17 07:44:43 delllap NetworkManager: <information>^IGoing to sleep. 
Aug 17 07:44:43 delllap NetworkManager: <information>^IWaking up from sleep. 
Aug 17 07:44:43 delllap NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'b44'. 
Aug 17 07:44:43 delllap NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Aug 17 07:44:43 delllap NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Aug 17 07:44:43 delllap NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Aug 17 07:44:43 delllap NetworkManager: <information>^IDeactivating device eth0. 
Aug 17 07:44:50 delllap kernel: [ 5722.592000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:44:58 delllap kernel: [ 5730.080000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:01 delllap ntpdate[9478]: can't find host ntp.ubuntu.com 
Aug 17 07:45:01 delllap ntpdate[9478]: no servers can be used, exiting
Aug 17 07:45:06 delllap kernel: [ 5737.572000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:13 delllap kernel: [ 5745.068000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:15 delllap gconfd (root-9375): GConf server is not in use, shutting down.
Aug 17 07:45:15 delllap gconfd (root-9375): Exiting
Aug 17 07:45:21 delllap kernel: [ 5752.560000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:28 delllap kernel: [ 5760.056000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:36 delllap kernel: [ 5767.548000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:44 delllap kernel: [ 5775.040000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:51 delllap kernel: [ 5782.532000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:45:59 delllap kernel: [ 5790.024000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:06 delllap kernel: [ 5797.516000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:14 delllap kernel: [ 5805.008000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:22 delllap kernel: [ 5812.500000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:29 delllap kernel: [ 5819.996000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:37 delllap kernel: [ 5827.488000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:44 delllap kernel: [ 5834.980000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:52 delllap kernel: [ 5842.476000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:46:59 delllap kernel: [ 5849.968000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:07 delllap kernel: [ 5857.460000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:15 delllap kernel: [ 5864.948000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:22 delllap kernel: [ 5872.464000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:30 delllap kernel: [ 5880.060000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:37 delllap kernel: [ 5887.560000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:45 delllap kernel: [ 5895.052000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:47:53 delllap kernel: [ 5902.552000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:48:00 delllap kernel: [ 5910.044000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:48:08 delllap kernel: [ 5917.532000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:48:15 delllap kernel: [ 5925.028000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 17 07:48:23 delllap kernel: [ 5932.552000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)

```

Can anybody help interpret these syslog messages? It seem very odd that originally both a live CD and a fresh install worked, now they do not.

---

### Post by dansen926 on 2007-08-21
I'm experiencing *exactly* the same problem! Please help!

---

### Post by odin1965 on 2007-08-24
> **dansen926 said:**
> I'm experiencing *exactly* the same problem! Please help!

Can you post the output of lshw -C network ? Mine is;
```
  *-network               
       description: Ethernet interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:5f:e5:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=0.0 0:0 () latency=0 multicast=yes
       resources: iomemory:fe8ff000-fe8fffff irq:17
```

I booted 7.04 live CD on an ACER with the 3945 that works and  I get this output;

```
 *-network
      description: Wireless interface
      product: PRO/Wireless 3945ABG Network Connection
      vendor: Intel Corporation
      physical id: 0
      bus info: pci@05:00.0
      logical name: eth1
      version: 02
      serial: 00:18:de:d4:16:d1
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp
firmware=14.2 1:0 () ip=192.168.0.109 latency=0 multicast=yes wireless=IEEE
802.11g
      resources: iomemory:d0100000-d0100fff irq:19
```

One difference that I can see is mine has the desciption, Ethernet interface, and the Acer has decription, Wireless Interface. Also, under capabilities, the Acer has wireless listed and mine does not. As well it has wireless=IEEE and mine does not. 

Anybody know if these make a difference? Can someone else with working wireless or non working wireless (3945 preferrably) post the output of lshw -C network

---

### Post by compmodder26 on 2007-08-26
Your firmware version doesn't look right either.  Note, the top  has it as 0.0, but under the live CD it has it as 14.2.  That command under my setup yields the same results as the live CD outputs.

---

### Post by gregbazar on 2007-08-27
Here is my output.  I am running the Intel chipset on an Acer 8210 and can't get wireless to connect.  It sees the access points, but just sits and spins.

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:66:99:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:90200000-90200fff irq:19

I have tried the latest gusty tribe and 7.04 and both have the same problem.

---

### Post by odin1965 on 2007-08-27
> **compmodder26 said:**
> Your firmware version doesn't look right either.  Note, the top  has it as 0.0, but under the live CD it has it as 14.2.  That command under my setup yields the same results as the live CD outputs.

I tried this;

>  Originally Posted by linux23dragon  View Post
Edit: I have an idea !!

First install linux-2.6.20-15 and then copy ipw3945.ucode and pw3945.ko to $(uname -r) like this (you might want to backup those files first):-

sudo cp /lib/firmware/2.6.20-15-generic/ipw3945.ucode /lib/firmware/$(uname -r)/ipw3945.ucode
sudo cp /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko /lib/modules/$(uname -r)/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
depmod -ae

From this post, [http://ubuntuforums.org/showthread.php?t=501195&page=23](http://ubuntuforums.org/showthread.php?t=501195&page=23) and now my output from lshw is like the Acer, but it still does not work.
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:5f:e5:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
```

---

### Post by linux23dragon on 2007-08-31
Just a heads up.

There is a bug report about it [here]("https://bugs.launchpad.net/ubuntu/+bug/134515").

---

### Post by odin1965 on 2007-08-31
> **linux23dragon said:**
> Just a heads up.

There is a bug report about it [here]("https://bugs.launchpad.net/ubuntu/+bug/134515").

I will add my comments and dmesg output on that bug. There are a lot of related bugs so I was relucant to create another, but it seem that what is probably the same bug causes different symptoms for different people. I STILL don't see how my card could have worked originally with the PCLinuxOS live  CD and now it doesn't. A live CD should be unchangeable and  a fresh install every time.

---

### Post by linux23dragon on 2007-08-31
> **odin1965 said:**
> I will add my comments and dmesg output on that bug. There are a lot of related bugs so I was relucant to create another, but it seem that what is probably the same bug causes different symptoms for different people. I STILL don't see how my card could have worked originally with the PCLinuxOS live  CD and now it doesn't. A live CD should be unchangeable and  a fresh install every time.

Mmmm

Would it be the same if you just used any encryption, or no encryption at all ?


UPDATE: I just found this interesting post > **dumbmatter said:**
> like Zorael, i have found that it connects much more reliably with a static IP address.  i'm going to try buying another router and hopefully that will fix the problem.  one of my roommates is having the same problem as me, but he uses vista.  so it's not just us linux guys with wireless problems.

Have a look [here]("http://ubuntuforums.org/showthread.php?t=536932&highlight=dell+1520")

I'm not sure what to think about that.

---

### Post by Zorael on 2007-09-01
I tried it with different permutations of WEP and DHCP toggled on/off, with no difference.

Well, it's certainly more reliable in connecting with DHCP disabled (much faster when it doesn't have to poll the server and retrieve an ip), but when it disconnects - either randomly or when I have to disconnect manually - it requires that reload or reboot to beat it back into shape.

If you found more related bugs (at launchpad), could you post links to them, please? I obviously fail at searching the launchpad. :)

---

### Post by linux23dragon on 2007-09-02
> **Zorael said:**
> I tried it with different permutations of WEP and DHCP toggled on/off, with no difference.

Well, it's certainly more reliable in connecting with DHCP disabled (much faster when it doesn't have to poll the server and retrieve an ip), but when it disconnects - either randomly or when I have to disconnect manually - it requires that reload or reboot to beat it back into shape.

If you found more related bugs (at launchpad), could you post links to them, please? I obviously fail at searching the launchpad. :)

OK :)
[bugs.launchpad.net]("https://bugs.launchpad.net/ubuntu/+bug/134466")
[bugs.launchpad.net]("https://bugs.launchpad.net/ubuntu/+bug/134466")
[url="https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129213]bugs.launchpad.net[/url
[bugs.launchpad.net]("https://bugs.launchpad.net/ipw3945")
[ubuntu-bugs]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg432615.html")
[laptop-testing-team]("http://www.mail-archive.com/laptop-testing-team@lists.ubuntu.com/msg01062.html")
[lists.ubuntu.com]("https://lists.ubuntu.com/archives/kernel-bugs/2007-August/028353.html")
[www.nabble.com]("http://www.nabble.com/Problems-with-ipw3945-t3524122.html")

---

### Post by odin1965 on 2007-09-16
> **linux23dragon said:**
> Just a heads up.

There is a bug report about it [here]("https://bugs.launchpad.net/ubuntu/+bug/134515").

I have posted a separate bug report for this as my symptoms are quite different;
[https://bugs.launchpad.net/ubuntu/+bug/139642](https://bugs.launchpad.net/ubuntu/+bug/139642)

I have posted on the other bug that mine is possibly related, however.

---

