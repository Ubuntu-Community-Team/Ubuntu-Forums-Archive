---
title: "Final missing steps to connecting to my wireless network?"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by ww711 on 2008-05-02
Having recently upgraded to HH-8.04 from GG7.10, my wireless stopped functioning. Having read other threads, I've now managed to get my laptop wireless light to light up and it detects the SSID of my router, only problem now is connecting; currently am using WPA-PSK. It attempts to configure, but refuses to connect, it appears to hang for a while then, nothing.

I am using wifi-radar and ndiswrapper tool driver tool to point to the relevant driver file. I have firestarter (firewall app) installed but not running.

Any suggestions as to how or what i can test to connect?

[B]
iwconfig[/B]
eth1      IEEE 802.11g  ESSID:off/any  Nickname:"Whiskey"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth1
       version: 01
       serial: //this value would be my MAC address...
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by Paris Heng on 2008-05-03
> **ww711 said:**
> Having recently upgraded to HH-8.04 from GG7.10, my wireless stopped functioning. Having read other threads, I've now managed to get my laptop wireless light to light up and it detects the SSID of my router, only problem now is connecting; currently am using WPA-PSK. It attempts to configure, but refuses to connect, it appears to hang for a while then, nothing.

I am using wifi-radar and ndiswrapper tool driver tool to point to the relevant driver file. I have firestarter (firewall app) installed but not running.

Any suggestions as to how or what i can test to connect?

[B]
iwconfig[/B]
eth1      IEEE 802.11g  ESSID:off/any  Nickname:"Whiskey"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth1
       version: 01
       serial: //this value would be my MAC address...
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Use WICD to connect to your WPA-PSK network. Configure you wpa_supplicant correctly.

---

### Post by Ayuthia on 2008-05-03
You might try to see if you can connect to it without any encryption.  You can also try changing the channel on your router in case it is getting interference from other wireless routers or other things.

---

### Post by ww711 on 2008-05-08
> **Paris Heng said:**
> Use WICD to connect to your WPA-PSK network. Configure you wpa_supplicant correctly.

I have attempted with the broadcom supplicant and ndiswrapper; still doesn't connect; now it doesn't even pick up my own wireless SSID, it picks up other SSIDs.

---

### Post by ww711 on 2008-05-08
> **Ayuthia said:**
> You might try to see if you can connect to it without any encryption.  You can also try changing the channel on your router in case it is getting interference from other wireless routers or other things.

I tried with out any encryption, still no connection and I highly doubt that
changing my wireless channel would cause my wireless connection to start functioning correctly. The laptop previous worked fine with wireless on GG 7.10, only when I upgraded to HH 8.04 did this problem start to occur.

Serves me right for upgrading - now I'll have to stay in Windows for the time being and it's a huge shame because I was trying to stay in Linux as much as possible.

Anything else I can test? I've already trawled through most of the related posts about this issue with wireless. I'm willing to post more outputs/configs of my linux setup if anyone can help me with this.

It's really really troublesome! 	](*,)

---

### Post by Ayuthia on 2008-05-08
> **ww711 said:**
> I have attempted with the broadcom supplicant and ndiswrapper; still doesn't connect; now it doesn't even pick up my own wireless SSID, it picks up other SSIDs.

Does it show up when you do sudo iwlist scan from the Terminal?  How are you trying to connect (NetworkManager, Wicd, /etc/network/interfaces)?

---

### Post by esteckis on 2008-05-08
Just a note, under Hardy Heron, the Keyring will not let you connect until you enter your log on password. I could not connect until I shut down my computer and restarted. Then as I logged on, On the desktop the keyring popped up a password window and I entered the password it then allowed the wireless to connect to the router.

---

### Post by ww711 on 2008-05-08
> **Ayuthia said:**
> Does it show up when you do sudo iwlist scan from the Terminal?  How are you trying to connect (NetworkManager, Wicd, /etc/network/interfaces)?

I'm using Wicd.

iwlist scan produces the following output:

[I][B]eth1      Scan completed :
          Cell 01 - Address: 00:11:50:82:0E:B4
                    ESSID:"PETER"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:12:17:DF:2B:5E
                    ESSID:"Jack"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:F6:74:F2:A9
                    ESSID:"BTHomeHub-35F7"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

[/B][/I]

Also I recall that when the wireless was working in GG-7.10, it would show wlan0, nothing seems to exist at the moment in HH.8.04. Only eth0 (wired) and eth1 (wireless)

ifconfig at present now while posting this...
[B][I]
eth0      Link encap:Ethernet  HWaddr some MAC Address  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:a4ff:fecd:eb9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1370117 (1.3 MB)  TX bytes:253180 (247.2 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr some MAC Address  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:c8000000-c8004000 

eth1:avahi Link encap:Ethernet  HWaddr some MAC Address  
          inet addr:169.254.2.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:c8000000-c8004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61508 (60.0 KB)  TX bytes:61508 (60.0 KB)
[/I][/B]

---

### Post by Ayuthia on 2008-05-08
You might try changing the channel on your router.  I recall having problems connecting when I was living in Peterborough (not saying that the UK is causing problems).

You could try adding this to /etc/network/interfaces:
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <passkey>

and then do sudo /etc/init.d/networking restart

If it doesn't work, you can clear it out.

---

### Post by ww711 on 2008-05-08
> **Ayuthia said:**
> You might try changing the channel on your router.  I recall having problems connecting when I was living in Peterborough (not saying that the UK is causing problems).

You could try adding this to /etc/network/interfaces:
auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <essid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <passkey>

and then do sudo /etc/init.d/networking restart

If it doesn't work, you can clear it out.

There were some existing variables and values already existing, so I added the ones that were missing in your template and re-ordered them as above, then followed through with the network restart - output. 
[B][I]Listening on LPF/eth1/mywireless mac addy
Sending on   LPF/eth1/mywireless mac addy
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
 * Stopping NTP server ntpd
   ...done.
[/I][/B]

---

### Post by ww711 on 2008-05-09
I am really tempted to wipe my Linux and re-install a fresh GG-7.10, rather than go for a fresh HH-8.04.

Has anyone had success with a fresh install of HH-8.04 and getting the wireless to function with mininal editing of config files for the product: BCM94311MCG wlan mini-PCI rev 01; laptop is a HP Compaq NX 6325.

---

### Post by ww711 on 2008-05-09
> **Ayuthia said:**
> You might try to see if you can connect to it without any encryption.  You can also try changing the channel on your router in case it is getting interference from other wireless routers or other things.

I decided to change the channel and turned off encryption, wicd detects the connection but refuses to connect....

---

### Post by Ayuthia on 2008-05-10
> **ww711 said:**
> I am really tempted to wipe my Linux and re-install a fresh GG-7.10, rather than go for a fresh HH-8.04.

Has anyone had success with a fresh install of HH-8.04 and getting the wireless to function with mininal editing of config files for the product: BCM94311MCG wlan mini-PCI rev 01; laptop is a HP Compaq NX 6325.

Actually, that is the card that I have and I am able to connect with WPA-PSK in ndiswrapper and b43.

Other options that you have besides reinstalling is to try the b43 driver.  To test it out, all you have to do is install b43-fwcutter (helps if you have a wired connection) then just do the following:
```
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig up
```You should be able to scan networks via sudo iwlist scan and try to connect.  If that works, then you will need to clean up the blacklisting and /etc/modules so that it will load up on future boots.

---

### Post by ww711 on 2008-05-10
> **Ayuthia said:**
> Actually, that is the card that I have and I am able to connect with WPA-PSK in ndiswrapper and b43.

Other options that you have besides reinstalling is to try the b43 driver.  To test it out, all you have to do is install b43-fwcutter (helps if you have a wired connection) then just do the following:
```
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe b43
sudo ifconfig up
```You should be able to scan networks via sudo iwlist scan and try to connect.  If that works, then you will need to clean up the blacklisting and /etc/modules so that it will load up on future boots.

I have enabled the b43 cutter...
iwscan list output gives me

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: some MAC addrress
                    ESSID:"Whiskey"
                    Mode:Master
                    Channel:12
                    Frequency:2.467 GHz
                    Quality=90/100  Signal level=-42 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000c6660a122

also a quick ipconfig -a gives me

eth0      Link encap:Ethernet  HWaddr 00:17:a4:cd:eb:9c  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:a4ff:fecd:eb9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:517513 (505.3 KB)  TX bytes:129400 (126.3 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:15:37:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:73:15:37:19  
          inet addr:169.254.2.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71316 (69.6 KB)  TX bytes:71316 (69.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-15-37-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


WICD knows my Wireless is there...I'm using the 'broadcom' supplicant driver in the wicd menu list, have tried the wext and nwdiswrapper also,  no joy.

---

### Post by Ayuthia on 2008-05-10
> **ww711 said:**
> I have enabled the b43 cutter...
iwscan list output gives me

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: some MAC addrress
                    ESSID:"Whiskey"
                    Mode:Master
                    Channel:12
                    Frequency:2.467 GHz
                    Quality=90/100  Signal level=-42 dBm  Noise level=-68 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000c6660a122

also a quick ipconfig -a gives me

eth0      Link encap:Ethernet  HWaddr 00:17:a4:cd:eb:9c  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:a4ff:fecd:eb9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:517513 (505.3 KB)  TX bytes:129400 (126.3 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:15:37:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:73:15:37:19  
          inet addr:169.254.2.153  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71316 (69.6 KB)  TX bytes:71316 (69.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-15-37-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


WICD knows my Wireless is there...I'm using the 'broadcom' supplicant driver in the wicd menu list, have tried the wext and nwdiswrapper also,  no joy.

You might try a channel less than 11 (1, 5, or 6).  Some drivers are not able to connect to the higher channels.  If you aren't, you might also try disconnecting the wired connection.  That can interfere with the wireless.  I have found that wext works with wicd with the b43 driver.

---

### Post by ww711 on 2008-05-10
> **Ayuthia said:**
> You might try a channel less than 11 (1, 5, or 6).  Some drivers are not able to connect to the higher channels.  If you aren't, you might also try disconnecting the wired connection.  That can interfere with the wireless.  I have found that wext works with wicd with the b43 driver.

Changed channel to 5 and tried various wpa supplicants, still no joy....

---

### Post by ww711 on 2008-05-10
For some reason, it works now!!!

Posting on the laptop with wireless.

Brief summary of apps that I'm using that may or may not aid others.

wicd
niswrapper driver installation tool - pointing to the bcwml5.inf file
b43-fwcutter

Thanks Ayuthia for the persistence in replies.

---

