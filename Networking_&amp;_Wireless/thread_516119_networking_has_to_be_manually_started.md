---
title: "networking has to be manually started"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by nanjil on 2007-08-02
hello:

I have the fiesty working with dl520 wireless pci card.
The problem is somebody has to log in and   manually start the network.

How can i make it so that it happens automatically at boot time?

my /etc/network/interfaces has the following line

auto wlan0
iface wlan0 inet dhcp

thanx

---

### Post by noob12 on 2007-08-02
Can you post the output of these commands?

```

lshw -C network

ifconfig -a

iwconfig

iwlist scan

cat /etc/network/interfaces

```

Post everything not excerpts.

---

### Post by nanjil on 2007-08-02
Ishw -C network
bash: Ishw: command not found
root@ubuntu64:/home/kumar# lshw -C network
  *-network
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@01:07.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:89:06:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.         1) ip=192.168.0.107 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=I         EEE 802.11g
       resources: iomemory:f5000000-f500ffff irq:17


ifconfig -a

ath0      Link encap:Ethernet  HWaddr 00:11:95:89:06:66  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe89:666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51513664 (49.1 MiB)  TX bytes:5386710 (5.1 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0F:EA:50:E7:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:EA:50:E7:67  
          inet addr:169.254.8.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5547510 (5.2 MiB)  TX bytes:5547510 (5.2 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-89-06-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86652 errors:0 dropped:0 overruns:0 frame:69395
          TX packets:31596 errors:140 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:58144616 (55.4 MiB)  TX bytes:6098419 (5.8 MiB)
          Interrupt:17 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"home2"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:EC:96:28   
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=18/94  Signal level=-76 dBm  Noise level=-94 dBm
          Rx invalid nwid:6498  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0D:88:EC:96:28
                    ESSID:"home2"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101001fff7f
          Cell 02 - Address: 00:18:39:D2:1A:0B
                    ESSID:"Studerez"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100


cat /etc/network/interfaces

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

---

### Post by noob12 on 2007-08-03
OK.  You seem to have the wifi0 logical name setup incorrectly.   You may want to fix that.

I'm going to use the ath0 name for the interface as that seems to be setup.  If you fix the wifi0 logical name to replace ath0, you will need to change these lines accordingly.

Also, this is based on your current association to "home2" which appears to be running unsecured.  If you are going to set it up secured then you need to do more configuration, depending on what kind you setup.

For your current situation, the following should work.  Replace the lines for **ath0** in /etc/network/interfaces with these:

```

auto ath0
iface ath0 inet dhcp
pre-up iwconfig ath0 essid home2

```

Make sure that the wireless is enabled in your BIOS on startup.

Configuring things in /etc/network/interfaces to start manually at boot will tell NetworkManager not to do its roaming treatment on this card.  This isn't what most people want.

Let me know if this works for you or if you need additional help.

---

### Post by nanjil on 2007-08-09
thans.
I will try your suggestion.

out of curiosity how did it associate name ath0 with my wireles card. where are these name association set up?

thanx,
i hope to report back my progress

---

### Post by nanjil on 2007-08-09
I just tested it ; it now automatically connects to teh network

thanx

---

