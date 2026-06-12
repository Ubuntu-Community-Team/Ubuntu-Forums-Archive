---
title: "Wireless disconnect after a while"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by akutae on 2007-12-09
I'm using Gutsy, D-Link DWA 130 USB wireless network card with ndiswrapper driver. When i first installed Gutsy, everything worked great. I had very good connection and speed. But after 1 week, my wireless connection kept crashing. I use the word "crash" because i can't ping anywhere, but the nm-applet still shows that i'm connected to my router. The annoying thing is I can't reconnect to any router after it crashes too, and only a fresh reboot can fix it. But that only works for another 10 mins or so, then the same thing happens again. I notice that it crashes when i download something heavy.

For diagnose purpose, i attach the stats i observe

Here is my ifconfig at the time it crashes

```

eth0      Link encap:Ethernet  HWaddr 00:19:D1:9A:D1:7A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6094 (5.9 KB)  TX bytes:6094 (5.9 KB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.215.1  Bcast:192.168.215.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:64:50:D6  
          inet addr:192.168.10.100  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23775092 (22.6 MB)  TX bytes:1771447 (1.6 MB)

```

I keep a ping to [www.google.com](www.google.com) to check my connection. And at the time it crashes, i got this

```
.......
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=182 ttl=238 time=76.0 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=183 ttl=238 time=103 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=184 ttl=238 time=64.0 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=185 ttl=238 time=91.9 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=186 ttl=238 time=93.2 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=187 ttl=238 time=60.0 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
.....
```

I googled for "no buffer space available" but found no solution. I tried to disable ipv6 as someone suggested but still no good.

After it crashes, i try to reconnect to my router, it can never connect, here is the daemon.log

```
Dec  9 03:26:11  NetworkManager: <debug> [1197188771.708229] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '(edited: my ssid)' 
Dec  9 03:26:11  NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / (edited: my ssid) 
Dec  9 03:26:11  NetworkManager: <info>  Deactivating device wlan0. 
Dec  9 03:26:11  dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6953
Dec  9 03:26:11  dhclient: killed old client process, removed PID file
Dec  9 03:26:11  dhclient: DHCPRELEASE on wlan0 to 192.168.10.1 port 67
Dec  9 03:26:11  avahi-daemon[6279]: Withdrawing address record for 192.168.10.100 on wlan0.
Dec  9 03:26:11  avahi-daemon[6279]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.10.100.
Dec  9 03:26:11  avahi-daemon[6279]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  9 03:26:15  NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Dec  9 03:26:15  NetworkManager: <info>  Device wlan0 activation scheduled... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) started... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0/wireless): access point '(edited: my ssid)' is encrypted, but NO valid key exists.  New key needed. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network '(edited: my ssid)'. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) New wireless user key for network '(edited: my ssid)' received. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  9 03:26:15  NetworkManager: <info>  Activation (wlan0/wireless): access point '(edited: my ssid)' is encrypted, and a key exists.  No new key needed. 
Dec  9 03:26:16  NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Dec  9 03:26:16  NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Dec  9 03:26:16  NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant6^I' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was '0' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4d65656b6572' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  9 03:26:19  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:26:19  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  9 03:26:21  ntpd[6245]: sendto(91.189.94.4) (fd=18): Invalid argument
Dec  9 03:26:23  NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '(edited: my ssid)'. 
Dec  9 03:26:23  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  9 03:26:23  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Dec  9 03:26:24  NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Dec  9 03:26:24  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Dec  9 03:26:24  NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Dec  9 03:26:24  dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Dec  9 03:26:25  NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Dec  9 03:26:27  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec  9 03:26:33  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Dec  9 03:26:46  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Dec  9 03:26:56  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Dec  9 03:26:58  dhclient: No DHCPOFFERS received.
Dec  9 03:26:58  avahi-autoipd(wlan0)[7897]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Dec  9 03:26:58  avahi-autoipd(wlan0)[7897]: Successfully called chroot().
Dec  9 03:26:58  avahi-autoipd(wlan0)[7897]: Successfully dropped root privileges.
Dec  9 03:26:58  avahi-autoipd(wlan0)[7897]: Starting with address 169.254.6.216
Dec  9 03:27:03  avahi-autoipd(wlan0)[7897]: Callout BIND, address 169.254.6.216 on interface wlan0
Dec  9 03:27:03  avahi-daemon[6279]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.216.
Dec  9 03:27:03  avahi-daemon[6279]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 03:27:03  avahi-daemon[6279]: Registering new address record for 169.254.6.216 on wlan0.IPv4.
Dec  9 03:27:07  avahi-autoipd(wlan0)[7897]: Successfully claimed IP address 169.254.6.216
Dec  9 03:27:07  NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Dec  9 03:27:26  ntpd[6245]: sendto(91.189.94.4) (fd=18): Invalid argument
```

after this point, nm-applet will ask me for my WEP key (it shouldn't have asked me, it has the key, i never have to enter my WEP key on a fresh boot, only after crashes). After i re-enter my WEP key, things still don't work

```
Dec  9 03:28:03  NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>99s), stopping it. 
Dec  9 03:28:03  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Dec  9 03:28:03  NetworkManager: <debug> [1197188883.538496] real_act_stage4_ip_config_timeout(): Activation (wlan0/wireless): could not get IP configuration info for '(edited: my ssid)', asking for new key. 
Dec  9 03:28:03  NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network '(edited: my ssid)'. 
Dec  9 03:28:03  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Dec  9 03:28:03  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Dec  9 03:28:29  ntpd[6245]: sendto(91.189.94.4) (fd=18): Invalid argument
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) New wireless user key for network '(edited: my ssid)' received. 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec  9 03:28:30  NetworkManager: <info>  Activation (wlan0/wireless): access point '(edited: my ssid)' is encrypted, and a key exists.  No new key needed. 
Dec  9 03:28:31  NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Dec  9 03:28:31  NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Dec  9 03:28:31  NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant7^I' 
Dec  9 03:28:35  avahi-daemon[6279]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  9 03:28:35  avahi-daemon[6279]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.216.
Dec  9 03:28:35  avahi-autoipd(wlan0)[7897]: SIOCSIFFLAGS failed: Permission denied
Dec  9 03:28:35  avahi-autoipd(wlan0)[7897]: Callout STOP, address 169.254.6.216 on interface wlan0
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Dec  9 03:28:35  avahi-daemon[6279]: Withdrawing address record for 169.254.6.216 on wlan0.
Dec  9 03:28:35  avahi-autoipd(wlan0)[7898]: client: RTNETLINK answers: No such process
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was '0' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4d65656b6572' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Dec  9 03:28:35  NetworkManager: <info>  SUP: response was 'OK' 
Dec  9 03:28:35  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec  9 03:28:40  NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point '(edited: my ssid)'. 
Dec  9 03:28:40  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec  9 03:28:40  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Dec  9 03:28:41  NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Dec  9 03:28:41  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Dec  9 03:28:41  NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Dec  9 03:28:42  NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Dec  9 03:28:44  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec  9 03:28:50  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Dec  9 03:28:58  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Dec  9 03:29:06  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Dec  9 03:29:15  dhclient: No DHCPOFFERS received.
Dec  9 03:29:15  avahi-autoipd(wlan0)[7951]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Dec  9 03:29:15  avahi-autoipd(wlan0)[7951]: Successfully called chroot().
Dec  9 03:29:15  avahi-autoipd(wlan0)[7951]: Successfully dropped root privileges.
Dec  9 03:29:15  avahi-autoipd(wlan0)[7951]: Starting with address 169.254.6.216
Dec  9 03:29:20  avahi-autoipd(wlan0)[7951]: Callout BIND, address 169.254.6.216 on interface wlan0
Dec  9 03:29:20  avahi-daemon[6279]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.6.216.
Dec  9 03:29:20  avahi-daemon[6279]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 03:29:20  avahi-daemon[6279]: Registering new address record for 169.254.6.216 on wlan0.IPv4.
Dec  9 03:29:24  avahi-autoipd(wlan0)[7951]: Successfully claimed IP address 169.254.6.216
Dec  9 03:29:24  NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface wlan0 
Dec  9 03:29:24  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Dec  9 03:29:24  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Dec  9 03:29:24  NetworkManager: <debug> [1197188964.851199] real_act_stage4_ip_config_timeout(): Activation (wlan0/wireless): could not get IP configuration info for '(edited: my ssid)', asking for new key. 
Dec  9 03:29:24  NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network '(edited: my ssid)'. 
Dec  9 03:29:24  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Dec  9 03:29:24  NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Dec  9 03:29:33  ntpd[6245]: sendto(91.189.94.4) (fd=18): Invalid argument
```

I tried restarting networkmanager and ndiswrapper using the following script
```
iwpriv wlan0 ndis_reset
/etc/dbus-1/event.d/25NetworkManager restart
```
but that didn't fix anything. Only a fresh reboot fixes it. However, even worse, sometimes i can soft-reboot my machine, it just stops at "Restarting computer..." something forever. Before the restarting message is the some error from network manager
```
NetworkManager: nm_dbus_signal_state_change: assertion `connection != NULL` failed
NetworkManager: nm_dbus_signal_state_change: assertion `cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_state_change: assertion `cb_data->data->dbus_connection' failed
```
I tried googling this and found out many people also got the same problem here
[http://ubuntuforums.org/showthread.php?t=603054](http://ubuntuforums.org/showthread.php?t=603054)
but no one got any solution.

It's been like this for a week now. I've never been able to use internet for more than 10 mins. I've tried all i can and google and such, but no hope. Any help would be really appreciated. At least if there is anyway to reset things without having to reboot my computer (rebooting 10+ times a day is not fun :(). Thanks a lot in advance.

Btw, i use gutsy, ndiswrapper 1.50 and latest windows driver from dlink. I have a windows dual boot, and it worked great in windows, so should not be hardware or router problem.

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by akutae on 2007-12-09
Bump

---

### Post by eriksallstrom on 2007-12-09
This is a longshot, but do you use multisync for bluetooth? I got serious troubles with my wireless and finally found out it was because of multisync. After I stopped using it, everything worked fine!

---

### Post by akutae on 2007-12-09
Thanks for the reply, but i don't use any bluetooth device...guess it's not the case then?

---

### Post by eriksallstrom on 2007-12-10
I guess not... so I guess you either have to start thinking about what you may have changed in you computer that may have corrupted your wifi or wait for someone who knows more than me to post a reply. sorry I couldn't help more.

---

### Post by kevdog on 2007-12-10
What does iwlist scan show?

---

### Post by eriksallstrom on 2007-12-10
run
sudo iwlist eth1 scan 
instead (replace eth1 with the name of you're wireless name if it's not the same) and it will list the wireless networks in range. Sometimes you have to run it several times to get all of them.

---

### Post by eriksallstrom on 2007-12-10
What is vmnet8 and what do you get if you run
route -n

---

### Post by akutae on 2007-12-10
Thanks for all the replies. vmnet8 is a NAT interface for vmware virtual machine. I've tried removing it, but still got the same problem. I couldn't recall installing anything special, i did go through my .bash_history for all those that i installed manually, but found nothing suspicious. Other than that, the only changes to my system should be from the automatic system update.

Here are some additional information as requested

```

$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:64:D3:08
                    **<<<< this is my router >>>>**
                    ESSID:"(edited: my ssid)"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0
          Cell 02 - Address: 00:14:A4:81:FB:2A
                    ESSID:"52b9"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:14:51:75:5A:BD
                    ESSID:"W180"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:6C:98:7A:BC
                    ESSID:"MONSTER"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:1B:2F:4B:88:5E
                    ESSID:"ACE212"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:14:BF:C3:F5:82
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:18:4D:86:52:44
                    ESSID:"Ho-house"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-97 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:12:0E:3C:15:19
                    ESSID:"06B403523563"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 09 - Address: 00:12:0E:59:42:58
                    ESSID:"06B411793264"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

```

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 wlan0

```

---

### Post by akutae on 2007-12-10
Bump

---

### Post by akutae on 2007-12-11
I think i've found the solution. The problem has gone after i removed lm-sensors. Still have no clue why lm-sensors affect my wireless connection though......

---

### Post by thk on 2007-12-11
Out of curiosity, have you installed any updates from the "proposed" repository? What happens if you revert?

I've noticed network manager acting strange the last couple of weeks. It worked much better in the past. I'm wondering if it isn't recent updates to network manager or restricted modules.

What I've noticed is that nm-applet churns and no connection comes up (despite my siting 6 ft from the router). It then begins asking for the passkey which I supply but does not work. I just went through a manual configuration of the interface and it works fine so clearly the issue is with network manager. One thing I just noticed is that once the passkey dialog pops up, nm-applet has already moved on and is trying to connect to one of many unsecured wifi signals nearby. That would appear to be some sort of race condition.

It is a shame to see something working become broken. Maybe I'll ditch the "proposed updates" option.

---

### Post by kevdog on 2007-12-11
Glad you found a solution, cant say I would have guessed the lm-sensor thing.

---

### Post by andresv on 2007-12-14
> **akutae said:**
> I think i've found the solution. The problem has gone after i removed lm-sensors. Still have no clue why lm-sensors affect my wireless connection though......

This is extremely strange. A problem very similar to yours started happening in my own ubuntu gutsy system (although I got about one hour of connection, not ten minutes). The outcomes of iwlist, iwconfig commands, etc. looked very similar).

Thanks for sharing the solution. Yet, lm-sensors is not installed in my computer ... ?

I wonder if this has to do with any of the recent ubuntu gutsy updates. It was not happening until about two weeks ago.

:confused:

---

### Post by johnnywellas on 2007-12-17
I'm having similar issues. I suppose that maybe forcing all the wireless interface parameters in the interfaces file could do some good, the trouble is that i just can't seem to find information on how to enter those parameters. You know, like my acess point mac and essid, the transmission rate, etc,

Any help is warmly welcome!

---

### Post by motin on 2008-01-08
EDIT: Sorry - though I was posting a new topic - not a reply. So here is the new topic: [http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4179566#post4179566](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4179566#post4179566)

---

### Post by sidefx2 on 2008-04-02
I'm having this problem two, it's only been recently that it has been an issue which leads me to believe it is an update problem as well.  Has anyone figured out if this is the case, and is there a way to remove a particular update to get wireless back to normal again?

---

