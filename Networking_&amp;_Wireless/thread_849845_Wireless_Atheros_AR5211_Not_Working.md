---
title: "Wireless Atheros AR5211 Not Working ??"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by elegua on 2008-07-04
Hi Guys,

I have installed Ubuntu 8.04 in a Toshiba Satellite P25 507 with Atheros AR5211 wireles card, for what i red in this forum i don't have the drivers installed on my laptop to get it working, also i'm a little confused with **MadWifi** and **ndiswrapper**, Please can someone tell me how to configure my wireless card?, i just have Ubuntu installed for less than a week so i'm like a baby here.

Here my Wireless Card:

 ```
Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
```

Here some output from my terminal:

```
gabby@gabby-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gabby@gabby-laptop:~$
``` 


```
gabby@gabby-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:82:3c:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.4.8 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:90:96:59:f5:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a
gabby@gabby-laptop:~$
```

```
gabby@gabby-laptop:~$ lspci | grep "Ethernet"
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5211 802.11ab NIC (rev 01)
gabby@gabby-laptop:~$
``` 

Thank You guys.

---

### Post by elegua on 2008-07-05
Hi Guys,

After red a lot of posts here in the forum and searching in google finally i can see mine AP and few other in my building but i can't connected to it, here is some outputs:

```
 gabby@gabby-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1A:2F:91:E2:D0
                    ESSID:"ITCS"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-49 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101830003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:11:20:1B:5B:DC
                    ESSID:"ITCS"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f20201018c0003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:14:BF:44:F5:38
                    ESSID:"Design"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:40:05:52:13:20
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:13:10:27:24:31
                    ESSID:"thegirls"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

gabby@gabby-laptop:~$
```

```
gabby@gabby-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"ITCS"  Nickname:""
          Mode:Managed  Frequency:5.805 GHz  Access Point: 00:11:20:1B:5B:DC   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gabby@gabby-laptop:~$
```

Here is the /wpa_supplicant.conf:

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant: 

network={
        ssid="ITCS"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="XXXXXXXXXX"
        psk=412b2cd41c1b055b44b7fdcbc313570925e7e8a34abf6fdc4404ae81a73a65d5
        pairwise=TKIP
        group=TKIP
}
```

Here is the /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-psk 412b2cd41c1b055b44b7fdcbc313570925e7e8a34abf6fdc4404ae81a73a65d5
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ITCS
```

Now here is the what i think is the problem:

```
gabby@gabby-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 7158
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:59:f5:dc
Sending on   LPF/ath0/00:90:96:59:f5:dc
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:59:f5:dc
Sending on   LPF/ath0/00:90:96:59:f5:dc
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
gabby@gabby-laptop:~$
```

The PC is not getting and IP from the AP, I'll try with a static IP to see what happen.

Thanks in advance.

---

### Post by mlissner on 2009-11-13
This post is rather old, but did you ever get it working?

---

### Post by elegua on 2009-11-20
> **mlissner said:**
> This post is rather old, but did you ever get it working?

Hi,

Never, i decided to install it in a desktop and leave XP running in my laptop.

Do you have the same problem or you know how to fix the problem?.

---

### Post by autofyrsto on 2010-05-10
I'm running an IBM Thinkpad R40 and just switched to Xubuntu 10.04 from Ubuntu 9.10.  Due to Atheros AR5211 problems, I've used a separate wireless Internet card since 9.10 was released.  My internal wireless could see and list routers, but it simply would not connect to any of them.  It looks like I just now got the internal wireless working with ndiswrapper.  This is what I did:

I opened the Ubuntu Software Installer and searched for "ndiswrapper".  I found a program called *"Windows Wireless Drivers: Ndiswrapper installation tool."*  I installed that.  The program also goes by the name _**[ndisgtk]("http://spohlenz.blogspot.com/")**_.  When I launched it, it asked for an *.inf* file to install.  Not having one, I scoured the web to find one. ** [I _found one here_]("http://members.driverguide.com/driver/detail.php?driverid=1364416&action=summary")**, at _**[http://www.driverguide.com/](http://www.driverguide.com/)**_.  You have the option to either pay, sign up, or watch a bunch of ads before downloading.  The choice was simple for me :).  The *.zip* file you get has a bunch of stuff in it; among the stuff is a file called *net5211.inf*.  I used ndisgtk to install that file, rebooted, and my internal wireless worked once again.  No more problems to report.....*for now!*

---

