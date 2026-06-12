---
title: "broadcom 1395 wl driver WPA2 works but WPA1 does not"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by stavka on 2008-07-15
Hello Everybody,
I just installed Ubuntu 8.04 on my Dell Vostro 1500 Laptop and everything works great, except for one thing. I can not connect to any WPA1 wireless points. WPA2 works fine. I tried different routers and manual config, to no avail. Here is my info:

route shows nothing (or only wired connection)

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:"anderso"
          Access Point: Not-Associated 
```  

sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:7E:2F:BB:76
                    ESSID:"anderson"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-52 dBm  Noise level:-10 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1E:52:79:B1:98
                    ESSID:"groovyonionz"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-50 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1D:7E:58:C1:42
                    ESSID:"aCozzitorto"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-74 dBm  Noise level:-24 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:1A:70:DC:72:65
                    ESSID:"snr"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-84 dBm  Noise level:-24 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:04:E2:97:98:B2
                    ESSID:"VINSMC"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-24 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 06 - Address: 00:12:0E:63:D1:35
                    ESSID:"07B402903356"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-24 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 00:0F:3D:4A:BF:42
                    ESSID:"juhee"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-18 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:14:6C:FF:71:60
                    ESSID:"BATCAVE"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
```


sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:7f:08:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c6:20:7e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
```

/etc/network/interfaces
```
auto lo
iface lo inet loopback
```

sudo ifdown -v eth1
ifdown: interface eth1 not configured

this is what show up in the logs:
daemon.log

```
Jul 15 23:13:59 victor-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jul 15 23:13:59 victor-laptop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jul 15 23:14:16 victor-laptop NetworkManager: <debug> [1216178056.713204] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'anderson' 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / anderson 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Deactivating device eth1. 
Jul 15 23:14:16 victor-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) started... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'anderson' is encrypted, but NO valid key exists.  New key needed. 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'anderson'. 
Jul 15 23:14:16 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'anderson' received. 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 15 23:14:25 victor-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'anderson' is encrypted, and a key exists.  No new key needed. 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was '0' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 616e646572736f6e' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jul 15 23:14:27 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 15 23:14:37 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:14:37 victor-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'anderson'. 
Jul 15 23:14:37 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul 15 23:14:37 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jul 15 23:14:38 victor-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jul 15 23:14:38 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jul 15 23:14:38 victor-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Jul 15 23:14:38 victor-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jul 15 23:14:39 victor-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jul 15 23:14:40 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:14:43 victor-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jul 15 23:14:44 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:14:48 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:14:48 victor-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Jul 15 23:14:52 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:14:56 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:14:59 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:15:02 victor-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jul 15 23:15:03 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:15:07 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:15:11 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:15:14 victor-laptop dhclient: No DHCPOFFERS received.
Jul 15 23:15:14 victor-laptop avahi-autoipd(eth1)[6451]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jul 15 23:15:14 victor-laptop avahi-autoipd(eth1)[6451]: Successfully called chroot().
Jul 15 23:15:14 victor-laptop avahi-autoipd(eth1)[6451]: Successfully dropped root privileges.
Jul 15 23:15:14 victor-laptop avahi-autoipd(eth1)[6451]: Starting with address 169.254.5.136
Jul 15 23:15:14 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:15:18 victor-laptop NetworkManager: <info>  Supplicant state changed: 0 
Jul 15 23:15:19 victor-laptop avahi-autoipd(eth1)[6451]: Callout BIND, address 169.254.5.136 on interface eth1
Jul 15 23:15:19 victor-laptop avahi-daemon[5289]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.5.136.
Jul 15 23:15:19 victor-laptop avahi-daemon[5289]: New relevant interface eth1.IPv4 for mDNS.
Jul 15 23:15:19 victor-laptop avahi-daemon[5289]: Registering new address record for 169.254.5.136 on eth1.IPv4.
Jul 15 23:15:21 victor-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jul 15 23:15:23 victor-laptop avahi-autoipd(eth1)[6451]: Successfully claimed IP address 169.254.5.136
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) failed for access point (anderson) 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Activation (eth1) failed. 
Jul 15 23:15:23 victor-laptop NetworkManager: <info>  Deactivating device eth1. 
Jul 15 23:15:23 victor-laptop avahi-daemon[5289]: Withdrawing address record for 169.254.5.136 on eth1.
Jul 15 23:15:23 victor-laptop avahi-daemon[5289]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.5.136.
Jul 15 23:15:23 victor-laptop avahi-daemon[5289]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul 15 23:15:23 victor-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
```

Any help is greatly appreciated.

Thank you,
Victor

---

### Post by lbarajas on 2008-07-30
I am having the same issue you have on my inspiron 1525, I can connect to WPA2 but WPA1 is not working.

I am using Ubuntu 8.04 64 bits

---

### Post by smalldog on 2008-08-01
I am very glad to heard that someone can using such WLAN card with WPA enabled successfully. I do have a Dell notebook computer with same WLAN card. However, I can't configure the WLAN using WPA 1/2 for the communication. I currently only using WEP for my WLAN encryption. Do you mind teach me the procedure to setup the WPA2. In addition, I am currently using NetworkManager to administrate all network configuration, is it compatible with WPA. I do have two wireless router. One router is configured using WEP with hidden SSID, another one using WPA1/2 with hidden SSID. But never successfully using WPA(1/2). Show me the steps. Thanks you very much

---

### Post by lbarajas on 2008-08-04
Well I basically follow this how to:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

But still no luck when connecting to WPA1, I even compiled the newer version of ndiswrapper 1.53.

Hope this helps

---

### Post by lbarajas on 2008-08-04
WPA1 works!

I changed the SSID to my acess point, for some reason when trying to connect I got on the logs that a key already exist so when the new name nothing else existed before with that name an got a connection.

The only issue I have so far is that it may not connect immediately after boot, I may need to try it a second time and works.

---

### Post by superm1 on 2008-08-04
> **smalldog said:**
> I am very glad to heard that someone can using such WLAN card with WPA enabled successfully. I do have a Dell notebook computer with same WLAN card. However, I can't configure the WLAN using WPA 1/2 for the communication. I currently only using WEP for my WLAN encryption. Do you mind teach me the procedure to setup the WPA2. In addition, I am currently using NetworkManager to administrate all network configuration, is it compatible with WPA. I do have two wireless router. One router is configured using WEP with hidden SSID, another one using WPA1/2 with hidden SSID. But never successfully using WPA(1/2). Show me the steps. Thanks you very much
If you are using TKIP on WPA1 there is a bug in the broadcom driver.  Activate hardy-proposed and install the linux 2.6.24-20 kernel image, lum package, and lrm package.

You can see some more details here: [http://ubuntuforums.org/showthread.php?p=5524663#post5524663](http://ubuntuforums.org/showthread.php?p=5524663#post5524663)

---

### Post by alvaradoma on 2008-09-07
alright guys, I recently got a dell vostro 1500 in my hands, and I've succesfully installed a working driver. Got in from the broadcom page.

In ubuntu just make sure you have the build-essential package installed.

download the driver from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and follow the instructions on the README.

So to resume, after you compile the kernel module you download from the broadcom page, I unloaded the previous one with "modprobe -r wl.ko" (all this in a console right...) and tried the one I compile with the broadcom readme instructions with "insmod wl.ko", this one worked. And if it did, then you can follow the following steps:

Ok, a little note on this for at least ubunt 8.04 on (which is what I installed it on).

First, this driver is very annoying, because it comes with linux-restricted-drivers package that comes with ubuntu. With my not so great knowledge over how modprobe works, and modules are listed and such, it took me some time, but I found out that inside your /lib/modules/`uname -r`/ there's a file called modules.dep. This program tells modprobe (the program used to load every driver/kernel module) where every module is, and what it depends on.

So after a couple of hours of suffering with this linux-restricted-drivers package, and not wanting to uninstall it cause it has nvidia drivers etc. I found a method.

1) Disable that specific driver from loading with the restricted drivers that come with ubuntu:

Edit: /etc/default/linux-restricted-modules-common

adding "wl" to the obvious place. So it should look like this inside that file:

DISABLED_MODULES="wl"

2) you have to edit modules.dep file that's inside your /lib/modules/`uname -r`/ (Note: `uname -r` --this isn't an apostrophy `'`'````-- thingy is just something that if you write it in a console it will evaluate. so basically that whole /lib....uname -r... line in my case when I copy/paste to a console it evaluates/says: /lib/modules/2.6.24-19-generic/)

so in this modules.dep file, (nano modules.dep) you can use ctrl + w, or in w/e editor you like, to search for wl.ko, and change that to where ever you compiled it or w/e.

mine said something like /lib/modules/blahblah/volatile/wl.ko and I copied my wl.ko to /lib/modules/blahmykernel/wifi/ folder I created.

ps: sorry for all the long texts, and typos, my english sometimes isn't the best being it my second language.

I have that bcm4312 chipset and if you read the README from the broadcom page it tells you what it supports. etc, etc, hope I can be usefull.

---

