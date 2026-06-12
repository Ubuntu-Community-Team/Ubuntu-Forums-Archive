---
title: "No DHCPOFFERS with Intel Pro Wireless 3945"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by philip_bretton on 2008-01-30
Hi

I just upgraded to Ubuntu 7.10. Before I upgraded my wireless adapter worked fine and I had not problems connecting to networks. Now I cannot connect.

Code:
```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:18:79:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociated

```

Code:
```
:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:18:79:11
Sending on   LPF/eth1/00:13:02:18:79:11
Sending on   Socket/fallback
```

So far all is good.

But then when I try to connect:

Code:
```
~$ sudo iwconfig eth1 essid "MAWUTORNET"
~$ sudo iwconfig eth1 mode managed
~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:18:79:11
Sending on   LPF/eth1/00:13:02:18:79:11
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

If I leave the Wireless adapter on I can look through the log and it simply goes round and round its startup procedure getting to the above point, failing and then starting again - it never manages to actually find the DHCP server.

Now if I plug my cable into the same router I get connected no problems. Also there are 10 other machines in the room all using wireless to connect and if I boot on my XP partition I can use my wireless adapter to connect.

Any ideas?

Thanks

---

### Post by blazercist on 2008-01-30
Why would you do this manually?  Why aren't you using the nm-applet?  I have the same Wireless chipset and I use the nm-applet with no tweaking it works perfectly out of the box.

---

### Post by philip_bretton on 2008-01-30
The only reason I did all that manually was to get the output - normally I do use the nm-applet but this essentially achieves the same thing but its a little more difficult to get the explicit output like you can get manually.

So even with nm-applet when I look in the system logs it just runs around chasing its own tail never finding the DHCP server.

---

### Post by blazercist on 2008-01-30
Ok a few things here.

First thing to do is to make sure all the security/encryption features on the router are turned off and try getting DHCP to work.

I couldn't get my router to give an address via DHCP for a long time for no clear reason and simply reseting my router to factory defaults made everything work.  Give it a try.

Try setting an IP address/gateway manually and see if it works, if so there may be a problem with your router's DHCP settings.

After setting your routers' essid and mode try checking if you have a signal "iwconfig eth1" and post the output.

---

### Post by philip_bretton on 2008-01-30
I can't really go about changing the router unfortunately cause I am in an Internet cafe in Ghana so its probably not a good idea to reset their router for them!! (although I do sometimes manipulate the firewall to stop certain people hogging bandwidth!)

I tried what you said and being as I am sitting 2 feet away from the router the signal strength is pretty good:

Code:
```
~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"MAWUTORNET"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:95:76:52:76   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-29 dBm  Noise level=-30 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:618   Missed beacon:0
```

Still unable to connect though. This is what the syslog has in it:

```

Jan 30 14:01:11 brett-laptop NetworkManager: <debug> [1201701671.073907] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'MAWUTORNET' 
Jan 30 14:01:11 brett-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / MAWUTORNET 
Jan 30 14:01:11 brett-laptop NetworkManager: <info>  Deactivating device eth1. 
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Withdrawing address record for 169.254.2.153 on eth1.
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.2.153.
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 30 14:01:11 brett-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jan 30 14:01:11 brett-laptop NetworkManager: <info>  Deactivating device eth0. 
Jan 30 14:01:11 brett-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6934
Jan 30 14:01:11 brett-laptop dhclient: killed old client process, removed PID file
Jan 30 14:01:11 brett-laptop dhclient: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Withdrawing address record for 192.168.0.100 on eth0.
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.100.
Jan 30 14:01:11 brett-laptop avahi-daemon[5427]: Interface eth0.IPv4 no longer relevant for mDNS.
Jan 30 14:01:12 brett-laptop avahi-daemon[5427]: Withdrawing address record for fe80::217:31ff:fe10:7a6 on eth0.
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) started... 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'MAWUTORNET' is encrypted, but NO valid key exists.  New key needed. 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'MAWUTORNET'. 
Jan 30 14:01:12 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 30 14:01:14 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'MAWUTORNET' received. 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 30 14:01:17 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'MAWUTORNET' is encrypted, and a key exists.  No new key needed. 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant2^I' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was '0' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4d415755544f524e4554' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:01:18 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 30 14:01:19 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Jan 30 14:01:19 brett-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'MAWUTORNET'. 
Jan 30 14:01:19 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 30 14:01:19 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan 30 14:01:19 brett-laptop kernel: [ 5462.756000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 30 14:01:20 brett-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan 30 14:01:20 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 30 14:01:20 brett-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Jan 30 14:01:20 brett-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan 30 14:01:20 brett-laptop avahi-daemon[5427]: Registering new address record for fe80::213:2ff:fe18:7911 on eth1.*.
Jan 30 14:01:20 brett-laptop avahi-autoipd(eth1)[7008]: Got SIGTERM, quitting.
Jan 30 14:01:20 brett-laptop avahi-autoipd(eth1)[7008]: Callout STOP, address 169.254.2.153 on interface eth1
Jan 30 14:01:20 brett-laptop avahi-autoipd(eth1)[7009]: client: RTNETLINK answers: Cannot assign requested address
Jan 30 14:01:20 brett-laptop avahi-autoipd(eth1)[7009]: Script execution failed with return value 2
Jan 30 14:01:21 brett-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jan 30 14:01:25 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jan 30 14:01:29 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 30 14:01:29 brett-laptop kernel: [ 5472.768000] eth1: no IPv6 routers present
Jan 30 14:01:33 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Jan 30 14:01:36 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jan 30 14:01:45 brett-laptop dhclient: No DHCPOFFERS received.
Jan 30 14:01:45 brett-laptop dhclient: No working leases in persistent database - sleeping.
Jan 30 14:01:45 brett-laptop avahi-autoipd(eth1)[7082]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan 30 14:01:45 brett-laptop avahi-autoipd(eth1)[7082]: Successfully called chroot().
Jan 30 14:01:45 brett-laptop avahi-autoipd(eth1)[7082]: Successfully dropped root privileges.
Jan 30 14:01:45 brett-laptop avahi-autoipd(eth1)[7082]: fopen() failed: Permission denied
Jan 30 14:01:45 brett-laptop avahi-autoipd(eth1)[7082]: Starting with address 169.254.2.153
Jan 30 14:01:46 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Jan 30 14:01:50 brett-laptop avahi-autoipd(eth1)[7082]: Callout BIND, address 169.254.2.153 on interface eth1
Jan 30 14:01:50 brett-laptop avahi-daemon[5427]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.2.153.
Jan 30 14:01:50 brett-laptop avahi-daemon[5427]: New relevant interface eth1.IPv4 for mDNS.
Jan 30 14:01:50 brett-laptop avahi-daemon[5427]: Registering new address record for 169.254.2.153 on eth1.IPv4.
Jan 30 14:01:54 brett-laptop avahi-autoipd(eth1)[7082]: Successfully claimed IP address 169.254.2.153
Jan 30 14:01:54 brett-laptop avahi-autoipd(eth1)[7082]: fopen() failed: Permission denied
Jan 30 14:01:56 brett-laptop dhclient: No DHCPOFFERS received.
Jan 30 14:01:56 brett-laptop dhclient: Trying recorded lease 192.168.254.11
Jan 30 14:01:56 brett-laptop avahi-autoipd(eth1)[7082]: A routable address has been configured.
Jan 30 14:01:56 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.2.153.
Jan 30 14:01:56 brett-laptop avahi-autoipd(eth1)[7082]: Callout UNBIND, address 169.254.2.153 on interface eth1
Jan 30 14:01:56 brett-laptop avahi-daemon[5427]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.254.11.
Jan 30 14:01:56 brett-laptop avahi-daemon[5427]: Registering new address record for 192.168.254.11 on eth1.IPv4.
Jan 30 14:01:56 brett-laptop avahi-daemon[5427]: Withdrawing address record for 169.254.2.153 on eth1.
Jan 30 14:01:59 brett-laptop avahi-autoipd(eth1)[7082]: No longer a routable address configured, restarting probe process.
Jan 30 14:01:59 brett-laptop avahi-daemon[5427]: Withdrawing address record for 192.168.254.11 on eth1.
Jan 30 14:01:59 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.254.11.
Jan 30 14:01:59 brett-laptop avahi-daemon[5427]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 30 14:01:59 brett-laptop dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Jan 30 14:01:59 brett-laptop dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface eth1 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jan 30 14:01:59 brett-laptop NetworkManager: <debug> [1201701719.067522] real_act_stage4_ip_config_timeout(): Activation (eth1/wireless): could not get IP configuration info for 'MAWUTORNET', asking for new key. 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'MAWUTORNET'. 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Jan 30 14:01:59 brett-laptop dhcdbd: Unrequested down ?:3
Jan 30 14:01:59 brett-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jan 30 14:02:04 brett-laptop avahi-autoipd(eth1)[7082]: Callout BIND, address 169.254.2.153 on interface eth1
Jan 30 14:02:04 brett-laptop avahi-daemon[5427]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.2.153.
Jan 30 14:02:04 brett-laptop avahi-daemon[5427]: New relevant interface eth1.IPv4 for mDNS.
Jan 30 14:02:04 brett-laptop avahi-daemon[5427]: Registering new address record for 169.254.2.153 on eth1.IPv4.
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'MAWUTORNET' received. 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 30 14:02:07 brett-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'MAWUTORNET' is encrypted, and a key exists.  No new key needed. 
Jan 30 14:02:08 brett-laptop avahi-autoipd(eth1)[7082]: Successfully claimed IP address 169.254.2.153
Jan 30 14:02:08 brett-laptop avahi-autoipd(eth1)[7082]: fopen() failed: Permission denied
Jan 30 14:02:08 brett-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 30 14:02:08 brett-laptop avahi-daemon[5427]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 30 14:02:08 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.2.153.
Jan 30 14:02:08 brett-laptop avahi-autoipd(eth1)[7082]: SIOCSIFFLAGS failed: Permission denied
Jan 30 14:02:08 brett-laptop avahi-autoipd(eth1)[7082]: Callout STOP, address 169.254.2.153 on interface eth1
Jan 30 14:02:08 brett-laptop dhclient: receive_packet failed on eth1: Network is down
Jan 30 14:02:08 brett-laptop avahi-daemon[5427]: Withdrawing address record for fe80::213:2ff:fe18:7911 on eth1.
Jan 30 14:02:08 brett-laptop avahi-daemon[5427]: Withdrawing address record for 169.254.2.153 on eth1.
Jan 30 14:02:08 brett-laptop avahi-autoipd(eth1)[7083]: client: RTNETLINK answers: No such process
Jan 30 14:02:08 brett-laptop NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant3^I' 
Jan 30 14:02:09 brett-laptop kernel: [ 5512.456000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was '0' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4d415755544f524e4554' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jan 30 14:02:09 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 30 14:02:10 brett-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'MAWUTORNET'. 
Jan 30 14:02:10 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 30 14:02:10 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan 30 14:02:10 brett-laptop kernel: [ 5513.792000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 30 14:02:11 brett-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan 30 14:02:11 brett-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 30 14:02:11 brett-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan 30 14:02:12 brett-laptop avahi-daemon[5427]: Registering new address record for fe80::213:2ff:fe18:7911 on eth1.*.
Jan 30 14:02:12 brett-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jan 30 14:02:16 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 30 14:02:21 brett-laptop kernel: [ 5524.704000] eth1: no IPv6 routers present
Jan 30 14:02:23 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jan 30 14:02:35 brett-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jan 30 14:02:47 brett-laptop dhclient: No DHCPOFFERS received.
Jan 30 14:02:47 brett-laptop dhclient: Trying recorded lease 192.168.254.11
Jan 30 14:02:47 brett-laptop avahi-daemon[5427]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.254.11.
Jan 30 14:02:47 brett-laptop avahi-daemon[5427]: New relevant interface eth1.IPv4 for mDNS.
Jan 30 14:02:47 brett-laptop avahi-daemon[5427]: Registering new address record for 192.168.254.11 on eth1.IPv4.
Jan 30 14:02:50 brett-laptop avahi-daemon[5427]: Withdrawing address record for 192.168.254.11 on eth1.
Jan 30 14:02:50 brett-laptop avahi-daemon[5427]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.254.11.
Jan 30 14:02:50 brett-laptop avahi-daemon[5427]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 30 14:02:50 brett-laptop avahi-autoipd(eth1)[7137]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jan 30 14:02:50 brett-laptop avahi-autoipd(eth1)[7137]: Successfully called chroot().
Jan 30 14:02:50 brett-laptop avahi-autoipd(eth1)[7137]: Successfully dropped root privileges.
Jan 30 14:02:50 brett-laptop avahi-autoipd(eth1)[7137]: fopen() failed: Permission denied
Jan 30 14:02:50 brett-laptop avahi-autoipd(eth1)[7137]: Starting with address 169.254.2.153
```

And it just keeps going round the same process again and again until it eventually gives up.

---

### Post by blazercist on 2008-01-30
Did you try setting an IP manually? 

If you can ping the router or some outside site by setting an IP manually then we can narrow this down a bit.

To tell you the truth I'm really surprised this doesn't just work for you... it does for me and I have the same hardware.

---

### Post by philip_bretton on 2008-01-30
OK so I just found a nearby unencrypted wireless and was able to get an IP from the DHCP server no problems (no internet connection on the network though :(

So why does it not see the DHCP server when I go wireless? VERY frustrating!

---

### Post by philip_bretton on 2008-01-30
When I use the network manager to set the IP address and subnet mask then I don't kow how to tell it to connect. The network icon on the toolbar only gives me 2 options :Wired network and Manual configuration...

If I look at iwconfig then it says that there is no signal strength but I don't know how to tell it to connect using the IP and subnet that I have assigned - it just seems to sit doing nothing.

Sorry reaching the ends of my very limited Linux knowledge.

---

### Post by philip_bretton on 2008-01-30
Ignore the last - just got it to work using static IP but only connecting to the other network. It will not connect to the encrypted network with a static IP even though the network has full strength in the Network Name drop down box. I can set it all up but when I do iwconfig it comes back as being not associated. 

Do the same thing with the unencrypted network and it connects fine.

---

### Post by blazercist on 2008-01-30
ok you do what you've been doing 

sudo iwconfig eth1 essid "MAWUTORNET"
sudo iwconfig eth1 mode managed
_sudo route add default gw 192.168.0.1  (OR WHATEVER THE GATEWAY ADDRESS IS)_


Then just set the ip and subnet and try to ping google.com

---

### Post by philip_bretton on 2008-01-30
I can do all the settings of the IP and netmask and then issue 

```
sudo ifconfig eth1 down
sudo ifconfig eth1 inet 192.168.0.150 netmask 255.255.255.0
sudo iwconfig eth1 essid "MAWUTORNET"
 sudo iwconfig eth1 mode managed
sudo ifconfig eth1 up
```

and everything looks fine but if I do iwconfig I get this:
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"MAWUTORNET"  
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:5   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1536   Missed beacon:0
```

Its just not associating with the network at all so no chance of getting through to the gateway and route won't set the default gateway if it cannot contact the gateway.

---

### Post by philip_bretton on 2008-01-30
I updated the firmware on the router in case that was the problem (caused a little disruption in the cafe, but hey)

so now I get this:
```
brett@brett-laptop:~$ sudo ifconfig eth0 down
brett@brett-laptop:~$ sudo ifconfig eth1 down
brett@brett-laptop:~$ sudo ifconfig eth1 inet 192.168.0.150 netmask 255.255.255.0
brett@brett-laptop:~$ sudo iwconfig eth1 essid "MAWUTORNET"
brett@brett-laptop:~$ sudo iwconfig eth1 mode managed
brett@brett-laptop:~$ sudo ifconfig eth1 up
brett@brett-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:10:07:A6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22801061 (21.7 MB)  TX bytes:4573942 (4.3 MB)
          Interrupt:22 Base address:0xe400 

eth1      Link encap:Ethernet  HWaddr 00:13:02:18:79:11  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe18:7911/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:691 dropped:2567 overruns:0 frame:0
          TX packets:0 errors:0 dropped:37 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:351894 (343.6 KB)  TX bytes:220764 (215.5 KB)
          Interrupt:17 Memory:fe7ff000-fe7fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:347 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37104 (36.2 KB)  TX bytes:37104 (36.2 KB)

brett@brett-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"MAWUTORNET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:76:52:76   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:5   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-27 dBm  Noise level=-28 dBm
          Rx invalid nwid:0  Rx invalid crypt:13  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1776   Missed beacon:0

brett@brett-laptop:~$ 

```

So it looks to me like the wireless is actually connected at some level but I can't even ping the router :
```
:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
From 192.168.0.100 icmp_seq=4 Destination Host Unreachable
From 192.168.0.100 icmp_seq=5 Destination Host Unreachable
From 192.168.0.100 icmp_seq=8 Destination Host Unreachable
From 192.168.0.100 icmp_seq=9 Destination Host Unreachable

```

---

### Post by blazercist on 2008-01-30
Wow, I'm totally out of ideas... Good luck with this... I would advise you to just goto a different cafe since its not worth the hassle.

---

### Post by philip_bretton on 2008-01-30
except that this cafe doesn't charge me and being a volunteer I just don't have the money to spend on internet.

---

### Post by philip_bretton on 2008-01-30
Hey I tried this and it worked in getting me connected but still can't get connected through the UI - any ideas why this is different?
```

brett@brett-laptop:~$ sudo iwconfig eth1 mode managed key feed082007
brett@brett-laptop:~$ sudo iwconfig eth1 essid "MAWUTORNET"
brett@brett-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 13673
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:18:79:11
Sending on   LPF/eth1/00:13:02:18:79:11
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.110 -- renewal in 265765 seconds.
brett@brett-laptop:~$ ping www.bbc.co.uk
PING www.bbc.net.uk (212.58.253.75) 56(84) bytes of data.
64 bytes from www6.cwwtf.bbc.co.uk (212.58.253.75): icmp_seq=1 ttl=244 time=240 ms
64 bytes from www6.cwwtf.bbc.co.uk (212.58.253.75): icmp_seq=2 ttl=244 time=210 ms

```

---

### Post by blazercist on 2008-02-04
Lol duh because you entered a key the network was secured no wonder you couldn't get an address via DHCP.

---

### Post by RyanJSull on 2008-02-05
I think I'm havin a similar problem here... got an Intel Pro Wireless 3945, and network manager will not connect to a WEP encrypted network, even with the correct key.

Network manager will connect to an unencrypted network, although I could not get it to work in terminal (maybee i was typing something wrong, i'm new to ubuntu).  It would always fail at dhclient, and it would not obtain an ip.  Network Manager just changed it to the unencrypted network after a while.  The problem is that I am at a University right now, and the WEP encrypted network is free for students, while the unecrypted network they make you pay for.  I have a router in my room, and Network manager can connect fine so long as it is unencrypted... but i would like to have wireless everywhere on campus.

It isn't the card... it works fine on vista.

---

### Post by philip_bretton on 2008-02-17
Hi

Thanks Blazercist for your help (and sorry about the long delay but I have been up-country where I am lucky to get electricity let alone internet!)

I have managed to resolve the problem - not entirely sure how but I was just trying loads of different things and now it works. But essentially I think that it is to do with the way the WEP key was entered, ASCII vs. HEX etc. 

Regards

Brett

---

### Post by tommohawk on 2008-02-17
> **philip_bretton said:**
> Hi

Thanks Blazercist for your help (and sorry about the long delay but I have been up-country where I am lucky to get electricity let alone internet!)

I have managed to resolve the problem - not entirely sure how but I was just trying loads of different things and now it works. But essentially I think that it is to do with the way the WEP key was entered, ASCII vs. HEX etc. 

Regards

Brett

Interesting because I have a similar problem with the same version of ubuntu and the same wireless chipset.  I have always tried to use network manager but sometimes I have had to revert to setting my connection manually.  My connection works fine on the rare occasions that I boot into windows but in linux I have random connection drops and sometimes it will just refuse to connect until I have entered the WPA key about 20 times.

It's not the router, it's not the network setup or a hardware problem.  There is something going on within ubuntu that is causing a problem.

Any suggestions?

---

### Post by blazercist on 2008-02-21
I use the same version of ubuntu and have the same chipset... I have never had a problem with my wireless connection and I use WEP at home and an open network at school.  nm-applet has done the job out of the box perfectly since I installed ubuntu with no tweaking...  I have no idea what could be causing your problems.  If has to be some odd configuration on either your router and your manual botching of the network interface configuration.  Good luck with this.

---

