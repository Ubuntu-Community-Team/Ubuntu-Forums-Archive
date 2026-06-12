---
title: "[SOLVED] Problem with wired internet"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by schakravarthi on 2007-08-24
My internet connection dies after a couple of hours. It is very erratic (on the number of hrs it takes to die)

So far, only solution i know is to reboot.. 
I am running ubuntu on a 7 yr old machine (and I have had many older linux distro's work very stably on the same hardware).  So I am sure it is not a hardware issue.

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:E0:18:2F:F9:F9  
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe2f:f9f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6070295 (5.7 MiB)  TX bytes:1091169 (1.0 MiB)
          Interrupt:16 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

more /etc/network/interfaces 
auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface eth0 inet dhcp

auto eth0

---

### Post by band-aid on 2007-08-24
Maybe your computers DHCP lease is running out? Hmmm, check in your router settings and see how long you have it set for.

---

### Post by dripter on 2007-08-24
are you using dsl or dial-up? check with your provider if it disconnect idle connection after x number of hours.

---

### Post by schakravarthi on 2007-08-28
I am using DSL. Will check to see if there is something I can change there.

I tried disable ipv6 as some posts suggested. Disabling ipv6 seemed to increase in my internet connection speed (download speeds) but no improvement in stability.

Few things to note:
Windows doesnt seem to have problem running in parallel.

Before loading Ubuntu I was running Mandriva 2006 with the same DSL and router (and didnt have a problem).

---

### Post by schakravarthi on 2007-08-31
I tried it with a different router with the dhcp max timeout set  to 4800 hrs. I still lost my network. 

Interestingly I find once the network is lost, it cannot resolve the router as well ([http://128.16*](http://128.16*)).

---

### Post by noob12 on 2007-08-31
At a point where you have lost your connectivity can you capture the result of these commands.  Save them to a file and post them when you are back online.

> 
sudo ethtool eth0

ifconfig -a

date

grep dhclient /var/log/syslog | tail -50


---

### Post by schakravarthi on 2007-09-01
srini@falcon:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

srini@falcon:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:E0:18:2F:F9:F9  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3891270 (3.7 MiB)  TX bytes:658826 (643.3 KiB)
          Interrupt:16 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10022 (9.7 KiB)  TX bytes:10022 (9.7 KiB)
srini@falcon:~$ date
Sat Sep  1 12:12:53 CDT 2007srini@falcon:~$ grep dhclient /var/log/syslog | tail -50

"No result"

Inserted all the file after the last reboot (3hrs)  (/var/log/syslog)
Sep  1 09:34:20 falcon syslogd 1.4.1#20ubuntu4: restart.
Sep  1 09:34:20 falcon anacron[5253]: Job `cron.daily' terminated
Sep  1 09:34:20 falcon anacron[5253]: Normal exit (1 job run)
Sep  1 09:47:22 falcon -- MARK --
Sep  1 10:07:22 falcon -- MARK --
Sep  1 10:17:01 falcon /USR/SBIN/CRON[6940]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 10:27:22 falcon -- MARK --
Sep  1 10:47:23 falcon -- MARK --
Sep  1 10:51:40 falcon kernel: [ 5197.672237] irq 16: nobody cared (try booting with the "irqpoll" option)
Sep  1 10:51:40 falcon kernel: [ 5197.672889]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Sep  1 10:51:40 falcon kernel: [ 5197.673084]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Sep  1 10:51:40 falcon kernel: [ 5197.673109]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Sep  1 10:51:40 falcon kernel: [ 5197.673120]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Sep  1 10:51:40 falcon kernel: [ 5197.673130]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Sep  1 10:51:40 falcon kernel: [ 5197.673141]  [<d085f1b6>] uhci_scan_schedule+0x736/0x8d0 [uhci_hcd]
Sep  1 10:51:40 falcon kernel: [ 5197.673165]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Sep  1 10:51:40 falcon kernel: [ 5197.673185]  [<d0860e84>] uhci_irq+0x34/0x170 [uhci_hcd]
Sep  1 10:51:40 falcon kernel: [ 5197.673198]  [__switch_to+198/496] __switch_to+0xc6/0x1f0
Sep  1 10:51:40 falcon kernel: [ 5197.673212]  [<d0882f32>] usb_hcd_irq+0x22/0x60 [usbcore]
Sep  1 10:51:40 falcon kernel: [ 5197.674020]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Sep  1 10:51:40 falcon kernel: [ 5197.674030]  [handle_fasteoi_irq+123/240] handle_fasteoi_irq+0x7b/0xf0
Sep  1 10:51:40 falcon kernel: [ 5197.674043]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Sep  1 10:51:40 falcon kernel: [ 5197.674056]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Sep  1 10:51:40 falcon kernel: [ 5197.674063]  [default_idle+0/96] default_idle+0x0/0x60
Sep  1 10:51:40 falcon kernel: [ 5197.674077]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
Sep  1 10:51:40 falcon kernel: [ 5197.674111]  [default_idle+61/96] default_idle+0x3d/0x60
Sep  1 10:51:40 falcon kernel: [ 5197.674116]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
Sep  1 10:51:40 falcon kernel: [ 5197.674124]  [start_kernel+869/1056] start_kernel+0x365/0x420
Sep  1 10:51:40 falcon kernel: [ 5197.674138]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Sep  1 10:51:40 falcon kernel: [ 5197.674155]  =======================
Sep  1 10:51:40 falcon kernel: [ 5197.674157] handlers:
Sep  1 10:51:40 falcon kernel: [ 5197.674160] [<d08b68c0>] (ahc_linux_isr+0x0/0x250 [aic7xxx])
Sep  1 10:51:40 falcon kernel: [ 5197.674780] [<d08f1bb0>] (rtl8139_interrupt+0x0/0x480 [8139too])
Sep  1 10:51:40 falcon kernel: [ 5197.674957] Disabling IRQ #16
Sep  1 10:52:08 falcon kernel: [ 5225.513642] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:52:11 falcon kernel: [ 5228.512284] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:52:11 falcon kernel: [ 5228.512294] eth0: Tx queue start entry 5143  dirty entry 5139.
Sep  1 10:52:11 falcon kernel: [ 5228.512298] eth0:  Tx descriptor 0 is 0008a03c.
Sep  1 10:52:11 falcon kernel: [ 5228.512303] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:52:11 falcon kernel: [ 5228.512306] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:52:11 falcon kernel: [ 5228.512310] eth0:  Tx descriptor 3 is 0008a03c. (queue head)
Sep  1 10:52:11 falcon kernel: [ 5228.512322] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 10:52:23 falcon kernel: [ 5240.506819] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:52:26 falcon kernel: [ 5243.505463] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:52:26 falcon kernel: [ 5243.505472] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 10:52:26 falcon kernel: [ 5243.505477] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 10:52:26 falcon kernel: [ 5243.505481] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:52:26 falcon kernel: [ 5243.505485] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:52:26 falcon kernel: [ 5243.505488] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 10:52:26 falcon kernel: [ 5243.505501] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 10:52:38 falcon kernel: [ 5255.499998] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:52:41 falcon kernel: [ 5258.498642] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:52:41 falcon kernel: [ 5258.498651] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 10:52:41 falcon kernel: [ 5258.498656] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 10:52:41 falcon kernel: [ 5258.498661] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:52:41 falcon kernel: [ 5258.498665] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:52:41 falcon kernel: [ 5258.498668] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 10:52:41 falcon kernel: [ 5258.498680] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 10:52:53 falcon kernel: [ 5270.489178] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:52:56 falcon kernel: [ 5273.487825] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:52:56 falcon kernel: [ 5273.487834] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 10:52:56 falcon kernel: [ 5273.487839] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 10:52:56 falcon kernel: [ 5273.487844] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:52:56 falcon kernel: [ 5273.487847] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:52:56 falcon kernel: [ 5273.487851] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 10:52:56 falcon kernel: [ 5273.487863] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 10:53:08 falcon kernel: [ 5285.482356] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:53:11 falcon kernel: [ 5288.481004] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:53:11 falcon kernel: [ 5288.481018] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 10:53:11 falcon kernel: [ 5288.481023] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 10:53:11 falcon kernel: [ 5288.481027] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:53:11 falcon kernel: [ 5288.481030] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:53:11 falcon kernel: [ 5288.481034] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 10:53:11 falcon kernel: [ 5288.481046] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 10:53:23 falcon kernel: [ 5300.475535] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 10:53:26 falcon kernel: [ 5303.474181] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 10:53:26 falcon kernel: [ 5303.474190] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 10:53:26 falcon kernel: [ 5303.474195] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 10:53:26 falcon kernel: [ 5303.474199] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 10:53:26 falcon kernel: [ 5303.474203] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 10:53:26 falcon kernel: [ 5303.474207] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 10:53:26 falcon kernel: [ 5303.474219] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:07:23 falcon -- MARK --
Sep  1 11:17:01 falcon /USR/SBIN/CRON[8385]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 11:22:08 falcon kernel: [ 7024.627135] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:22:11 falcon kernel: [ 7027.625709] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:22:11 falcon kernel: [ 7027.625719] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:22:11 falcon kernel: [ 7027.625724] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:22:11 falcon kernel: [ 7027.625728] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:22:11 falcon kernel: [ 7027.625732] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:22:11 falcon kernel: [ 7027.625735] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:22:11 falcon kernel: [ 7027.625747] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:22:23 falcon kernel: [ 7039.620245] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:22:26 falcon kernel: [ 7042.618891] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:22:26 falcon kernel: [ 7042.618900] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:22:26 falcon kernel: [ 7042.618905] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:22:26 falcon kernel: [ 7042.618909] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:22:26 falcon kernel: [ 7042.618913] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:22:26 falcon kernel: [ 7042.618916] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:22:26 falcon kernel: [ 7042.618929] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:22:38 falcon kernel: [ 7054.609430] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:22:41 falcon kernel: [ 7057.608068] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:22:41 falcon kernel: [ 7057.608078] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:22:41 falcon kernel: [ 7057.608083] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:22:41 falcon kernel: [ 7057.608087] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:22:41 falcon kernel: [ 7057.608091] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:22:41 falcon kernel: [ 7057.608094] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:22:41 falcon kernel: [ 7057.608107] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:22:53 falcon kernel: [ 7069.602603] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:22:56 falcon kernel: [ 7072.601249] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:22:56 falcon kernel: [ 7072.601258] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:22:56 falcon kernel: [ 7072.601263] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:22:56 falcon kernel: [ 7072.601268] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:22:56 falcon kernel: [ 7072.601271] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:22:56 falcon kernel: [ 7072.601275] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:22:56 falcon kernel: [ 7072.601288] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:23:08 falcon kernel: [ 7084.595782] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:23:11 falcon kernel: [ 7087.594424] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:23:11 falcon kernel: [ 7087.594434] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:23:11 falcon kernel: [ 7087.594439] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:23:11 falcon kernel: [ 7087.594443] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:23:11 falcon kernel: [ 7087.594446] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:23:11 falcon kernel: [ 7087.594450] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:23:11 falcon kernel: [ 7087.594462] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:23:23 falcon kernel: [ 7099.588960] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:23:26 falcon kernel: [ 7102.587605] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:23:26 falcon kernel: [ 7102.587614] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:23:26 falcon kernel: [ 7102.587619] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:23:26 falcon kernel: [ 7102.587624] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:23:26 falcon kernel: [ 7102.587627] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:23:26 falcon kernel: [ 7102.587631] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:23:26 falcon kernel: [ 7102.587643] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:29:32 falcon kernel: [ 7468.405153] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:29:35 falcon kernel: [ 7471.403799] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:29:35 falcon kernel: [ 7471.403808] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:29:35 falcon kernel: [ 7471.403813] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:29:35 falcon kernel: [ 7471.403817] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:29:35 falcon kernel: [ 7471.403821] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:29:35 falcon kernel: [ 7471.403824] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:29:35 falcon kernel: [ 7471.403837] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:29:47 falcon kernel: [ 7483.398331] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:29:50 falcon kernel: [ 7486.396980] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:29:50 falcon kernel: [ 7486.396989] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:29:50 falcon kernel: [ 7486.396994] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:29:50 falcon kernel: [ 7486.396999] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:29:50 falcon kernel: [ 7486.397002] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:29:50 falcon kernel: [ 7486.397006] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:29:50 falcon kernel: [ 7486.397018] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:30:02 falcon kernel: [ 7498.391509] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:30:05 falcon kernel: [ 7501.390155] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:30:05 falcon kernel: [ 7501.390164] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:30:05 falcon kernel: [ 7501.390169] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:30:05 falcon kernel: [ 7501.390174] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:30:05 falcon kernel: [ 7501.390177] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:30:05 falcon kernel: [ 7501.390181] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:30:05 falcon kernel: [ 7501.390193] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:30:17 falcon kernel: [ 7513.384688] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:30:20 falcon kernel: [ 7516.383333] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:30:20 falcon kernel: [ 7516.383343] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:30:20 falcon kernel: [ 7516.383348] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:30:20 falcon kernel: [ 7516.383352] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:30:20 falcon kernel: [ 7516.383356] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:30:20 falcon kernel: [ 7516.383359] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:30:20 falcon kernel: [ 7516.383371] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:30:32 falcon kernel: [ 7528.377866] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:30:35 falcon kernel: [ 7531.376511] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:30:35 falcon kernel: [ 7531.376521] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:30:35 falcon kernel: [ 7531.376526] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:30:35 falcon kernel: [ 7531.376530] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:30:35 falcon kernel: [ 7531.376534] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:30:35 falcon kernel: [ 7531.376537] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:30:35 falcon kernel: [ 7531.376549] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:30:47 falcon kernel: [ 7543.371044] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:30:50 falcon kernel: [ 7546.369690] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:30:50 falcon kernel: [ 7546.369699] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:30:50 falcon kernel: [ 7546.369704] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:30:50 falcon kernel: [ 7546.369708] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:30:50 falcon kernel: [ 7546.369712] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:30:50 falcon kernel: [ 7546.369716] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:30:50 falcon kernel: [ 7546.369728] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:35:20 falcon kernel: [ 7816.234893] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:35:23 falcon kernel: [ 7819.233534] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:35:23 falcon kernel: [ 7819.233543] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:35:23 falcon kernel: [ 7819.233547] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:35:23 falcon kernel: [ 7819.233552] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:35:23 falcon kernel: [ 7819.233555] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:35:23 falcon kernel: [ 7819.233559] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:35:23 falcon kernel: [ 7819.233571] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:35:35 falcon kernel: [ 7831.228071] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:35:38 falcon kernel: [ 7834.226715] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:35:38 falcon kernel: [ 7834.226724] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:35:38 falcon kernel: [ 7834.226728] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:35:38 falcon kernel: [ 7834.226733] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:35:38 falcon kernel: [ 7834.226736] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:35:38 falcon kernel: [ 7834.226740] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:35:38 falcon kernel: [ 7834.226752] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:35:50 falcon kernel: [ 7846.221250] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:35:53 falcon kernel: [ 7849.219891] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:35:53 falcon kernel: [ 7849.219900] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:35:53 falcon kernel: [ 7849.219905] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:35:53 falcon kernel: [ 7849.219909] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:35:53 falcon kernel: [ 7849.219913] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:35:53 falcon kernel: [ 7849.219916] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:35:53 falcon kernel: [ 7849.219929] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:36:05 falcon kernel: [ 7861.214428] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:36:08 falcon kernel: [ 7864.213071] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:36:08 falcon kernel: [ 7864.213080] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:36:08 falcon kernel: [ 7864.213084] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:36:08 falcon kernel: [ 7864.213089] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:36:08 falcon kernel: [ 7864.213092] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:36:08 falcon kernel: [ 7864.213096] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:36:08 falcon kernel: [ 7864.213108] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:36:20 falcon kernel: [ 7876.207606] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:36:23 falcon kernel: [ 7879.206247] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:36:23 falcon kernel: [ 7879.206256] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:36:23 falcon kernel: [ 7879.206261] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:36:23 falcon kernel: [ 7879.206265] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:36:23 falcon kernel: [ 7879.206269] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:36:23 falcon kernel: [ 7879.206272] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:36:23 falcon kernel: [ 7879.206285] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:36:35 falcon kernel: [ 7891.196786] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:36:38 falcon kernel: [ 7894.195430] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:36:38 falcon kernel: [ 7894.195438] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:36:38 falcon kernel: [ 7894.195443] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:36:38 falcon kernel: [ 7894.195448] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:36:38 falcon kernel: [ 7894.195451] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:36:38 falcon kernel: [ 7894.195455] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:36:38 falcon kernel: [ 7894.195467] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:41:02 falcon kernel: [ 8158.067363] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:41:05 falcon kernel: [ 8161.066008] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:41:05 falcon kernel: [ 8161.066017] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:41:05 falcon kernel: [ 8161.066021] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:41:05 falcon kernel: [ 8161.066026] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:41:05 falcon kernel: [ 8161.066029] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:41:05 falcon kernel: [ 8161.066033] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:41:05 falcon kernel: [ 8161.066045] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:41:17 falcon kernel: [ 8173.060542] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:41:20 falcon kernel: [ 8176.059186] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:41:20 falcon kernel: [ 8176.059194] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:41:20 falcon kernel: [ 8176.059199] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:41:20 falcon kernel: [ 8176.059203] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:41:20 falcon kernel: [ 8176.059207] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:41:20 falcon kernel: [ 8176.059210] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:41:20 falcon kernel: [ 8176.059223] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:41:32 falcon kernel: [ 8188.053720] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:41:35 falcon kernel: [ 8191.052363] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:41:35 falcon kernel: [ 8191.052375] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:41:35 falcon kernel: [ 8191.052380] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:41:35 falcon kernel: [ 8191.052384] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:41:35 falcon kernel: [ 8191.052388] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:41:35 falcon kernel: [ 8191.052391] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:41:35 falcon kernel: [ 8191.052403] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:41:47 falcon kernel: [ 8203.042901] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:41:50 falcon kernel: [ 8206.041543] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:41:50 falcon kernel: [ 8206.041552] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:41:50 falcon kernel: [ 8206.041556] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:41:50 falcon kernel: [ 8206.041561] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:41:50 falcon kernel: [ 8206.041564] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:41:50 falcon kernel: [ 8206.041568] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:41:50 falcon kernel: [ 8206.041580] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:42:02 falcon kernel: [ 8218.036079] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:42:05 falcon kernel: [ 8221.034720] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:42:05 falcon kernel: [ 8221.034728] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:42:05 falcon kernel: [ 8221.034733] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:42:05 falcon kernel: [ 8221.034737] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:42:05 falcon kernel: [ 8221.034741] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:42:05 falcon kernel: [ 8221.034745] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:42:05 falcon kernel: [ 8221.034757] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:42:17 falcon kernel: [ 8233.029257] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:42:20 falcon kernel: [ 8236.027901] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:42:20 falcon kernel: [ 8236.027910] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:42:20 falcon kernel: [ 8236.027915] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:42:20 falcon kernel: [ 8236.027919] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:42:20 falcon kernel: [ 8236.027923] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:42:20 falcon kernel: [ 8236.027927] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:42:20 falcon kernel: [ 8236.027939] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:46:50 falcon kernel: [ 8505.897105] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:46:53 falcon kernel: [ 8508.895747] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:46:53 falcon kernel: [ 8508.895756] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:46:53 falcon kernel: [ 8508.895761] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:46:53 falcon kernel: [ 8508.895766] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:46:53 falcon kernel: [ 8508.895770] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:46:53 falcon kernel: [ 8508.895773] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:46:53 falcon kernel: [ 8508.895785] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:47:05 falcon kernel: [ 8520.886285] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:47:08 falcon kernel: [ 8523.884928] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:47:08 falcon kernel: [ 8523.884937] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:47:08 falcon kernel: [ 8523.884942] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:47:08 falcon kernel: [ 8523.884946] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:47:08 falcon kernel: [ 8523.884950] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:47:08 falcon kernel: [ 8523.884953] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:47:08 falcon kernel: [ 8523.884965] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:47:20 falcon kernel: [ 8535.879464] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:47:23 falcon kernel: [ 8538.878104] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:47:23 falcon kernel: [ 8538.878112] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:47:23 falcon kernel: [ 8538.878117] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:47:23 falcon kernel: [ 8538.878121] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:47:23 falcon kernel: [ 8538.878125] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:47:23 falcon kernel: [ 8538.878129] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:47:23 falcon kernel: [ 8538.878141] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:47:35 falcon kernel: [ 8550.872641] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:47:38 falcon kernel: [ 8553.871285] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:47:38 falcon kernel: [ 8553.871294] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:47:38 falcon kernel: [ 8553.871299] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:47:38 falcon kernel: [ 8553.871303] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:47:38 falcon kernel: [ 8553.871307] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:47:38 falcon kernel: [ 8553.871311] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:47:38 falcon kernel: [ 8553.871323] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:47:50 falcon kernel: [ 8565.865820] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:47:53 falcon kernel: [ 8568.864461] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:47:53 falcon kernel: [ 8568.864470] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:47:53 falcon kernel: [ 8568.864475] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:47:53 falcon kernel: [ 8568.864479] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:47:53 falcon kernel: [ 8568.864483] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:47:53 falcon kernel: [ 8568.864486] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:47:53 falcon kernel: [ 8568.864499] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:48:05 falcon kernel: [ 8580.858999] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:48:08 falcon kernel: [ 8583.857642] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:48:08 falcon kernel: [ 8583.857651] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:48:08 falcon kernel: [ 8583.857656] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:48:08 falcon kernel: [ 8583.857660] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:48:08 falcon kernel: [ 8583.857664] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:48:08 falcon kernel: [ 8583.857667] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:48:08 falcon kernel: [ 8583.857679] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:52:08 falcon kernel: [ 8823.740490] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:52:11 falcon kernel: [ 8826.739136] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:52:11 falcon kernel: [ 8826.739145] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:52:11 falcon kernel: [ 8826.739150] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:52:11 falcon kernel: [ 8826.739154] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:52:11 falcon kernel: [ 8826.739158] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:52:11 falcon kernel: [ 8826.739161] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:52:11 falcon kernel: [ 8826.739174] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:52:23 falcon kernel: [ 8838.733668] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:52:26 falcon kernel: [ 8841.732316] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:52:26 falcon kernel: [ 8841.732325] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:52:26 falcon kernel: [ 8841.732330] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:52:26 falcon kernel: [ 8841.732334] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:52:26 falcon kernel: [ 8841.732338] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:52:26 falcon kernel: [ 8841.732342] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:52:26 falcon kernel: [ 8841.732354] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:52:38 falcon kernel: [ 8853.726846] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:52:41 falcon kernel: [ 8856.725496] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:52:41 falcon kernel: [ 8856.725505] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:52:41 falcon kernel: [ 8856.725509] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:52:41 falcon kernel: [ 8856.725514] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:52:41 falcon kernel: [ 8856.725517] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:52:41 falcon kernel: [ 8856.725521] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:52:41 falcon kernel: [ 8856.725533] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:52:53 falcon kernel: [ 8868.720025] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:52:56 falcon kernel: [ 8871.718670] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:52:56 falcon kernel: [ 8871.718679] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:52:56 falcon kernel: [ 8871.718684] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:52:56 falcon kernel: [ 8871.718688] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:52:56 falcon kernel: [ 8871.718692] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:52:56 falcon kernel: [ 8871.718695] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:52:56 falcon kernel: [ 8871.718707] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:53:08 falcon kernel: [ 8883.713203] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:53:11 falcon kernel: [ 8886.711844] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:53:11 falcon kernel: [ 8886.711852] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:53:11 falcon kernel: [ 8886.711857] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:53:11 falcon kernel: [ 8886.711862] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:53:11 falcon kernel: [ 8886.711865] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:53:11 falcon kernel: [ 8886.711869] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:53:11 falcon kernel: [ 8886.711881] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:53:23 falcon kernel: [ 8898.706381] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:53:26 falcon kernel: [ 8901.705026] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:53:26 falcon kernel: [ 8901.705035] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:53:26 falcon kernel: [ 8901.705040] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:53:26 falcon kernel: [ 8901.705045] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:53:26 falcon kernel: [ 8901.705048] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:53:26 falcon kernel: [ 8901.705052] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:53:26 falcon kernel: [ 8901.705064] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:53:38 falcon kernel: [ 8913.699559] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:53:41 falcon kernel: [ 8916.698201] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:53:41 falcon kernel: [ 8916.698210] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:53:41 falcon kernel: [ 8916.698215] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:53:41 falcon kernel: [ 8916.698219] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:53:41 falcon kernel: [ 8916.698223] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:53:41 falcon kernel: [ 8916.698226] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:53:41 falcon kernel: [ 8916.698238] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:53:53 falcon kernel: [ 8928.692738] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:53:56 falcon kernel: [ 8931.687547] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:53:56 falcon kernel: [ 8931.687637] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:53:56 falcon kernel: [ 8931.687654] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:53:56 falcon kernel: [ 8931.687662] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:53:56 falcon kernel: [ 8931.687669] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:53:56 falcon kernel: [ 8931.687676] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:53:56 falcon kernel: [ 8931.687792] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 11:54:08 falcon kernel: [ 8943.681918] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 11:54:11 falcon kernel: [ 8946.680569] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 11:54:11 falcon kernel: [ 8946.680579] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 11:54:11 falcon kernel: [ 8946.680584] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 11:54:11 falcon kernel: [ 8946.680588] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 11:54:11 falcon kernel: [ 8946.680592] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 11:54:11 falcon kernel: [ 8946.680595] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 11:54:11 falcon kernel: [ 8946.680608] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:04:18 falcon kernel: [ 9552.384986] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:04:20 falcon kernel: [ 9555.383615] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:04:20 falcon kernel: [ 9555.383626] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:04:20 falcon kernel: [ 9555.383631] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:04:20 falcon kernel: [ 9555.383635] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:04:20 falcon kernel: [ 9555.383639] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:04:20 falcon kernel: [ 9555.383642] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:04:20 falcon kernel: [ 9555.383656] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:04:32 falcon kernel: [ 9567.374159] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:04:35 falcon kernel: [ 9570.372795] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:04:35 falcon kernel: [ 9570.372804] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:04:35 falcon kernel: [ 9570.372809] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:04:35 falcon kernel: [ 9570.372814] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:04:35 falcon kernel: [ 9570.372817] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:04:35 falcon kernel: [ 9570.372821] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:04:35 falcon kernel: [ 9570.372834] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:04:47 falcon kernel: [ 9582.367324] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:04:50 falcon kernel: [ 9585.365972] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:04:50 falcon kernel: [ 9585.365982] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:04:50 falcon kernel: [ 9585.365987] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:04:50 falcon kernel: [ 9585.365991] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:04:50 falcon kernel: [ 9585.365995] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:04:50 falcon kernel: [ 9585.365998] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:04:50 falcon kernel: [ 9585.366011] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:05:02 falcon kernel: [ 9597.360504] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:05:05 falcon kernel: [ 9600.359153] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:05:05 falcon kernel: [ 9600.359163] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:05:05 falcon kernel: [ 9600.359171] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:05:05 falcon kernel: [ 9600.359175] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:05:05 falcon kernel: [ 9600.359179] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:05:05 falcon kernel: [ 9600.359182] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:05:05 falcon kernel: [ 9600.359195] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:05:17 falcon kernel: [ 9612.353683] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:05:20 falcon kernel: [ 9615.352336] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:05:20 falcon kernel: [ 9615.352346] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:05:20 falcon kernel: [ 9615.352351] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:05:20 falcon kernel: [ 9615.352355] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:05:20 falcon kernel: [ 9615.352359] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:05:20 falcon kernel: [ 9615.352362] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:05:20 falcon kernel: [ 9615.352375] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:05:32 falcon kernel: [ 9627.346860] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:05:35 falcon kernel: [ 9630.345507] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:05:35 falcon kernel: [ 9630.345516] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:05:35 falcon kernel: [ 9630.345521] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:05:35 falcon kernel: [ 9630.345526] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:05:35 falcon kernel: [ 9630.345529] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:05:35 falcon kernel: [ 9630.345533] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:05:35 falcon kernel: [ 9630.345545] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:05:47 falcon kernel: [ 9642.340038] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:05:50 falcon kernel: [ 9645.338685] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:05:50 falcon kernel: [ 9645.338695] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:05:50 falcon kernel: [ 9645.338700] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:05:50 falcon kernel: [ 9645.338704] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:05:50 falcon kernel: [ 9645.338708] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:05:50 falcon kernel: [ 9645.338711] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:05:50 falcon kernel: [ 9645.338725] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:06:02 falcon kernel: [ 9657.333216] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:06:05 falcon kernel: [ 9660.331871] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:06:05 falcon kernel: [ 9660.331881] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:06:05 falcon kernel: [ 9660.331886] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:06:05 falcon kernel: [ 9660.331890] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:06:05 falcon kernel: [ 9660.331894] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:06:05 falcon kernel: [ 9660.331897] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:06:05 falcon kernel: [ 9660.331910] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:06:17 falcon kernel: [ 9672.322401] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:06:20 falcon kernel: [ 9675.321051] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:06:20 falcon kernel: [ 9675.321061] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:06:20 falcon kernel: [ 9675.321067] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:06:20 falcon kernel: [ 9675.321071] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:06:20 falcon kernel: [ 9675.321074] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:06:20 falcon kernel: [ 9675.321078] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:06:20 falcon kernel: [ 9675.321091] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:06:32 falcon kernel: [ 9687.315670] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:06:35 falcon kernel: [ 9690.314230] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:06:35 falcon kernel: [ 9690.314240] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:06:35 falcon kernel: [ 9690.314245] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:06:35 falcon kernel: [ 9690.314249] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:06:35 falcon kernel: [ 9690.314253] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:06:35 falcon kernel: [ 9690.314257] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:06:35 falcon kernel: [ 9690.314270] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:06:47 falcon kernel: [ 9702.308760] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:06:50 falcon kernel: [ 9705.307408] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:06:50 falcon kernel: [ 9705.307417] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:06:50 falcon kernel: [ 9705.307422] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:06:50 falcon kernel: [ 9705.307426] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:06:50 falcon kernel: [ 9705.307430] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:06:50 falcon kernel: [ 9705.307434] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:06:50 falcon kernel: [ 9705.307447] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:07:02 falcon kernel: [ 9717.301938] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:07:05 falcon kernel: [ 9720.300588] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:07:05 falcon kernel: [ 9720.300598] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:07:05 falcon kernel: [ 9720.300604] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:07:05 falcon kernel: [ 9720.300608] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:07:05 falcon kernel: [ 9720.300611] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:07:05 falcon kernel: [ 9720.300615] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:07:05 falcon kernel: [ 9720.300628] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:07:17 falcon kernel: [ 9732.295119] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:07:20 falcon kernel: [ 9735.293768] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:07:20 falcon kernel: [ 9735.293778] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:07:20 falcon kernel: [ 9735.293783] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:07:20 falcon kernel: [ 9735.293788] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:07:20 falcon kernel: [ 9735.293791] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:07:20 falcon kernel: [ 9735.293795] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:07:20 falcon kernel: [ 9735.293809] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:07:32 falcon kernel: [ 9747.288298] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:07:35 falcon kernel: [ 9750.286945] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:07:35 falcon kernel: [ 9750.286955] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:07:35 falcon kernel: [ 9750.286960] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:07:35 falcon kernel: [ 9750.286964] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:07:35 falcon kernel: [ 9750.286968] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:07:35 falcon kernel: [ 9750.286972] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:07:35 falcon kernel: [ 9750.286984] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:07:47 falcon kernel: [ 9762.281474] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:07:50 falcon kernel: [ 9765.280121] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:07:50 falcon kernel: [ 9765.280131] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:07:50 falcon kernel: [ 9765.280136] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:07:50 falcon kernel: [ 9765.280140] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:07:50 falcon kernel: [ 9765.280143] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:07:50 falcon kernel: [ 9765.280147] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:07:50 falcon kernel: [ 9765.280160] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:08:02 falcon kernel: [ 9777.270652] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:08:05 falcon kernel: [ 9780.269299] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:08:05 falcon kernel: [ 9780.269310] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:08:05 falcon kernel: [ 9780.269315] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:08:05 falcon kernel: [ 9780.269319] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:08:05 falcon kernel: [ 9780.269323] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:08:05 falcon kernel: [ 9780.269326] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:08:05 falcon kernel: [ 9780.269340] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:08:17 falcon kernel: [ 9792.263826] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:08:20 falcon kernel: [ 9795.262472] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:08:20 falcon kernel: [ 9795.262482] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:08:20 falcon kernel: [ 9795.262487] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:08:20 falcon kernel: [ 9795.262492] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:08:20 falcon kernel: [ 9795.262495] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:08:20 falcon kernel: [ 9795.262499] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:08:20 falcon kernel: [ 9795.262512] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:08:32 falcon kernel: [ 9807.257004] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:08:35 falcon kernel: [ 9810.255653] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:08:35 falcon kernel: [ 9810.255663] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:08:35 falcon kernel: [ 9810.255668] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:08:35 falcon kernel: [ 9810.255672] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:08:35 falcon kernel: [ 9810.255676] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:08:35 falcon kernel: [ 9810.255679] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:08:35 falcon kernel: [ 9810.255692] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:08:47 falcon kernel: [ 9822.250181] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:08:50 falcon kernel: [ 9825.248828] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:08:50 falcon kernel: [ 9825.248838] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:08:50 falcon kernel: [ 9825.248843] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:08:50 falcon kernel: [ 9825.248850] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:08:50 falcon kernel: [ 9825.248854] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:08:50 falcon kernel: [ 9825.248857] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:08:50 falcon kernel: [ 9825.248871] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:10:02 falcon kernel: [ 9897.212074] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:10:05 falcon kernel: [ 9900.210721] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:10:05 falcon kernel: [ 9900.210731] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:10:05 falcon kernel: [ 9900.210736] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:10:05 falcon kernel: [ 9900.210740] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:10:05 falcon kernel: [ 9900.210744] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:10:05 falcon kernel: [ 9900.210747] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:10:05 falcon kernel: [ 9900.210760] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:10:17 falcon kernel: [ 9912.205252] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:10:20 falcon kernel: [ 9915.203899] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:10:20 falcon kernel: [ 9915.203909] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:10:20 falcon kernel: [ 9915.203914] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:10:20 falcon kernel: [ 9915.203919] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:10:20 falcon kernel: [ 9915.203922] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:10:20 falcon kernel: [ 9915.203926] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:10:20 falcon kernel: [ 9915.203939] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:10:32 falcon kernel: [ 9927.198431] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:10:35 falcon kernel: [ 9930.197077] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:10:35 falcon kernel: [ 9930.197087] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:10:35 falcon kernel: [ 9930.197092] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:10:35 falcon kernel: [ 9930.197097] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:10:35 falcon kernel: [ 9930.197100] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:10:35 falcon kernel: [ 9930.197104] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:10:35 falcon kernel: [ 9930.197116] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:10:47 falcon kernel: [ 9942.191609] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:10:50 falcon kernel: [ 9945.190255] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:10:50 falcon kernel: [ 9945.190265] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:10:50 falcon kernel: [ 9945.190270] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:10:50 falcon kernel: [ 9945.190274] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:10:50 falcon kernel: [ 9945.190278] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:10:50 falcon kernel: [ 9945.190282] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:10:50 falcon kernel: [ 9945.190296] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:11:02 falcon kernel: [ 9957.184797] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:11:05 falcon kernel: [ 9960.183442] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:11:05 falcon kernel: [ 9960.183452] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:11:05 falcon kernel: [ 9960.183457] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:11:05 falcon kernel: [ 9960.183461] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:11:05 falcon kernel: [ 9960.183464] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:11:05 falcon kernel: [ 9960.183468] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:11:05 falcon kernel: [ 9960.183481] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:11:17 falcon kernel: [ 9972.177974] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:11:20 falcon kernel: [ 9975.176626] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:11:20 falcon kernel: [ 9975.176637] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:11:20 falcon kernel: [ 9975.176642] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:11:20 falcon kernel: [ 9975.176646] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:11:20 falcon kernel: [ 9975.176650] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:11:20 falcon kernel: [ 9975.176653] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:11:20 falcon kernel: [ 9975.176667] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  1 12:15:50 falcon kernel: [10245.041817] NETDEV WATCHDOG: eth0: transmit timed out
Sep  1 12:15:53 falcon kernel: [10248.040467] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Sep  1 12:15:53 falcon kernel: [10248.040476] eth0: Tx queue start entry 4  dirty entry 0.
Sep  1 12:15:53 falcon kernel: [10248.040482] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep  1 12:15:53 falcon kernel: [10248.040486] eth0:  Tx descriptor 1 is 0008a03c.
Sep  1 12:15:53 falcon kernel: [10248.040490] eth0:  Tx descriptor 2 is 0008a03c.
Sep  1 12:15:53 falcon kernel: [10248.040493] eth0:  Tx descriptor 3 is 0008a03c.
Sep  1 12:15:53 falcon kernel: [10248.040506] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

---

### Post by Naddiseo on 2007-09-01
Good to see I'm not the only one with this problem; I'm getting the same Tx descriptor errors. My windows works just fine, but all the kernels I try, and both feisty and dapper live CDs wont connect to my router, which is strange because eariler last week the live Cds worked OK, and I thought it was just a broken package I downloaded for gutsy. This issue is really bothering me though, I'm stuck on windows!!

---

### Post by noob12 on 2007-09-01
The errors in your syslog are indicative of PCI routing problems during the boot.  This might address the remaining issues; I think it's a prerequisite to getting over the flakiness anyway.

Can you post the output of these to show what hardware and driver you have running, and
the boot log.
```

lspci -nn

sudo lshw -C network

dmesg

```
From the dmesg output we want to see if we can determine a set of boot flags we might use to avoid these.

---

### Post by schakravarthi on 2007-09-01
lspci -nn

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller [1022:700e] (rev 13)
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge [1022:700f]
00:04.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 40)
00:04.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:04.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 16)
00:04.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 16)
00:04.4 SMBus [0c05]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 40)
00:0b.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:044e] (rev 02)
00:0e.0 SCSI storage controller [0100]: Adaptec AHA-7850 [9004:5078] (rev 03)
00:0f.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
00:0f.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
00:12.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:05.0 VGA compatible controller [0300]: nVidia Corporation NV15 [GeForce2 GTS/Pro] [10de:0150] (rev a3)

lshw- C network

 *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 10
       serial: 00:e0:18:2f:f9:f9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.11.4 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e0000400-e00004ff irq:16

##############################################
dmesg

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6000 size: 000000000001a000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fef0000 end: 000000000fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fff0000 size: 000000000000fc00 end: 000000000ffffc00 type: 3
[    0.000000] copy_e820_map() start: 000000000ffffc00 size: 0000000000000400 end: 0000000010000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65520
[    0.000000]   HighMem     65520 ->    65520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65520
[    0.000000] On node 0 totalpages: 65520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60945 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f77f0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0fffb5d6
[    0.000000] ACPI: FADT (v001 HP     Bermuda  0x06040000 PTL  0x00000001) @ 0x0fffb606
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x0ffffb88
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0ffffbd8
[    0.000000] ACPI: DSDT (v001     HP  Bermuda 0x06040000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] Detected 1327.466 MHz processor.
[   18.142318] Built 1 zonelists.  Total pages: 65009
[   18.142324] Kernel command line: root=UUID=357b4b1b-369d-4285-a8b0-43f7e17b976c ro quiet splash
[   18.142575] mapped APIC to ffffd000 (fee00000)
[   18.142579] mapped IOAPIC to ffffc000 (fec00000)
[   18.142584] Enabling fast FPU save and restore... done.
[   18.142601] Initializing CPU#0
[   18.142693] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   18.143861] Console: colour VGA+ 80x25
[   18.144165] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.144360] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   18.157790] Memory: 248760k/262080k available (1992k kernel code, 12736k reserved, 900k data, 328k init, 0k highmem)
[   18.157807] virtual kernel memory layout:
[   18.157809]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.157811]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.157813]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   18.157815]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[   18.157817]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.157819]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.157822]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.157826] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.234655] Calibrating delay using timer specific routine.. 2657.52 BogoMIPS (lpj=5315058)
[   18.234721] Security Framework v1.0.0 initialized
[   18.234731] SELinux:  Disabled at boot.
[   18.234757] Mount-cache hash table entries: 512
[   18.234984] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[   18.234997] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.235002] CPU: L2 Cache: 256K (64 bytes/line)
[   18.235006] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000
[   18.235023] Compat vDSO mapped to ffffe000.
[   18.235033] Remapping vsyscall page to ffffe000
[   18.235047] Checking 'hlt' instruction... OK.
[   18.250700] SMP alternatives: switching to UP code
[   18.251073] Freeing SMP alternatives: 11k freed
[   18.251436] Early unpacking initramfs... done
[   18.723937] ACPI: Core revision 20060707
[   18.726004] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.726970] ACPI Error (psloop-0196): Found unknown opcode 4 at AML address d080cb87 offset 44E9, ignoring [20060707]
[   18.727764] ACPI Error (psloop-0196): Found unknown opcode 4 at AML address d080cb87 offset 44E9, ignoring [20060707]
[   18.739697] CPU0: AMD Athlon(tm) Processor stepping 04
[   18.739729] Total of 1 processors activated (2657.52 BogoMIPS).
[   18.740482] ENABLING IO-APIC IRQs
[   18.740803] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.886412] Brought up 1 CPUs
[   18.886849] Booting paravirtualized kernel on bare hardware
[   18.886961] Time: 16:24:12  Date: 08/01/107
[   18.887012] NET: Registered protocol family 16
[   18.887162] EISA bus registered
[   18.887169] ACPI: bus type pci registered
[   18.895392] PCI: PCI BIOS revision 2.10 entry at 0xfd7ee, last bus=1
[   18.895395] PCI: Using configuration type 1
[   18.895398] Setting up standard PCI resources
[   18.903941] ACPI: Interpreter enabled
[   18.903951] ACPI: Using IOAPIC for interrupt routing
[   18.904476] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.904485] PCI: Probing PCI hardware (bus 00)
[   18.904944] PCI quirk: region 6800-687f claimed by vt82c686 HW-mon
[   18.904950] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[   18.905244] Boot video device is 0000:01:05.0
[   18.905283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.909514] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   18.909836] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[   18.910173] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   18.910553] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   18.910901] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 7 9 14 15) *0, disabled.
[   18.911251] ACPI: PCI Interrupt Link [LNKS] (IRQs 3 4 5 6 7 10 14 15) *0, disabled.
[   18.914100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[   18.915681] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.915700] pnp: PnP ACPI init
[   18.918824] ACPI Error (dsopcode-0548): Field [ALB2] at 120 exceeds Buffer [CRSA] size 104 (bits) [20060707]
[   18.918835] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node ce4df98c), AE_AML_BUFFER_LIMIT
[   18.918871] ACPI Error (uteval-0212): Method execution failed [\_SB_.PCI0.PIB_.SIO0.LPT_._CRS] (Node ce4df98c), AE_AML_BUFFER_LIMIT
[   18.918882] pnp: PnPACPI: METHOD_NAME__CRS failure for PNP0401
[   18.919232] pnp: PnP ACPI: found 12 devices
[   18.919239] PnPBIOS: Disabled by ACPI PNP
[   18.919340] PCI: Using ACPI for IRQ routing
[   18.919347] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.921143] NET: Registered protocol family 8
[   18.921146] NET: Registered protocol family 20
[   18.921362] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   18.921368] pnp: 00:08: ioport range 0x8000-0x807f could not be reserved
[   18.921373] pnp: 00:08: ioport range 0x6800-0x687f has been reserved
[   18.921377] pnp: 00:08: ioport range 0x400-0x40f has been reserved
[   18.921816] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:01:05.0
[   18.921869] PCI: Bridge: 0000:00:01.0
[   18.921872]   IO window: disabled.
[   18.921878]   MEM window: e1000000-e1ffffff
[   18.921883]   PREFETCH window: f0000000-f7ffffff
[   18.921935] NET: Registered protocol family 2
[   18.958453] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   18.958576] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   18.958805] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   18.958920] TCP: Hash tables configured (established 8192 bind 4096)
[   18.958925] TCP reno registered
[   18.970488] checking if image is initramfs... it is
[   19.864659] Freeing initrd memory: 6786k freed
[   19.864949] Simple Boot Flag at 0x36 set to 0x1
[   19.865413] audit: initializing netlink socket (disabled)
[   19.865435] audit(1188663853.796:1): initialized
[   19.865603] VFS: Disk quotas dquot_6.5.1
[   19.865633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.865712] io scheduler noop registered
[   19.865717] io scheduler anticipatory registered
[   19.865720] io scheduler deadline registered
[   19.865732] io scheduler cfq registered (default)
[   19.865749] PCI: Enabling Via external APIC routing
[   19.866118] isapnp: Scanning for PnP cards...
[   20.220282] isapnp: No Plug & Play device found
[   20.264613] Real Time Clock Driver v1.12ac
[   20.264693] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.264869] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.265194] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.266241] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.266722] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.267086] mice: PS/2 mouse device common for all mice
[   20.267965] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.268377] input: Macintosh mouse button emulation as /class/input/input0
[   20.268431] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.268437] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.268737] PNP: PS/2 Controller [PNP0303:KBC] at 0x60,0x64 irq 1
[   20.268742] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   20.269182] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.269190] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.269385] EISA: Probing bus 0 at eisa.0
[   20.269400] Cannot allocate resource for EISA slot 1
[   20.269406] Cannot allocate resource for EISA slot 2
[   20.269426] Cannot allocate resource for EISA slot 6
[   20.269434] Cannot allocate resource for EISA slot 8
[   20.269437] EISA: Detected 0 cards.
[   20.299729] TCP cubic registered
[   20.299740] NET: Registered protocol family 1
[   20.299777] Using IPI No-Shortcut mode
[   20.299908] ACPI: (supports S0 S1 S3 S4 S5)
[   20.299971]   Magic number: 7:164:438
[   20.300861] Freeing unused kernel memory: 328k freed
[   20.301642] Time: tsc clocksource has been installed.
[   20.317784] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.636452] Capability LSM initialized
[   22.462840] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   22.462874] VP_IDE: chipset revision 6
[   22.462878] VP_IDE: not 100% native mode: will probe irqs later
[   22.462892] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:04.1
[   22.462903]     ide0: BM-DMA at 0x1400-0x1407, BIOS settings: hda:pio, hdb:DMA
[   22.462921]     ide1: BM-DMA at 0x1408-0x140f, BIOS settings: hdc:pio, hdd:pio
[   22.462931] Probing IDE interface ide0...
[   22.500226] usbcore: registered new interface driver usbfs
[   22.500264] usbcore: registered new interface driver hub
[   22.500304] usbcore: registered new device driver usb
[   22.501815] USB Universal Host Controller Interface driver v3.0
[   22.554071] SCSI subsystem initialized
[   22.605648] 8139too Fast Ethernet driver 0.9.28
[   22.759782] Floppy drive(s): fd0 is 1.44M
[   22.795786] FDC 0 is a post-1991 82077
[   22.928639] hda: ST340810A, ATA DISK drive
[   23.208505] hdb: WDC WD1200JB-00FUA0, ATA DISK drive
[   23.272353] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.283436] Probing IDE interface ide1...
[   24.148071] hdc: LITE-ON LTR-12101B, ATAPI CD/DVD-ROM drive
[   24.931703] hdd: LG CD-ROM CRD-8485B, ATAPI CD/DVD-ROM drive
[   24.988006] ide1 at 0x170-0x177,0x376 on irq 15
[   25.003296] libata version 2.20 loaded.
[   25.007202] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 9
[   25.007220] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKU] -> GSI 9 (level, low) -> IRQ 9
[   25.007239] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   25.007867] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   25.007912] uhci_hcd 0000:00:04.2: irq 9, io base 0x00001420
[   25.008826] usb usb1: configuration #1 chosen from 1 choice
[   25.009182] hub 1-0:1.0: USB hub found
[   25.009205] hub 1-0:1.0: 2 ports detected
[   25.024502] hda: max request size: 128KiB
[   25.037027] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   25.037041] hda: cache flushes not supported
[   25.037113]  hda: hda1 hda2 hda3
[   25.098499] hdb: max request size: 512KiB
[   25.099657] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=14593/255/63, UDMA(100)
[   25.101498] hdb: cache flushes supported
[   25.101542]  hdb:<6>ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKU] -> GSI 9 (level, low) -> IRQ 9
[   25.111633] uhci_hcd 0000:00:04.3: UHCI Host Controller
[   25.111673] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[   25.111701] uhci_hcd 0000:00:04.3: irq 9, io base 0x00001440
[   25.111863] usb usb2: configuration #1 chosen from 1 choice
[   25.111904] hub 2-0:1.0: USB hub found
[   25.111919] hub 2-0:1.0: 2 ports detected
[   25.118656]  hdb1 hdb2 hdb3 hdb4
[   25.143002] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   25.143017] Uniform CD-ROM driver Revision: 3.20
[   25.187715] hdd: ATAPI 48X CD-ROM drive, 128kB Cache, DMA
[   25.215757] PCI: Enabling device 0000:00:0e.0 (0010 -> 0013)
[   25.215777] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 16
[   25.216931] ahc_pci:0:14:0: Host Adapter Bios disabled.  Using default SCSI device parameters
[   25.351332] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   25.532754] usb 1-1: configuration #1 chosen from 1 choice
[   25.771127] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   25.851559] Attempting manual resume
[   25.851566] swsusp: Resume From Partition 3:2
[   25.851568] PM: Checking swsusp image.
[   25.851805] PM: Resume from disk failed.
[   25.898054] kjournald starting.  Commit interval 5 seconds
[   25.898075] EXT3-fs: mounted filesystem with ordered data mode.
[   25.944460] usb 1-2: configuration #1 chosen from 1 choice
[   26.186919] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   26.354024] usb 2-1: configuration #1 chosen from 1 choice
[   26.594743] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   26.826706] usb 2-2: configuration #1 chosen from 1 choice
[   26.829809] usbcore: registered new interface driver libusual
[   27.328232] Initializing USB Mass Storage driver...
[   27.328362] scsi1 : SCSI emulation for USB Mass Storage devices
[   27.328443] usb-storage: device found at 2
[   27.328446] usb-storage: waiting for device to settle before scanning
[   27.328524] scsi2 : SCSI emulation for USB Mass Storage devices
[   27.328581] usb-storage: device found at 3
[   27.328584] usb-storage: waiting for device to settle before scanning
[   27.328597] usbcore: registered new interface driver usb-storage
[   27.328601] USB Mass Storage support registered.
[   32.326806] usb-storage: device scan complete
[   32.328076] usb-storage: device scan complete
[   32.362624] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 740e  42FF PQ: 0 ANSI: 0
[   35.133513] scsi 2:0:0:0: Direct-Access     USB-HS   SAMSUNG HD300LD  0.01 PQ: 0 ANSI: 0
[   40.216346] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   40.216350]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   40.216352]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   40.216355] 
[   40.217018] PCI: Enabling device 0000:00:12.0 (0000 -> 0003)
[   40.217032] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 17 (level, low) -> IRQ 16
[   40.217328] eth0: RealTek RTL8139 at 0xd0828400, 00:e0:18:2f:f9:f9, IRQ 16
[   40.217333] eth0:  Identified 8139 chip type 'RTL-8139C'
[   42.912733] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.720362] NET: Registered protocol family 17
[   45.466255] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.529421] shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 ss_did 0
[   45.529432] shpchp: shpc_init: cannot reserve MMIO region
[   45.529456] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.730907] parport_pc: VIA 686A/8231 detected
[   45.730914] parport_pc: probing current configuration
[   45.730934] parport_pc: Current parallel port base: 0x378
[   45.731018] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   45.825793] parport_pc: VIA parallel port: io=0x378, irq=7
[   45.961322] PCI: Enabling device 0000:00:0f.1 (0000 -> 0001)
[   45.976928] gameport: EMU10K1 is pci0000:00:0f.1/gameport0, io 0x1468, speed 1296kHz
[   46.256638] Linux agpgart interface v0.102 (c) Dave Jones
[   46.479518] agpgart: Detected AMD 761 chipset
[   46.496783] agpgart: AGP aperture is 128M @ 0xe8000000
[   46.549257] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   47.232027] input: PC Speaker as /class/input/input2
[   47.262442] usbcore: registered new interface driver hiddev
[   47.271147] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   47.271981] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   47.335278] input: Logitech Trackball as /class/input/input3
[   47.335429] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:04.2-2
[   47.335460] usbcore: registered new interface driver usbhid
[   47.335466] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   47.473896] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   47.473962] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   47.594592] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1706
[   47.594618] usbcore: registered new interface driver usblp
[   47.594734] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   47.783911] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[   47.853202] sda: Write Protect is off
[   47.853209] sda: Mode Sense: 0b 00 00 08
[   47.853213] sda: assuming drive cache: write through
[   47.861368] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[   47.875874] sda: Write Protect is off
[   47.875918] sda: Mode Sense: 0b 00 00 08
[   47.875933] sda: assuming drive cache: write through
[   47.875989]  sda: sda1
[   47.897225] sd 2:0:0:0: Attached scsi disk sda
[   48.273683] PCI: Enabling device 0000:00:0f.0 (0000 -> 0001)
[   48.273703] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 17
[   49.128915] fuse init (API version 7.8)
[   49.180941] lp0: using parport0 (interrupt-driven).
[   49.237075] Adding 971924k swap on /dev/disk/by-uuid/90fd0f38-7f4f-469d-9ad5-1bc3a876d61d.  Priority:-1 extents:1 across:971924k
[   49.820294] EXT3 FS on hda3, internal journal
[  129.755080] kjournald starting.  Commit interval 5 seconds
[  129.755464] EXT3 FS on hdb1, internal journal
[  129.755473] EXT3-fs: mounted filesystem with ordered data mode.
[  139.136317] ibm_acpi: ec object not found
[  139.258929] input: Power Button (FF) as /class/input/input4
[  139.259341] ACPI: Power Button (FF) [PWRF]
[  139.301707] input: Power Button (CM) as /class/input/input5
[  139.302134] ACPI: Power Button (CM) [PWRB]
[  139.373909] No dock devices found.
[  139.810828] Using specific hotkey driver
[  139.954237] pcc_acpi: loading...
[  140.698392] powernow: No powernow capabilities detected
[  151.967366] ppdev: user-space parallel port driver
[  160.129021] apm: BIOS not found.
[  163.476505] Bluetooth: Core ver 2.11
[  163.476616] NET: Registered protocol family 31
[  163.476619] Bluetooth: HCI device and connection manager initialized
[  163.476626] Bluetooth: HCI socket layer initialized
[  163.668970] Bluetooth: L2CAP ver 2.8
[  163.668978] Bluetooth: L2CAP socket layer initialized
[  163.975344] Bluetooth: RFCOMM socket layer initialized
[  163.975373] Bluetooth: RFCOMM TTY layer initialized
[  163.975376] Bluetooth: RFCOMM ver 1.8
[ 2028.524453] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 2028.525124]  [<c01543a4>] __report_bad_irq+0x24/0x80
[ 2028.525332]  [<c015465e>] note_interrupt+0x25e/0x290
[ 2028.525352]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[ 2028.525363]  [<c0154f91>] handle_fasteoi_irq+0xc1/0xf0
[ 2028.525374]  [<c0105b70>] do_IRQ+0x40/0x80
[ 2028.525389]  [<c0104233>] common_interrupt+0x23/0x30
[ 2028.525396]  [<c0101e00>] default_idle+0x0/0x60
[ 2028.525411]  [<c011c092>] native_safe_halt+0x2/0x10
[ 2028.525524]  [<c0101e3d>] default_idle+0x3d/0x60
[ 2028.525530]  [<c0101409>] cpu_idle+0x49/0xd0
[ 2028.525543]  [<c03d97f5>] start_kernel+0x365/0x420
[ 2028.525676]  [<c03d9230>] unknown_bootoption+0x0/0x260
[ 2028.525702]  =======================
[ 2028.525708] handlers:
[ 2028.525715] [<d08b68c0>] (ahc_linux_isr+0x0/0x250 [aic7xxx])
[ 2028.526349] [<d08f1bb0>] (rtl8139_interrupt+0x0/0x480 [8139too])
[ 2028.526368] Disabling IRQ #16
[ 3023.442023] NETDEV WATCHDOG: eth0: transmit timed out
[ 3026.440621] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3026.440631] eth0: Tx queue start entry 20  dirty entry 16.
[ 3026.440636] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3026.440641] eth0:  Tx descriptor 1 is 0008a03c.
[ 3026.440644] eth0:  Tx descriptor 2 is 0008a03c.
[ 3026.440648] eth0:  Tx descriptor 3 is 0008a03c.
[ 3026.440660] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3038.434972] NETDEV WATCHDOG: eth0: transmit timed out
[ 3041.433573] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3041.433583] eth0: Tx queue start entry 4  dirty entry 0.
[ 3041.433588] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3041.433593] eth0:  Tx descriptor 1 is 0008a03c.
[ 3041.433596] eth0:  Tx descriptor 2 is 0008a03c.
[ 3041.433600] eth0:  Tx descriptor 3 is 0008a03c.
[ 3041.433613] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3053.427958] NETDEV WATCHDOG: eth0: transmit timed out
[ 3056.426523] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3056.426532] eth0: Tx queue start entry 4  dirty entry 0.
[ 3056.426537] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3056.426541] eth0:  Tx descriptor 1 is 0008a03c.
[ 3056.426545] eth0:  Tx descriptor 2 is 0008a03c.
[ 3056.426548] eth0:  Tx descriptor 3 is 0008a03c.
[ 3056.426560] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3068.420876] NETDEV WATCHDOG: eth0: transmit timed out
[ 3071.419474] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3071.419483] eth0: Tx queue start entry 4  dirty entry 0.
[ 3071.419488] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3071.419492] eth0:  Tx descriptor 1 is 0008a03c.
[ 3071.419496] eth0:  Tx descriptor 2 is 0008a03c.
[ 3071.419500] eth0:  Tx descriptor 3 is 0008a03c.
[ 3071.419512] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3083.413828] NETDEV WATCHDOG: eth0: transmit timed out
[ 3086.412426] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3086.412436] eth0: Tx queue start entry 4  dirty entry 0.
[ 3086.412440] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3086.412445] eth0:  Tx descriptor 1 is 0008a03c.
[ 3086.412448] eth0:  Tx descriptor 2 is 0008a03c.
[ 3086.412452] eth0:  Tx descriptor 3 is 0008a03c.
[ 3086.412464] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3098.406780] NETDEV WATCHDOG: eth0: transmit timed out
[ 3101.405379] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3101.405388] eth0: Tx queue start entry 4  dirty entry 0.
[ 3101.405393] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3101.405397] eth0:  Tx descriptor 1 is 0008a03c.
[ 3101.405401] eth0:  Tx descriptor 2 is 0008a03c.
[ 3101.405404] eth0:  Tx descriptor 3 is 0008a03c.
[ 3101.405416] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3113.399736] NETDEV WATCHDOG: eth0: transmit timed out
[ 3116.398331] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3116.398341] eth0: Tx queue start entry 4  dirty entry 0.
[ 3116.398346] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3116.398350] eth0:  Tx descriptor 1 is 0008a03c.
[ 3116.398353] eth0:  Tx descriptor 2 is 0008a03c.
[ 3116.398357] eth0:  Tx descriptor 3 is 0008a03c.
[ 3116.398369] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3128.392685] NETDEV WATCHDOG: eth0: transmit timed out
[ 3131.391284] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3131.391294] eth0: Tx queue start entry 4  dirty entry 0.
[ 3131.391299] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3131.391303] eth0:  Tx descriptor 1 is 0008a03c.
[ 3131.391307] eth0:  Tx descriptor 2 is 0008a03c.
[ 3131.391310] eth0:  Tx descriptor 3 is 0008a03c.
[ 3131.391322] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3143.381640] NETDEV WATCHDOG: eth0: transmit timed out
[ 3146.380237] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3146.380246] eth0: Tx queue start entry 4  dirty entry 0.
[ 3146.380251] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3146.380255] eth0:  Tx descriptor 1 is 0008a03c.
[ 3146.380258] eth0:  Tx descriptor 2 is 0008a03c.
[ 3146.380262] eth0:  Tx descriptor 3 is 0008a03c.
[ 3146.380274] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3158.374591] NETDEV WATCHDOG: eth0: transmit timed out
[ 3161.373193] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3161.373201] eth0: Tx queue start entry 4  dirty entry 0.
[ 3161.373206] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3161.373210] eth0:  Tx descriptor 1 is 0008a03c.
[ 3161.373214] eth0:  Tx descriptor 2 is 0008a03c.
[ 3161.373217] eth0:  Tx descriptor 3 is 0008a03c.
[ 3161.373230] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3173.367544] NETDEV WATCHDOG: eth0: transmit timed out
[ 3176.366166] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3176.366176] eth0: Tx queue start entry 4  dirty entry 0.
[ 3176.366181] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3176.366185] eth0:  Tx descriptor 1 is 0008a03c.
[ 3176.366189] eth0:  Tx descriptor 2 is 0008a03c.
[ 3176.366192] eth0:  Tx descriptor 3 is 0008a03c.
[ 3176.366205] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3187.670290] hdc: tray open
[ 3187.670980] end_request: I/O error, dev hdc, sector 0
[ 3187.670989] Buffer I/O error on device hdc, logical block 0
[ 3187.670996] Buffer I/O error on device hdc, logical block 1
[ 3187.671001] Buffer I/O error on device hdc, logical block 2
[ 3187.671005] Buffer I/O error on device hdc, logical block 3
[ 3187.671010] Buffer I/O error on device hdc, logical block 4
[ 3187.671014] Buffer I/O error on device hdc, logical block 5
[ 3187.671018] Buffer I/O error on device hdc, logical block 6
[ 3187.671022] Buffer I/O error on device hdc, logical block 7
[ 3187.671495] hdc: tray open
[ 3187.672071] end_request: I/O error, dev hdc, sector 0
[ 3187.672076] Buffer I/O error on device hdc, logical block 0
[ 3187.672582] hdc: tray open
[ 3187.673157] end_request: I/O error, dev hdc, sector 4
[ 3187.673162] Buffer I/O error on device hdc, logical block 1
[ 3187.673727] hdc: tray open
[ 3187.674302] end_request: I/O error, dev hdc, sector 0
[ 3187.674814] hdc: tray open
[ 3187.675390] end_request: I/O error, dev hdc, sector 4
[ 3187.675908] hdc: tray open
[ 3187.676483] end_request: I/O error, dev hdc, sector 0
[ 3187.676994] hdc: tray open
[ 3187.677603] end_request: I/O error, dev hdc, sector 4
[ 3187.678121] hdc: tray open
[ 3187.678699] end_request: I/O error, dev hdc, sector 0
[ 3187.679210] hdc: tray open
[ 3187.679990] end_request: I/O error, dev hdc, sector 4
[ 3187.680468] hdc: tray open
[ 3187.681166] end_request: I/O error, dev hdc, sector 0
[ 3187.681811] hdc: tray open
[ 3187.682341] end_request: I/O error, dev hdc, sector 4
[ 3187.689735] hdd: tray open
[ 3187.689924] end_request: I/O error, dev hdd, sector 0
[ 3187.690196] hdd: tray open
[ 3187.690382] end_request: I/O error, dev hdd, sector 0
[ 3187.690521] hdd: tray open
[ 3187.690723] end_request: I/O error, dev hdd, sector 4
[ 3187.690907] hdd: tray open
[ 3187.691092] end_request: I/O error, dev hdd, sector 0
[ 3187.691236] hdd: tray open
[ 3187.691423] end_request: I/O error, dev hdd, sector 4
[ 3187.691701] hdd: tray open
[ 3187.691887] end_request: I/O error, dev hdd, sector 0
[ 3187.692029] hdd: tray open
[ 3187.692215] end_request: I/O error, dev hdd, sector 4
[ 3187.692400] hdd: tray open
[ 3187.692587] end_request: I/O error, dev hdd, sector 0
[ 3187.692741] hdd: tray open
[ 3187.692927] end_request: I/O error, dev hdd, sector 4
[ 3187.693115] hdd: tray open
[ 3187.693301] end_request: I/O error, dev hdd, sector 0
[ 3187.693442] hdd: tray open
[ 3187.693628] end_request: I/O error, dev hdd, sector 4
[ 3187.992611] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3187.992780]     Additional sense: Medium not present
[ 3187.992941] end_request: I/O error, dev sr0, sector 0
[ 3188.000533] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.000547]     Additional sense: Medium not present
[ 3188.000560] end_request: I/O error, dev sr0, sector 0
[ 3188.007531] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.007540]     Additional sense: Medium not present
[ 3188.007547] end_request: I/O error, dev sr0, sector 4
[ 3188.014467] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.014474]     Additional sense: Medium not present
[ 3188.014479] end_request: I/O error, dev sr0, sector 0
[ 3188.021495] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.021507]     Additional sense: Medium not present
[ 3188.021515] end_request: I/O error, dev sr0, sector 4
[ 3188.028494] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.028506]     Additional sense: Medium not present
[ 3188.028514] end_request: I/O error, dev sr0, sector 0
[ 3188.035488] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.035516]     Additional sense: Medium not present
[ 3188.035521] end_request: I/O error, dev sr0, sector 4
[ 3188.042480] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.042494]     Additional sense: Medium not present
[ 3188.042502] end_request: I/O error, dev sr0, sector 0
[ 3188.049481] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.049487]     Additional sense: Medium not present
[ 3188.049494] end_request: I/O error, dev sr0, sector 4
[ 3188.056473] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.056492]     Additional sense: Medium not present
[ 3188.056497] end_request: I/O error, dev sr0, sector 0
[ 3188.063474] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3188.063507]     Additional sense: Medium not present
[ 3188.063515] end_request: I/O error, dev sr0, sector 4
[ 3188.360575] NETDEV WATCHDOG: eth0: transmit timed out
[ 3191.359099] eth0: Transmit timeout, status 0c 0005 c07f media 10.
[ 3191.359109] eth0: Tx queue start entry 4  dirty entry 0.
[ 3191.359113] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
[ 3191.359118] eth0:  Tx descriptor 1 is 0008a03c.
[ 3191.359121] eth0:  Tx descriptor 2 is 0008a03c.
[ 3191.359125] eth0:  Tx descriptor 3 is 0008a03c.
[ 3191.359137] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 3196.958172] hdc: tray open
[ 3196.958828] end_request: I/O error, dev hdc, sector 0
[ 3196.958835] printk: 44 messages suppressed.
[ 3196.958840] Buffer I/O error on device hdc, logical block 0
[ 3196.959588] hdc: tray open
[ 3196.960449] end_request: I/O error, dev hdc, sector 0
[ 3196.960927] hdc: tray open
[ 3196.961655] end_request: I/O error, dev hdc, sector 4
[ 3196.962385] hdc: tray open
[ 3196.963043] end_request: I/O error, dev hdc, sector 0
[ 3196.963561] hdc: tray open
[ 3196.964237] end_request: I/O error, dev hdc, sector 4
[ 3196.964755] hdc: tray open
[ 3196.965575] end_request: I/O error, dev hdc, sector 0
[ 3196.966077] hdc: tray open
[ 3196.966785] end_request: I/O error, dev hdc, sector 4
[ 3196.967509] hdc: tray open
[ 3196.968191] end_request: I/O error, dev hdc, sector 0
[ 3196.968718] hdc: tray open
[ 3196.969376] end_request: I/O error, dev hdc, sector 4
[ 3196.969887] hdc: tray open
[ 3196.970577] end_request: I/O error, dev hdc, sector 0
[ 3196.971095] hdc: tray open
[ 3196.971914] end_request: I/O error, dev hdc, sector 4
[ 3196.979170] hdd: tray open
[ 3196.979360] end_request: I/O error, dev hdd, sector 0
[ 3196.979994] hdd: tray open
[ 3196.980182] end_request: I/O error, dev hdd, sector 0
[ 3196.980320] hdd: tray open
[ 3196.980507] end_request: I/O error, dev hdd, sector 4
[ 3196.981296] hdd: tray open
[ 3196.981481] end_request: I/O error, dev hdd, sector 0
[ 3196.981626] hdd: tray open
[ 3196.981811] end_request: I/O error, dev hdd, sector 4
[ 3196.982630] hdd: tray open
[ 3196.982815] end_request: I/O error, dev hdd, sector 0
[ 3196.982975] hdd: tray open
[ 3196.983161] end_request: I/O error, dev hdd, sector 4
[ 3196.983893] hdd: tray open
[ 3196.984082] end_request: I/O error, dev hdd, sector 0
[ 3196.984263] hdd: tray open
[ 3196.984467] end_request: I/O error, dev hdd, sector 4
[ 3196.985200] hdd: tray open
[ 3196.985386] end_request: I/O error, dev hdd, sector 0
[ 3196.985527] hdd: tray open
[ 3196.985713] end_request: I/O error, dev hdd, sector 4
[ 3197.319796] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.319808]     Additional sense: Medium not present
[ 3197.319833] end_request: I/O error, dev sr0, sector 0
[ 3197.327785] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.327792]     Additional sense: Medium not present
[ 3197.327798] end_request: I/O error, dev sr0, sector 0
[ 3197.334829] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.334860]     Additional sense: Medium not present
[ 3197.334865] end_request: I/O error, dev sr0, sector 4
[ 3197.342813] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.342829]     Additional sense: Medium not present
[ 3197.342837] end_request: I/O error, dev sr0, sector 0
[ 3197.349801] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.349808]     Additional sense: Medium not present
[ 3197.349815] end_request: I/O error, dev sr0, sector 4
[ 3197.356799] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.356814]     Additional sense: Medium not present
[ 3197.356820] end_request: I/O error, dev sr0, sector 0
[ 3197.363791] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.363809]     Additional sense: Medium not present
[ 3197.363818] end_request: I/O error, dev sr0, sector 4
[ 3197.370789] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.370804]     Additional sense: Medium not present
[ 3197.370813] end_request: I/O error, dev sr0, sector 0
[ 3197.377781] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.377790]     Additional sense: Medium not present
[ 3197.377795] end_request: I/O error, dev sr0, sector 4
[ 3197.384780] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.384796]     Additional sense: Medium not present
[ 3197.384803] end_request: I/O error, dev sr0, sector 0
[ 3197.391738] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[ 3197.391744]     Additional sense: Medium not present
[ 3197.391750] end_request: I/O error, dev sr0, sector 4

---

### Post by schakravarthi on 2007-09-01
I did see an error that flashed during boot. something about Avahi not installing correctly.

---

### Post by Naddiseo on 2007-09-01
schakravarthi, if you have windows installed too (like I did) this may help:
[http://forums.fedoraforum.org/showthread.php?p=853822#post853822](http://forums.fedoraforum.org/showthread.php?p=853822#post853822)

I *just* tried it and it worked. Damn evil windows.

---

### Post by noob12 on 2007-09-01
Here's what's notable:
> 
[ 40.217018] PCI: Enabling device 0000:00:12.0 (0000 -> 0003)
[ 40.217032] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 40.217328] eth0: RealTek RTL8139 at 0xd0828400, 00:e0:18:2f:f9:f9, IRQ 16
[ 40.217333] eth0: Identified 8139 chip type 'RTL-8139C'
[ 42.912733] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

...

[ 2028.524453] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 2028.525124] [<c01543a4>] __report_bad_irq+0x24/0x80
[ 2028.525332] [<c015465e>] note_interrupt+0x25e/0x290
[ 2028.525352] [<c01538d0>] handle_IRQ_event+0x30/0x60
[ 2028.525363] [<c0154f91>] handle_fasteoi_irq+0xc1/0xf0
[ 2028.525374] [<c0105b70>] do_IRQ+0x40/0x80
[ 2028.525389] [<c0104233>] common_interrupt+0x23/0x30
[ 2028.525396] [<c0101e00>] default_idle+0x0/0x60
[ 2028.525411] [<c011c092>] native_safe_halt+0x2/0x10
[ 2028.525524] [<c0101e3d>] default_idle+0x3d/0x60
[ 2028.525530] [<c0101409>] cpu_idle+0x49/0xd0
[ 2028.525543] [<c03d97f5>] start_kernel+0x365/0x420
[ 2028.525676] [<c03d9230>] unknown_bootoption+0x0/0x260
[ 2028.525702] =======================
[ 2028.525708] handlers:
[ 2028.525715] [<d08b68c0>] (ahc_linux_isr+0x0/0x250 [aic7xxx])
[ 2028.526349] [<d08f1bb0>] (rtl8139_interrupt+0x0/0x480 [8139too])
[ 2028.526368] Disabling IRQ #16


I am surprised the device continues to work after that point at all.

There are some related bugs on launchpad
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87078](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87078)
[https://bugs.launchpad.net/ubuntu/+source/gnome-network/+bug/35683](https://bugs.launchpad.net/ubuntu/+source/gnome-network/+bug/35683)

I'd suggest trying to boot with  **pci=noacpi**  first and then try **acpi=off** and see if either flag improves things.

To try boot flags for a single boot, hit the **e** key when the boot selection menu comes up; this should put you in a mode editing the boot commands. Use the arrow keys to move to the **kernel** line, hit the **e** key again; this should put you in a mode editing this line. Add a space and the boot flag(s) you want, each separated by a space.  Hit ESC once and then **b** to boot.  You entered the flags properly if you see them  on the boot command using the command **dmesg | grep 'Kernel command line:' ** after booting.

If these work for you you can add them to the command line in **/boot/grub/menu.lst** to be used every time.

---

### Post by schakravarthi on 2007-09-01
The first option(pci=noacpi) wasnt recognized. But the second seemed to have removed the irq error. But there are a bunch apci errors.
 see dmesg with flag **acpi=off**

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e6000 size: 000000000001a000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fef0000 end: 000000000fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fff0000 size: 000000000000fc00 end: 000000000ffffc00 type: 3
[    0.000000] copy_e820_map() start: 000000000ffffc00 size: 0000000000000400 end: 0000000010000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65520
[    0.000000]   HighMem     65520 ->    65520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65520
[    0.000000] On node 0 totalpages: 65520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60945 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] Detected 1327.509 MHz processor.
[ 1404.443658] Built 1 zonelists.  Total pages: 65009
[ 1404.443664] Kernel command line: root=UUID=357b4b1b-369d-4285-a8b0-43f7e17b976c ro quiet splash acpi=off
[ 1404.443926] Found and enabled local APIC!
[ 1404.443931] mapped APIC to ffffd000 (fee00000)
[ 1404.443936] Enabling fast FPU save and restore... done.
[ 1404.443953] Initializing CPU#0
[ 1404.444055] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 1404.445220] Console: colour VGA+ 80x25
[ 1404.445541] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 1404.445751] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 1404.459199] Memory: 248760k/262080k available (1992k kernel code, 12736k reserved, 900k data, 328k init, 0k highmem)
[ 1404.459216] virtual kernel memory layout:
[ 1404.459218]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[ 1404.459220]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 1404.459222]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[ 1404.459224]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[ 1404.459227]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[ 1404.459229]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[ 1404.459231]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[ 1404.459236] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 1404.536016] Calibrating delay using timer specific routine.. 2657.56 BogoMIPS (lpj=5315134)
[ 1404.536085] Security Framework v1.0.0 initialized
[ 1404.536096] SELinux:  Disabled at boot.
[ 1404.536122] Mount-cache hash table entries: 512
[ 1404.536346] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[ 1404.536360] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 1404.536365] CPU: L2 Cache: 256K (64 bytes/line)
[ 1404.536369] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000
[ 1404.536386] Compat vDSO mapped to ffffe000.
[ 1404.536396] Remapping vsyscall page to ffffe000
[ 1404.536410] Checking 'hlt' instruction... OK.
[ 1404.552065] SMP alternatives: switching to UP code
[ 1404.552436] Freeing SMP alternatives: 11k freed
[ 1404.552797] Early unpacking initramfs... done
[ 1405.025340] CPU0: AMD Athlon(tm) Processor stepping 04
[ 1405.025350] SMP motherboard not detected.
[ 1405.131804] Brought up 1 CPUs
[ 1405.132218] Booting paravirtualized kernel on bare hardware
[ 1405.132334] Time: 20:39:00  Date: 08/01/107
[ 1405.132386] NET: Registered protocol family 16
[ 1405.132539] EISA bus registered
[ 1405.140787] PCI: PCI BIOS revision 2.10 entry at 0xfd7ee, last bus=1
[ 1405.140791] PCI: Using configuration type 1
[ 1405.140794] Setting up standard PCI resources
[ 1405.142129] ACPI: Interpreter disabled.
[ 1405.142137] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 1405.142149] pnp: PnP ACPI: disabled
[ 1405.142154] PnPBIOS: Scanning system for PnP BIOS support...
[ 1405.142185] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7810
[ 1405.142190] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa07e, dseg 0x400
[ 1405.147868] spurious 8259A interrupt: IRQ7.
[ 1405.149599] PnPBIOS: 20 nodes reported by PnP BIOS; 20 recorded by driver
[ 1405.149679] PCI: Probing PCI hardware
[ 1405.149687] PCI: Probing PCI hardware (bus 00)
[ 1405.150013] PCI quirk: region 6800-687f claimed by vt82c686 HW-mon
[ 1405.150019] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[ 1405.150313] Boot video device is 0000:01:05.0
[ 1405.151155] PCI: Using IRQ router VIA [1106/0686] at 0000:00:04.0
[ 1405.151173] PCI: setting IRQ 10 as level-triggered
[ 1405.151178] PCI: Found IRQ 10 for device 0000:00:0b.0
[ 1405.151190] PCI: Sharing IRQ 10 with 0000:00:0f.0
[ 1405.153003] NET: Registered protocol family 8
[ 1405.153007] NET: Registered protocol family 20
[ 1405.153112] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[ 1405.153117] pnp: 00:0a: ioport range 0x8000-0x807f has been reserved
[ 1405.153122] pnp: 00:0a: ioport range 0x400-0x40f has been reserved
[ 1405.153132] pnp: 00:0b: ioport range 0x3400-0x347f has been reserved
[ 1405.153620] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:01:05.0
[ 1405.153678] PCI: Bridge: 0000:00:01.0
[ 1405.153681]   IO window: disabled.
[ 1405.153687]   MEM window: e1000000-e1ffffff
[ 1405.153692]   PREFETCH window: f0000000-f7ffffff
[ 1405.153743] NET: Registered protocol family 2
[ 1405.179843] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 1405.179968] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 1405.180193] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 1405.180308] TCP: Hash tables configured (established 8192 bind 4096)
[ 1405.180313] TCP reno registered
[ 1405.191882] checking if image is initramfs... it is
[ 1406.088084] Freeing initrd memory: 6786k freed
[ 1406.088786] audit: initializing netlink socket (disabled)
[ 1406.088809] audit(1188679140.728:1): initialized
[ 1406.088971] VFS: Disk quotas dquot_6.5.1
[ 1406.089001] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1406.089083] io scheduler noop registered
[ 1406.089087] io scheduler anticipatory registered
[ 1406.089091] io scheduler deadline registered
[ 1406.089106] io scheduler cfq registered (default)
[ 1406.089123] PCI: Disabling Via external APIC routing
[ 1406.089445] isapnp: Scanning for PnP cards...
[ 1406.443682] isapnp: No Plug & Play device found
[ 1406.486983] Real Time Clock Driver v1.12ac
[ 1406.487166] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 1406.487338] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1406.487684] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 1406.488668] 00:10: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1406.489150] 00:11: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 1406.489534] mice: PS/2 mouse device common for all mice
[ 1406.490421] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 1406.490811] input: Macintosh mouse button emulation as /class/input/input0
[ 1406.490866] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1406.490872] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1406.491287] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 1406.491692] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1406.491701] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1406.491882] EISA: Probing bus 0 at eisa.0
[ 1406.491897] Cannot allocate resource for EISA slot 1
[ 1406.491902] Cannot allocate resource for EISA slot 2
[ 1406.491906] Cannot allocate resource for EISA slot 3
[ 1406.491920] Cannot allocate resource for EISA slot 6
[ 1406.491929] Cannot allocate resource for EISA slot 8
[ 1406.491932] EISA: Detected 0 cards.
[ 1406.492209] TCP cubic registered
[ 1406.492219] NET: Registered protocol family 1
[ 1406.492297] Testing NMI watchdog ... OK.
[ 1406.532068] Using IPI No-Shortcut mode
[ 1406.532103]   Magic number: 7:347:699
[ 1406.533002] Freeing unused kernel memory: 328k freed
[ 1406.535036] Time: tsc clocksource has been installed.
[ 1406.550375] input: AT Translated Set 2 keyboard as /class/input/input1
[ 1407.873836] Capability LSM initialized
[ 1407.955198] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 1408.722853] usbcore: registered new interface driver usbfs
[ 1408.722909] usbcore: registered new interface driver hub
[ 1408.722948] usbcore: registered new device driver usb
[ 1408.724403] USB Universal Host Controller Interface driver v3.0
[ 1408.724491] PCI: setting IRQ 9 as level-triggered
[ 1408.724497] PCI: Found IRQ 9 for device 0000:00:04.2
[ 1408.724508] PCI: Sharing IRQ 9 with 0000:00:04.3
[ 1408.724533] uhci_hcd 0000:00:04.2: UHCI Host Controller
[ 1408.724770] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[ 1408.724804] uhci_hcd 0000:00:04.2: irq 9, io base 0x00001420
[ 1408.725009] usb usb1: configuration #1 chosen from 1 choice
[ 1408.725050] hub 1-0:1.0: USB hub found
[ 1408.725067] hub 1-0:1.0: 2 ports detected
[ 1408.792947] SCSI subsystem initialized
[ 1408.830095] PCI: Found IRQ 9 for device 0000:00:04.3
[ 1408.830108] PCI: Sharing IRQ 9 with 0000:00:04.2
[ 1408.830133] uhci_hcd 0000:00:04.3: UHCI Host Controller
[ 1408.830169] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
[ 1408.830198] uhci_hcd 0000:00:04.3: irq 9, io base 0x00001440
[ 1408.830360] usb usb2: configuration #1 chosen from 1 choice
[ 1408.830412] hub 2-0:1.0: USB hub found
[ 1408.830427] hub 2-0:1.0: 2 ports detected
[ 1408.833906] 8139too Fast Ethernet driver 0.9.28
[ 1408.938341] PCI: Enabling device 0000:00:0e.0 (0010 -> 0013)
[ 1408.938359] PCI: setting IRQ 11 as level-triggered
[ 1408.938364] PCI: Assigned IRQ 11 for device 0000:00:0e.0
[ 1408.938381] PCI: Sharing IRQ 11 with 0000:00:12.0
[ 1408.939425] ahc_pci:0:14:0: Using left over BIOS settings
[ 1409.081755] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 1409.127615] Floppy drive(s): fd0 is 1.44M
[ 1409.182512] FDC 0 is a post-1991 82077
[ 1409.271630] usb 1-1: configuration #1 chosen from 1 choice
[ 1409.517475] usb 1-2: new low speed USB device using uhci_hcd and address 3
[ 1409.699307] usb 1-2: configuration #1 chosen from 1 choice
[ 1409.945256] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1410.115493] usb 2-1: configuration #1 chosen from 1 choice
[ 1410.361053] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 1410.600149] usb 2-2: configuration #1 chosen from 1 choice
[ 1410.602354] usbcore: registered new interface driver libusual
[ 1410.609646] Initializing USB Mass Storage driver...
[ 1410.609776] scsi1 : SCSI emulation for USB Mass Storage devices
[ 1410.609855] usb-storage: device found at 2
[ 1410.609858] usb-storage: waiting for device to settle before scanning
[ 1410.609940] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1410.609998] usb-storage: device found at 3
[ 1410.610001] usb-storage: waiting for device to settle before scanning
[ 1410.610014] usbcore: registered new interface driver usb-storage
[ 1410.610018] USB Mass Storage support registered.
[ 1410.610274] usbcore: registered new interface driver hiddev
[ 1410.628759] input: Logitech Trackball as /class/input/input2
[ 1410.628792] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:04.2-2
[ 1410.628823] usbcore: registered new interface driver usbhid
[ 1410.628829] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 1415.612367] usb-storage: device scan complete
[ 1415.614709] usb-storage: device scan complete
[ 1415.648826] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 740e  42FF PQ: 0 ANSI: 0
[ 1415.720058] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[ 1415.720186] Uniform CD-ROM driver Revision: 3.20
[ 1415.723183] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1415.740093] sr 1:0:0:0: Attached scsi generic sg0 type 5
[ 1417.632893] scsi 2:0:0:0: Direct-Access     USB-HS   SAMSUNG HD300LD  0.01 PQ: 0 ANSI: 0
[ 1417.634917] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[ 1417.671312] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[ 1417.676312] sda: Write Protect is off
[ 1417.676340] sda: Mode Sense: 0b 00 00 08
[ 1417.676356] sda: assuming drive cache: write through
[ 1417.682010] SCSI device sda: 586072368 512-byte hdwr sectors (300069 MB)
[ 1417.686975] sda: Write Protect is off
[ 1417.686978] sda: Mode Sense: 0b 00 00 08
[ 1417.686982] sda: assuming drive cache: write through
[ 1417.686995]  sda: sda1
[ 1417.705078] sd 2:0:0:0: Attached scsi disk sda
[ 1423.942053] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[ 1423.942057]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[ 1423.942060]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[ 1423.942063] 
[ 1423.944663] PCI: Enabling device 0000:00:12.0 (0000 -> 0003)
[ 1423.944677] PCI: Found IRQ 11 for device 0000:00:12.0
[ 1423.944693] PCI: Sharing IRQ 11 with 0000:00:0e.0
[ 1423.945297] eth0: RealTek RTL8139 at 0xd081c400, 00:e0:18:2f:f9:f9, IRQ 11
[ 1423.945302] eth0:  Identified 8139 chip type 'RTL-8139C'
[ 1423.949335] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 1423.949996] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[ 1423.950059] VP_IDE: chipset revision 6
[ 1423.950063] VP_IDE: not 100% native mode: will probe irqs later
[ 1423.950114] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:04.1
[ 1423.950126]     ide0: BM-DMA at 0x1400-0x1407, BIOS settings: hda:DMA, hdb:pio
[ 1423.950145]     ide1: BM-DMA at 0x1408-0x140f, BIOS settings: hdc:DMA, hdd:DMA
[ 1423.950158] Probing IDE interface ide0...
[ 1424.370009] hda: ST340810A, ATA DISK drive
[ 1424.649866] hdb: WDC WD1200JB-00FUA0, ATA DISK drive
[ 1424.713787] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 1424.714330] Probing IDE interface ide1...
[ 1425.581397] hdc: LITE-ON LTR-12101B, ATAPI CD/DVD-ROM drive
[ 1426.029197] hdd: LG CD-ROM CRD-8485B, ATAPI CD/DVD-ROM drive
[ 1426.085450] ide1 at 0x170-0x177,0x376 on irq 15
[ 1426.101797] libata version 2.20 loaded.
[ 1426.117851] hda: max request size: 128KiB
[ 1426.141876] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[ 1426.141889] hda: cache flushes not supported
[ 1426.141961]  hda: hda1 hda2 hda3
[ 1426.194194] hdb: max request size: 512KiB
[ 1426.208407] hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=14593/255/63, UDMA(33)
[ 1426.210213] hdb: cache flushes supported
[ 1426.210256]  hdb: hdb1 hdb2 hdb3 hdb4
[ 1426.266266] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[ 1426.272559] hdd: ATAPI 48X CD-ROM drive, 128kB Cache, DMA
[ 1426.942057] Attempting manual resume
[ 1426.942064] swsusp: Resume From Partition 3:2
[ 1426.942067] PM: Checking swsusp image.
[ 1426.942395] PM: Resume from disk failed.
[ 1426.993088] kjournald starting.  Commit interval 5 seconds
[ 1426.993110] EXT3-fs: mounted filesystem with ordered data mode.
[ 1444.185895] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1446.038011] NET: Registered protocol family 17
[ 1446.894179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1446.902191] shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 ss_did 0
[ 1446.902218] shpchp: shpc_init: cannot reserve MMIO region
[ 1446.902246] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 1446.953781] parport_pc: VIA 686A/8231 detected
[ 1446.953788] parport_pc: probing current configuration
[ 1446.953808] parport_pc: Current parallel port base: 0x378
[ 1446.953887] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[ 1447.058380] parport_pc: VIA parallel port: io=0x378, irq=7
[ 1447.371562] Linux agpgart interface v0.102 (c) Dave Jones
[ 1447.395898] agpgart: Detected AMD 761 chipset
[ 1447.412991] agpgart: AGP aperture is 128M @ 0xe8000000
[ 1447.795458] PCI: Enabling device 0000:00:0f.1 (0000 -> 0001)
[ 1447.811049] gameport: EMU10K1 is pci0000:00:0f.1/gameport0, io 0x1468, speed 1325kHz
[ 1448.371620] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1706
[ 1448.371822] usbcore: registered new interface driver usblp
[ 1448.371828] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[ 1448.966528] input: PC Speaker as /class/input/input3
[ 1449.745210] PCI: Enabling device 0000:00:0f.0 (0000 -> 0001)
[ 1449.745224] PCI: Found IRQ 10 for device 0000:00:0f.0
[ 1449.745238] PCI: Sharing IRQ 10 with 0000:00:0b.0
[ 1450.156271] fuse init (API version 7.8)
[ 1450.209406] lp0: using parport0 (interrupt-driven).
[ 1450.266063] Adding 971924k swap on /dev/disk/by-uuid/90fd0f38-7f4f-469d-9ad5-1bc3a876d61d.  Priority:-1 extents:1 across:971924k
[ 1450.915204] EXT3 FS on hda3, internal journal
[ 1538.638582] kjournald starting.  Commit interval 5 seconds
[ 1538.638982] EXT3 FS on hdb1, internal journal
[ 1538.638991] EXT3-fs: mounted filesystem with ordered data mode.
[ 1548.277548] powernow_k7: Unknown symbol acpi_processor_notify_smm
[ 1548.277607] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[ 1548.277723] powernow_k7: Unknown symbol acpi_processor_register_performance
[ 1548.367055] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[ 1548.367115] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[ 1548.367249] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[ 1548.367318] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[ 1559.707861] ppdev: user-space parallel port driver
[ 1568.246111] apm: BIOS not found.
[ 1570.994614] Bluetooth: Core ver 2.11
[ 1570.994726] NET: Registered protocol family 31
[ 1570.994730] Bluetooth: HCI device and connection manager initialized
[ 1570.994736] Bluetooth: HCI socket layer initialized
[ 1571.398189] Bluetooth: L2CAP ver 2.8
[ 1571.398197] Bluetooth: L2CAP socket layer initialized
[ 1571.493586] Bluetooth: RFCOMM socket layer initialized
[ 1571.493614] Bluetooth: RFCOMM TTY layer initialized
[ 1571.493617] Bluetooth: RFCOMM ver 1.8

---

### Post by noob12 on 2007-09-02
> 
The first option(pci=noacpi) wasnt recognized. But the second seemed to have removed the irq error. But there are a bunch apci errors. see dmesg with flag acpi=off


OK.  Using acpi=off is a broad hammer approach because it also means the ACPI power management features won't work.  But it does indicate that your problem is related to the ACPI-based PCI routing.  It may be worthwhile verifying that the ethernet works more reliably when booted.

You say the first option isn't recognized.  But the option **pci=noacpi** should be recognized.  Did you mean you got an error message?  Please check that you typed it correctly.  That option will just disable ACPI for PCI routing,  Hopefully that will address your problem without losing the other ACPI features.

You should file a bug report or hook onto one of the reported bugs on launchpad regarding the pci routing problem with your card.

---

### Post by schakravarthi on 2007-09-02
pci=noacpi did work. The dmesg is now clean. And my internet is working for the last 10 hrs. So it appears this fixed it.  Thanks a lot. I will file a bug report.

---

### Post by noob12 on 2007-09-03
Great to hear.  In order to change this to be the default in future boots, you can find and edit the same "kernel" line in your **/boot/grub/menu.lst** file. 

You may want to mark the thread solved as well.

---

