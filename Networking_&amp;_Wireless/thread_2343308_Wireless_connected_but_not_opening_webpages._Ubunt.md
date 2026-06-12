---
title: "Wireless connected but not opening webpages. Ubuntu 16.04"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by Federico_Carta on 2016-11-15
Hi, I am relatively new to Ubuntu, and I have just installed 16.04 on a Acer Aspire Nitro V17 Black Edition.
I have a strange problem with the Wifi. It looks connected normally (network manager recognized all the different connections around, and let me connect to any) but still I am not able to open any webpage.
Could someone please help?
Thank you very much

---

### Post by ajgreeny on 2016-11-15
Could be a DNS problem.

Open a terminal and run command ```
ping 216.58.204.174 && ping google.com
```and copy back the output here.
Please use **"Code tags"** for the terminal output, See below for a "How-To"
Also click on your network icon and show us what the "Connection information" says for **Primary DNS:**

---

### Post by Federico_Carta on 2016-11-15
Thanks for the quick reply.
I cannot ping anything, apparently... I get

```

ping 216.58.204.174 && ping google.com
PING 216.58.204.174 (216.58.204.174) 56(84) bytes of data.
From 192.168.44.168 icmp_seq=1 Destination Host Unreachable
From 192.168.44.168 icmp_seq=2 Destination Host Unreachable

```
...
Then it goes on forever, incrementing the seq=N.

If I only run ping google.com I get
```

ping google.com
ping: unknown host google.com

```

In "Connection information" for Primary DNS it says 
150.244.9.100

---

### Post by ajgreeny on 2016-11-15
How do you connect to the network and have you any idea where that Primary DNS comes from?  I can ping that IP from here but do not know what it is.
A quick search shows it to be a nameserver in Spain; does that make sense?

If you are using a router can you ping that? If you are not sure about that, its IP is usually shown on its label and most likely is 192.168.1.1 or something similar.

---

### Post by Federico_Carta on 2016-11-15
Hi. 
Yes, I work in Madrid, Spain, and that "primary DNS" is the one of the connection we use at my workplace.
I don't know where it comes from precisely.
I tried now to ping the primary DNS, but it does not work either. The output is the same as when I tried to ping 216.58.204.174 before.

However, I think the problem is not only with this specific connection.
With this I mean that I tried to connect to many different connections in the past days, and always the situation is the same: properly connected but not loading webpages.
So maybe it is more related to some general setting of my PC.

I don't know if this could be of any help...

---

### Post by ajgreeny on 2016-11-15
Sorry, but I think this is now beyond my ability to help you further.
Hopefully others will be along soon and may be able to help you more than I've been able to.

---

### Post by ahears on 2016-11-15
I apologize in advance if I am stepping on anyones "toes" by responding  here. If this is happening everywhere would it be safe to assume you are  not using a web portal to access the Internet? First try to ping  '8.8.8.8'. If you can ping 8.8.8.8 and get a response, but ping  'google.com' and get a timeout, then it's a Domain Name Server or DNS  problem. However, if you cannot ping 8.8.8.8 or any other website (which  may true in your case) I would first look at your cables and physical  connection (Layer 1) to make sure that you are actually connected. Note  that if you are using a Primary DNS server address from work  (216.58.204.174), it is not accessible from outside the work place and  this is the second part of your problem. The 216.58.204.174 IP address  is a non-routable Class C Address, and will only be used for inside your  Work place. I would use Google (8.8.8.8) or someone else you trust for  DNS outside of work. * See comment area below. Anyway, I would look at  the IP configuration for your computer to make sure you are addressed  correctly. For this we can use DHCP or Dynamic Host Control Protocol.  This is what will automatically configure you address information so you  can connect everywhere else. To do this we need to answer a few  questions: 

1) Are you manually entering the address information (Statically  assigned), or are you using the DHCP to have your network interface  auto-configured for you? To find out which you can view this in the  '/etc/network/interfaces' file by opening a terminal and entering the  following:
```

cat /etc/network/interfaces

```

-Please post the result.

2) Which interface are you using, wired or wireless, and what is the  state of these interfaces when connected to the access point? (eth0 or  wlan0)

```

ifconfig

```
and..
```

iwconfig

```
and..
```

sudo lshw -C network

```

-Please post the result.

If you are statically assigned, you will need to change your network  configuration to use DHCP in your '/etc/network/interfaces' file: 
```

sudo cp /etc/network/interfaces /etc/network/interfaces.bak
gksu gedit /etc/network/interfaces

```
Then modify or add the lines: ** See comment area below.
> 
auto **[COLOR=#000000][FONT=&quot]enp8s0[/FONT][/COLOR]**
iface **[COLOR=#000000][FONT=&quot]enp8s0[/FONT][/COLOR]** inet dhcp


* DNS is what converts the numbers of an IP address (8.8.8.8) into the  human readable website name, such as 'Google.com'. You should create  another wireless profile for you to use away  from  work, and do not  modify the same profile you use at work - for use  everywhere else. This  will help simplify the problem, because from what you have told us it  looks like you are "adopting" the existing profile from work and editing  it, and this has created some confusion with the settings. The file for  this is found under '/etc/NetworkManager/system-connections/'  but I  would only use the GUI tool 'nm-applet' to create a new  one. Usually  this is located at the toolbar at the top of your screen and looks like a  WiFi indicator. Use this to set your IP and DHCP settings to  'Automatic', reconnect, and save the profile as something other than  "Work", maybe call it "Mobile". Using the 'nm-applet' might be easier  than using the command line.

****** Assuming that the "**[COLOR=#000000][FONT=&quot]enp8s0[/FONT][/COLOR]**" *wired* interface is the issue! If it is the **[COLOR=#000000][FONT=&quot]wlp7s0[/FONT][/COLOR]** interface or "wireless" interface then modify that entry accordingly  with '**[COLOR=#000000][FONT=&quot]wlp7s0[/FONT][/COLOR]**' instead of '**[COLOR=#000000][FONT=&quot]enp8s0[/FONT][/COLOR]**' and reboot, then post the results.

---

### Post by Federico_Carta on 2016-12-12
Thank you for your answer Ahears, and sorry for the late reply.
I still have not been been able to solve the problem.

I confirm that with any wifi connection, I get a timeout when trying to ping 8.8.8.8, or google.com, or any other website.
The connection looks like it is established, but I simply cannot open any webpage.
With the ethernet cable, everything works fine tough.

Here I will answer the questions above:
1) ```

federico@FedeLaptopWork:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

2)

This is the output of "ifconfig".

```

federico@FedeLaptopWork:~$ ifconfig
enp8s0    Link encap:Ethernet  IndirizzoHW 30:65:ec:6e:56:91  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35127 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:62392544 (62.3 MB)  Byte TX:17441881 (17.4 MB)

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3720 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1 
          Byte RX:308417 (308.4 KB)  Byte TX:308417 (308.4 KB)

wlp7s0    Link encap:Ethernet  IndirizzoHW d0:53:49:48:24:b3  
          indirizzo inet:192.168.42.209  Bcast:192.168.42.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::b3ee:942d:8f7:e03c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4548 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:2716402 (2.7 MB)  Byte TX:507776 (507.7 KB)

```

This one for "iwconfig"
```

federico@FedeLaptopWork:~$ iwconfig
lo        no wireless extensions.

enp8s0    no wireless extensions.

wlp7s0    IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:6C:F5:56:50   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:51   Missed beacon:0

```

And finally lshw -C network...
```

federico@FedeLaptopWork:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 20
       serial: d0:53:49:48:24:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-51-generic firmware=SW_RM.1.1.1-00157-QCARMSWPZ-1 ip=192.168.42.209 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:35 memory:d1400000-d15fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 0c
       serial: 30:65:ec:6e:56:91
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:31 ioport:3000(size=256) memory:d1700000-d1700fff memory:d1600000-d1603fff

```

As for the last point, how could I see if I am statically assigned?

I hope someone could help with this.
Thanks in advance.

---

### Post by jeremy31 on 2016-12-12
I wonder if the wifi powersave is causing issues with your wifi
 ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by Federico_Carta on 2016-12-12
Thanks for the answer jeremy31.
I tried this, but it did not have any effect.

---

### Post by jeremy31 on 2016-12-12
Can you look at the wireless script link in my signature and post your results?  I would imagine the eduroam has multiple access points with the same SSID and it is possible that you may be roaming between them and need to go into network manager settings for eduroam and set a MAC address for BSSID to hopefully keep it from roaming

---

### Post by Federico_Carta on 2016-12-13
Thanks for the reply.
Here is the result of the script. I apologize but I had some problem uploading the .tar.gz file, as well as the .txt file.
So I copy here the content of the .txt file.

```


########## wireless info START ##########

Report from: 13 Dec 2016 11:05 CET +0100

Booted last: 13 Dec 2016 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-51-generic #72-Ubuntu SMP Thu Nov 24 18:29:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0804]
    Kernel driver in use: ath10k_pci

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04f2:b469 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 06cb:2970 Synaptics, Inc. touchpad
Bus 003 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 005: ID 04ca:3011 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
wl                   6365184  0
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  4 wl,ath,mac80211,ath10k_core
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  40960  3 i915,acer_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp8s0    Link encap:Ethernet  HWaddr <MAC 'enp8s0' [IF1]>  
          inet addr:150.244.221.244  Bcast:150.244.221.255  Mask:255.255.255.0
          inet6 addr: fe80::fdc6:b973:90ea:f2ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81057660 (81.0 MB)  TX bytes:887828 (887.8 KB)

wlp7s0    Link encap:Ethernet  HWaddr <MAC 'wlp7s0' [IF2]>  
          inet addr:192.168.42.209  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b3ee:942d:8f7:e03c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82441 (82.4 KB)  TX bytes:10598 (10.5 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

wlp7s0    IEEE 802.11abgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'eduroam' [AN8]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:22   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         150.244.221.1   0.0.0.0         UG    100    0        0 enp8s0
0.0.0.0         192.168.42.1    0.0.0.0         UG    600    0        0 wlp7s0
150.244.221.0   0.0.0.0         255.255.255.0   U     100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.42.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp7s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1178     1  0 11:00 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connessione via cavo 1
GENERAL.CON-UUID:                       dff6ad6c-93c5-3e78-aa1a-f3de382acc53
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dff6ad6c-93c5-3e78-aa1a-f3de382acc53 | Connessione via cavo 1
IP4.ADDRESS[1]:                         150.244.221.244/24
IP4.GATEWAY:                            150.244.221.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             150.244.9.100
IP4.DNS[2]:                             150.244.9.200
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1481644814
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 150.244.221.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 150.244.221.244
DHCP4.OPTION[17]:                       unknown_224 = FG600B3911600883
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 10800
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 150.244.221.255
DHCP4.OPTION[22]:                       domain_name_servers = 150.244.9.100 150.244.9.200
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 21600
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 18900
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 150.244.221.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 150.244.221.1
IP6.ADDRESS[1]:                         fe80::fdc6:b973:90ea:f2ab/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-51-generic
GENERAL.FIRMWARE-VERSION:               SW_RM.1.1.1-00157-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlp7s0
GENERAL.IP-IFACE:                       wlp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     eduroam
GENERAL.CON-UUID:                       a9aaed34-fe61-4d64-b5ed-7ca1425696c0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   65794a2e-fb8f-48ae-a2d6-97249594ef32 | IFT
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   a9aaed34-fe61-4d64-b5ed-7ca1425696c0 | eduroam
IP4.ADDRESS[1]:                         192.168.42.209/24
IP4.GATEWAY:                            192.168.42.1
IP4.DNS[1]:                             150.244.9.100
IP4.DNS[2]:                             150.244.9.200
IP4.DNS[3]:                             161.111.10.3
IP4.DNS[4]:                             161.111.80.11
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.42.1
DHCP4.OPTION[10]:                       expiry = 1481666613
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 43200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.42.209
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.42.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.42.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 150.244.9.100 150.244.9.200 161.111.10.3 161.111.80.11
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.42.1
IP6.ADDRESS[1]:                         fe80::b3ee:942d:8f7:e03c/64
IP6.GATEWAY:                            

SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
IFT      <MAC 'IFT' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2              no        
ICMAT    <MAC 'ICMAT' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2              no        
IFT      <MAC 'IFT' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2              no        
ICMAT    <MAC 'ICMAT' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2              no        
ICMAT    <MAC 'ICMAT' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2              no        
eduroam  <MAC 'eduroam' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
eduroam  <MAC 'eduroam' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
eduroam  <MAC 'eduroam' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 802.1X  yes     * 
IFT      <MAC 'IFT' [AN9]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2              no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MOVISTAR_FBAC]] (600 root)
[connection] id=MOVISTAR_FBAC | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=MOVISTAR_FBAC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IFT]] (600 root)
[connection] id=IFT | type=wifi | permissions=user:federico:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=IFT
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:federico:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=eduroam
[802-1x] ca-cert=/home/federico/ca-bundle_uam.pem
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp8s0    no frequency information.

wlp7s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

wlp7s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-51-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[ath10k_pci]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-51-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-51-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.963262] r8169 0000:08:00.0 enp8s0: link up
[   13.963284] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready
[   74.695278] ath10k_pci 0000:07:00.0: no channel configured; ignoring frame(s)! (repeated 3 times)
[  210.060073] wlp7s0: authenticate with <MAC 'eduroam' [AN8]>
[  210.107617] wlp7s0: send auth to <MAC 'eduroam' [AN8]> (try 1/3)
[  210.111097] wlp7s0: authenticated
[  210.111202] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[  210.111205] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
[  210.114376] wlp7s0: associate with <MAC 'eduroam' [AN8]> (try 1/3)
[  210.121502] wlp7s0: RX AssocResp from <MAC 'eduroam' [AN8]> (capab=0x431 status=0 aid=4)
[  210.123670] wlp7s0: associated
[  210.123709] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0: link becomes ready

########## wireless info END ############


```

Anyways, I wanted to point out that the problem is not related only to Eduroam.
Any wireless connection does the same: I can see the connection and connect with it, but can't open any webpage nor ping any adress.
I tried it with a free wifi connection of the city of Madrid, as well as my home connection and one at a friend's house.
So my guess is that this problem does not depend on Eduroam specifically, but rather some configurations of the laptop.

Again thank you for your time.

---

### Post by jeremy31 on 2016-12-13
Lets set the country code
```

sudo iw reg set ES
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda

```
Then we can remove the broadcom driver that was installed
```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```
Reboot

Does the IFT network work better?

---

### Post by Federico_Carta on 2016-12-13
I did the two steps above, but the situation is the same as before.
Both with IFT and eduroam.

Is there anything else I could try?

I read that Qualcomm Atheros QCA6174 sometimes has driver issues with Ubuntu 16.04.
Could this be the case?

---

### Post by jeremy31 on 2016-12-13
You could try Ubuntu 16.10 and see if works any better

---

### Post by Federico_Carta on 2016-12-13
Some time ago I moved to 16.10, but the same problem was present.
Then I decided to switch back to 16.04 due to some other problems I was experiencing with 16.10.
So in the end I think I prefer the 14.04 LTS, at least for the moment...

I really don't know what this wifi problem could be, 'tough...

---

### Post by Federico_Carta on 2016-12-15
Could this problem possibly be related to what Ahears was saying some posts before, about modifying the '/etc/network/interfaces' file?
In my case, that file reads

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

However, I checked that changing "loopback" to "dhcp" still does not work.

---

### Post by jeremy31 on 2016-12-15
About the only other thing I can think of it to go into Network Manager settings and change IPv6 to off or ignore for the wireless connections

---

### Post by Federico_Carta on 2016-12-16
I tried to switch off IPv6 in network manager, but nothing changes...
Bobnn, what is rvrrthing?

---

### Post by Federico_Carta on 2016-12-16
Ah I see...

Anyways this problem with the wifi is quite annoying, and I don't know anymore what to do.
Anyone has something else to suggest?

---

### Post by Federico_Carta on 2017-01-09
Hi, I am still trying to solve the problem, and I think I have an update.
My driver is ath10k. 
Now, by running

```

dmesg | grep ath10k

```

I get the following output

```

[    9.231023] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    9.468073] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[   10.729674] ath10k_pci 0000:07:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff sub 11ad:0804) fw SW_RM.1.1.1-00157-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   10.729679] ath10k_pci 0000:07:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   10.812690] ath10k_pci 0000:07:00.0 wlp7s0: renamed from wlan0
[   16.988514] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[   16.988518] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
[  579.027731] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[  579.027733] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
[  615.940463] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[  615.940468] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
[ 1179.052835] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[ 1179.052840] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP

```

In pariticular the line that concerns me is 

```

Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2

```

So in particular I think that my problem is related to the firmware.
Is there anything I could do?

Long ago, with the same machine but with Ubuntu 14.04 I had a very related issue, discussed here.
[https://ubuntuforums.org/showthread.php?t=2317452&page=2](https://ubuntuforums.org/showthread.php?t=2317452&page=2)

Is it possible to do now something along the lines of that?
The error seems very similar...

---

### Post by jeremy31 on 2017-01-09
I am not worried about that firmware file as it doesn't exist yet.  The firmware Ubuntu is now using came from that source.  I am more concerned with these errors
```
[  579.027733] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
[  615.940463] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
```
This might be causing constant disconnect/reconnects.  I do know that some of the newer Qualcomm cards do not work well with older access points

See [this post](https://ubuntuforums.org/showthread.php?t=2348926&p=13592787#post13592787)

I recommend that you file a bug report also, after an internet search for ```
"disabling VHT as WMM/QoS is not supported by the AP" ath10k
```
I only saw one issue that was ever solved and that was because the poster updated the wireless access point

---

### Post by Federico_Carta on 2017-01-10
> **jeremy31 said:**
> 
I only saw one issue that was ever solved and that was because the poster updated the wireless access point

I am no expert at all, but what is strange to me is that the same laptop, with exactly the same wireless access point, worked fine with earlier versions of Ubuntu.
But in 16.04 and 16.10 this problem is present. So I tend to suspect this problem is more related to an incompatibility of 16.04 with the Qualcomm card, rather than the access point itself.
Also because I tried to connect to approximately 50 different wifi networks over the past months, and the problem was identically in all of them.
I find it unlikely that the problem is in the access point.

I hope there will be a way to solve this problem somehow, since it seems quite common and not being able to use the wifi is very frustrating.

Later I look into how to do a bug report. I never did one.

---

### Post by Federico_Carta on 2017-03-22
Hi everybody.

I wanted to kindly ask if by chance there is any update regarding this situation.

---

### Post by jeff666 on 2017-03-22
Basically if 'ping   'ping 8.8.8.8' doesn't work, but wifi is connecting it is joining the network and decrypting the wifi (so data link layer is ok) moving up to the network layer (ip) is where your problem is. Most likely this is a dhcp (what tells you your ip) error caused by slow connection and time out with the router try '
```

sudo dhclient -r wlp3s7
sudo dhclient wlp3s7

```
 (while already connected) 
now try your web browser or ping. now if that doesn't work the router is either blocking you or the router doesn't have a dhcp server. If the router doesn't have a dhcp server the only way to connect is with a static connection. This could be simple but the guy that set it up could have also made its set up to be more complex. try this 'sudo nano /etc/network/interfeaces' and add to the bottom
```

auto wlp3s7
iface wlp3s7 inet static
address 192.168.1.199
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 208.67.222.222 208.67.220.220
wpa-ssid <name of wifi here>
wpa-psk <wifi passwprd here>

```
(note syntax must be perfect)
now run this in order to get the connection up
```

sudo systemctl stop NetworkManager
sudo dhclient -r wlp3s7
sudo ifconfig wlp3s7 down
sudo ifup wlp3s7

```
 and try
```

ping 192.168.1.1
ping 208.67.222.222
ping duckduckgo.org
firefox -new-window duckduckgo.org

```

post some more output and i will try and help you some more if that doesn't work like also include uname -r i would also like to know when the last time you ran sudo apt upgrade ?

---

### Post by jeff666 on 2017-03-22
sorry reading this again you have the wrong driver thats all:KS first run 'sudo find /lib/modules -iname  *BCM* and see if anything comes out if not then you need to download install the the right driver and stop old driver(see instructions below to stop old driver). If a broadcom driver does come up with your search 'lsmod | grep -i bcm' to see if it is loaded and competing with ath10k. If is is loaded then you can remove ath10k with 'rmmod ath10K' and the wifi should work untill reboot. Now to make this work after a reboot or if BCM driver isn't loaded just run 'sudo nano /etc/modprobe.d/blacklist' and add "black-list ath10k" to the bottom and reboot problem should be solved.To download the right driver first 'lspci' and find the broadcom output which should have the name of the device. You will have to figure out what package you need to install do a little research try search online "ubuntu <card name> what driver" or try 'apt search bcm' (i think the right package may be "bcmwl-kernel-source"  which might contain a few drivers the kernel should know which to use just black list the ath10k).

---

### Post by Federico_Carta on 2017-03-23
Hi, thank you for your reply.

If I do
```

sudo dhclient -r wlp3s7
sudo dhclient wlp3s7

```
then the first command runs fine, but for the second I get the error
```

Cannot find device "wlp3s7"

```
This happens indifferently, with two different wifi connenctions.

Then I have not tried the subsequent steps you proposed in your first comment, since I was confused about your second comment.
Sorry about that.
Do you think it is a dhcp problem, or more like a driver problem?

Regarding your second comment, the output of sudo find /lib/modules -iname  *BCM* is the following
```

/lib/modules/4.4.0-66-generic/kernel/net/can/can-bcm.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/staging/media/bcm2048
/lib/modules/4.4.0-66-generic/kernel/drivers/staging/media/bcm2048/radio-bcm2048.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/input/mouse/bcm5974.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/watchdog/bcm7038_wdt.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/net/phy/bcm-phy-lib.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/net/phy/bcm87xx.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/net/phy/mdio-bcm-unimac.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/net/phy/bcm7xxx.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/phy/phy-bcm-kona-usb2.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/media/dvb-frontends/bcm3510.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/regulator/bcm590xx-regulator.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/bcma
/lib/modules/4.4.0-66-generic/kernel/drivers/bcma/bcma.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/usb/host/bcma-hcd.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/mfd/bcm590xx.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/bluetooth/bcm203x.ko
/lib/modules/4.4.0-66-generic/kernel/drivers/bluetooth/btbcm.ko
/lib/modules/4.8.0-040800-generic/kernel/net/can/can-bcm.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/staging/media/bcm2048
/lib/modules/4.8.0-040800-generic/kernel/drivers/staging/media/bcm2048/radio-bcm2048.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/input/keyboard/bcm-keypad.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/input/mouse/bcm5974.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/phy/bcm-phy-lib.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/phy/bcm87xx.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/phy/mdio-bcm-unimac.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/phy/bcm7xxx.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/ethernet/broadcom/bcmsysport.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/net/dsa/bcm_sf2.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/phy/phy-bcm-kona-usb2.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/media/dvb-frontends/bcm3510.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/leds/leds-bcm6358.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/leds/leds-bcm6328.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/regulator/bcm590xx-regulator.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/bcma
/lib/modules/4.8.0-040800-generic/kernel/drivers/bcma/bcma.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/usb/host/bcma-hcd.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/mfd/bcm590xx.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/bluetooth/bcm203x.ko
/lib/modules/4.8.0-040800-generic/kernel/drivers/bluetooth/btbcm.ko

```
The only broadcom I see here is for ethernet, but ethernet works perfectly so I don't kno if this driver is what we are looking for.

The output of lsmod | grep -i bcm is
```

btbcm                  16384  1 btusb
bluetooth             548864  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb

```

Now, there is this "btbcm" driver, but I don't know if this is the correct one.
On the other hand, running "rmmod ath10K" gives the following error:
```

rmmod: ERROR: Module ath10K is not currently loaded

```

So I am extremely confused. Does it mean I have no driver at all, nor ath10k, nor broadcom?
If so, why Network Manager works fine, and tells me I am connected to the wifi (qithout allowing me to open webpages) ?
Do I really have no driver, and need to download one?

Furthermore, you asked me what is the last time I did sudo apt-get update and sudo apt-get upgrade.
It was yesterday.

Thank you very much for all your help with this issue.

---

### Post by jeff666 on 2017-03-23
try 
rmmod bluetooth
modeprobe ath10K

if that works just black list bluetooth both my posts are actually wrong i thought you had a broadcom card lol (my eyes play tricks) you have a qualcom however you do have a broadcom driver for bluetooth that could be an issue try that if not
you could try 'rmmod ath10k; modeprobe ath9k' (there could be some risk with the ath9k you might want to research what driver someone else has used with that card and works, worst case i would just go buy a intel card have it installed, probably cost you about 20$ if you did it your self its not very hard)

---

### Post by Federico_Carta on 2017-03-24
Hi, thanks for the reply.
So, if I do "rmmod bluetooth" I get the following error.

```

rmmod: ERROR: Module bluetooth is in use by: btrtl btintel bnep btbcm rfcomm btusb

```

Instead, if I do "rmmod ath10k; modeprobe ath9k", I get this other error

```

rmmod: ERROR: Module ath10k is not currently loaded

```

Does this mean I don't have the ath10k driver?

---

### Post by jeff666 on 2017-03-24
```

lsmod | grep -i ath                                                                                       //should be called ath10k_pci
sudo apt install bluez aircrack-ng wireless-tools wpa_supplicant             //install blue tooth,& wireless utilities will need Internet for this:
hciconfig                                                                                                      //to get name of interface 
sudo hciconfig <name of interface here>  down                                      // bring down bluetooth

```

now try wifi on 2.4ghz if not

```

sudo systemctl stop NetworkManager                                                                                            // stops network manager might also be named network-manager
sudo ifconfig wlp3s7 down                                                                                                               //bring down interface
sudo airodump-ng  wlp3s7                                                                                                                 //will show you names of access points in area
CTRL-c                                                                                                                                                // to stop it take note of the channel of your accesses point (CH column) 
sudo iwconfig wlp3s7 channel <what ever number here>                                                             //set your card to static channel may not support this but could 
sudo touch /etc/wpa_supplicant.conf                                                                                              // make a file
sudo chmod o+w /etc/wpa_supplicant.conf                                                                                  //set permission on that file
wpa_passphrase your-wifi-name password > /etc/wpa_supplicant.conf                                      // add your wifi info to file
nano /etc/wpa_supplicant.conf                                                                                                      

```

change the line with you password on it to say key_mgmt=WPA-PSK
leave the rest how it is

```

sudo dhclient -r  wlp3s7                                                                                  //clear any old ip info from you interface
sudo ifconfig wlp3s7 up                                                                                 //bring up interface
sudo wpa_supplicant -i wlp3s7 -c /etc/wpa_supplicant.conf                        //decrypt your access point look at out put if its says wrong password you might need '' or "" around name or password on the wpa_passphrase part
CTRL-c                                                                                                            //put out put in background which may spit out at you you could also just open new terminal
sudo dhclient wlp3s7                                                                                    //get a ip adresse for your interface 
ping google.com
try web browser

```
this could work because it might reduce the work network manager puts on your card (rawest way to connect to wifi) if it does work it won't work well you will have bad speeds. your cards firmware isn't actually supported ath10k_pci but is similar (older) than ones that are supported so that sums up why it kinda of works. Sometimes changing a wifi card is as simple as unscrewing a backplane and unhooking antennas, you could find a very cheap solution on ebay or take apart a old competer on craigs-list . There might also be a way to use windows driver although i haven't done it my self so im not sure. sorry if i couldn't help

---

### Post by Federico_Carta on 2017-03-28
Hi,

By doing your commands, I find an error in 
```

sudo apt install bluez aircrack-ng wireless-tools wpa_supplicant

```

It says "impossible to find wpa_supplicant.

Then doing 
```

hciconfig                                                                                                      //to get name of interface
sudo hciconfig hci0  down

```
works with no error, but has no effect at all on the wifi.

Then doing 
```

sudo ifconfig wlp3s7 down

```

It says that there is "no device corresponding to wlp3s7".

What does that mean?

---

### Post by ahears on 2017-06-20
Is this thread still open? Please refer to my original post. Read it carefully. It looks like I may have overlooked the fact that you are connected on '[FONT=Ubuntu Mono][COLOR=#000000]wlp7s0" not 'wlan0'. This is because of the new naming scheme that is in use with later releases of Ubuntu. That said, lets try some of the basics to see what is going on. [/COLOR][/FONT][COLOR=#000000][FONT=&amp]In your first post I see that you bind two commands together using '&&' at the terminal. Don't do that while we are diagnosing your problem in the future. This is because we cant tell which instruction in your set of commands is throwing the error. Lets try again, please[/FONT][/COLOR][COLOR=#000000][FONT=&amp] disable IPV6 in your 'nm-applet' for your WiFi connection. Check the ignore box to disable it and just to eliminate that as a problem. This is because your IPV6 could be mis-configured at the router! and that is a whole other situation. After disabling IPV6 start again here: [/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
**(1)**[FONT=Ubuntu Mono][COLOR=#000000]```
ping 127.0.0.1
``` 
If you get a response then your network interface card is fine because it sends and receives OK. This is a self diagnostic simulation that sends a packet out through a built in loopback connector [/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]which then receives the same packet back if the circuitry is working and not damaged[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000].[/COLOR][/FONT]
[COLOR=#000000]**(2)**[FONT=Ubuntu Mono]```
ping 8.8.8.8 
``` If you can get a response, that is good because you can see Google's server, and you have a valid IP Address. If not, then we are not getting past your router. Please see step 5, complete the steps there and reboot, and start this again from step 1.[/FONT]
[/COLOR]**[COLOR=#000000][FONT=&amp](3)[/FONT][/COLOR]**[FONT=Ubuntu Mono][COLOR=#000000]```
traceroute 8.8.8.8 
``` 
The very first IP listed at position 1 of the output IS the first router between your PC and the Internet. Number 2 is the second router and so on. How far does the traceroute go? Please post the results. It should trace all the way to 8.8.8.8 and list every router from you to Google (8.8.8.8 is Google.com but without DNS to translate the number into a human readable name). This will tell us how far your internet connection is going before it looses contact with the internet. If there are no IP addresses listed by the 'traceroute' command, this means you do not have a valid IP address assigned by the DHCP server in the router Access Point (AP) you are connecting to.[/COLOR][/FONT]
**[COLOR=#000000][FONT=&amp](4)[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]```
ping google.com
``` 
If you can get a response than your DNS is OK and you can view web pages.If you can ping Google.com then your problem IS the web browser you are using. not your network configuration, i[/FONT][/COLOR][COLOR=#000000][FONT=&amp]f not than your problem IS DNS. [/FONT][/COLOR][COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp](5) [/FONT][/COLOR]**[COLOR=#000000][FONT=&amp]Please modify your '/etc/network/interfaces' only if you do not have a valid IP. [/FONT][/COLOR]This will allow your network card to be configured by the Access Point you are using and will get you an address automatically.
```

s[COLOR=#000000][FONT=&amp]udo cp /etc/network/interfaces /etc/network/interfaces.bak
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]gksu gedit /etc/network/interfaces
[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
and add the code:
[/FONT][/COLOR]```

auto [COLOR=#000000][FONT=&amp]enp8s0[/FONT][/COLOR]
[COLOR=#000000]iface [/COLOR][COLOR=#000000][FONT=&amp]enp8s0[/FONT][/COLOR][COLOR=#000000] inet dhcp[/COLOR]

auto [COLOR=#000000][FONT=&amp]wlp7s0
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]iface wlp7s0 inet dhcp
[/FONT][/COLOR]
```

**Please carefully explain when steps '1,2,3,4, or 5' stopped working.**

---

### Post by Federico_Carta on 2017-07-17
Hi, yes. The thread is still open and I still have not been able to fix this problem.

Step (1) works fine.
I can get a response.

Step (2) gives "destination host unreachable".
I am unable to ping 8.8.8.8

I then did what you suggest in step (5) and rebooted.
The situation looks worse then before. Now Network Manager will not even recognize the different WiFi connections.
It says "dispositivo non gestito" (I have the language set in italian) which translates to "device not present".
So it seems that modifying  [COLOR=#000000][FONT=&amp]/etc/network/interfaces did not solve the issue[/FONT].

The original [COLOR=#000000][COLOR=#000000][FONT=&amp]/etc/network/interfaces[/FONT][/COLOR][/COLOR] file was

[COLOR=#000000][COLOR=#000000][FONT=&amp]```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```[/FONT][/COLOR][/COLOR]

The modified [COLOR=#000000][FONT=&amp]/etc/network/interfaces instead looked like

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp8s0
iface enp8s0 inet dhcp

auto wlp7s0
iface wlp7s0 inet dhcp

```[/FONT][/COLOR]

I now have reset the original [COLOR=#000000][FONT=&amp]/etc/network/interfaces file as with the original one I can at least see the different WiFi connections.

Is there something else which I could try?
Thanks for all the help.[/FONT][/COLOR]
[/COLOR]

---

### Post by ahears on 2017-07-17
[FONT=Times New Roman]You restored the 'etc/network/interfaces' file, good. It was worth a try. You should now be booted, at step 2, and unable to ping 8.8.8.8.Correct? Continue to step three and post the output from that command:
```

traceroute 8.8.8.8

```
The 'traceroute' command should tell us what IP your router is using and exactly where (the IP address) the data stops at. Then we can go from there. If there is no IPs listed from the output of the 'traceroute' command then the DHCP server on your router is not assigning you an address and you can stop here! You will not be able to get an address unless you have access to the router you are attempting to request addressing from. You will need either access to configure the router,or you will need an 'static address' given to you by the Admin who controls the router. That said, lets continue&#8230;t[/FONT][COLOR=#222222][FONT=Times New Roman]he last IP shown in the 'traceroute' is where the problem will be. [/FONT][/COLOR][COLOR=#222222][FONT=Times New Roman]This might be the first IP listed. Please post the output from the Traceroute*.[/FONT][/COLOR]

[FONT=Times New Roman]*Note:Honestly I see you have entered a lot of commands since I last posted, so I don't know where you are at with this. Please post the output of:[/FONT]
```

[FONT=Times New Roman][COLOR=#000000]lspci -nnk| grep -iA2 net[/COLOR][/FONT]

```

[COLOR=#000000][FONT=Times New Roman]This may tell me if your wireless drivers are still installed, and [/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]what the status is. If your drivers are now screwed up see this post:[/FONT][/COLOR]
```

[FONT=Times New Roman][[COLOR=#000000]h[/COLOR][COLOR=#222222]ttps://ubuntuforums.org/showthread.php?t=2323812[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2323812")[/FONT]

```

[FONT=Times New Roman]for more info that may help get the driver working again.[/FONT]

---

### Post by Federico_Carta on 2017-07-19
Hi Ahears, yes. 
I modified the interfaces file and then rebooted. However, after doing so the situation seemed worse as Network Manager could not even see any WiFi connection, and so I could not connect.
So what I did was going back with the old interface file. With the old one, I can at least connect to any WiFi connection, but I cannot open webpages.

Right now I have the old interfaces file on.
The output of traceroute is

```

traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
1  192.168.42.123 (192.168.42.123)  1416.756 ms !H  1416.742 ms !H  1416.736 ms !H

```

The output of [FONT=Times New Roman][COLOR=#000000]lspci -nnk| grep -iA2 net[/COLOR][/FONT][FONT=Times New Roman][COLOR=#000000] is[/COLOR][/FONT]
[FONT=Times New Roman][COLOR=#000000]
```

07:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0804]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci, wl
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

It seems there is an Ip adress in the output of traceroute. What does that mean?
Thanks
[/COLOR][/FONT]

---

### Post by ahears on 2017-07-19
The output "**!H**" seen below:
> 
1        192.168.42.123        (192.168.42.123)        1416.756 ms  **!H**        1416.742   **!H**        1416.736   **!H**
 
indicates that your problem is **(1.)** and **(1a.)** below:
> 
[FONT=Segoe UI][COLOR=#2a2a2a]This message indicates one of two problems: **(1.)** the local system has no route to the desired destination, (2.) a remote router reports that it has no route to the destination. The two problems can be distinguished by the form of the message: [/COLOR][/FONT][FONT=Segoe UI][COLOR=#2a2a2a]**(1a)** If the message is simply "Destination Host Unreachable," then there is no route from the local system, and the packets to be sent were never put on the wire. Use the Route utility to check the local routing table.[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=#2a2a2a](2a.) If the message is "Reply From < [/COLOR][/FONT]*IP address*[FONT=Segoe UI][COLOR=#2a2a2a] >: Destination Host Unreachable," then the routing problem occurred at a remote router, whose address is indicated by the "< [/COLOR][/FONT]*IP address*[FONT=Segoe UI][COLOR=#2a2a2a] >" field. Use the appropriate utility or facility to check the IP routing table of the router assigned the IP address of < [/COLOR][/FONT]*IP address*[FONT=Segoe UI][COLOR=#2a2a2a] >.[/COLOR][/FONT]


[COLOR=#000000][FONT=&amp]Y[/FONT][/COLOR]our router never received anything, so we need to check it with the following command 'route' and post the output again:***see note**
```

route -nv

```
Take the time to also make sure that if you are using the 'network-manager' or 'nm-applet' that you configure your connection for IPv4 to use 'automatic (DHCP )' settings and if there is a DNS server manually set, that you set that to be automatic also and clear any manually configured entries there. This can be done by clicking the Wifi logo at the top right and selecting 'edit connections', choose the wireless access point you are working on, and choose the 'IPv4' tab.
[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][FONT=arial]Another solution is to turn off the 'uncomplicated Firewall' or 'ufw' firewall in Ubuntu and try the 'traceroute' process again. [/FONT]
[COLOR=#222222][FONT=Verdana][FONT=arial]```

sudo ufw disable

```
To turn it on again:
```

sudo ufw enable

```
Sometimes this can help to rule out the firewall as a problem. Since you have nothing listening on any ports yet and you are behind a router firewall it should be fine for testing. Also, i[/FONT][/FONT][/COLOR]t is ok to post your internal IP info here because these are not external facing addresses and pose no real external/internal threat, but don't post your external facing IP.

**&#8203;* Note: **[FONT=arial]I would contact the Admin of the AP you are attempting to access and see if they are blocking "icmp packets" and if they are using any type of filtering to prevent access from [/FONT][COLOR=#000000][FONT=arial]'new/unauthorized/unknown'[/FONT][/COLOR][FONT=arial] devices, such as 'mac address filtering' or 'port address filtering'. My college blocks 'ping' (icmp) in the technical labs so I would not be surprised. I would say you have IP and it is [/FONT]'192.168.42.123' assigned by DHCP, but no bytes are sent out on the wire[COLOR=#000000][FONT=arial]. In my opinion, y[/FONT][/COLOR][COLOR=#000000][FONT=arial]ou will need access to configure the router, or you will need to talk to the Admin who controls the router at the workplace about their policies for 'new/unauthorized/unknown' devices on the network. This seems like a company security policy may be in place and I would ask permission to connect a new device to the network. They may also be using an 'web portal' to control access the internet, or administration may have a specific IP address you will need to obtain so you can authenticate and be allowed internet access. That may solve your problem.

If you have attempted these steps on more than one access point (AP), then I would replace the wifi adapter with a known working network adapter [/FONT][/COLOR][COLOR=#000000][FONT=arial]and try again.[/FONT][/COLOR][COLOR=#000000][FONT=arial] A USB Wireless adapter will work for testing purposes. You may have a card which is passing the self test but still not putting packets onto the "wire". If you choose to use a USB key for further testing, disable or remove the old adapter temporarily (there is a WiFi switch on the side of the laptop which can be used for this purpose), and start at step 1 in my first post.[/FONT][/COLOR]

---

### Post by Federico_Carta on 2017-07-20
Hi, the output of 

```

route -nv

```

is the following:

```

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.1    0.0.0.0         UG    600    0        0 wlp7s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp7s0
192.168.42.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp7s0

```

I also tried to disable the firewall as you suggested, and do "traceroute 8.8.8.8" again, and the output is the same I posted before.
So this rules out the firewall as a problem, no?

Anyways, I tried with three different WiFi connections, and the problem is the same. One is "eduroam" which is present in many universities/collages, and the other two are some WiFI connection we have at my workplace here.
I kind of assumed that since I am having this problem with different WiFi connection then probably this is not related to some Admin preventing me to access, as the same problem happens with all of them.
Also, sorry if the question is naive, but how can I "access to configure the router"? I don't own the router, as all these WiFi connection are either public or from my workplace.

One think I could try is to try many other different Wifi connections, and see if the problem happens with all of them or only these three ones.

---

### Post by ahears on 2017-07-20
[FONT=arial]Seems like the College *would* be using a Web Portal to allow access to students and would be implementing security policies which may make testing here difficult. The work place might have need for limiting new/unauthorized/unknown devices also so you might be caught between them. At the college I think you can get someone in the tech department to tell you how to connect, please see the **NOTE***.

Moving forward with the "work place" in mind, it looks like you found the "Gateway" at '[/FONT][COLOR=#000000][FONT=arial]192.168.42.1'. Can you ping the gateway?[/FONT]
```

[FONT=arial]ping 192.168.42.1[/FONT]

```
[FONT=arial]Please post the output and lets re-configure the 'nm-applet':[/FONT]
```

[FONT=arial]ps ax | grep nm-applet[/FONT]

```
[FONT=arial]If the 'nm-applet' is listed on two or more lines, ignore the second line (or any line) that displays the 'grep' command because that is an output of the running command you just typed in, and is not useful here. In this example only the first line is useful.[/FONT]
[/COLOR]```
**2568 ?        Sl          2:20 nm-applet**
14556 pts/3    S+     0:00 grep  nm-applet

```
[FONT=arial][COLOR=#000000]That means the 'nm-applet' is what you are using to manage your WiFi connections. Hopefully it is. Let's modify the configuration for your Wifi a little because t[/COLOR][/FONT][COLOR=#000000][FONT=arial]his could be screwing everything up also. [/FONT][/COLOR][COLOR=#000000]This can be done by clicking the Wifi logo or whatever icon is used to represent the wifi manager at the top right and selecting '"edit connections", choose the wireless access point you are working on, and choose to edit that connection. Select the "Wifi" tab and clear any information in the "BSSID" field. This would lock you to a specific AP, and not allow a proper connection to other AP's such as "[/COLOR]eduroam" which may have many access points with the same name (BSSID)[COLOR=#000000]. Select the 'IPv4' tab, and choose "automatic (DHCP), and remove any pre-existing DNS entries here. Then select the IPv6 tab and disable that for now by selecting "ignore" from the drop down dialog box, and select "Save" at the bottom to make the changes stick. [/COLOR][COLOR=#000000][FONT=arial]Then close the 'nm-applet' and disconnect/reconnect to your wireless AP (or restart the nm-applet): [/FONT]
```

[FONT=arial]sudo service nm-applet restart[/FONT]

```
[FONT=arial]Start at step 2 in my first list of steps, and post the output. These steps will usually get you the info you need to diagnose your connectivity.***** If repeating the steps in my first post still doesn't work for you, [/FONT]*and you have tried this procedure with a known working wireless adapter for testing such as the USB wireless adapter mentioned earlier*[FONT=arial], the problem isn't the computer. [/FONT]As for the WiFi at work, y[/COLOR][COLOR=#000000][FONT=arial]ou're blocked in my opinion, and I would contact the workplace admin, (or college tech department) and ask permission to connect and they will help you (refer to the note in post #38).[/FONT][/COLOR][COLOR=#000000]

**[FONT=arial]*NOTE: [/FONT]**[/COLOR][COLOR=#000000][FONT=arial]'www.eurodam.org' [/FONT][/COLOR]*has a special app*[COLOR=#000000][FONT=arial] *used to connect which will install a "certificate" used to authenticate on your machine* and this is why you can't just connect. [/FONT][/COLOR]See 'https://www.eduroam.org/about/connect-yourself/' Once you configure your device for eduroam network access on your home institution's campus, you can connect to other member networks using your eduroam username and passphrase. Go to 'https://cat.eduroam.org/' to get the installer for Linux. Keep in mind this could also be true for your work place Wifi, as this would prevent an unauthorized user from sitting outside the workplace and getting internet, but still allow people who work in the building to plug in a laptop via "wired" connection. 
[FONT=arial][COLOR=#000000]
[/COLOR][/FONT]

---

### Post by Federico_Carta on 2017-07-21
Hi, thank you very much for all the help.

I tried to ping the [FONT=arial]"Gateway" at '[/FONT][COLOR=#000000][FONT=arial]192.168.42.1' , but it does not work.[/FONT][/COLOR]
The output is:

```

PING 192.168.42.1 (192.168.42.1) 56(84) bytes of data.
From 192.168.42.123 icmp_seq=1 Destination Host Unreachable
From 192.168.42.123 icmp_seq=2 Destination Host Unreachable
From 192.168.42.123 icmp_seq=3 Destination Host Unreachable
...

```

On the other hand, the output of 
```

[COLOR=#000000][FONT=arial]ps ax | grep nm-applet[/FONT][/COLOR]

```
  wasthe following
```

2270 ?        Sl     0:00 nm-applet
4062 pts/2    S+     0:00 grep --color=auto nm-applet

```

In the "only meaningful line" I have a 0:00 while you have 2:20. What does this mean?
Anyways, when I tried to restart the nm-applet with
```

[COLOR=#000000][FONT=arial]sudo service nm-applet restart[/FONT][/COLOR]

```
I got the following error:
```

Failed to restart nm-applet.service: Unit nm-applet.service not found.

```

Regarding eduroam, I know that there is a certificate to download, in order to authenticate the machine. I did that long time ago. For some period long time ago I was able to normally use the eduroam connection, as well as the one I have at work, with this laptop. Also as far as I know I am the only one at work experiencing these problems, so I kind of think it is more a problem of the computer (either the machine or Ubuntu), and not someone blocking me.
Anyways, I will talk with the people in charge of the IT here, to see if such a block is present.

---

### Post by vasa1 on 2017-07-21
Re.> Also as far as I know I am the only one at work experiencing these problems, so I kind of think it is more a problem of the computer (either the machine or Ubuntu)

Can you make a [live USB of Ubuntu]("https://www.ubuntu.com/download/desktop") and try that to see if you have wifi connectivity?

I find [mkusb]("https://help.ubuntu.com/community/mkusb") very useful for making the live USB.

Using a live USB will help you determine if there's an issue with your machine or with the OS.

---

### Post by ahears on 2017-07-21
[FONT=arial]Ok, it could be that the "certificate" for authentication on your machine has expired but lets just put a pin in that for now. (Your cert is at '/home/federico/ca-bundle_uam.pem'.) Lets try to look at the logs for error messages. First I would like to know the Kernel Version:
```

cat /etc/lsb-release; uname -a

```
Then lets look at the logs for anything error related to the wireless driver "[COLOR=#000000]ath"[/COLOR]
```

dmesg | grep ath

```
I am looking mainly for errors in the log files. so hopefully there will be something useful here.
Now lets backup the drivers to your "Downloads" folder for safe keeping:
```

cp -r /lib/firmware/ath10k ~/Downloads/ 

```
Only if the 'cp' command completed successfully, continue to remove any modified drivers:
```

sudo rm -r /lib/firmware/ath10k

```
Now lets re-install the firmware: (please see the **note***)
```

sudo apt-get install --reinstall linux-firmware

```
Now lets disable the Power management in the configuration for the Wifi device:
```

sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
This will find and replace "wifi.powersave = 3" with "wifi.powersave = 2" in the file '/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf' effectively turning off power management in the config for the network adapter. This should keep it from dropping connections. After you post the output from these six commands, please reboot.


***NOTE: **Posts number 25, 26, 27, 30, and 31 all have a serious typographical errors! When you were working through the steps "Jeff666" posted some info and commands in numerous posts for you to try which may have helped, but both of you failed to notice that your wireless adapter device name is "[COLOR=#000000]wlp7s0" not "[/COLOR][COLOR=#000000]wlp3s7". Oops! Syntax is important. It seems like months of wasted time from February to March! 

It also looks like your problem was already solved in another post '[/COLOR][/FONT]https://ubuntuforums.org/showthread.php?t=2317452' (Ubuntu 14.04 not 16.04) but for the exact same wireless adapter. Have you tried that? Here are the compiled and edited results from that post:
> 
[COLOR=#000000][FONT=&amp]sudo apt-get install git
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo cp -r ath10k-firmware/QCA6174 /lib/firmware/ath10k/
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo shutdown -H now
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR][COLOR=#000000][FONT=arial]On the "up side" of things, your hardware seems to be ok, there aren't any network collisions, dropped packets, jumbo frames, or network jabber that would normally be caused by a misconfigured/defective network adapter when connected to a network.[/FONT][/COLOR]

---

### Post by Kjeld Flarup on 2017-08-13
Yesterday my Wifi stopped working, and the symptoms seems like the ones in this thread


It finds the Wifi router and gets a DHCP answer. With tcpdump I can see that ARP requests are received on the Wifi interface. But somehow I think that my packets are not transmitted. All the attempts I make is also in tcpdump, but I never gets any answer, except for ARP.
Booting in windows partition find that the Wifi works fine there. Also the USB dongle for cable networks is working.


```
sudo tcpdump -i wlp2s0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlp2s0, link-type EN10MB (Ethernet), capture size 262144 bytes
11:04:52.504427 IP 192.168.2.15.60262 > 192.168.2.1.domain: 36411+ A? mtalk.google.com. (34)
11:04:52.507089 IP 192.168.2.15.60262 > 192.168.2.1.domain: 15508+ PTR? 1.2.168.192.in-addr.arpa. (42)
11:04:53.822256 IP 192.168.2.15.60262 > 192.168.2.1.domain: 55475+ A? docs.google.com. (33)
11:04:53.827609 IP 192.168.2.15.60262 > 192.168.2.1.domain: 41941+ A? play.google.com. (33)
11:04:53.984964 IP 192.168.2.15.60262 > 192.168.2.1.domain: 7745+ A? clients4.google.com. (37)
11:04:53.987486 IP 192.168.2.15.60262 > 192.168.2.1.domain: 3089+ A? [www.google.com]("http://www.google.com"). (32)
11:04:53.991646 IP 192.168.2.15.60262 > 192.168.2.1.domain: 16977+ A? clientservices.googleapis.com. (47)
11:05:13.127821 ARP, Request who-has 192.168.2.10 tell 192.168.2.1, length 28
11:05:13.128184 IP 192.168.2.15.60262 > 192.168.2.1.domain: 46160+ PTR? 10.2.168.192.in-addr.arpa. (43)
```

Here my computer asks for the MAC address of the router, and gets an answer.
```
11:06:00.052817 ARP, Request who-has 192.168.2.1 tell 192.168.2.15, length 28
11:06:00.057330 ARP, Reply 192.168.2.1 is-at 00:50:7f:ad:b2:c8 (oui Unknown), length 28

```


I don't know what happened yesterday, except that I rebooted.  I do have automatic security updates enabled though.

I do have ath10k driver problems, but they does not seem to affect the Wifi networking, as the problem existed before I lost Wifi connectivity.
```
zgrep -a 'Direct firmware load for ath10k' /var/log/syslog.3.gz 
Aug 10 21:33:54 kjeld-XPS-15-9560 kernel: [    3.878610] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
Aug 10 21:33:54 kjeld-XPS-15-9560 kernel: [    3.878618] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
Aug 10 21:33:54 kjeld-XPS-15-9560 kernel: [    3.878862] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2

```

---

### Post by vasa1 on 2017-08-13
Please use Code tags instead of quote tags for posting data. Thanks!

---

### Post by Kjeld Flarup on 2017-08-16
[COLOR=#000000][COLOR=#000000][I]```

sudo apt-get install git
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)
[/I][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][I]sudo cp -r ath10k-firmware/QCA6174 /lib/firmware/ath10k/
[/I][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][I]sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
[/I][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][I]sudo shutdown -H now
[/I][/COLOR][/COLOR]
```[COLOR=#000000][I]

I thought I had tried this earlier, but not quite. Instead of overwriting [/I][/COLOR][COLOR=#000000]*QCA6174 I did a mv to save the contents, and thus copied a fresh *[/COLOR][COLOR=#000000]*QCA6174 in. That did not work, apparently there are some files which still is needed, and then this solution works.*[/COLOR][COLOR=#000000][/COLOR]

---

