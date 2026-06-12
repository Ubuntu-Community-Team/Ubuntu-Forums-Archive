---
title: "Ubuntu 12.04 and RTL 8211CL not working"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by mstanger on 2013-10-23
Hi community,

I need your help, I face some network problems, ...during install and after install ubuntu wasn't enable to connect to the network. It keep saying that the network cable is unplugged or without connection. 
I did an update throught wireless USB connection but it dosen't resolve the problem, I follow some post sugestion about downgrade network-manager and so on, but nothing change. 

Here are some facts and details.
* In my router, the clients's **DHCP** table shows the machine host name and it assigned an IP... (that means that my router sees the PC in a right way?), although doing ping return nothing.
* **Parted-Magic** running on the same machine connects to internet without any problem, also I did try to compare some settings and information and everything looks the same (as far as I understand).


Mobo: Asrock N68-VGS3 FX 
Lan: Realtek Giga PHY **RTL8211CL** 10/100/1000 (onboard)

**lshw**
*-bridge[INDENT]description: Ethernet interface[/INDENT]
[INDENT]product: MCP61 Ethernet[/INDENT]
[INDENT]vendor: NVIDIA Corporation[/INDENT]
[INDENT]physical id: 7[/INDENT]
[INDENT]bus info: pci@0000:00:07.0[/INDENT]
[INDENT]logical name: eth0[/INDENT]
[INDENT]version: a2[/INDENT]
[INDENT]serial: XX:XX:XX:XX:XX:XX[/INDENT]
[INDENT]size: 100000000[/INDENT]
[INDENT]capacity: 1000000000[/INDENT]
[INDENT]width: 32 bits[/INDENT]
[INDENT]clock: 66MHz[/INDENT]
[INDENT]capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation[/INDENT]
[INDENT]configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=XXX.XXX.X.XXX latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s[/INDENT]
[INDENT]resources: irq:23 memory:efffd000-efffdfff ioport:e080(size=8)[/INDENT]

Thanks in advance, and if you need any further detail just ask me, thanks.

---

### Post by varunendra on 2013-10-25
Hi, Welcome to the forums :)

With the usb wireless connection, please install ethtool -
```
sudo apt-get install ethtool
```
Then post back the outputs of the following -
```
sudo ethtool eth0
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
dmesg | grep forcedeth
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mstanger on 2013-10-26
Hi, thanks for reply!

Here is the commands results, hope that this could give some clue about the problem. Thanks.

**sudo ethtool eth0**
```

Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 3
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes

```

**nm-tool**
```
NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        XX:XX:XX:XX:XX:XX


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on

```


**cat /etc/network/interfaces **
```
auto lo
iface lo inet loopback

```

**cat /etc/NetworkManager/NetworkManager.conf **
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

**cat /var/lib/NetworkManager/NetworkManager.state **
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

**dmesg | grep forcedeth**
```
[    1.244522] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.244777] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.244781] forcedeth 0000:00:07.0: setting latency timer to 64
[    1.309252] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 3, addr xx:xx:xx:xx:xx:xx
[    1.309255] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[   19.006290] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X

```

---

### Post by varunendra on 2013-10-26
Everything looks solid, most probably it is just a DHCP issue. Please try -
```
sudo dhclient -r
sudo dhclient -v eth0
```
..and post back the full output here if it doesn't help getting a connection.

And also try this as a test -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 *XXX.XXX.X.XXX*
```
..replace *XXX.XXX.X.XXX* with a valid IP address available on your network. Keep it different from what the router has already assigned.

---

### Post by mstanger on 2013-10-26
Nop, it didn't work :( 

**sudo dhclient -v eth0**
```
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
```

**This is what my router see**
```
[TABLE="width: 673"]
[TR]
[TD="colspan: 4, align: left"][FONT=Arial]Dirección IP del servidor DHCP:[/FONT] **  [FONT=Arial]192.168.1.1[/FONT]**[/TD]
[TD="align: center"][/TD]
[/TR]
[TR="bgcolor: #b3b3b3"]
[TH][COLOR=black]Nombre de host cliente[/COLOR][/TH]
[TH][COLOR=black]Dirección IP[/COLOR][/TH]
[TH][COLOR=black]Dirección MAC[/COLOR][/TH]
[TH][COLOR=black]Vence el[/COLOR][/TH]
[TD][/TD]
[/TR]
[TR="bgcolor: cccccc"]
[TD]x[/TD]
[TD]XXX.XXX.X.XXX[/TD]
[TD]xx:xx:xx:xx:xx:xx[/TD]
[TD]23:59:56[/TD]
[TD][/TD]
[/TR]
[/TABLE]

```

---

### Post by varunendra on 2013-10-26
And how about the manual IP assignment with the "ifconfig eth0 xx.." command? For example -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.100
```
Does it let you connect?

If not, try clearing the DHCP pool of your router > turn it off and disconnect it from power source > wait for about 4 minutes > reconnect and turn it on again. Then try the "dhclient" command again, if still unsuccessful, try the manual IP as suggested above.

If it remains the same, try setting a lower speed -
```
sudo mii-tool -F 10baseT-FD eth0
```
and post back the output of "sudo ethtool eth0" again.

Obviously, 10baseT-FD is a super slow speed, we just need to check if it lets you connect at all.

---

### Post by mstanger on 2013-10-30
Hi [COLOR=#000000]varunendra,

Well there was no change on situation, I did what you said but it dont work.
[/COLOR]"**mii-tool**" is not suported, anyway I was able to change speed with **ethtool** but it dosent work, and ethtool logs show almost the same. 
This problem is drive me crazy... loading Parted-Magic from CD connects without problem using the same drivers same IP etc etc...

Varunendra again, thanks for your time and patience... I dont know what could be the next step.

---

### Post by varunendra on 2013-10-30
Please post these outputs from both parted magic and ubuntu sessions -
```
unamr -mr
lspci -nnk | grep -A3 0200
sudo ethtool eth0
modinfo forcedeth
```
Maybe it's just the kernel making the difference, but let's compare all of above.

---

### Post by mstanger on 2013-10-30
Hi,

Here are the info for Ubuntu.

**uname -mr**
```
3.2.0-55-generic-pae i686

```
**lspci -nnk | grep -A3 0200**
This return nothing


**sudo ethtool eth0**
```
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 3
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes

```

**modinfo forcedeth **
```
filename:       /lib/modules/3.2.0-55-generic-pae/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
license:        GPL
description:    Reverse Engineered nForce ethernet driver
author:         Manfred Spraul <manfred@colorfullife.com>
srcversion:     CA755A5F4551AAEB136EC46
alias:          pci:v000010DEd00000D7Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB3sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB2sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB1sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB0sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000763sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000762sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000761sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000760sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DEsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DCsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Fsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Esv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000453sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000452sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000451sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000450sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003EFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000003EEsv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E6sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E5sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000373sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000372sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000269sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000268sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000038sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000037sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000057sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000056sv*sd*bc*sc*i*
alias:          pci:v000010DEd000000DFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000E6sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000008Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000086sv*sd*bc*sc*i*
alias:          pci:v000010DEd000000D6sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000066sv*sd*bc*sc*i*
alias:          pci:v000010DEd000001C3sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-55-generic-pae SMP mod_unload modversions 686 
parm:           max_interrupt_work:forcedeth maximum events handled per interrupt (int)
parm:           optimization_mode:In throughput mode (0), every tx & rx packet will generate an interrupt. In CPU mode (1), interrupts are controlled by a timer. In dynamic mode (2), the mode toggles between throughput and CPU mode based on network load. (int)
parm:           poll_interval:Interval determines how frequent timer interrupt is generated by [(time_in_micro_secs * 100) / (2^10)]. Min is 0 and Max is 65535. (int)
parm:           msi:MSI interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
parm:           msix:MSIX interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
parm:           dma_64bit:High DMA is enabled by setting to 1 and disabled by setting to 0. (int)
parm:           phy_cross:Phy crossover detection for Realtek 8201 phy is enabled by setting to 1 and disabled by setting to 0. (int)
parm:           phy_power_down:Power down phy and disable link when interface is down (1), or leave phy powered up (0). (int)

```

---

### Post by mstanger on 2013-10-30
Here is the info for PartedMagic

**uname -mr**
```
3.5.6-pmagic i686
```

**lspci -nnk | grep -A3 0200**
This return nothing

**sudo ethtool eth0**
```
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 3
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Link detected: yes

```
[B]
modinfo forcedeth [/B]
```
filename:       /lib/modules/3.5.6-pmagic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
license:        GPL
description:    Reverse Engineered nForce ethernet driver
author:         Manfred Spraul <manfred@colorfullife.com>
alias:          pci:v000010DEd00000D7Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB3sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB2sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB1sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000AB0sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000763sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000762sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000761sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000760sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DEsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007DCsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Fsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Esv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000054Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000453sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000452sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000451sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000450sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003EFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000003EEsv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E6sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E5sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000373sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000372sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000269sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000268sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000038sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000037sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000057sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000056sv*sd*bc*sc*i*
alias:          pci:v000010DEd000000DFsv*sd*bc*sc*i*
alias:          pci:v000010DEd000000E6sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000008Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000086sv*sd*bc*sc*i*
alias:          pci:v000010DEd000000D6sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000066sv*sd*bc*sc*i*
alias:          pci:v000010DEd000001C3sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.6-pmagic SMP mod_unload PENTIUMIII 
parm:           max_interrupt_work:forcedeth maximum events handled per interrupt (int)
parm:           optimization_mode:In throughput mode (0), every tx & rx packet will generate an interrupt. In CPU mode (1), interrupts are controlled by a timer. In dynamic mode (2), the mode toggles between throughput and CPU mode based on network load. (int)
parm:           poll_interval:Interval determines how frequent timer interrupt is generated by [(time_in_micro_secs * 100) / (2^10)]. Min is 0 and Max is 65535. (int)
parm:           msi:MSI interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
parm:           msix:MSIX interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
parm:           dma_64bit:High DMA is enabled by setting to 1 and disabled by setting to 0. (int)
parm:           phy_cross:Phy crossover detection for Realtek 8201 phy is enabled by setting to 1 and disabled by setting to 0. (int)
parm:           phy_power_down:Power down phy and disable link when interface is down (1), or leave phy powered up (0). (int)
parm:           debug_tx_timeout:Dump tx related registers and ring when tx_timeout happens (bool)

```

---

### Post by varunendra on 2013-10-30
The major difference is the kernel and respectively the driver version.

Also, this may be significant -
> **xcMseAD said:**
> 
**lspci -nnk | grep -A3 0200**
This return nothing

The lshw shows it is on a PCI bus -
> **xcMseAD said:**
> 
lshw
*-bridge[INDENT]description: Ethernet interface[/INDENT]
....
[INDENT]**bus info: [COLOR="#FF0000"]pci[/COLOR]**@0000:00:07.0[/INDENT][/INDENT]
It also shows it is "bridged", but what is it bridged to? Does this motherboard have two onboard interfaces?

Please check -
```
lspci -nnk | grep -iA3 net
```
Does it show the ethernet interface?

And I would strongly recommend to try a Live CD of 12.04.3 as it uses kernel 3.8, and hopefully, a much better driver.

Alternatively, you may choose to upgrade the current installation to the latest kernel, along with latest supported [hardware enablement]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") stack. But trying 12.04.3 in live mode is a much safer option.

---

### Post by mstanger on 2013-11-03
Hi varunendra,

I try what you said and nothing... ](*,)

**sudo lspci -nnk | grep -iA3 net **
```
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```

About live CD,  I tested both versions 32b and 64b for 12.04.3 in live mode, and network problem didnt change.

I bought this machine a month ago and I can't use it yet. Also there is another issue with power, it do not shutdown or restart by it self, I have to press the buttons for both actions.

About motherbiard as far as I know it only has one interface.

Anyway thanks again for your time and advice.

---

### Post by varunendra on 2013-11-09
> **xcMseAD said:**
> ```
00:07.0 **[COLOR="#FF0000"]Bridge [0680][/COLOR]**: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```
....
About motherbiard as far as I know it only has one interface.
Apparently, you added the "it only has one interface" part one day later, which now makes me even more confused.

Its PCI bus address (0680) is strange for me and the mode "Bridged" is mysterious. The driver "forcedeth" is not very uncommon though, so you shouldn't be out of luck yet.

Unfortunately, as late as I am replying to this (and that too after being reminded by PM..), I may get even busier for next few days. So I'm not sure when (and if) I'd be able to dig up and post something meaningful, I'm not very good with ethernet issues anyway.

I don't have any experience with such 'bridged' interface, and am absolutely clueless at this point. Sooo.. _I'm posting this just as a **BUMP, and a CALL FOR HELP !! Anyone reading this post, please jump in if you have any ideas to share with us.**_

---

### Post by praseodym on 2013-11-21
Please check the module parameters:
```

echo "options forcedeth msi=0 msix=0" | sudo tee -a /etc/modprobe.d/forcedeth.conf
```
Reboot and reset the BIOS to default. Check the outputs again

---

### Post by mstanger on 2013-11-27
Hi praseodym, thanks for reply!!!..

Well I was a bit busy this days, but  finally I did try your advice..., the first thing is that forcedeth.conf wasnt  created yet, I run your command and did a BIOS reset...

Not connection yet... now, what are the outputs that I need to recheck??? :???:

Many thanks in advance.

---

### Post by praseodym on 2013-11-28
Lets have a look at
```

lsmod
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces
route -n
dmesg | egrep 'eth|force'
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/NetworkManager.conf
```

---

