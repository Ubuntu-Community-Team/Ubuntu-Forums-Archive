---
title: "Wired, moden, but not wireless!"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by prexium01 on 2008-04-01
Ok, so I finally got my drivers for my Rosewill wireless G internet card installed. I reboot the computer, and I go to configure the wireless internet. It only has options for Wired, Moden connection. No wireless option. I am positive that the card is plugged in. Ubuntu says that the drivers are working properly, etc. Anyone that can tell me why I'm not getting a wireless option? Any help would be appreciated!

Using ubuntu 7.10

---

### Post by olskar on 2008-04-01
Can you post the output when typing "ifconfig" in the terminal please?

---

### Post by prexium01 on 2008-04-01
eth0    Link encap:Ethernet  HWaddr 00:13:D3:11:BA:5B 
                UP BROADCAST MULTICAST  MTU:1500  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:1000
                RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
                Interrupt:18 Base address:0xec00
       
      lo        Link encap:Local Loopback 
                inet addr:127.0.0.1  Mask:255.0.0.0
                inet6 addr: ::1/128 Scope:Host
                UP LOOPBACK RUNNING  MTU:16436  Metric:1
                RX packets:4 errors:0 dropped:0 overruns:0 frame:0
                TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by olskar on 2008-04-01
Hm..looks like ubuntu only knows about one card..and that would be the wired one.. what is the output from > lspci | grep eth*?

---

### Post by prexium01 on 2008-04-01
[   33.348699] eth0: VIA Rhine II at 0x1ec00, 00:13:d3:11:ba:5b, IRQ 18.
[   33.349414] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   45.391230] eth0: link down
[  944.272038] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by ksukumar on 2008-04-14
Hello,

I installed Ubuntu 8.04(beta) yesterday on my laptop...But it had problems with its video card and wireless..it cudnot detect both of them...can u please tell me from where i can get the drivers for them..the configuration is given below..

AMD Turion(tm) 64 X2 Mobile Technology TL-58 1.9 Ghz
graphis card- nVidia GForce 7000M
the wireless is Atheros Ethernet Adaptor 802.11 Wireless..


Thank you!!!!

---

### Post by superprash2003 on 2008-04-14
go to the terminal and type ifconfig and post results here

---

### Post by ksukumar on 2008-04-15
eth0      Link encap:Ethernet  HWaddr 00:1e:68:00:8e:c9  
          inet addr:128.46.108.12  Bcast:128.46.108.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe00:8ec9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11271188 (10.7 MB)  TX bytes:2702005 (2.5 MB)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9500 (9.2 KB)  TX bytes:9500 (9.2 KB)



these r the results......
oh n my wireless card is  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

---

### Post by 67GTA on 2008-04-15
I'm having the same problem with my atheros wireless with 8.04. The restricted driver manager shows the driver is enabled, but no wireless option in network manager. It shows up with lspci:

shawnr@fastback:~$ lspci | grep eth*
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

When I run sudo ifconfig ath0 down/up, I get:

ath0: ERROR while getting interface flags: No such device

---

### Post by superprash2003 on 2008-04-15
read this- something similar to your problem [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

---

### Post by 67GTA on 2008-04-15
I actually just got mine to work with this thread [http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007](http://ubuntuforums.org/showthread.php?t=743299&highlight=atheros+ar5007) It turns out that Ubuntu was not correctly identifying my card. I booted into Vista, checked the device manager, and it said I had an Atheros AR5007. The drivers in the restricted drivers manager weren't doing squat, because they weren't for my card.

---

