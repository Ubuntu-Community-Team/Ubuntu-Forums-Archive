---
title: "Restart WiFi without rebooting Ubuntu?"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by desconocido on 2008-09-07
Hello,

I have a Gateway ml6226b laptop with 1 GigaByte of RAM and a Celeron processor. I installed Ubuntu 8.04 (Hardy Heron), Kernel 2.6.24-19-generic.
Just installed from the CD and it all works fine so far.

One problem with WiFi though.
Here is some info: it seems to be a USB WiFi thing, even though it's hidden inside the case.

```
$ lsusb
Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
```

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c5:fa:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:a8:e1:49:c7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11g
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"3Com"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:7C:4F:FA:7C   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=60/64  Signal level=37/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I have tried it on a variety of networks and a lot of the time it works fine. However if anything does go wrong, like out of range, someone turns the router off, I don't get the password for WPA right, or as in this case, the router is having problems with DHCP etc, I get the sort of problem shown in the following output. Once I get to the stage where it is saying "NetworkManager: <info>  Old device 'wlan0' activating, won't change." there is no way back. I have to reboot the computer to get WiFi working again. By the way, is that verb "won't" present tense or future tense?

[B]My question is: is there a command to quickly turn the WiFi off and on again so as to avoid rebooting; or a configuration file I could edit so that I would not need to reboot?
[/B]

Here is the output (not always exactly like this, it usually does not go into "NetworkManager: [Thread debugging using libthread_db enabled]").

```
Sep  4 09:42:55 faustino dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.1.1 port 67
Sep  4 09:42:55 faustino dhclient: DHCPACK of 192.168.1.3 from 192.168.1.1
Sep  4 09:42:55 faustino NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface wlan0 

```[.....]
```
Sep  4 10:07:11 faustino dhclient: bound to 192.168.1.3 -- renewal in 729 seconds.
Sep  4 10:17:01 faustino /USR/SBIN/CRON[6865]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  4 10:19:20 faustino dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.1.1 port 67
Sep  4 10:19:49 faustino last message repeated 3 times
Sep  4 10:20:48 faustino last message repeated 4 times
Sep  4 10:22:03 faustino last message repeated 5 times
Sep  4 10:23:12 faustino last message repeated 5 times
Sep  4 10:24:02 faustino last message repeated 4 times
Sep  4 10:24:14 faustino kernel: [ 4157.902783] wlan0: RX deauthentication from 00:14:7c:4f:fa:7c (reason=2)
Sep  4 10:24:14 faustino kernel: [ 4157.902789] wlan0: deauthenticated
Sep  4 10:24:14 faustino NetworkManager: <info>  Supplicant state changed: 0 
Sep  4 10:24:15 faustino kernel: [ 4158.901001] wlan0: authenticate with AP 00:14:7c:4f:fa:7c
Sep  4 10:24:15 faustino kernel: [ 4159.100864] wlan0: authenticate with AP 00:14:7c:4f:fa:7c
Sep  4 10:24:15 faustino kernel: [ 4159.300731] wlan0: authenticate with AP 00:14:7c:4f:fa:7c
Sep  4 10:24:15 faustino kernel: [ 4159.500583] wlan0: authentication with AP 00:14:7c:4f:fa:7c timed out
Sep  4 10:24:19 faustino dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.1.1 port 67
Sep  4 10:24:29 faustino dhclient: DHCPREQUEST of <null address> on wlan0 to 192.168.1.1 port 67
Sep  4 10:24:34 faustino NetworkManager: <info>  wlan0: link timed out. 
Sep  4 10:24:34 faustino NetworkManager: <info>  SWITCH: found better connection 'wlan0/3Com' than current connection 'wlan0/3Com'.  same_ssid=1, have_link=0 
Sep  4 10:24:34 faustino NetworkManager: <info>  Will activate connection 'wlan0/3Com'. 
Sep  4 10:24:34 faustino NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep  4 10:24:34 faustino NetworkManager: <info>  Deactivating device wlan0. 
Sep  4 10:24:34 faustino dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 5884
Sep  4 10:24:34 faustino dhclient: killed old client process, removed PID file
Sep  4 10:24:34 faustino dhclient: wmaster0: unknown hardware address type 801
Sep  4 10:24:34 faustino dhclient: wmaster0: unknown hardware address type 801
Sep  4 10:24:34 faustino dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Sep  4 10:24:34 faustino avahi-daemon[4939]: Withdrawing address record for 192.168.1.3 on wlan0.
Sep  4 10:24:34 faustino avahi-daemon[4939]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Sep  4 10:24:34 faustino avahi-daemon[4939]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep  4 10:24:35 faustino avahi-daemon[4939]: Withdrawing address record for fe80::2c0:a8ff:fee1:49c7 on wlan0.
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) started... 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  4 10:24:35 faustino NetworkManager: <info>  Activation (wlan0/wireless): access point '3Com' is unencrypted, no key needed. 
Sep  4 10:24:35 faustino NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Sep  4 10:24:35 faustino NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan0 
Sep  4 10:24:35 faustino NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Sep  4 10:24:36 faustino NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Sep  4 10:24:36 faustino NetworkManager: <info>  SUP: response was 'OK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: response was 'OK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: response was '0' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 33436f6d' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: response was 'OK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: response was 'OK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep  4 10:24:37 faustino NetworkManager: <info>  SUP: response was 'OK' 
Sep  4 10:24:37 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  4 10:24:39 faustino NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  4 10:25:16 faustino last message repeated 5 times
Sep  4 10:25:31 faustino last message repeated 2 times
Sep  4 10:25:37 faustino NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Sep  4 10:25:37 faustino NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Sep  4 10:25:37 faustino NetworkManager: <info>  Activation (wlan0) failed for access point (3Com) 
Sep  4 10:25:37 faustino NetworkManager: <info>  Activation (wlan0) failed. 
Sep  4 10:25:37 faustino NetworkManager: <info>  Deactivating device wlan0. 
```
[.....]
```
Sep  4 12:45:47 faustino NetworkManager: <info>  User request to disable wireless. 
Sep  4 12:45:47 faustino NetworkManager: <info>  Deactivating device wlan0. 
Sep  4 12:45:58 faustino NetworkManager: <info>  User request to enable wireless. 
Sep  4 12:46:21 faustino kernel: [12678.637995] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  4 12:48:53 faustino NetworkManager: <debug> [1220528933.592220] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '3Com' 
Sep  4 12:48:53 faustino NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / 3Com 
Sep  4 12:48:53 faustino NetworkManager: <info>  Deactivating device wlan0. 
Sep  4 12:48:53 faustino NetworkManager: <info>  Device wlan0 activation scheduled... 

```[.....]
```
Sep  4 12:51:49 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  4 12:51:56 faustino NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  4 12:52:28 faustino last message repeated 4 times
Sep  4 12:52:43 faustino last message repeated 2 times
Sep  4 12:52:49 faustino NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Sep  4 12:52:49 faustino NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Sep  4 12:52:49 faustino NetworkManager: <info>  Activation (wlan0) failed for access point (3Com) 
Sep  4 12:52:49 faustino NetworkManager: <info>  Activation (wlan0) failed. 
Sep  4 12:52:49 faustino NetworkManager: <info>  Deactivating device wlan0. 

```[.....]
```
Sep  4 13:04:04 faustino NetworkManager: <debug> [1220529844.109569] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '3Com' 
Sep  4 13:04:04 faustino NetworkManager: <WARN>  nm_device_802_11_wireless_get_activation_ap(): nm_device_802_11_wireless_get_activation_ap: tried to manually connect to network '3Com' without providing security information! 
Sep  4 13:04:04 faustino NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / 3Com 
Sep  4 13:04:04 faustino NetworkManager: <info>  Deactivating device wlan0. 
Sep  4 13:04:04 faustino NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) started... 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  4 13:04:04 faustino NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  4 13:04:04 faustino NetworkManager: <WARN>  nm_signal_handler(): Caught signal 6.  Generating backtrace... 
Sep  4 13:04:04 faustino NetworkManager: ******************* START **********************************
Sep  4 13:04:04 faustino NetworkManager: (no debugging symbols found)
Sep  4 13:04:04 faustino last message repeated 11 times
Sep  4 13:04:04 faustino NetworkManager: [Thread debugging using libthread_db enabled]
Sep  4 13:04:04 faustino NetworkManager: [New Thread 0xb7af2720 (LWP 4892)]
Sep  4 13:04:04 faustino NetworkManager: [New Thread 0xb7af1b90 (LWP 8698)]
Sep  4 13:04:04 faustino NetworkManager: [New Thread 0xb72f0b90 (LWP 8695)]
Sep  4 13:04:04 faustino NetworkManager: [New Thread 0xb6aefb90 (LWP 5848)]
Sep  4 13:04:04 faustino NetworkManager: (no debugging symbols found)

Sep  4 13:04:04 faustino last message repeated 9 times
Sep  4 13:04:04 faustino NetworkManager: 0xb7eee410 in __kernel_vsyscall ()
Sep  4 13:04:04 faustino NetworkManager: ******************* END **********************************

```

Any help gratefully received.

---

### Post by elishock2420 on 2008-09-07
What does "/etc/init.d/networking restart" do for you in a temrinal?

---

### Post by desconocido on 2008-09-08
Hi elishock2420,

It didn't seem to do much. I provoked the network by changing to manual connection and then

```
$ sudo /etc/init.d/networking restart
[sudo] password for user: 
 * Reconfiguring network interfaces...                               [ OK ] 

```

It may be coincidence but at this point the WiFi router lost its connection to DNS, disrupting the other computers on the network. I had to restart mine but maybe I should have waited until the router was sorted.

---

### Post by slakkie on 2008-09-08
[http://ubuntuforums.org/showpost.php?p=5752871&postcount=2](http://ubuntuforums.org/showpost.php?p=5752871&postcount=2)

I don't think /etc/init.d/networking will work, because he uses a network manager which doesn't write the configuration to the interfaces file.

Probably you will get your wireless up and running again after you logout, and login again (no reboot, just logout from your current session). 

If you configure your network via the interfaces file you will be able to restart your network via /etc/init.d/networking

---

### Post by desconocido on 2009-10-19
Finally found a way of provoking the WiFi to restart without too much delay (reboot takes 3 minutes):

Right click on Networking icon (nm-applet 0.6.6) in panel at top of screen;
Untick Enable Networking;
Right click on Networking icon...
Retick Enable Networking;
If necessary, left click on Networking icon... and select WiFi network.

This typically takes a few seconds.

Relief!

---

### Post by mariosx on 2011-11-04
wouldn't 

sudo ifconfig eth1 down
sudo ifconfig eth1 up

do the trick? (eth1 = your network interface. Could be wlan0 or something like that)

---

### Post by s.fox on 2011-11-04
Necromancy. Please start your own thread.

Thread closed.

---

