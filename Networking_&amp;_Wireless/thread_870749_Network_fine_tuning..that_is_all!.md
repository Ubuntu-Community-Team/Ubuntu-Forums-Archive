---
title: "Network fine tuning..that is all!"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by alspal on 2008-07-26
alspal@alspal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.462 GHz  Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level:-76 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alspal@alspal-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:61:62:58:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xd000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0d:61:62:58:61  
          inet addr:169.254.5.59  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87156 (85.1 KB)  TX bytes:87156 (85.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:19:5b:d2:dd:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:37170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78635 errors:10752 dropped:10752 overruns:0 carrier:0
          collisions:120 txqueuelen:1000 
          RX bytes:3652614 (3.4 MB)  TX bytes:0 (0.0 B)
          Interrupt:19 

alspal@alspal-desktop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1D:6A:20:42:F8
                    ESSID:"Goosen-WLAN"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s

when running dhclient
output is no dhcpoffers recieved
sleeping


alspal@alspal-desktop:~$ gedit /etc/network/interfaces

auto lo
iface lo inet loopback



alspal@alspal-desktop:~$ sudo gedit /etc/Wireless/RT61STA/rt61sta.dat


[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=Goosen-WLAN
NetworkType=Infra.....Dont know if this is correct
Channel=0
AuthMode=WPAPSK.....Dont know if this is correct
EncrypType=AES.....Dont know if this is correct
DefaultKeyID=1
Key1Type=0
Key1Str=HNA16A0064090....this is the number under the router, should this be the network password?
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
WmmCapable=0
APSDCapable=0
APSDAC=0;0;0;0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0
NativeWpa=1






I have posted the output from what I think is necessary for you to help me configure my network settings. I have at the moment one computer running Windows connected to the existing network "Goosen-WLAN" with the following network settings:


For the broadband 802.11g network adapter
using windows to configure internet settings
network ssid: Goosen-WLAN
network authentication: WPA-PSK
Data encryption: AES
Network key:########
networks to access: any available network(access point preferred)


For WAN miniport PPPOE
broadband connection: point to point protocal over ethernet
obtain ip address automatically


That is it, from this u should be beable to see if what is not corresponding and therefore what need to be changed. I am a total newbie at ubuntu..please help.

---

### Post by caljohnsmith on 2008-07-26
Have you tried to set up your connection with the Network Manager (System > Admin > Network)? Your iwconfig output does not show your network's ESSID, "Goosen-WLAN", so it doesn't appear you are fully connected. And by the way, you should run "sudo iwlist ra0 scan" instead of "iwlist scanning" because if you don't run that command as root, it will merely return the last cached scan (which may not be currently accurate).

---

### Post by alspal on 2008-07-26
Yes, I have tried setting up my network connection through System > Admin > Network

I know I am not fully connected that is why I am writing this post, what can I do to be connected..that is the question?

sudo iwlist ra0 scan, produces the same output as iwlist scanning...any other help..please or suggestions

---

### Post by caljohnsmith on 2008-07-26
Is that "Goosen-WLAN" network yours? Can you turn off the encryption? That would help alot in troubleshooting your connection problems, because that would remove one more layer of complexity. After disabling encryption, try connecting again with the Network Manager, and be sure to specify DHCP to get your IP address. And make sure you have DHCP enabled in your router (I'm assuming the Goosen-WLAN belongs to you). Then at the command line do "route": see what IP address it returns for the entry that says "default". Then try pinging that address, e.g. "ping 192.168.1.1" or it will be a similar IP address most likely. Let me know what you get. Please post the output of all those commands along with "ifconfig" and "iwconfig" after you connect without using encryption.

---

