---
title: "Serious: &quot;SIOCSIFFLAGS: function not implemented&quot;  when trying to bring interfaces up"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by rayene.benrayana on 2007-04-27
Hello,

I have a machine with 3 ethernet pci cards and a wireless pci card.
Actually, I'm only using one of the ethernet cards.

I recently upgraded to feisty and then added some software (not directly related to network).

Yesterday, after a bad reboot (due to a freezed service), I realised that the network does not work anymore :

ifconfig gives only one of the interfaces :


```
 
rayene@SoHo:~$ ifconfig 
eth2      Link encap:Ethernet  HWaddr 00:11:5B:4B:EE:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

rayene@SoHo:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:A1:7A:F7:69  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:08:A1:77:8A:D0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth2      Link encap:Ethernet  HWaddr 00:11:5B:4B:EE:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```

eth2 is integrated to the motherboard, it didn't work the first time I tried it so I used one of the realtek NICs. (eth0)

```
 
rayene@SoHo:~$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Function not implemented

rayene@SoHo:~$ sudo ifconfig eth1 up
SIOCSIFFLAGS: Function not implemented

rayene@SoHo:~$ sudo ifconfig eth2 up
SIOCSIFFLAGS: Function not implemented


```

but all the cards are recognized in lspci.

```

rayene@SoHo:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)


```

and here's some output of dmesg

```

rayene@SoHo:~$ dmesg |grep eth0
[   15.622690] eth0: RTL8169s/8110s at 0xe0828000, 00:08:a1:7a:f7:69, IRQ 16
rayene@SoHo:~$ dmesg |grep eth2
[   16.107605] eth2: VIA Rhine II at 0x1c000, 00:11:5b:4b:ee:eb, IRQ 23.
[   16.108325] eth2: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   43.347366] eth2: link down
[   48.671441] ADDRCONF(NETDEV_UP): eth2: link is not ready


```


What I want to do is just recover one of the "Realtek" interfaces (eth0 or eth1).

Any clue ?:confused:  Please tell me if you need additional information.

Thanks in advance !

Rayene,

---

### Post by rayene.benrayana on 2007-04-29
Hello,

Everything is fine now ! it was due to a bad filesystem I think.
a simple fsck solved the problem !

;)

---

