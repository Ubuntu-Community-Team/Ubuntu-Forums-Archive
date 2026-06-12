---
title: "eth0 crash"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Niker on 2007-06-03
Hi, my server has been acting weird lately with my new 20mb internet speed.

specs: Aopen EZ482
running latest kubuntu feisty fawn

I download a torrent at around 1600kb/s and after a while eth0 just dies and I cant reinit it without rebooting. I saw alot of bad stuff in the logs so here are some parts of it, hopefully it can get me somewhere:


it starts here
```

un  3 15:41:45 b0ne kernel: [47878.728000] NETDEV WATCHDOG: eth0: transmit timed out
Jun  3 15:41:45 b0ne kernel: [47878.728000] sky2 eth0: disabling interface
Jun  3 15:41:45 b0ne kernel: [47878.728000] sky2 eth0: enabling interface
Jun  3 15:41:45 b0ne kernel: [47878.732000] sky2 eth0: ram buffer 48K
Jun  3 15:41:48 b0ne kernel: [47881.864000] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
Jun  3 15:57:39 b0ne kernel: [48831.864000] NETDEV WATCHDOG: eth0: transmit timed out
Jun  3 15:57:39 b0ne kernel: [48831.864000] sky2 eth0: disabling interface
Jun  3 15:57:39 b0ne kernel: [48831.864000] sky2 eth0: enabling interface
Jun  3 15:57:39 b0ne kernel: [48831.868000] sky2 eth0: ram buffer 48K
Jun  3 15:57:42 b0ne kernel: [48834.964000] sky2 eth0: Link is up at 1000 Mbps, full duplex, flow control both
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__skb_checksum_complete+93/96] __skb_checksum_complete+0x5d/0x60
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__tcp_checksum_complete_user+41/48] __tcp_checksum_complete_user+0x29/0x30
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [tcp_rcv_established+164/2368] tcp_rcv_established+0xa4/0x940
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__wake_up_common+57/96] __wake_up_common+0x39/0x60
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [tcp_v4_do_rcv+718/1360] tcp_v4_do_rcv+0x2ce/0x550
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [ip_route_input+57/3440] ip_route_input+0x39/0xd70
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__activate_task+33/64] __activate_task+0x21/0x40
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [try_to_wake_up+70/1152] try_to_wake_up+0x46/0x480
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [sock_def_readable+120/128] sock_def_readable+0x78/0x80
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [udp_queue_rcv_skb+323/1056] udp_queue_rcv_skb+0x143/0x420
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [tcp_v4_rcv+1937/2352] tcp_v4_rcv+0x791/0x930
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [ip_local_deliver+290/704] ip_local_deliver+0x122/0x2c0
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__wake_up+56/80] __wake_up+0x38/0x50
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [ip_rcv+700/1280] ip_rcv+0x2bc/0x500
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [netif_receive_skb+519/768] netif_receive_skb+0x207/0x300
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [show_affected_cpus+120/176] show_affected_cpus+0x78/0xb0
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [<f89bdda8>] sky2_poll+0x428/0xa10 [sky2]
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [hrtimer_run_queues+188/336] hrtimer_run_queues+0xbc/0x150
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [net_rx_action+201/544] net_rx_action+0xc9/0x220
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [__do_softirq+130/256] __do_softirq+0x82/0x100
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [do_softirq+85/96] do_softirq+0x55/0x60
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [default_idle+0/96] default_idle+0x0/0x60
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [default_idle+61/96] default_idle+0x3d/0x60
Jun  3 16:02:38 b0ne kernel: [49131.180000]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
Jun  3 16:02:38 b0ne kernel: [49131.180000]  =======================

```

which repeats for a while. then goes to

```

Jun  3 16:02:59 b0ne kernel: [49152.256000] recvmsg bug: copied 39DF1E3F seq 39DF23AF
Jun  3 16:02:59 b0ne kernel: [49152.260000] recvmsg bug: copied 39DF1E3F seq 39DF23AF
Jun  3 16:02:59 b0ne last message repeated 71 times
Jun  3 16:02:59 b0ne kernel: [49152.264000] recvmsg bug: copied 39DF1E3F seq 39DF23AF
Jun  3 16:02:59 b0ne last message repeated 64 times
Jun  3 16:02:59 b0ne kernel: 9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed
Jun  3 16:02:59 b0ne kernel: [49K) failed at net/ipv9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) fai
Jun  3 16:02:59 b0ne kernel: net/ipv4/tcp.c9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K) failed at net/ip9K)

```

which also repeats alot. Then I also see this:

```

Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne last message repeated 2 times
Jun  3 16:03:00 b0ne kernel: <K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne last message repeated 6 times
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne last message repeated 5 times
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: 9K) failed at net/ipv4/tcp.c (1183)
Jun  3 16:03:00 b0ne kernel: <9K) failed at net/ipv4/tcp.c (1183)

```

then those two last segments repeat until i reboot the machine.


```

eth0      Link encap:Ethernet  HWaddr 00:01:80:60:C1:60
          inet addr:10.0.0.20  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::201:80ff:fe60:c160/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:705133 (688.6 KiB)  TX bytes:7331150 (6.9 MiB)
          Interrupt:20

```

thanks in advance

---

### Post by chazmo on 2007-06-03
I have the exact same problem except that mine dies when it's inactive for a while. If I'm downloading or surfing the web it seems to be fine. One way I found to re-enable it without rebooting was to go to System --> Administration --> Network then de-select the network controller (wait a few seconds) and then re-select it.

My message log shows "NETDEV WATCHDOG: eth0: transmit timed out" same as yours.

Which NIC card are you using? I have a "Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)"

I'll post back if I find out any additional info.

---

### Post by Niker on 2007-06-03
Hey mate,

lan: Gigabit LAN Network Controller 10/100/1000Gbps

I red this [http://www.linuxarkivet.se/mlists/linux-kernel/0310/msg01603.html](http://www.linuxarkivet.se/mlists/linux-kernel/0310/msg01603.html) and having a go at the answer at  [http://www.linuxarkivet.se/mlists/linux-kernel/0310/msg01660.html](http://www.linuxarkivet.se/mlists/linux-kernel/0310/msg01660.html)

lets see how it resolvs.First test is with noapic in kernel boot.

```

# cat /proc/interrupts
           CPU0       CPU1
  0:      60968          0    XT-PIC-XT        timer
  1:          3          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  3:       3663          0    XT-PIC-XT        HDA Intel
  5:     196299          0    XT-PIC-XT        eth0
  6:          2          0    XT-PIC-XT        floppy
  8:          3          0    XT-PIC-XT        rtc
  9:          1          0    XT-PIC-XT        acpi
 10:          0          0    XT-PIC-XT        libata
 11:      57912          0    XT-PIC-XT        libata, ehci_hcd:usb1, ohci_hcd:usb2, ohci_hcd:usb3
 14:       2084          0    XT-PIC-XT        ide0
NMI:          0          0
LOC:      60836      60839
ERR:         47
MIS:          0

```

---

### Post by Niker on 2007-06-03
no luck with the apic.

One thing I tought of was that I didn't have this problem with the original  2.6.20-15-generic kernel. So now im inside it and see that 

```

cat /proc/interrupts
           CPU0       CPU1
  0:     148184          0  local-APIC-edge-fasteio   timer
  1:          1          1   IO-APIC-edge      i8042
  6:          1          1   IO-APIC-edge      floppy
  8:          3          0   IO-APIC-edge      rtc
 14:       5192          1   IO-APIC-edge      ide0
 16:     114469          1   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
 17:       4157          1   IO-APIC-fasteoi   HDA Intel
 18:          0          0   IO-APIC-fasteoi   libata
 19:      13370          1   IO-APIC-fasteoi   libata
 20:       6451      36731   IO-APIC-fasteoi   eth0
 21:          0          1   IO-APIC-fasteoi   acpi
NMI:          0          0
LOC:     148057     148122
ERR:          2
MIS:          0

```

cpu1 of eth0 is active. but was 0 on the latest kernel. not sure if this means anything. Will see if the eth0 goes down with this kernel running for a while.

---

### Post by Frankenchrist on 2007-06-03
I have this same problem with my integrated Nforce2 network controller.  I would love a fix to it so I can get my file-server up and running again.

---

### Post by Niker on 2007-06-04
no luck yet in any approach. What are you using your servers for? filesharing, www etc. 
And when does it crash for you guys?

---

### Post by apureevil1 on 2007-06-04
I am having the same problem, I had no issues with 6.10 and then had to do a forced rebuild, now upgraded to 7.04 and I loose my wired network connection VT6102 [Rhine-II], however my wireless connection works fine.

---

### Post by Niker on 2007-06-06
guess this is not the way to get help for ubuntu.. the forum should be called "ubuntu, do it yourself - forum" :)

---

### Post by netztier on 2007-06-06
> **Niker said:**
> guess this is not the way to get help for ubuntu.. the forum should be called "ubuntu, do it yourself - forum" :)

Well, there's always [launchpad.net]("https://launchpad.net"), where Ubuntu bugs are reported and tracked, but also where support questions find a home. Check it out.

best regards

Marc

---

### Post by Niker on 2007-06-06
well why didn't you tell me before dammit :)

[https://bugs.launchpad.net/linux/+bug/83009](https://bugs.launchpad.net/linux/+bug/83009)

seems like my solution! since i have the marvell card. thank you netztier

---

