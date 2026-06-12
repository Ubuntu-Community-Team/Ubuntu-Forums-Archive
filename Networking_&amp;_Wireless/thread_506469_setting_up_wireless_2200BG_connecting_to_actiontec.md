---
title: "setting up wireless 2200BG connecting to actiontec"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by xcalibur32 on 2007-07-21
Hi,
I am trying to set-up my wireless. I tried different methods posted but none worked. 

Here is my config:
**lspci|grep Wireless**
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
**iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:731  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The scanning works properly 


I need to connect to: 

          Cell 02 - Address: 00:0F:B3:08:C3:DE
                    ESSID:"#####"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    Extra: Last beacon: 40ms ago

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet dhcpconf 
wpa-driver wext
wpa-conf managed
wpa-ssid #####
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmy WPA-PSK
wpa-psk hex-generated-spk

Any help is appreciated 

Thanks

---

### Post by bernied on 2007-07-21
What happens when you try to do the dhcp manually:
```
sudo dhclient eth0
ifconfig
```
I'm not familiar with the dhcpconf at the end of the iface line in the interfaces file. Is that a typo?

---

### Post by bernied on 2007-07-21
woah, sorry. I was confused, thought that scan output was from iwconfig. So you're not yet associated, right?

When I was messing about with this stuff, I got unstuck with old wpa_supplicant processes from previous hacking attempts. They somehow stop any changes to the interface. So
```
ps -ef | grep wpa
```
Then 'kill -9' any processes that look like they shouldn't be there. 

Or reboot any time you make a change - gets kind of tedious.

My most recent install on the laptop with that interface uses network-manager, which seems to be working, for now.

---

