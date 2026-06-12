---
title: "can not find answer to my question"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by kenjpowers on 2007-04-27
Hi all, I am the newest of new to this, I have never used linux but I want to learn.  I can get internet with my wired nic card on my laptop, I have wireless and my card appears to be recognized, The light for the card is not on and I can not find an answer I can understand.  also I use a d link wireless router.  I understand how to enter comands into the terminal, but thats about it.  Can anyone tell me what I and doing wrong and how I can make it work.

---

### Post by dbott67 on 2007-04-27
Well, we need to find out what hardware you have first, so I'll need you to post the output for the following commands:
```
dbott@dapper:~$ [COLOR=Red]cat /etc/network/interfaces [/COLOR]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

This command shows ALL network interfaces on the system (whether enabled or not):

```
dbott@dapper:~$ [COLOR=Red]ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
dbott@dapper:~$ [COLOR=Red]sudo lshw -C network[/COLOR]
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

This command tries to detect wireless access points using each NIC:

```
dbott@dapper:~$ [COLOR=Red]iwlist scanning[/COLOR]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

And finally, this command prints out PCI information:

```
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR="Red"]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```

-Dave

---

### Post by kenjpowers on 2007-04-27
I feel dumb asking this but do I just cut and paste these codes into my terminal?

---

### Post by kenjpowers on 2007-04-27
In my device manager this is what is what it gives me for device details for the wireless NIC
BCM4306 802.11b/g Wireless LAN  and a whole lot of stuff I don't understand

---

### Post by dbott67 on 2007-04-27
You bet.  Just paste the command part (in red) into your terminal.  Paste the output back here in between the [ code]  insert output here [/ code] tags.

I've just included the output from my computer so you can get an idea of how it should look.

-Dave

---

### Post by kenjpowers on 2007-04-27
ok I am getting stuff on the screen but how do I post it in th"code" box like you did?? sorry I feel like a turd for not knowing this.

---

### Post by kenjpowers on 2007-04-27
cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid default

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp










auto eth0

auto eth1

Code:
ken@ken-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:0A:C7:59
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe0a:c759/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:79267038 (75.5 MiB)  TX bytes:5025785 (4.7 MiB)
          Interrupt:201 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:14:A5:22:26:4F
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4012 (3.9 KiB)  TX bytes:4012 (3.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Code:
ken@ken-laptop:~$ sudo lshw -C network
Password:
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:14:a5:22:26:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-28-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e8200000-e8201fff irq:209
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:0a:c7:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:e8204000-e82040ff irq:201

Code:
ken@ken-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

Code:
ken@ken-laptop:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:07.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
ken@ken-laptop:~$

I hope this what you wanted to see

---

### Post by dbott67 on 2007-04-27
> **kenjpowers said:**
> 

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid default

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

auto eth1
```

```

ken@ken-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:0A:C7:59
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe0a:c759/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:79267038 (75.5 MiB)  TX bytes:5025785 (4.7 MiB)
          Interrupt:201 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:14:A5:22:26:4F
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4012 (3.9 KiB)  TX bytes:4012 (3.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```

ken@ken-laptop:~$ sudo lshw -C network
Password:
  *-network:0 [COLOR=Red]DISABLED[/COLOR]
       description: Wireless interface
       product: [COLOR=Red]BCM4306 802.11b/g Wireless LAN Controller[/COLOR]
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name:[COLOR=Red] eth1[/COLOR]
       version: 03
       serial: 00:14:a5:22:26:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-28-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e8200000-e8201fff irq:209
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:0a:c7:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:e8204000-e82040ff irq:201
```

```

ken@ken-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.
```

```

ken@ken-laptop:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
[COLOR=Red] 0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/COLOR]
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
0000:02:07.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
ken@ken-laptop:~$
```

I hope this what you wanted to see

Yep.  I've highlighted the parts in red that are important.  You've got a Broadcom BCM4306 wireless card.  Broadcom has some support using native bcmxx drivers, but sometimes requires you to use ndiswrapper.

A couple of generous folks have written some scripts and what-not to help out those with BCM43xx cards.

Check this [thread]("http://ubuntuforums.org/showthread.php?t=405990&highlight=4306")... lots of success.

-Dave

---

### Post by kenjpowers on 2007-04-27
Thanks alot I have nidiswapper on here but don't know how to use it, I will check that link, This is kinda fun, confusing but fun

---

### Post by kenjpowers on 2007-04-27
ok I have that on another workspace, but how do I navigate to the folder on my desktop in the terminal, All I know is the old dos comands like dir and cd rd and all that, how do i navigate

---

### Post by kenjpowers on 2007-04-28
Thanks alot!!! dbott67 I am on my wireless now, It was actually easy when I figured out the terminal.  I see you live in St Catherines, my mom grew up there, and my Dad grew up just outside Pelham, Small world eh.  Again Thankyou so much, now I just have to figure out how to run winrar

---

### Post by Ptero-4 on 2007-04-28
Hi. A classmate just brought a laptop, It`s brand/model name (or logo) was somehow peeled/scratched off, so I don`t know for sure what make it is, but so far all I know is that it seems to use a PPC CPU and the PCMCIA Wifi that was put in it doesn`t seem to be recognized. Right now I opened the terminal window (from the Docker this guy got),
ifconfig -a says:
```

lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
        inet6 ::1 prefixlen 128 
        inet6 fe80::1 prefixlen 64 scopeid 0x1 
        inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::203:93ff:fe4e:e362 prefixlen 64 scopeid 0x4 
        inet 192.168.1.33 netmask 0xffffff00 broadcast 192.168.1.255
        ether 00:03:93:4e:e3:62 
        media: autoselect (100baseTX <full-duplex>) status: active
        supported media: none autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback>
fw0: flags=8822<BROADCAST,SMART,SIMPLEX,MULTICAST> mtu 2030
        lladdr 00:03:93:ff:fe:4e:e3:62 
        media: autoselect <full-duplex> status: inactive
        supported media: autoselect <full-duplex>

```

but for some reason I just can`t imagine every other command output the "command not found" response. Hence I don`t know how to go on from here.

P.d: uname -r says:
```
7.9.0
```

---

### Post by dbott67 on 2007-04-28
> **kenjpowers said:**
> Thanks alot!!! dbott67 I am on my wireless now, It was actually easy when I figured out the terminal.  I see you live in St Catherines, my mom grew up there, and my Dad grew up just outside Pelham, Small world eh.  Again Thankyou so much, now I just have to figure out how to run winrar

Hi Ken,

Small world, indeed!  Glad everything is working.

As for the "code" box (and quote, URL, PHP tags, etc.) there are a few ways.

1. If you click "Advanced" at the bottom of your post while editing, it will create a new toolbar with all of the advanced tags, smilies, font & style tags, bullets & lists, etc.  Just highlight the portion you want and click the appropriate button.

2. You can also just type the tags in yourself.  The *opening* code tag is just the word 'code' surrounded by opening & closing square brackets [ ].  Then you type/paste your desired text in and follow with the *closing* code tag, which is the work '/code' surrounded by opening & closing square brackets [ ].

3. A little tip to see it in action is to use the quote feature when replying to a message.  You will see the raw tags and be able to see how the message was composed.

Just hit QUOTE when replying to this message and you should see the code tags revealed.

```
this is an opening code tag [ c o d e ] and this is a closing code tag [ / c o d e ]. 

Just remove the spaces.
```-Dave

---

