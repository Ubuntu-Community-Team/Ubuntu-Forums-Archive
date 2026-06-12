---
title: "unable to connect with wifi without password"
date: 2015-07-22
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2015-07-22
I am currently travelling with my laptop, I notice that Ubuntu is unable to connect at wifi hotspots that don't require password e.g the three airports that I passed through and (no kidding) monkey cafe across my temporary lodging. Ubuntu detects the networks, gnnome-network-manager indicates that I am connected but I am not able to visit any website.  On all these network there is no security (no password required) and on Network manager entry for wifi security is "none" (on other hotspots that require passwords Ubuntu has no problem connecting. e.g the place I am now) 

I think it is due to some kind of Linux security features that I am not able to connect, I would like to be able to use this free service (nothing sensitive or important in this computer anyway). How should I do it?

O.S is Ubuntu 15.04. 

Wifi card info

```

*-network
       description: Wireless interface
       product: RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 00
       serial: c0:f8:da:b0:85:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=4.1.0-040100rc8-generic firmware=0.34 ip=192.168.1.214 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff

```

---

### Post by SeijiSensei on 2015-07-22
Many of these services launch a webpage at start up that you must fill out to become authorized to use the connection.  If you opened a browser, did you see such a page?

When you are connected, can you ping remote machines by IP address, e.g., Google's DNS server at 8.8.8.8?  If so, then you have a problem with DNS resolution.  Are you using the default resolvconf/dnsmasq configuration, or did you set the DNS addresses manually?

When  connected, open a terminal and run "route -n".  Do you see an entry for the "default" route (0.0.0.0) pointing to the server provider's upstream router?

---

### Post by monkeybrain20122 on 2015-07-23
There should be a page about agreeing to terms and services in the airport but even that takes forever to launch and then it just doesn't connect any more. In the coffee shop it was just server not found wherever I go. But network applet said I was connected.

---

### Post by monkeybrain20122 on 2015-07-23
> **SeijiSensei said:**
> Many of these services launch a webpage at start up that you must fill out to become authorized to use the connection.  If you opened a browser, did you see such a page?

When you are connected, can you ping remote machines by IP address, e.g., Google's DNS server at 8.8.8.8?  If so, then you have a problem with DNS resolution.  Are you using the default resolvconf/dnsmasq configuration, or did you set the DNS addresses manually?

When  connected, open a terminal and run "route -n".  Do you see an entry for the "default" route (0.0.0.0) pointing to the server provider's upstream router?

Hi, ping google didn't do anything. I didn't mess with dns so it is the default resolveconf/dnsmasq config that I am using.

```
-localhost:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    1024   0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1

```

After connected dmesg | tail produced
```
dmesg | tail
[   92.036918] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   92.036923] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   92.036927] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   92.036931] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   93.182903] wlan1: authenticate with 96:10:3e:09:49:0f
[   93.196916] wlan1: send auth to 96:10:3e:09:49:0f (try 1/3)
[   93.198432] wlan1: authenticated
[   93.200927] wlan1: associate with 96:10:3e:09:49:0f (try 1/3)
[   93.214846] wlan1: RX AssocResp from 96:10:3e:09:49:0f (capab=0x401 status=0 aid=38)
[   93.215012] wlan1: associated

```

I also ran wireless-info but UF complains that I cannot upload the file because it is 41kb and exceeds the upload size limit, so maybe I can excerpt the useful info to upload? Which part should I post?


**P.S **the info above was obtained about half an hour ago at the monkey cafe when network manager showed connected but I couldn't visit any website. But for some reasons the owner just reset the wifi about 5 minutes ago and now it asks for a password. Now Firefox opens to a page that requests the password, I entered it and  can browse with no problem and post this reply. **But the original question is still not resolved**, I can't connect if it doesn't ask for a password e.g in  the airport so I think the info posted here may help,--obviously I can't go to the airport to obtain the data.

---

### Post by monkeybrain20122 on 2015-07-23
Strange thing is that it asks for password from the browser (instead of popup from network manager) which shows the router I think (has a Linksley logo) and in network-manager (Edited connection > wifi security) It still shows "none".

---

### Post by SeijiSensei on 2015-07-23
That's because the password isn't associated with the router itself.  It comes from the commercial wifi management software places like these use.  You're authenticating yourself to that software; the router probably doesn't have a wifi password at all.

---

### Post by monkeybrain20122 on 2015-07-23
Is there any idea why I couldn't get on the web in the airports? I found a few old threads on UF (back in 2010 ~ 2012) Not sure if it is the same issue here,  since  in my case network manager did see the network and say it was connected even though I couldn't go anywhere. These were not resolved but I couldn't find more recent threads on the issues so presumably it was fixed?? (or people just use their phones instead??)

[http://ubuntuforums.org/showthread.php?t=1585607](http://ubuntuforums.org/showthread.php?t=1585607)
[http://ubuntuforums.org/showthread.php?t=1527429](http://ubuntuforums.org/showthread.php?t=1527429)
[http://askubuntu.com/questions/137155/why-cant-i-connect-to-unsecure-open-wireless-networks](http://askubuntu.com/questions/137155/why-cant-i-connect-to-unsecure-open-wireless-networks)
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/689007](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/689007)

---

### Post by monkeybrain20122 on 2015-07-27
Sometimes network-manager just doesn't find the network (but can see others) and reboot a few times then it picks it up but can't display the log in page (have to use Firefox > history to bring it up). It happens sporadically as I come to this cafe for an hour or two everyday, sometimes it connect without issues, other times like I described above. Is this their set up or mine? How do I find out? It is not just this cafe but I have previously having similar problems at airports so I think it is either 1) my setup 2) the wifi card or 3) Ubuntu. Any suggestion?

---

### Post by SeijiSensei on 2015-07-27
I'd guess the problem is their router.  Is it better or worse depending on where you sit in the cafe?

Do you have an outboard USB wifi adapter around somewhere?  Try using that at the cafe instead and see if it's any better.

---

### Post by monkeybrain20122 on 2015-07-27
No, I always sit at the same spot (where there is a power outlet)

---

### Post by bapoumba on 2015-07-27
Mind you, networking is not my piece of cake :)
What does happen when you try to go to any web page that does not require https the first time around ? (such as [http://ubuntuforums.org](http://ubuntuforums.org)) ? Does it show you the hotspot login page ?

---

### Post by monkeybrain20122 on 2015-07-28
> **bapoumba said:**
> Mind you, networking is not my piece of cake :)
What does happen when you try to go to any web page that does not require https the first time around ? (such as [http://ubuntuforums.org](http://ubuntuforums.org)) ? Does it show you the hotspot login page ?

No, it just shows unable to connect to server. This is the cafe. In the airport it does reroute to the login page, which basically asks you to agree to terms of use, but after agreeing still cannot get online.

---

### Post by monkeybrain20122 on 2015-07-28
Just now at the cafe network manager cannot even see the network (though it finds a bunch of others), the network of the cafe only shows up after disabling and enabling wifi for network manager.

---

### Post by bapoumba on 2015-07-28
Hmm, may be you could get Wild Man's wireless script and run it when you are at the place you cannot get connected ?
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Then paste the result here, others will know how to read it.

---

### Post by monkeybrain20122 on 2015-07-28
> **bapoumba said:**
> Hmm, may be you could get Wild Man's wireless script and run it when you are at the place you cannot get connected ?
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Then paste the result here, others will know how to read it.


Here we go

```


########## wireless info START ##########

Report from: 23 Jul 2015 15:21 EDT -0400

Booted last: 23 Jul 2015 15:17 EDT -0400

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 4.1.0-040100rc8-generic #201506150335 SMP Mon Jun 15 02:37:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 [103c:1611]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] [1814:539f]
    Subsystem: Hewlett-Packard Company Pavilion DM1Z-3000 PCIe wireless card [103c:1637]
    Kernel driver in use: rt2800pci

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 148f:2000 Ralink Technology, Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 174f:1134 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0 
rt2800mmio             24576  1 rt2800pci
rt2800lib              98304  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              786432  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              589824  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.3.111  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::c2f8:daff:feb0:859b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102035 (102.0 KB)  TX bytes:121404 (121.4 KB)

##### iwconfig ##########################

eth1      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"monkeymonkey"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'monkeymonkey' [AC1]>   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:48  Invalid misc:46   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    1024   0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search no.cox.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       694     1  0 15:17 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan1
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip] (Pavilion DM1Z-3000 PCIe wireless card)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.1.0-040100rc8-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/wlan1
GENERAL.IP-IFACE:                       wlan1
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     monkeymonkey
GENERAL.CON-UUID:                       b91be82a-c966-439b-aa37-50885c9bf935
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     57 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b91be82a-c966-439b-aa37-50885c9bf935 | monkeymonkey
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   fbb7fdd6-09fe-4986-81ed-7bb5a1d78e18 | ATT168
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.3.111/24, gw = 192.168.3.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.3.1
IP4.DOMAIN[1]:                          no.cox.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ecosystem.home.cisco.com
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.3.1
DHCP4.OPTION[6]:                        ip_address = 192.168.3.111
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.3.1
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.3.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.3.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = no.cox.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1437682675
DHCP4.OPTION[22]:                       host_name = bee-localhost
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.3.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.3.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         ip = fe80::c2f8:daff:feb0:859b/64, gw = ::

GENERAL.DEVICE:                         eth1
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Pavilion DM1Z-3000)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth1
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Performance PT  <MAC 'Performance PT' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1       no        
Virus Found!!   <MAC 'Virus Found!!' [AC17]>  Infra  6     2437 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ATT648          <MAC 'ATT648' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
scoozer_ATTACK  <MAC 'scoozer_ATTACK' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ULGNO           <MAC 'ULGNO' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
ATT432          <MAC 'ATT432' [AC7]>  Infra  3     2422 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
ab341f          <MAC 'ab341f' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
ATT920          <MAC 'ATT920' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
ULGNO-TENANTS   <MAC 'ULGNO-TENANTS' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
ATT672          <MAC 'ATT672' [AC18]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
linksys         <MAC 'linksys' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1       no        
--              <MAC '--' [AN12]>  Infra  3     2422 MHz  54 Mbit/s  19      &#9602;___  --         no        
monkeymonkey    <MAC 'monkeymonkey' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  --         yes     * 
ASAC GUEST      <MAC 'ASAC GUEST' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
ULGNO-TENANTS   <MAC 'ULGNO-TENANTS' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
CraigsRoute     <MAC 'CraigsRoute' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
ULGNO-GUEST     <MAC 'ULGNO-GUEST' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
ASAC 2.4        <MAC 'ASAC 2.4' [AC6]>  Infra  2     2417 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
ULGNO-GUEST     <MAC 'ULGNO-GUEST' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
ATT416          <MAC 'ATT416' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
ULGNO           <MAC 'ULGNO' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
ATT168          <MAC 'ATT168' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
ATT680          <MAC 'ATT680' [AN23]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
Lauren          <MAC 'Lauren' [AN24]>  Infra  1     2412 MHz  54 Mbit/s  15      &#9602;___  WEP        no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/BELL558]] (600 root)
[connection] id=BELL558 | type=wifi
[wifi] ssid=BELL558 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATL Free Wi-Fi]] (600 root)
[connection] id=ATL Free Wi-Fi | type=wifi
[wifi] ssid=ATL Free Wi-Fi | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Toronto Pearson Wi-Fi]] (600 root)
[connection] id=Toronto Pearson Wi-Fi | type=wifi
[wifi] ssid=Toronto Pearson Wi-Fi | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT168]] (600 root)
[connection] id=ATT168 | type=wifi
[wifi] ssid=ATT168 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BELL195 1]] (600 root)
[connection] id=BELL195 1 | type=wifi
[wifi] ssid=BELL195 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BELL195]] (600 root)
[connection] id=BELL195 | type=wifi
[wifi] ssid=BELL195 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/monkeymonkey]] (600 root)
[connection] id=monkeymonkey | type=wifi
[wifi] ssid=monkeymonkey | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

##### iwlist channels ###################

eth1      no frequency information.

lo        no frequency information.

wlan1     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      7   APs on   Frequency:2.462 GHz (Channel 11)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'monkeymonkey' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"monkeymonkey"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012e0edbc3a
                    Extra: Last beacon: 28000ms ago
          Cell 02 - Address: <MAC 'ASAC GUEST' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ASAC GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030c925ca133
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ULGNO' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ULGNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000052ecfcff180
                    Extra: Last beacon: 4024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ULGNO-GUEST' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"ULGNO-GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000052ecfd18180
                    Extra: Last beacon: 4000ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ATT416' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ATT416"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b85a3e519
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ASAC 2.4' [AC6]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ASAC 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030c925c6a18
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'ATT432' [AC7]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"ATT432"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000486ee1781e
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'ab341f' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ab341f"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b864424b9
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ATT920' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ATT920"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b83e41183
                    Extra: Last beacon: 29844ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'ATT648' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ATT648"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007c600ca0d
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'scoozer_ATTACK' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"scoozer_ATTACK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000012ed645006
                    Extra: Last beacon: 2836ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ATT168' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"ATT168"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003680bc183
                    Extra: Last beacon: 1872ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'ULGNO-GUEST' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ULGNO-GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000052eccb95180
                    Extra: Last beacon: 28084ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Performance PT' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Performance PT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b865e8ad3
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'ULGNO' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ULGNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000052ece4f4244
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'ULGNO-TENANTS' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ULGNO-TENANTS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=002c062ece4f557e
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'Virus Found!!' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Virus Found!!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c0712cfc8
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'ATT672' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ATT672"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001748235183
                    Extra: Last beacon: 2324ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5C7768FC9D600016BB9062C
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EA7A45E50305BDF0A76BD50
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     FB5D7E052ACF0C0F68B6EE7
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512

[rt2x00pci]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F2A3F87D3DBCA573A6F6E05
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512

[rt2x00mmio]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     879F1B5CBAAA72A33F68B51
depends:        rt2x00lib
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     0827788BF4224A80A592340
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5F217E3E605BFE2A9C4566D
depends:        cfg80211
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.1.0-040100rc8-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2151DA0D0F0543B97999E87
depends:        
intree:         Y
vermagic:       4.1.0-040100rc8-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        FC:1C:37:16:92:C8:E7:E5:17:9C:06:C5:5F:C4:DF:7E:19:00:A9:0F
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/libopenni-sensor-primesense0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan1 power off

[/etc/pm/power.d/wireless~] (644 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1680 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   40.563998] r8169 0000:01:00.0 eth1: link down
[   40.572068] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   40.589211] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   41.903301] wlan1: authenticate with <MAC 'monkeymonkey' [AC1]>
[   41.909357] wlan1: send auth to <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   41.917289] wlan1: authenticated
[   41.921257] wlan1: associate with <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   41.939616] wlan1: RX AssocResp from <MAC 'monkeymonkey' [AC1]> (capab=0x401 status=0 aid=38)
[   41.939794] wlan1: associated
[   73.202657] wlan1: authenticate with <MAC 'monkeymonkey' [AC1]>
[   73.216647] wlan1: send auth to <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   73.220631] wlan1: authenticated
[   73.224495] wlan1: associate with <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   73.237423] wlan1: RX AssocResp from <MAC 'monkeymonkey' [AC1]> (capab=0x401 status=0 aid=38)
[   73.237591] wlan1: associated
[   93.182903] wlan1: authenticate with <MAC 'monkeymonkey' [AC1]>
[   93.196916] wlan1: send auth to <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   93.198432] wlan1: authenticated
[   93.200927] wlan1: associate with <MAC 'monkeymonkey' [AC1]> (try 1/3)
[   93.214846] wlan1: RX AssocResp from <MAC 'monkeymonkey' [AC1]> (capab=0x401 status=0 aid=38)
[   93.215012] wlan1: associated
[  276.082098] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 8 times)

########## wireless info END ############

```

---

### Post by wildmanne39 on 2015-07-28
We are going to try a paramter with that driver, it has been known to have issues, and it is just beginning to work with the 5390 at all. There may be another driver we can try but let's go this route first. I am travelling so it may take a while for me to reply but maybe some one else will jump in if they are around.

Please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```

---

### Post by monkeybrain20122 on 2015-07-29
> **Wild Man said:**
> We are going to try a paramter with that driver, it has been known to have issues, and it is just beginning to work with the 5390 at all. There may be another driver we can try but let's go this route first. I am travelling so it may take a while for me to reply but maybe some one else will jump in if they are around.

Please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```

Hi, thanks for the advice. I am travelling too so I understand. But before I try these commands can you explain what they do and in case things got worse how should I reverse them?

Thanks.

---

### Post by bapoumba on 2015-07-29
Thanks Wild Man :)

---

### Post by SeijiSensei on 2015-07-29
I believe it disables hardware encryption on the wifi adapter.  The first command adds an option to the configuration file for the rt2800pci driver.  The other two reload the module and check for it being correctly updated.

---

### Post by wildmanne39 on 2015-07-29
It changes the encryption from hardware to software enabled, which in many cases will help connect to networks and stay connected. Do you have any connection issues once you are connected using this driver?
The parameter can be removed by removing the whole file like this:
```
sudo rm /etc/modprobe.d/rt2800pci.conf
```

I have had an issue where the page to connect to wifi does not open in my browser and that was due to noscript or adblock or related application stopping it from opening.

I connect all over the United States using and atheros card, but linux in general has trouble connecting to some networks depending how they are setup, linux works best with just wpa2 AES not TKIP.
@Baps your very welcome!
Thanks

---

### Post by monkeybrain20122 on 2015-07-30
> **Wild Man said:**
> It changes the encryption from hardware to software enabled, which in many cases will help connect to networks and stay connected. Do you have any connection issues once you are connected using this driver?
The parameter can be removed by removing the whole file like this:
```
sudo rm /etc/modprobe.d/rt2800pci.conf
```

I have had an issue where the page to connect to wifi does not open in my browser and that was due to noscript or adblock or related application stopping it from opening.

I connect all over the United States using and atheros card, but linux in general has trouble connecting to some networks depending how they are setup, linux works best with just wpa2 AES not TKIP.
@Baps your very welcome!
Thanks

I don't have noscrip but I do have adblock, I will see if disabling it makes a difference. But in the airport the page does show up, only after that I still could not connect. The coffee shop's network also doesn't show up sometimes and then it show after disabling enabling wifi. 

Other than these I have no problem, for example, I am now in the guest house and wifi works great (it requires a password) 

Once connected in general I have no issue except for this [http://ubuntuforums.org/showthread.php?t=2285892](http://ubuntuforums.org/showthread.php?t=2285892) but wifi doesn't disconnect any more if putting the battery back in or disabling power management (still don't know how to permanently disable it)

---

### Post by monkeybrain20122 on 2015-07-30
So it seems that adblock was preventing the wifi login page from showing up at the monkey cafe. Today I started Firefox with a new profile and the page appeared. But still not 100% sure because it sometimes does appear even with adblock on and still doesn't explain why network-manager sometimes doesn't find the network at all and need disabling and reenabling wifi. I have that problem even at home (occasionally, not often) and I thought that may be because of the position of the router even though another Ubuntu machine right next to this connects with no issue,--that one has a notorious broadcom card but everything works without issues ( I have no access to the router since I share wifi and it is located upstairs in a house with separate entrance) Also even sitting side by side wifi signal is stronger for the other Ubuntu machine (also 15.04)

I will try wildman's remedy before I leave and test again in the airport and report back.

**Edited:** Hmm.. I got disconnected from the cafe's wifi after about an hr and the network just disappeared from network manager. Disabling and enabling wifi didn't help but after reboot it comes back again.

---

### Post by wildmanne39 on 2015-07-30
Did the parameter help? if not I will research to see if the 5390 driver is available for 15.04 it is possible that the driver has not been updated for 15.04 yet.

---

### Post by monkeybrain20122 on 2015-07-31
I have set the parameter and gone to the cafe and wifi does something very strange, not sure if it is related or just coincidence. It sees the cafe's network but refuses to connect to it. But it also picks up my house network across the street and connects to that instead. It kind of works but the signal is a bit weak. I reversed the change by

```
sudo rm /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

then reboot

But the behaviour persists. It still insists on connecting to the house network. I am now making this post from the cafe using the network in my house!

Edited: The owner of the cafe kindly resets the wifi for me and it is working now, I am not sure whether this whole thing has to do with me changing the parameter or just a coincidence...

---

### Post by monkeybrain20122 on 2015-08-02
It is strange. I am on my way home through the same airports and this time everything works without a hitch (found network, connect, open browser, login page appear, agree to terms of use, then vola, online) It connects in fact even with adblock on. I have changed the parameter a few days ago but I believed I have undone it (see last post) The only difference it seems is that the airports are less busy today so I mange to find an AC outlet for the laptop(but I have tried disabling power management before with no avail IIRC) and of course different locations in the airport.

Anyway, thanks wildman and everyone for the help. I guess I should mark this as solved even though I have no idea what is happening.

---

### Post by wildmanne39 on 2015-08-05
I am glad it is working! sorry for the late reply I have been in the hospital and am just taking it nice a slow.

---

### Post by monkeybrain20122 on 2015-08-05
> **Wild Man said:**
> I am glad it is working! sorry for the late reply I have been in the hospital and am just taking it nice a slow.

Oh, I am sorry to hear this. I hope everything is ok. Get some rest and get well soon. Best wishes.

---

