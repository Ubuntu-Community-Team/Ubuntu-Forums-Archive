---
title: "Problems with wireless. IPW3945."
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by nameneeded on 2007-09-28
K, so I'm a noob so please be basic with me.

Everything worked with xp.

I have recently instaled Ubuntu Feisty (from Ultimate 1.4 distro)

I cannot hookup to my wireless network. The network manager sees my network with excellent signal. I try to hook up it asks for my network password, then tries to hook up then asks again for the password then tries and gives up. Sometimes my wireless option just dissapears and I requre a reboot to get it back.

I am running a Gateway CX2724 tablet with an Intel PRO/Wireless 3945ABG card.

This is the next step to fix before I try to get the pen working. There is no going back for me. My XP disc can't find my HD now so this is it!

THX

---

### Post by noob12 on 2007-09-28
Blind suggestions:
- Turn on ESSID broadcast on the router.
- I've seen more success reported using WPA2 Personal (WPA2 PSK).
- Remove all stanzas from /etc/network/interfaces except the first one for loopback.

If those don't work, posting the output of these might help drive better suggestions:

```

sudo lshw -C network

iwconfig

sudo iwlist scan

```

---

### Post by nameneeded on 2007-09-28
[COLOR="Blue"]I already have the ssid on and am using wpa2. Not sure how to remove those stands but I know it is on loop according to the network manager. Here is what I got from those commands.[/COLOR]

kinder@feisty-frank:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:af:63:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:17
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:d6000000-d6000fff irq:16
kinder@feisty-frank:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



kinder@feisty-frank:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



kinder@feisty-frank:~$ 

[COLOR="Blue"]
I noticed it says no wireless extensions..... thats a prob right....[/COLOR]


I have also tried this........

kinder@feisty-frank:~$ sudo modprobe ipw3945
kinder@feisty-frank:~$ sudo modprobe -r ipw3945
kinder@feisty-frank:~$ 

[COLOR="SlateGray"][COLOR="Blue"]
I've tried apt-get iwp3945 on the off chance I needed it but its not the right name for it I guess. [/COLOR][/COLOR]

---

### Post by noob12 on 2007-09-28
This **UNCLAIMED** here indicates that no driver has claimed the 3945 device.

```

*-network UNCLAIMED
description: Network controller
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@03:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: iomemory:d6000000-d6000fff irq:16

```

As a result you have no network interface with wireless extensions and the scan of course fails as well.

Whatever you think you're seeing as a strong signal isn't your wireless, at least not in this condition. 

The ipw3945 driver is shipped with Feisty in the kernel.  Can you post the output of **uname -r** and **modinfo ipw3945** ?  Is it missing in the Ultimate edition?

---

### Post by noob12 on 2007-09-28
This might be explained if you had done a **modprobe -r ipw3945** before running it.  That would have unloaded  the driver(!)
Do a **modprobe ipw3945** and try re-running those diagnostics again.

---

### Post by nameneeded on 2007-09-29
[COLOR="Blue"]K, here you go.  Yes its just not there I guess.[/COLOR]

kinder@feisty-frank:~$ uname -r
2.6.20-16-generic


kinder@feisty-frank:~$ modinfo iwp3945
modinfo: could not find module iwp3945


kinder@feisty-frank:~$ 
[COLOR="Blue"]
So how can I fix?[/COLOR]

---

### Post by noob12 on 2007-09-29
First try the correct spelling?  **modinfo ipw3945**

If it is there, then try **modprobe ipw3945**.  Then try repeating the diagnostic commands.

---

### Post by nameneeded on 2007-09-29
[COLOR="Blue"]K...... I'm a moron. :lolflag:[/COLOR]


kinder@feisty-frank:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
kinder@feisty-frank:~$

---

### Post by noob12 on 2007-09-29
That's better.  Now **modprobe ipw3945** and try rerunning the diagnostics from earlier in posting #2 on this thread.

---

### Post by nameneeded on 2007-09-30
Sorry for the delay.

I ended up reinstalling Ulti 1.4 as I messed it up playing with PCLinux.  So I have redone all the tasks in order as you asked me to before. (Yes its still not working.) So here goes.

From terminal:


kinder@feisty-frank:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:af:63:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:87:fd:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d6000000-d6000fff irq:16
kinder@feisty-frank:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:B7:43:98   
          Bit Rate:5.5 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/100  Signal level=-90 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2890   Missed beacon:0

kinder@feisty-frank:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:53:A0:ED
                    ESSID:"HOME SWEET HOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-48 dBm  Noise level=-48 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 208ms ago
          Cell 02 - Address: 00:13:46:B7:43:98
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    Extra: Last beacon: 272ms ago

kinder@feisty-frank:~$ uname -r
2.6.20-16-generic
kinder@feisty-frank:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
kinder@feisty-frank:~$ modprobe ipw3945
kinder@feisty-frank:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:af:63:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:87:fd:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d6000000-d6000fff irq:16
kinder@feisty-frank:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:B7:43:98   
          Bit Rate:5.5 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/100  Signal level=-87 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2898   Missed beacon:0

kinder@feisty-frank:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:53:A0:ED
                    ESSID:"HOME SWEET HOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-48 dBm  Noise level=-48 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 208ms ago
          Cell 02 - Address: 00:13:46:B7:43:98
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    Extra: Last beacon: 68ms ago

kinder@feisty-frank:~$

---

### Post by noob12 on 2007-09-30
Which of the access points is yours "HOME SWEET HOME" or "default" ?

You've connected to the one called "default" and it has assigned you a private network IP address of 192.168.1.106 .  If this is yours you may be online already.  I would suggest setting a different ESSID and also using WPA.  If you aren't online, we can do further diagnostics.

If "HOME SWEET HOME" is your AP, then you are not connected to it.  You should rename it to something without spaces like, "HOMESWEETHOME".  After doing that, try to connect by left clicking on the NM icon and selecting that network from the scan list.

Since you have now connected to the ESSID "default", NM may try to connect back there until you remove it from its list which is stored in gconf.  If you have that problem, I'll give you instructions on how to find and remove it from your list.

---

### Post by nameneeded on 2007-10-03
I have renamed my network HOMESWEETHOME and my xp wireless box is working fine on it.

I had my laptop working on it for 1 night intermittently. It would connect then a short while later it would lose connection but then I could reconnect. The next morning it wouldn't connect.

I noticed others having problems with Ultimate so I have installed Feisty 7.04.
Same problems. No wireless connections.  It just tries forever asks for network password a few times then gives up. if my wired connection is attached it just connects to it after failing a few times at the wireless connection. It doesn't try any other networks. and if I try to connect to any other ones it fails as well.

here's the commands from before.

kinder@feisty-frank:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:af:63:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:87:fd:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:d6000000-d6000fff irq:16
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:45  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33432   Missed beacon:0

kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:CA:5B:1A
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=38/100  Signal level=-86 dBm  Noise level=-86 dBm
                    Extra: Last beacon: 212ms ago
          Cell 02 - Address: 00:13:46:B7:43:98
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=26/100  Signal level=-93 dBm  Noise level=-93 dBm
                    Extra: Last beacon: 6800ms ago
          Cell 03 - Address: 00:18:39:D5:30:0A
                    ESSID:"samsworld"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-90 dBm  Noise level=-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 376ms ago
          Cell 04 - Address: 00:1B:11:53:A0:ED
                    ESSID:"HOMESWEETHOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=84/100  Signal level=-49 dBm  Noise level=-49 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 212ms ago

kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ uname -r
2.6.20-16-generic
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ modprobe ipw3945
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:e0:b8:af:63:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d4000000-d401ffff ioport:2000-201f irq:17
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:87:fd:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:d6000000-d6000fff irq:16
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:45  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33685   Missed beacon:0

kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:CA:5B:1A
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=38/100  Signal level=-86 dBm  Noise level=-86 dBm
                    Extra: Last beacon: 200ms ago
          Cell 02 - Address: 00:13:46:B7:43:98
                    ESSID:"default"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=24/100  Signal level=-94 dBm  Noise level=-94 dBm
                    Extra: Last beacon: 204ms ago
          Cell 03 - Address: 00:18:39:D5:30:0A
                    ESSID:"samsworld"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=26/100  Signal level=-93 dBm  Noise level=-93 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 744ms ago
          Cell 04 - Address: 00:1B:11:53:A0:ED
                    ESSID:"HOMESWEETHOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-47 dBm  Noise level=-47 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                       Preauthentication Supported
                    Extra: Last beacon: 208ms ago

kinder@feisty-frank:~$ 
kinder@feisty-frank:~$ 
kinder@feisty-frank:~$

---

### Post by nameneeded on 2007-10-03
And suddenly its working......  I'm not sure whether to laugh, dance or cry.

I'll update tomorrow if its still working.

---

### Post by nameneeded on 2007-10-03
So this is what i have learned....... nothing.

Its still working and the only thing I did was dump Ultimate 1.4 for Feisty 7.04 and then do all the commands in order that Noob requested.

*Sigh* Would have been nice to learn what I did to get it to work.

---

### Post by noob12 on 2007-10-03
My own suspicion is that the driver was loading fine initially with Ultimate 1.4 but that the spaces in the ESSID were causing the main issue.

If tis knowledge ye seek (and ye be brave) then you can try putting the ESSID back to "HOME SWEET HOME" with spaces and see if the surroundings resemble your former wireless limbo.  :-)

You may not want to tempt fate though.  ;-)

---

### Post by nameneeded on 2007-10-06
Alas wireless stopped working 2days ago. :(

Still no reasons why. Just stopped while I was netting the surf as they say.

*sigh*  this is vey discouraging. my understanding is that this is one of the most common wirless setups on laptops. It shouldn"t be this hard should it? 

As such I decided to remove ubuntu from my laptop and put xp back on. Now I have a new problem. :(  (see new thread here 

[http://ubuntuforums.org/showthread.php?p=3488384#post3488384](http://ubuntuforums.org/showthread.php?p=3488384#post3488384)  )

---

### Post by winsur8 on 2007-10-10
Howdy,
I'm new to posting so i'm not sure if i'm supposed to hit the reply or start a new thread.  I have an hp dv1660se with the 3945 intel wireless card.  The card worked fine under the default ubuntu 7.04 install(gnome.) Currently i have a the Command Line Install(off the the alternate cd)  and Icewm.  When I run ifconfig i only get eth0(wired) and the lo.  When running default i had eth0, eth1 and lo.  The one thing right off the batt i havn't tried is compiling from source(ipw3945.)  lspci looks normal - same as default ubuntu.  

uname -r = 2.6.20-16-lowlatency

just recently if i try to set the ssid and key i get the following error message.  
"Error for wireless request "Set ESSID" (8B1A):
    Set failed on device eth1 ; Resource temporaily unavailble.

I'm heading to bed shortly

I very much appriate all of the Help
Dan

---

