---
title: "[SOLVED] Wireless Card problem....AR5007EG"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by web-qwerty on 2008-01-04
```
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# make
make -C driver
make[1]: Entering directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [all] Error 2
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# sudo make install
make -C driver install
make[1]: Entering directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [install] Error 2

```

i have tried again and again but no... 

when i install the ndiswrapper which comes with UBuntu there is no such error but then there is an error when i am trying to access the device...
dumb story....:mad:

---

### Post by web-qwerty on 2008-01-04
> **web-qwerty said:**
> ```
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper': Is a directory
make: *** [uninstall] Error 1
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# make
make -C driver
make[1]: Entering directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [all] Error 2
root@WebAdm1n:/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5# sudo make install
make -C driver install
make[1]: Entering directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c: In function ‘register_devices’:
/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.c:930: error: ‘struct usb_driver’ has no member named ‘owner’
make[3]: *** [/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/w3b4dm1n/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [install] Error 2

```

i have tried again and again but no... 

when i install the ndiswrapper which comes with UBuntu there is no such error but then there is an error when i am trying to access the device...
dumb story....:mad:

can anyone do some help plss :) :popcorn:

---

### Post by rustybronco on 2008-01-04
I doubt I can, but visit the ndis forum about error1 and error2, or there was a post about the ar5007eg and ndiswrapper [http://ubuntuforums.org/showpost.php?p=3101929&postcount=1](http://ubuntuforums.org/showpost.php?p=3101929&postcount=1)

---

### Post by web-qwerty on 2008-01-05
> **rustybronco said:**
> I doubt I can, but visit the ndis forum about error1 and error2, or there was a post about the ar5007eg and ndiswrapper [http://ubuntuforums.org/showpost.php?p=3101929&postcount=1](http://ubuntuforums.org/showpost.php?p=3101929&postcount=1)

I have installed NDISWRAPPER drivers and everything successfully (actually the deed was that it was downloading 1.50 instead of the stable 1.51 stable version..



Now i am again concerned... how to put my wireless card into action... tried all what i could do

added all the information needed in interfaces, ifconfig wlan0 up... 

everything seems fine but still it can not detect any network !! :mad::mad::mad::mad:

---

### Post by web-qwerty on 2008-01-05
Hey again. Let me make it simpler:

I have installed the drivers for my card according to 

[This tutorial]("http://ubuntuforums.org/showpost.php?p=3101929&postcount=1")

They are working fine

iwlist wlan0
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have configured my dhcp router and then configured my wireless card for manipulating with WPA2 AES
[This tutorial]("http://ubuntuforums.org/showthread.php?t=574501")

now it is givin me the following result of the command:

```
wpa_supplicant -w -D wext -i wlan0 -c /etc/wpa_supplicant.conf -dd 
```


```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=14):
     57 69 72 65 4c 65 73 73 41 50 48 30 4d 33         WireLessAPH0M3  
PSK (ASCII passphrase) - hexdump_ascii(len=47): [REMOVED]
key_mgmt: 0x2
proto: 0x3
pairwise: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='WireLessAPH0M3'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:c0:a8:d9:d5:96
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec

```

and then it is repeating the search again and again...

i have tried to connect without using encryption but still the same problem exists
dhclient finds nothing at all....


i am pretty sure that the dhcp of my router is working fine because i am connecting without any problems under vista...



DOES ANYONE HAVE SOME IDEAS ? :confused::confused::confused::confused:

---

### Post by wieman01 on 2008-01-06
To begin with, please post:
> sudo iwlist scan
> sudo ndiswrapper -l
> sudo gedit /etc/network/interfaces
Why don't you use Network Manager for wireless networking?

---

### Post by web-qwerty on 2008-01-06
so here is the results:


iwlist scan:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```


ndiswrapper -l:

```
net5211 : driver installed
        device (168C:001C) present

```


gedit /etc/network/interfaces :

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid "WireLessAPH0M3"
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk a73c2731f597e957e27019637b74068434c036e309d7dd69f4a67822c954c2a1

```


I am using wpa_supplicant so my wpa_supplicant.conf looks like this:

```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
	ssid="WireLessAPH0M3"
        psk=here is my password in quotes
        key_mgmt=WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
}
```


i am not using network manager or wicd or anything else like wifi radar because i am trying to keep the things simple- manual connection i think is the best alternative.
As an addition i tried to use NM and it is showing the wireless driver, but when i try to configure it and put it on dhcp - it transforms the wireless to wired and wirtes WIred connection on eth0.... alTHOUGH i have inserted eth0 as wired and wlan0 as wireless sources.....

so that is why i am trying to do it manually :)

---

### Post by wieman01 on 2008-01-06
There are no scan results which isn't really a good sign. Anyway, please adjust "/etc/network/interfaces" so that it looks like this:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid **[COLOR="Red"]WireLessAPH0M3[/COLOR]**
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk a73c2731f597e957e27019637b74068434c036e309d7dd69f4a67822c954c2a1
**[COLOR="Red"]No quotes please. [/COLOR]**

You don't need "wpa_supplicant.conf" if you configure your network via "/etc/network/interfaces". 

Now do this and post the results please:
> sudo ifdown -v wlan0
> sudo ifup -v wlan0
> sudo lshw -C network

---

### Post by web-qwerty on 2008-01-06
```
root@w3b4dm1n:/home/w3b4dm1n# ifdown -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
RTNETLINK answers: No such process
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:a8:d9:d5:96
Sending on   LPF/wlan0/00:c0:a8:d9:d5:96
Sending on   Socket/fallback
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 7332).
root@w3b4dm1n:/home/w3b4dm1n# ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "WireLessAPH0M3" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:a8:d9:d5:96
Sending on   LPF/wlan0/00:c0:a8:d9:d5:96
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

```



lshw -C network
```
  *-network               
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:d9:d5:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.51+,11/15/2006,5.1.1.9 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:63:05:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.11.12.113 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

---

### Post by kevdog on 2008-01-06
With iwlist scan, this must show some networks in the area.  If you keep typing this command and nothing comes back (like No Scan Results) then your wireless card doesnt see any nearby networks, and you are never going to connect.  Try moving closer to the router or something.  Until you see networks, we are wasting our time configuring the other files.

---

### Post by wieman01 on 2008-01-06
The adapter is not working as Kevdog has pointed out. On what version of Ubuntu are you on? 32-bit or 64-bit?

---

### Post by Paris Heng on 2008-01-06
How abt you trying Atheros'd own WiFi driver Madwifi? Thank you.

---

### Post by web-qwerty on 2008-01-06
actually I am in one and the same room with the rooter :-D

That is why I was thinking the wireless card is not working properly...according to ifconfig it  does, but still the same problem still exists,,,(Except the light lid in front- it is just not lighting...)


It is strange because under Windows I have to use Launch Manager in order to have the card activated... 
dunno....


:confused:

P.S. I am running 32 bit Ubuntu 7.10 - the Gutsy Gibbon
I have tried with the WiFI drivers of Atheros and also applied the patch... still this sh*t does not work....

same thing No scan results.... again and again :)

---

### Post by wieman01 on 2008-01-06
The LED is not lit? Then the device is not working, I am pretty sure. 

What tutorial have you followed? And what driver have you blacklisted? What device have you got?

---

### Post by kevdog on 2008-01-06
Ok just a couple of things.  It looks like your device shows up when you do 

lshw -C network

It shows the driver ndiswrapper + zxxxx

So at least Ubuntu is detecting the card.

Can you post ifconfig?

And make sure you have brought the device up
sudo ifconfig wlan0 up

Why are you using ndiswrapper??  Madwifi drivers should also work in your situation.

---

### Post by web-qwerty on 2008-01-06
Hey again. When I install the madwifi drivers and apply the patch it is writing tons of errors like 801 unknown hardware and bla bla....

that is why I am trying with ndiswrapper 1.51

the result from ifconfig
```
root@w3b4dm1n:/home/w3b4dm1n# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:63:05:F6  
          inet addr:10.11.12.113  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe63:5f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5784906 (5.5 MB)  TX bytes:1514061 (1.4 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:D9:D5:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:c0000000-c0010000 

wlan0:ava Link encap:Ethernet  HWaddr 00:C0:A8:D9:D5:96  
          inet addr:169.254.10.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:c0000000-c0010000 


```

now strangely from nowhere appeared wlan0:ava ... whatever that means :D
and still no search found in the iwlist....

on the questions of wieman01:

i have used net5211.inf (for AR5006EG)
i have blacklisted ath_pci as shown in the tutorial 

[http://ubuntuforums.org/showpost.php?p=3101929&postcount=1]("http://ubuntuforums.org/showpost.php?p=3101929&postcount=1")

Of course with some corrections with mine because the tutorial way downloads the UNSTABLE 1.50 version and then i got the error in #1 post. Then I've made some changes and did it with 1.51 Stable version and everything is working fine if we are talking about the ndiswrapper....



i just don't have any idea what is the problem now :):confused:



as you see for the device eth0 the DHCP of the router is working perfectly...if there is someone to find it :(((((

---

### Post by wieman01 on 2008-01-06
> **web-qwerty said:**
> On the questions of wieman01:

i have used net5211.inf (for AR5006EG)
i have blacklisted ath_pci as shown in the tutorial 

[http://ubuntuforums.org/showpost.php?p=3101929&postcount=1]("http://ubuntuforums.org/showpost.php?p=3101929&postcount=1")
While you deployed the .INF file, were any other files present? E.g. .CAT, etc.? They need to be present as well in order for ndiswrapper to install the device correctly...

---

### Post by web-qwerty on 2008-01-06
I sure now that but for that exact driver I thing there was no cat, only .sys file and it was there (as you see ubuntu recognizes the device)

OK. Lets try another approach.. I will now try again with the MadWifi 0.9.3.3 drivers which SHOULD do the work....

now
```

ifconfig wlan0 down
pushd ndiswrapper*
ndiswrapper -r net5211
make uninstall
popd
gedit /etc/modules   (removing the line for autostarting ndiswrapper)
gedit /etc/modprobe.d/blacklist (removing the line for blacklisting ath_pci)
gedit /etc/network/interfaces  (removing everything for wlan0)
init 6

```


after the restart: 
```

pushd madwifi*
make
make install
popd

```

what should be done now? I am asking to verify whether the thing which i am doing is right....

By the way here are the results from the install:

```
root@w3b4dm1n:/home/w3b4dm1n/madwifi-0.9.3.3# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/if_ath.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/if_ath_pci.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ah_os.o
  HOSTCC  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/uudecode
  UUDECODE /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/i386-elf.hal.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/amrr.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/onoe.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/sample.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/if_media.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_beacon.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_none.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_input.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_node.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_output.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_power.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_proto.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_wireless.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_linux.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_monitor.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_rate.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_acl.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan_ap.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan_sta.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_xauth.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 13 modules
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
root@w3b4dm1n:/home/w3b4dm1n/madwifi-0.9.3.3# make install
sh scripts/find-madwifi-modules.sh 2.6.22-14-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_hal'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_hal.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_hal'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate'
for i in amrr/ onoe/ sample/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr'
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe'
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_sample.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample'
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/net80211'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install $f.ko //lib/modules/2.6.22-14-generic/net; \
        done
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/net80211'
(export KMODPATH=/lib/modules/2.6.22-14-generic/net; /sbin/depmod -ae 2.6.22-14-generic)
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'

```

---

### Post by malignor on 2008-01-06
Hi.

I have an Atheros wireless card (not working) and I got it working fine in old Feisty Fawn. I upgraded to Gutsy and for now the same procedure (using ndiswrapper to operate the windows driver, SINCE ATHEROS ONLY HAS A WINDOWS DRIVER) may or may not work.

Here's the problem:

- ignore the LED (it never lights, even when the card works; I speak from 1st hand experience).
- ignore the scan stuff. The card's drivers can be applied with the included version of ndiswrapper, but they don't work because the Gutsy-included ndiswrapper is too old, so the "working driver" is window dressing.
- The one and only problem is that the latest ndiswrapper (1,5) cannot "make install". Thus **_ndiswrapper 1.5 is the only problem_** for this issue. Specifically line 930 of the driver loader.c file where it talks about USB driver properties which are not valid.

Can anyone provide any insight as to how to fix this ndiswrapper issue?

---

### Post by web-qwerty on 2008-01-06
megalior... as i stated DOWNLOAD THE STABLE VERSION 1.51 of ndiswrapper
 just try to find tar in the net you will

remove the old 1.5 (it is unstable beta or whatever it is)

install the new one and you should not have any problems... that is the only thing which MUST BE DONE differently from the tutorial i stated

---

### Post by web-qwerty on 2008-01-06
> **web-qwerty said:**
> I sure now that but for that exact driver I thing there was no cat, only .sys file and it was there (as you see ubuntu recognizes the device)

OK. Lets try another approach.. I will now try again with the MadWifi 0.9.3.3 drivers which SHOULD do the work....

now
```

ifconfig wlan0 down
pushd ndiswrapper*
ndiswrapper -r net5211
make uninstall
popd
gedit /etc/modules   (removing the line for autostarting ndiswrapper)
gedit /etc/modprobe.d/blacklist (removing the line for blacklisting ath_pci)
gedit /etc/network/interfaces  (removing everything for wlan0)
init 6

```


after the restart: 
```

pushd madwifi*
make
make install
popd

```

what should be done now? I am asking to verify whether the thing which i am doing is right....

By the way here are the results from the install:

```
root@w3b4dm1n:/home/w3b4dm1n/madwifi-0.9.3.3# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/w3b4dm1n/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/if_ath.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/if_ath_pci.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ah_os.o
  HOSTCC  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/uudecode
  UUDECODE /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/i386-elf.hal.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/amrr.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/onoe.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/sample.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/if_media.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_beacon.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_none.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_input.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_node.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_output.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_power.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_proto.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_wireless.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_linux.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_monitor.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_rate.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_acl.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan_ap.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_scan_sta.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/ieee80211_xauth.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 13 modules
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath/ath_pci.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_hal/ath_hal.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_acl.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_ccmp.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_ap.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_scan_sta.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_tkip.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_wep.ko
  CC      /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.mod.o
  LD [M]  /home/w3b4dm1n/madwifi-0.9.3.3/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
root@w3b4dm1n:/home/w3b4dm1n/madwifi-0.9.3.3# make install
sh scripts/find-madwifi-modules.sh 2.6.22-14-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_hal'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_hal.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_hal'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate'
for i in amrr/ onoe/ sample/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/amrr'
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/onoe'
make[2]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_sample.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate/sample'
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/ath_rate'
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/net80211'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install $f.ko //lib/modules/2.6.22-14-generic/net; \
        done
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/net80211'
(export KMODPATH=/lib/modules/2.6.22-14-generic/net; /sbin/depmod -ae 2.6.22-14-generic)
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/home/w3b4dm1n/madwifi-0.9.3.3/tools'

```

i forgot to mention that  now everything is just looking fine but still i do not have any idea how to start it, because the lid is not lighting at all.... and also  i am not sure that the drivers work properly:

---

### Post by Digger78 on 2008-01-06
forgive me if this is thought of as a stupid line of thought.

Is your card enabled?  do you have a key combo to enable/disable your card?  (fn + F1 maybe)

Desktop or laptop? which model?

I have the same card in my FSC esprimo mobile V5515, Ndiswrapper + XP driver was the only way i could get the card working

could i suggest removing all security temporarily till you get connected to your network.

---

### Post by web-qwerty on 2008-01-06
> **Digger78 said:**
> forgive me if this is thought of as a stupid line of thought.

Is your card enabled?  do you have a key combo to enable/disable your card?  (fn + F1 maybe)

Desktop or laptop? which model?

I have the same card in my FSC esprimo mobile V5515, Ndiswrapper + XP driver was the only way i could get the card working

could i suggest removing all security temporarily till you get connected to your network.
I THINK THE SAME THING DIGGER BUT I DONT FIND ANY WAY TO ENABLE IT ;)

I have enabled wireless from the BIOS (it is working perfect under Vista)

The problem as  I suppose is the following:

I CAN NOT ENABLE THE CARD.... that is because EVEN UNDER VISTA and any other windows TO ACTIVATE the card I HAVE TO USE LAUNCH MANAGER (extra program....) then IT ACTIVATES the buttons on my pad (the special buttons like WiFi button and SIlent-Normal mode changer for the ventilator...)

SO... under windows i DO NOT HAVE ANY KEY COMBO to run the WiFi.
THat is why I dont have under Ubuntu either....else i would have tried thousands of times until now.....

My laptop is Fujitsu Siemens AMILO 1718
..



any idea will be great :):lolflag:

---

### Post by web-qwerty on 2008-01-06
I HAVE FINALLY FOUND A SOLUTION!

THE PROBLEM WAS IN MY LAPTOP-S MODEL. THE MODEL FUJITSU SIEMENS AMILO 1718 IS JUST CONFIGURED NOT TO RUN AUTOMATICALLY THE HOTKEYS.

This is done in order to have the program Launch Manager installed. And it can be installed only in Windows...which is coming licensed with this PC ... Strange way to make people pay for your shits....


anyway I found a solution. A hack ... to apply the hack and have your wireless button activated under Ubuntu 7.xx you have to write the following in the terminal:

```

HowTo:

wget http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh

chmod 755 fsca16xx.sh

sudo ./fsca16xx.sh setup 


```

Then log-out and login.
Press the button with the antenna and voala - it is activated without bothering with Launch Manager and other shits.... :lolflag::lolflag::lolflag::lolflag:

---

### Post by Digger78 on 2008-01-06
LoL you spying on my browsing?

I was just about to post the same thing, found on the amilo forums [http://www.amilo-forum.com/topic,929,fadc1b56a8b316f670cefdc33a100834,-linux-on-amilo-li-1718.html](http://www.amilo-forum.com/topic,929,fadc1b56a8b316f670cefdc33a100834,-linux-on-amilo-li-1718.html)

From the same thread, apparently there is a madwifi driver for the AR5007EG [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

I might give it a try to see if or how well it works

Glad you got it sorted.

Dont forget to mark the thread solved  (thread tools)

---

### Post by Digger78 on 2008-01-06
The madwifi driver i posted above does work with the AR5007EG (im using it to post this)

I will check later tonight if it holds out on torrents and edit this post

---

### Post by web-qwerty on 2008-01-06
Final post (Summary)

For PERFECT RUNNING of your AR5006-7EG card WITHOUT NDISWRAPPER:

Download the following driver: [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz")

Then follow the instructions from here:
[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

You will have perfect connection with no troubles under Ubuntu 7.xx


P.S. If you are using AMILO 1718 or other FUJITSU or ACER computer which hotkeys pad can not be activated just do the following:

```

wget http://fscamiloa16xx.googlecode.com/svn/trunk/fsca16xx.sh

chmod 755 fsca16xx.sh

sudo ./fsca16xx.sh setup
```


....


Web-qwerty

---

### Post by Prometheum on 2008-01-06
Its important to note that the above version of Madwifi will **ONLY WORK ON 32-BIT x86 PLATFORMS.** This means if you use PPC, x86_64 (amd64), or anything else that isn't 32-bit x86, that driver WILL NOT WORK FOR YOU.

---

### Post by kevdog on 2008-01-07
Ive been monitoring this thread, and glad you guys came to a resolution.  I noticed the madwifi drivers you guys recommended downloading were in a special folder in the archive.  Could you guys have just compiled the generic madwifi driver from svn rather than installing this precompiled package?  Just trying to make sense why this particular driver would work and not the madwifi generic driver?

---

### Post by Digger78 on 2008-01-07
> **kevdog said:**
> Ive been monitoring this thread, and glad you guys came to a resolution.  I noticed the madwifi drivers you guys recommended downloading were in a special folder in the archive.  Could you guys have just compiled the generic madwifi driver from svn rather than installing this precompiled package?  Just trying to make sense why this particular driver would work and not the madwifi generic driver?

I will give it a try later tonight when i get some time, it was a couple of months ago that i tried madwifi (not from SVN)

I will post back with the results.

---

### Post by Digger78 on 2008-01-07
I tried the latest release (0.9.3.3) and from SVN.

Neither of them worked. same result with both.

[QUOTE=dmesg]MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)[/QUOTE]

 however there is a patch available for the latest release -http://madwifi.org/ticket/1679

I had already removed version 0.9.3.3 so i have not tried the patch.

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)  is not precompiled

---

### Post by Prometheum on 2008-01-07
> **kevdog said:**
> Ive been monitoring this thread, and glad you guys came to a resolution.  I noticed the madwifi drivers you guys recommended downloading were in a special folder in the archive.  Could you guys have just compiled the generic madwifi driver from svn rather than installing this precompiled package?  Just trying to make sense why this particular driver would work and not the madwifi generic driver?

This version has a patched version of the HAL. The patch was provided to Madwifi by Atheros to allow the driver to work on AR5007EG cards. It breaks binary compatibility with the rest of the Madwifi ABI, and can't be integrated into the source tree for the SVN for that reason.

---

### Post by kevdog on 2008-01-07
Thanks for the info -- so the only difference is the patch applied to the svn sources.  Good investigation.  Im going to add this to me list of useful networking related threads I maintain in a separate thread.  Thanks a lot.

---

### Post by Prometheum on 2008-01-07
No problem. If it hasn't already been posted, this is the support ticket on madwifi that outlines things in a more complete manner.
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by web-qwerty on 2008-01-16
> **Prometheum said:**
> No problem. If it hasn't already been posted, this is the support ticket on madwifi that outlines things in a more complete manner.
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

sorry but about the particular card this patch it does not work... tested hundred times....

so only the above stated drivers from Digger are relevant and compatiable!!! :lolflag:

---

### Post by Prometheum on 2008-01-16
That's the ticket which includes the patch that enables AR5007EG support on x86 machines. Digger posted the prepatched snapshot. Its the same thing.

:lolflag:

---

