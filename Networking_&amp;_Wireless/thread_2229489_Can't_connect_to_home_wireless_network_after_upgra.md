---
title: "Can't connect to home wireless network after upgrade to 14.04?"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by westcoast2 on 2014-06-13
Hello all,

I had a working installation of 10.04 on my Dell laptop with Intel Centrino Ultimate-N 6300 wireless card. I just upgraded to 14.04 (through 12.04 first) and haven't been able to get the wireless to work; the system recognizes the wireless card, and networks show up in the GNOME applet (sudo iwlist scan seems to work), but I can't connect to my  parents' network (which is a hidden and secured WEP); at best the applet keeps asking me for the password every thirty seconds.  I didn't have this problem when I was on 10.04. I'm wondering if anyone knows what I might do in this situation? Any help would be greatly appreciated. 

Here are some specifics. 

Model info: Dell Latitude E6410. 
Distribution: Ubuntu 14.04
Kernel: 3.2.0-64-generic-pae i686

```

sudo iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
eth0      no wireless extensions.

```

```
[INDENT]sudo lspci -v

03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e6e00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-24-d7-ff-ff-06-f1-18
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
[/INDENT]

```


```

sudo lshw -C network

*-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:06:f1:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-64-generic-pae firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:e6e00000-e6e01fff


```

---

### Post by grahammechanical on 2014-06-13
The first thing to keep in mind is that if the Network Manager shows networks/wireless access points in range, then Ubuntu has recognised the wireless network card/adapter and there is an installed driver for it. As lshw -C network shows

> driver=iwlwifi driverversion=3.2.0-64-generic-pae

and lspci -v shows

> Kernel driver in use: iwlwifi

But iwconfig shows

> Access Point: Not-Associated

which is what we get when we do not have a connection to the wireless access point/router. The password being asked for is not your user password but the password/wireless key/pass phrase that we need to make a connection to a secured router. You should find it typed on a label stuck on the bottom of the router.

This requirement has existed since before 10.04 was released. It is not new in Ubuntu. It is this requirement for this pass phrase that stops your neighbours using your router and your internet connection. And us from using their connections to an ISP.

Regards.

---

### Post by westcoast2 on 2014-06-13
Thanks for pointing this out. 

Could you explain how to associate the access point? 

"sudo iwconfig ap "...." " 

doesn't seem to work for me. I also tried the directions given [here]("http://askubuntu.com/questions/40038/how-can-i-force-network-manager-to-associate-to-a-specific-access-point") to add the address of the router to the connection, but was still unable to connect (or associate the access point).

---

### Post by westcoast2 on 2014-06-13
After playing around with it a bit more, I still haven't been able to get online (using wireless; the wired internet works fine), but I was able to use "Create new wireless network" in the GNOME applet to connect to the desired network -- entering in the desired SSID and passcode. My laptop connects quickly to the network if I do that, but there isn't actual wireless access. Does anyone know what might be going on here? 

After I do that, here is what I get: 

```

sudo iwconfig
wlan0     IEEE 802.11abg  ESSID:"8Z688"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: B2:A8:56:BA:63:E2   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key: <key>
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.



```
```

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [8Z688 6] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:24:D7:06:F1:18

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BERRYMAN FAMILY: Infra, 58:6D:8F:23:39:39, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    A-Home-Lan:      Infra, 00:16:B6:DC:F5:2B, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    POWNetwork:      Infra, 00:7F:28:E9:69:B0, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    8QKSK:           Infra, F8:E4:FB:AA:45:C1, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    XMG04:           Infra, 00:26:62:66:D8:3E, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    CableWiFi:       Infra, 20:3A:07:98:A7:C3, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    optimumwifi:     Infra, 20:3A:07:98:A7:C0, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    TWCWiFi:         Infra, 20:3A:07:98:A7:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    3HWZD:           Infra, 00:7F:28:76:AB:54, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    796I3:           Infra, 00:18:01:F3:61:59, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WEP
    679YJ:           Infra, F8:E4:FB:A1:3B:4C, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    8Z688:           Infra, 00:1F:90:E1:A7:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WEP
    xfinitywifi:     Infra, 20:3A:07:98:A7:C1, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    *8Z688:          Ad-Hoc, B2:A8:56:BA:63:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WEP
    wireless-bl:     Infra, 20:4E:7F:C4:E6:81, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Sunsurfer:       Infra, 20:4E:7F:11:DD:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *8Z688:          Ad-Hoc, B2:A8:56:BA:63:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP

  IPv4 Settings:
    Address:         10.42.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        00:26:B9:BE:DB:8B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.1.1
    DNS:             71.250.0.12




```

This output seems to indicate that I'm connected to the wireless network; however (when I disconnect from the wired network), I get:

```

ping google.com
ping: unknown host google.com

```

---

### Post by dmitry22 on 2014-06-13
Hi, it seems i had similar problem, just few moments ago: [http://ubuntuforums.org/showthread.php?t=2229455](http://ubuntuforums.org/showthread.php?t=2229455)
Try to disable LAN conneciton:

[COLOR=#000000]Run "ifconfig" to find out interfaces:[/COLOR]
```
[COLOR=#000000]xxx@yyy:~$ ifconfig
p2p1    Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
        inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
        inet6 addr: XXXX:XXXX:XXXX:XXXX:XXXX/64 Scope:Link
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
[/COLOR][COLOR=#000000]        RX packets:2511995 errors:0 dropped:0 overruns:0 frame:0
[/COLOR][COLOR=#000000]        TX packets:3704518 errors:0 dropped:0 overruns:0 carrier:0
[/COLOR][COLOR=#000000]        collisions:0 txqueuelen:1000 
[/COLOR][COLOR=#000000]        RX bytes:1241874794 (1.2 GB)  TX bytes:3640666674 (3.6 GB)[/COLOR]

```
[COLOR=#000000]and then to shut one down:[/COLOR][COLOR=#000000]
```
xxx@yyy:~$ sudo ifconfig [*interface*] down
```[/COLOR]

---

### Post by wildmanne39 on 2014-06-13
You have it setup as ad-hoc, it needs to be changed to infrastructure in the wireless settings in network manager.

Then the encryption in your router is set to wep it should be changed to just wpa2 (CCMP) if possible and nothing else.

---

### Post by westcoast2 on 2014-06-13
Somewhat embarrassingly, it turns out that there wasn't a problem after all; after rebooting the router the wireless seems to work fine. 

Thanks to all for the help.

---

### Post by denverdash on 2014-09-12
Don't be embarrassed - the exact same thing happened to me. It was not a trivial thing because my other devices were connecting to the router fine. Thanks to you I got it fixed now!

---

