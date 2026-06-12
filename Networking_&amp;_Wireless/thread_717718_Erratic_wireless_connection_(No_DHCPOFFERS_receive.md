---
title: "Erratic wireless connection (No DHCPOFFERS received) with Atheros 5006EG"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by nsudha on 2008-03-07
Hi,

I have a Toshiba Satellite P205D with AMD Turion 64x2 and the wireless card:
Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

To get the wireless connection working, I installed the following ndiswrapper:
/etc/network$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

/etc/network$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 


The connection works fine 50% of the time, but when it fails, I cannot get it to start again short of restarting the machine (and since the hibernate/suspend/restart has not been configured, this means a shutdown and hard power on!). Sometimes even that does not help.

Here is the syslog when it is trying to connect:

Mar  7 09:32:10 banjara NetworkManager: <info>  Device wlan0 activation scheduled... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) started... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0/wireless): access point 'GardenPebbles' is encrypted, but NO valid key exists.  New key needed. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'GardenPebbles'. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'GardenPebbles' received. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar  7 09:32:10 banjara NetworkManager: <info>  Activation (wlan0/wireless): access point 'GardenPebbles' is encrypted, and a key exists.  No new key needed. 
Mar  7 09:32:11 banjara NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Mar  7 09:32:11 banjara NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant8^I' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was '0' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 47617264656e506562626c6573' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Mar  7 09:32:11 banjara NetworkManager: <info>  SUP: response was 'OK' 
Mar  7 09:32:11 banjara NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar  7 09:32:14 banjara kernel: [ 1056.168286] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  7 09:32:16 banjara avahi-daemon[5044]: Registering new address record for fe80::200:ff:fe00:0 on wlan0.*.
Mar  7 09:32:17 banjara NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'GardenPebbles'. 
Mar  7 09:32:17 banjara NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar  7 09:32:17 banjara NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Mar  7 09:32:19 banjara NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Mar  7 09:32:19 banjara NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Mar  7 09:32:19 banjara NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Mar  7 09:32:20 banjara NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Mar  7 09:32:21 banjara dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Mar  7 09:32:25 banjara kernel: [ 1066.769212] wlan0: no IPv6 routers present
Mar  7 09:32:27 banjara dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Mar  7 09:32:37 banjara dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar  7 09:32:45 banjara dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Mar  7 09:32:56 banjara dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Mar  7 09:33:08 banjara dhclient: No DHCPOFFERS received. *********
Mar  7 09:33:08 banjara dhclient: Trying recorded lease 192.168.2.2
Mar  7 09:33:08 banjara avahi-daemon[5044]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.2.
Mar  7 09:33:08 banjara avahi-daemon[5044]: New relevant interface wlan0.IPv4 for mDNS.
Mar  7 09:33:08 banjara avahi-daemon[5044]: Registering new address record for 192.168.2.2 on wlan0.IPv4.
Mar  7 09:33:11 banjara avahi-daemon[5044]: Withdrawing address record for 192.168.2.2 on wlan0.
Mar  7 09:33:11 banjara avahi-daemon[5044]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.2.
Mar  7 09:33:11 banjara avahi-daemon[5044]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar  7 09:33:11 banjara avahi-autoipd(wlan0)[6474]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Mar  7 09:33:11 banjara avahi-autoipd(wlan0)[6474]: Successfully called chroot().
Mar  7 09:33:11 banjara avahi-autoipd(wlan0)[6474]: Successfully dropped root privileges.
Mar  7 09:33:11 banjara avahi-autoipd(wlan0)[6474]: Starting with address 169.254.0.1
Mar  7 09:33:16 banjara avahi-autoipd(wlan0)[6474]: Callout BIND, address 169.254.0.1 on interface wlan0
Mar  7 09:33:16 banjara avahi-daemon[5044]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.0.1.
Mar  7 09:33:16 banjara avahi-autoipd(wlan0)[6474]: A routable address has been configured.
Mar  7 09:33:16 banjara avahi-autoipd(wlan0)[6474]: Callout UNBIND, address 169.254.0.1 on interface wlan0
Mar  7 09:33:16 banjara avahi-daemon[5044]: New relevant interface wlan0.IPv4 for mDNS.
Mar  7 09:33:16 banjara avahi-daemon[5044]: Registering new address record for 169.254.0.1 on wlan0.IPv4.
Mar  7 09:33:16 banjara dhcdbd: dhco_input_option: Value 4294967295 cannot be converted to type L 
Mar  7 09:33:16 banjara dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = 4294967295 
Mar  7 09:33:16 banjara NetworkManager: <info>  DHCP daemon state is now 8 (timeout) for interface wlan0 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Mar  7 09:33:16 banjara avahi-autoipd(wlan0)[6474]: No longer a routable address configured, restarting probe process.
Mar  7 09:33:16 banjara avahi-daemon[5044]: Withdrawing address record for 169.254.0.1 on wlan0.
Mar  7 09:33:16 banjara avahi-daemon[5044]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.0.1.
Mar  7 09:33:16 banjara avahi-daemon[5044]: Interface wlan0.IPv4 no longer relevant for mDNS.
Mar  7 09:33:16 banjara avahi-autoipd(wlan0)[6475]: client: RTNETLINK answers: No such process
Mar  7 09:33:16 banjara NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface wlan0 
Mar  7 09:33:16 banjara dhcdbd: Unrequested down ?:3
Mar  7 09:33:16 banjara NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) failed for access point (GardenPebbles) 
Mar  7 09:33:16 banjara NetworkManager: <info>  Activation (wlan0) failed. 
Mar  7 09:33:16 banjara NetworkManager: <info>  Deactivating device wlan0. 
Mar  7 09:33:16 banjara avahi-daemon[5044]: Withdrawing address record for fe80::200:ff:fe00:0 on wlan0.
Mar  7 09:33:16 banjara NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Mar  7 09:33:17 banjara avahi-autoipd(wlan0)[6474]: SIOCSIFFLAGS failed: Permission denied
Mar  7 09:33:38 banjara kernel: [ 1139.695683] ADDRCONF(NETDEV_UP): wlan0: link is not ready

My interfaces file looks like this:
/etc/network$ more interfaces

auto lo
iface lo inet loopback

I've tried manual configuration and changed the interfaces file as below, but that didn't work either:

/etc/network$ more interfaces.te  
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

;pre-up ifconfig wlan0 up
;pre-up ifconfig wlan0 down
;pre-up ifconfig wlan0 up
;pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "GardenPebbles"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="%%%"
pre-up ifconfig wlan0 up

What else should I be trying?!

Thanks,
Sudha

---

### Post by ittiam on 2008-03-07
Can you post the output of

```
iwconfig
```
```
ifconfig wlan0
```

Also there are some silly things that might work, for example removing the ndiswrapper module and modprobing it again. 

> 
modprobe -r ndiswrapper
modprobe ndiswrapper


After this try configuring it again. And also double check your /etc/resolv.conf and then the number of users supported in your router.

---

### Post by nsudha on 2008-03-07
Hi,

I unloaded and loaded the ndiswrapper as you suggested and it's working! The iwconfig info may be moot now but here it is:

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"GardenPebbles"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:1B:AF:31   
          Bit Rate=54 Mb/s   
          Power Management: off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:136   Missed beacon:0

> ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:84:63:A5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fe84:63a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5214 (5.0 KB)  TX bytes:11134 (10.8 KB)
          Interrupt:19 Memory:f8200000-f8210000 

So is this what I should do each time I fail to get a connection? 
Should I incorporate modprobe in /etc/network/interfaces ?

Thanks,
Sudha

---

### Post by ittiam on 2008-03-07
I guess it is not necessary, if you have ndiswrapper in your /etc/modules you should be connected during boot time. As far as my experience goes this happens whenever I try to switch from one wireless network to another. And I do not know to explain as why or how this happens. One more suggestion is to try using knetworkmanager, i feel it is lot better than nm-applet or you can use wpa_supplicant from command line. I use the latter.

---

### Post by ittiam on 2008-03-07
One more thing I noticed is in your /etc/network/interfaces file you have not indicated dhcp to happen, hence when you boot you wouldnt have got an ip address from your AP although you are connected to it. I suggest you add the following line in that file

```
iface wlan0 inet dhcp
```

---

### Post by nsudha on 2008-03-07
I'll try both your suggestions - thanks!

---

### Post by wheelie77 on 2008-03-09
Hey nsudha,

I am a bit of a noob to ubuntu as well and was having a **** of a time with my connection dropping out every few seconds. My signal would go from 67/70 to 0/70 then back again for no reason :( . Anyway, I wrote some notes on my blog that might help or just confuse you some more?? 

[My Blog]("http://edens-gate.com/wordpressmu/blog/2008/03/09/ubuntu-and-wireless-dropout/")

Let me know how you go?

Dave

---

