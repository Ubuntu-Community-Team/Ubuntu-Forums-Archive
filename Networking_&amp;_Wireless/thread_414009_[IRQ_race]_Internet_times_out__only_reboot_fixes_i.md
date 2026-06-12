---
title: "[IRQ race?] Internet times out / only reboot fixes it 3com 3c900B"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Baji on 2007-04-19
```
Linux flyingdutchman 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

randomly my internet connection stalls and finally times out. I get these kind of messages in dmesg.
It seems to happen when there is a lot of traffic (exp downloading big files fast)

```
[ 4855.672000]   0: @dfdb6200  length 800000a1 status 0c0100a1
[ 4855.672000]   1: @dfdb62a0  length 800000a1 status 0c0100a1
[ 4855.672000]   2: @dfdb6340  length 800000a1 status 0c0100a1
[ 4855.672000]   3: @dfdb63e0  length 80000045 status 0c010045
[ 4855.672000]   4: @dfdb6480  length 80000045 status 0c010045
[ 4855.672000]   5: @dfdb6520  length 80000045 status 0c010045
[ 4855.672000]   6: @dfdb65c0  length 80000045 status 0c010045
[ 4855.672000]   7: @dfdb6660  length 80000045 status 0c010045
[ 4855.672000]   8: @dfdb6700  length 80000045 status 0c010045
[ 4855.672000]   9: @dfdb67a0  length 800000a1 status 0c0100a1
[ 4855.672000]   10: @dfdb6840  length 800000a1 status 0c0100a1
[ 4855.672000]   11: @dfdb68e0  length 800000a1 status 8c0100a1
[ 4855.672000]   12: @dfdb6980  length 800000a1 status 8c0100a1
[ 4855.672000]   13: @dfdb6a20  length 800000a1 status 0c0100a1
[ 4855.672000]   14: @dfdb6ac0  length 8000006f status 0c01006f
[ 4855.672000]   15: @dfdb6b60  length 800000a1 status 0c0100a1
[ 4855.672000] eth1: Resetting the Tx ring pointer.
[ 4865.672000] NETDEV WATCHDOG: eth1: transmit timed out
[ 4865.672000] eth1: transmit timed out, tx_status 00 status e601.
[ 4865.672000]   diagnostics: net 0cc8 media 8880 dma 0000003a fifo 0000
[ 4865.672000] eth1: Interrupt posted but not delivered -- IRQ blocked by another device?
[ 4865.672000]   Flags; bus-master 1, dirty 228029(13) current 228029(13)
[ 4865.672000]   Transmit list 00000000 vs. dfdb6a20.

[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=81.203.166.229 DST=24.132.209.74 LEN=66 TOS=0x00 PREC=0x00 TTL=112 ID=30116 PROTO=UDP SPT=1774 DPT=4672 LEN=46 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=83.42.8.240 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=114 ID=1641 PROTO=UDP SPT=46037 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=82.122.229.219 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=49 ID=31555 PROTO=UDP SPT=4682 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=85.55.42.244 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=113 ID=2926 PROTO=UDP SPT=17547 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=87.6.124.38 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=114 ID=60533 PROTO=UDP SPT=6054 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=87.68.41.244 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=113 ID=1036 PROTO=UDP SPT=4672 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=88.9.71.241 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=50 ID=59286 PROTO=UDP SPT=16631 DPT=4672 LEN=43 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=201.58.156.157 DST=24.132.209.74 LEN=55 TOS=0x00 PREC=0x00 TTL=114 ID=52400 PROTO=UDP SPT=8712 DPT=4672 LEN=35 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=201.58.156.157 DST=24.132.209.74 LEN=66 TOS=0x00 PREC=0x00 TTL=114 ID=52401 PROTO=UDP SPT=8712 DPT=4672 LEN=46 
[ 5025.676000] Unknown ForwardIN=eth1 OUT=eth1 SRC=83.17.226.174 DST=24.132.209.74 LEN=63 TOS=0x00 PREC=0x00 TTL=113 ID=43814 PROTO=UDP SPT=6969 DPT=4672 LEN=43 

```

especially the**  eth1: Resetting the Tx ring pointer**. and** NETDEV WATCHDOG: eth1: transmit timed out **stands out
Ive read somewhere this was irq related. Somehting with the driver. Anyone got this problem / maybe a solution?

> The driver thinks that the Tx ring is full, yet it has six spare slots. 
It remains in limbo until a Tx timeout. 

ifconfig (online)
```
eth0      Link encap:Ethernet  HWaddr 00:15:F2:54:B3:FB  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe54:b3fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:16 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:01:02:9F:25:12  
          inet addr:24.xx.xx.xx  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe9f:2512/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181925 errors:0 dropped:0 overruns:108 frame:0
          TX packets:129611 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:270307921 (257.7 MiB)  TX bytes:7965557 (7.5 MiB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39518 (38.5 KiB)  TX bytes:39518 (38.5 KiB)

```

my interface

```
             description: Ethernet interface
             product: 3c900B-TPO Etherlink XL [Cyclone]
             vendor: 3Com Corporation
             physical id: 7
             bus info: pci@05:07.0
             logical name: eth1
             version: 04
             serial: 00:01:02:9f:25:12
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=24.132.209.74 latency=32 link=yes maxlatency=48 mingnt=10 multicast=yes port=MII speed=10MB/s
             resources: ioport:a000-a07f iomemory:d1005000-d100507f irq:20

```

the 3c900B might be fault aswel.. Ive been able to just reproduce this problem 3 times, booting up, wget an iso of 600 mb at 700kbs, wait 1 minute, bam gone, same messages in dmesg

help is greatly appreciated!

---

### Post by Baji on 2007-04-19
im marking [http://ubuntuforums.org/showthread.php?t=402818]("http://ubuntuforums.org/showthread.php?t=402818") a quite possible duplicate of this problem


edit: another same syptoms, after large file transfers
[http://ubuntuforums.org/showthread.php?t=202808]("http://ubuntuforums.org/showthread.php?t=202808")

another unresolved one...
[http://ubuntuforums.org/showthread.php?t=169854&highlight=NETDEV+WATCHDOG]("http://ubuntuforums.org/showthread.php?t=169854&highlight=NETDEV+WATCHDOG")

---

### Post by willix on 2007-05-25
I'm having similar problems. Did you find a solution to this?

---

### Post by willix on 2007-05-28
As I said I have kind of the same problem but still have no clues to what's going wrong. Could someone please point me to what MIGHT be wrong?

I've got an old Compaq Armada E700 with an old 3COM pcmcia network card. I've installled a minimal system (no X) form Ubuntu 6.10 and now Ubuntu 7.04 but I get the same problem.

If I ssh to the Armada and check dmesg a couple of time, it eventually blocks for a few minutes before recovering. I then get the following in dmesg

[ 9403.449466] NETDEV WATCHDOG: eth0: transmit timed out
[ 9403.449495] eth0: transmit timed out, tx_status 00 status 8000.
[ 9403.449591]   diagnostics: net 0cc2 media a800 dma 000000a0 fifo 0000
[ 9403.449669]   Flags; bus-master 1, dirty 10835(3) current 10851(3)
[ 9403.449741]   Transmit list 0f3cd3e0 vs. cf3cd3e0.
[ 9403.449812]   0: @cf3cd200  length 8000002a status 0000002a
[ 9403.449883]   1: @cf3cd2a0  length 8000002a status 8000002a
[ 9403.449954]   2: @cf3cd340  length 8000009c status 8c00009c
[ 9403.450024]   3: @cf3cd3e0  length 800005ea status 0c0005ea
[ 9403.450095]   4: @cf3cd480  length 800000ba status 0c0000ba
[ 9403.450165]   5: @cf3cd520  length 80000522 status 0c000522
[ 9403.450235]   6: @cf3cd5c0  length 80000522 status 0c000522
[ 9403.450306]   7: @cf3cd660  length 80000522 status 0c000522
[ 9403.450376]   8: @cf3cd700  length 80000522 status 0c000522
[ 9403.450448]   9: @cf3cd7a0  length 80000522 status 0c000522
[ 9403.450518]   10: @cf3cd840  length 8000009c status 0c00009c
[ 9403.450590]   11: @cf3cd8e0  length 8000009c status 0c00009c
[ 9403.450661]   12: @cf3cd980  length 800000be status 0c0000be
[ 9403.450732]   13: @cf3cda20  length 800000be status 0c0000be
[ 9403.450803]   14: @cf3cdac0  length 80000522 status 0c000522
[ 9403.450873]   15: @cf3cdb60  length 8000002a status 0000002a
[ 9403.450943] eth0: Resetting the Tx ring pointer.

This thread suggests that it's a interrupt issue so I cat /proc/interrupts

           CPU0       
  0:   34232522          XT-PIC  timer
  1:       1055          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          1          XT-PIC  parport0
  8:          5          XT-PIC  rtc
 11:    1560042          XT-PIC  uhci_hcd:usb1, yenta, yenta, ESS Maestro, eth0
 12:       1286          XT-PIC  i8042
 14:    1243703          XT-PIC  ide0
 15:    1209105          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

From what I see, I've got a lot depending on interrupt 11. Is that normal?

Also in dmesg, I see 

[  649.036039] pcmcia: Detected deprecated PCMCIA ioctl usage from process: discover.
[  649.036068] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  649.036086] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

and since my network card is a pcmcia, I am a little worried this might be a issue. Yet the web site talks about pcmciautils which I'm already using.


So I am a little stuck here. Could someone suggest something, please?

---

