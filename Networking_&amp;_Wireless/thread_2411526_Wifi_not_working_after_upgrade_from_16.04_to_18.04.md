---
title: "Wifi not working after upgrade from 16.04 to 18.04"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by B99 on 2019-01-31
Hi!

I have a FriendlyArm NanoPi A64.  I flashed the Ubuntu 16.04 image that the Friendly provided and upgraded to 18.04.  Wifi is not working.  For some reason netplan was not installed as far as I can tell. 

[http://paste.ubuntu.com/p/rVb8v9cnJv/](http://paste.ubuntu.com/p/rVb8v9cnJv/)

Thanks!

---

### Post by Autodave on 2019-01-31
Upgrading often causes issues like this.  My suggestion would be to download the 18.04 image that you want to use, burn it as an .iso file to either DVD or thumb drive, and do a clean install.

---

### Post by B99 on 2019-01-31
This is a small SBC with only a 16.04 image available from the manufacturer and unfortunately compiling my own custom image is beyond my skill set at the moment.

---

### Post by B99 on 2019-02-06
I took Autodave's advice and found an 18.04 image that booted my NanoPi.  It has two wifi interfaces wlan0 and wlan1. After setting up netplan, wlan1 works and wlan0 does not.   Syslog is full of wlan0 related errors. 

Here are the results of the wireless script:

[http://paste.ubuntu.com/p/YQkSMMrKTv/](http://paste.ubuntu.com/p/YQkSMMrKTv/)

Thanks!

ETA: The script doesn't redact SSIDS and passwords from netplan.  Doesn't concern me much but should probably be fixed.

---

### Post by B99 on 2019-02-06
There's a lot in syslog that the script didn't seem to pick up.  Here's  sample:

```
Feb  6 18:55:35 nanopi-a64 systemd[1]: Stopped Network Name Resolution.Feb  6 18:55:35 nanopi-a64 systemd[1]: Starting Network Name Resolution...
Feb  6 18:55:35 nanopi-a64 systemd-resolved[3840]: Positive Trust Anchors:
Feb  6 18:55:35 nanopi-a64 systemd-resolved[3840]: . IN DS 19036 8 2 49aac11d7b6f6446702e54a1607371607a1a41855200fd2ce1cdde32f24e8fb5
Feb  6 18:55:35 nanopi-a64 systemd-resolved[3840]: . IN DS 20326 8 2 e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d
Feb  6 18:55:35 nanopi-a64 systemd-resolved[3840]: Negative trust anchors: 10.in-addr.arpa 16.172.in-addr.arpa 17.172.in-addr.arpa 18.172.in-addr.arpa 19.172.in-addr.arpa 20.172.in-addr.arpa 21.172.in-addr.arpa 22.172.in-addr.arpa 23.172.in-addr.arpa 24.172.in-addr.arpa 25.172.in-addr.arpa 26.172.in-addr.arpa 27.172.in-addr.arpa 28.172.in-addr.arpa 29.172.in-addr.arpa 30.172.in-addr.arpa 31.172.in-addr.arpa 168.192.in-addr.arpa d.f.ip6.arpa corp home internal intranet lan local private test
Feb  6 18:55:35 nanopi-a64 systemd-resolved[3840]: Using system hostname 'nanopi-a64'.
Feb  6 18:55:35 nanopi-a64 systemd[1]: Started Network Name Resolution.
Feb  6 18:57:21 nanopi-a64 kernel: [15088.454757] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45482 PROTO=2
Feb  6 18:57:25 nanopi-a64 systemd-resolved[3840]: Address 'sudo' is invalid, in line /etc/hosts:1.
Feb  6 18:57:25 nanopi-a64 systemd-resolved[3840]: Address 'change/add' is invalid, in line /etc/hosts:2.
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[3363]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="Cellcom-WiFi_2.4"
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[3363]: wlan0: Trying to associate with 10:5a:f7:05:f1:41 (SSID='Cellcom-WiFi_2.4' freq=2462 MHz)
Feb  6 18:58:20 nanopi-a64 kernel: [15147.160464] RTL871X: rtw_set_802_11_connect(wlan0)  fw_state=0x00000008
Feb  6 18:58:20 nanopi-a64 kernel: [15147.244404] RTL871X: start auth
Feb  6 18:58:20 nanopi-a64 kernel: [15147.245456] RTL871X: auth success, start assoc
Feb  6 18:58:20 nanopi-a64 kernel: [15147.246920] RTL871X: rtw_cfg80211_indicate_connect(wlan0) BSS not found !!
Feb  6 18:58:20 nanopi-a64 kernel: [15147.246958] RTL871X: assoc success
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[2529]: wlan0: No network configuration found for the current AP
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[3363]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[3363]: wlan0: Associated with 10:5a:f7:05:f1:41
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[3363]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[2529]: wlan0: CTRL-EVENT-DISCONNECTED bssid=10:5a:f7:05:f1:41 reason=3 locally_generated=1
Feb  6 18:58:20 nanopi-a64 wpa_supplicant[2529]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Feb  6 18:58:30 nanopi-a64 wpa_supplicant[3363]: wlan0: Authentication with 10:5a:f7:05:f1:41 timed out.
Feb  6 18:58:30 nanopi-a64 wpa_supplicant[3363]: wlan0: CTRL-EVENT-DISCONNECTED bssid=10:5a:f7:05:f1:41 reason=3 locally_generated=1
Feb  6 18:58:30 nanopi-a64 wpa_supplicant[3363]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Cellcom-WiFi_2.4" auth_failures=59 duration=860 reason=CONN_FAILED
Feb  6 18:59:27 nanopi-a64 kernel: [15214.460787] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45483 PROTO=2
Feb  6 19:01:33 nanopi-a64 kernel: [15340.492706] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45484 PROTO=2
Feb  6 19:02:59 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x8e856f42)
Feb  6 19:03:02 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x8e856f42)
Feb  6 19:03:08 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x8e856f42)
Feb  6 19:03:15 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x8e856f42)Feb  6 19:03:30 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x8e856f42)Feb  6 19:03:38 nanopi-a64 kernel: [15465.595090] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45485 PROTO=2
Feb  6 19:03:42 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x8e856f42)Feb  6 19:04:01 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x8e856f42)
Feb  6 19:04:09 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x8e856f42)Feb  6 19:04:29 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x8e856f42)
Feb  6 19:04:38 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x8e856f42)Feb  6 19:04:51 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x8e856f42)Feb  6 19:05:06 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x8e856f42)
Feb  6 19:05:14 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x8e856f42)Feb  6 19:05:34 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x8e856f42)Feb  6 19:05:43 nanopi-a64 kernel: [15590.500804] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45486 PROTO=2
Feb  6 19:05:52 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x8e856f42)Feb  6 19:06:10 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x8e856f42)Feb  6 19:06:29 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x8e856f42)Feb  6 19:06:42 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x8e856f42)Feb  6 19:07:03 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x8e856f42)Feb  6 19:07:21 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x8e856f42)Feb  6 19:07:32 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x8e856f42)Feb  6 19:07:48 nanopi-a64 kernel: [15715.509543] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:10:5a:f7:05:f1:43:08:00 SRC=10.100.102.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45487 PROTO=2
Feb  6 19:07:49 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x8e856f42)
Feb  6 19:07:56 nanopi-a64 dhclient[2761]: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 (xid=0x8e856f42)
Feb  6 19:08:00 nanopi-a64 dhclient[2761]: No DHCPOFFERS received.
Feb  6 19:08:00 nanopi-a64 dhclient[2761]: No working leases in persistent database - sleeping.
Feb  6 19:08:01 nanopi-a64 systemd[1]: Stopping Network Name Resolution...
Feb  6 19:08:01 nanopi-a64 systemd[1]: Stopped Network Name Resolution.
Feb  6 19:08:01 nanopi-a64 systemd[1]: Starting Network Name Resolution...
Feb  6 19:08:01 nanopi-a64 systemd-resolved[4081]: Positive Trust Anchors:
Feb  6 19:08:01 nanopi-a64 systemd-resolved[4081]: . IN DS 19036 8 2 49aac11d7b6f6446702e54a1607371607a1a41855200fd2ce1cdde32f24e8fb5
Feb  6 19:08:01 nanopi-a64 systemd-resolved[4081]: . IN DS 20326 8 2 e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d

```

---

### Post by akocak2 on 2019-02-06
"lspci -vnn | grep Network"      showed 
then apt-get install  'showed-module'

---

### Post by B99 on 2019-02-07
> **akocak2 said:**
> [COLOR=#242729][FONT=Consolas]"lspci -vnn | grep Network"      showed 
then apt-get install  'showed-module'[/FONT][/COLOR]


Sorry, I'm not understanding. 

And I for $ lspic

I get -bash: lspci: command not found

---

### Post by B99 on 2019-02-10
Is there something wrong with the way I asked this question that I'm not getting much in the way of help?  Should I have started a new thread now that my problem doesn't fit the title?

---

