---
title: "PRO/Wireless 3945ABG on HP dv2130ea connects but no traffic. (Ubuntu 7.10)"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by InSearchOf on 2007-10-30
Hey!

I was a linux-virgin until a week ago when i finally installed 7.10. It went fiiine. Love it, but I would love it even more if my wireless connection would work properly. This is my problem:

Wireless card is identified and the Proprietary Restricted Driver is in use. My wireless network is identified and connected - all seems fine and dandy (99% signal strength, recieves IP from DHCP etc...). Only thing is that no traffic happens. Can't browse, im, ftp and stuff like that at all. Can't even ping my local gateway (even though I recieve IP). If I configure static IP its not any better. WEP or no ectryption makes no difference. 

So I installed ndiswrapper, did "sudo modprobe ndiswrapper", and same **** happens. All seems fine and dandy, but no sigar. No internet. No nothing. Only a ******* useless IP-adress :-/ 

Wired connection works swell "out of the box" :)

To sum up: restricted proprietary driver in use and ndiswrapper (with proprietary restricted driver not in use - I assumed I had to disable it when using ndiswrapper) leaves me with the same result. Connection seems fine, but no traffic happens...

Please help me, I want to get away from my Microsoft dependency... Thanks in advance...

Regards from Norway :-)

 I'll leave you with som additional info:
_________________________
lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:7b:10:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw39x5 driverversion=1.45+Intel,11/15/2006,10.5.1.75 ip=192.168.0.115 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:10:79:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.0.120 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes


iwconfig:

eth1      IEEE 802.11b  ESSID:"myssid"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6A:08:76   
          Bit Rate=11 Mb/s   
          Fragment thr=-196739292 B   
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Lambert on 2007-10-30
So to do some simple testing can you ping your loop back interface and the interface?

After bringing up the interface and getting an ip address assigned, what is the output of 

```

sudo ip route

```

---

### Post by InSearchOf on 2007-10-31
Thanks for the reply :-)
Here's the requested output. (My wired connection was not connected, but is set up with static IP *.120)
---------------------------------------
sudo ip route: 

192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.120 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.115 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth1 
default via 192.168.0.1 dev eth0  metric 100

---

### Post by Lambert on 2007-10-31
If your wired device is unplugged, try removing the default route and see if you can connect.

```

sudo ip route delete default via 192.168.0.1 dev eth0

```

---

### Post by InSearchOf on 2007-10-31
Ok.
1. I unplugged the wired connection.
2. I enabled my wireless card, and as described earlier it seemingly connects and recieves IP, but no traffic happens.
3. I did "sudo ip route delete default via 192.168.0.1 dev eth0". This created no output in terminal window. Tried to browse internet, nothing happens. Pinging my local gateway 192.168.0.1 results in "Destination Host Unreachable" (as it did earlier).
4. Then I did "sudo ip route", which now resulted in the following output:
---------------
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.120 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.115 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth1 
--------------
5. I then had to to "sudo ip route add default via 192.168.0.1 dev eth0" to get back online with my wired connection to post this :-)

---

### Post by InSearchOf on 2007-11-02
I have done some more testing, and I found this, which seems some kind of weird. When pinging my local gateway (192.168.0.1) from my wireless connection (which has received IP (192.168.0.119) and seems all good) I get this output in terminal:
---------------------------
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.120 icmp_seq=1 Destination Host Unreachable
From 192.168.0.120 icmp_seq=2 Destination Host Unreachable
From 192.168.0.120 icmp_seq=5 Destination Host Unreachable
From 192.168.0.120 icmp_seq=6 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
8 packets transmitted, 0 received, +4 errors, 100% packet loss, time 7010ms
, pipe 2
--------------------------

Now, why the heck does my wired hardware (unconnected by the way) reply? Does this indicate some kind of conflict? To me, in this case, it seems logical to assume that my wireless connection in some way has to go via/through my wired connection (which is configured with a fixed IP), and a conflict occurs. Does it has to do with my routing-configuration for my wireless card / connection? (How-to-fix if that may be the case?)

If I connect my wired connection (and my wireless stays up), pinging local gateway is OK (i am assuming that the reason for this is that I am actually pinging FROM my wired card), but I cannot browse internet, neither by DNS or IP-adresses.

Suggestions, anyone?

Heres output from "ifconfig", in case there is any relevance (eth1 = wireless)
---------------------------------
eth0      Link encap:Ethernet  HWaddr 00:16:D3:10:79:EF  
          inet addr:192.168.0.120  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe10:79ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4404407 (4.2 MB)  TX bytes:492106 (480.5 KB)

eth1      Link encap:Ethernet  HWaddr 00:18:DE:7B:10:59  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe7b:1059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:237 overruns:0 frame:0
          TX packets:10 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208646 (203.7 KB)  TX bytes:4412 (4.3 KB)
          Interrupt:19 Base address:0x2000 Memory:d6000000-d6000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7236 (7.0 KB)  TX bytes:7236 (7.0 KB)
-----------------------------------

---

### Post by Lambert on 2007-11-02
First you can't have two default routes to the gateway.

> 
default via 192.168.0.1 dev eth1 
default via 192.168.0.1 dev eth0 metric 100


The reason when you're pinging it shows response from you're wired device is because the interface is up with an ip and it has an ip route pointing to the gateway. The kernel is first trying the wireless interface and it's failing so it's now trying the other route.

When trouble shooting, make sure your eth0 interface is down and not assigned an ip address and there's no default route for that device. That doesn't mean cable unplugged, when running ifconfig you shouldn't see eth0 listed and when running the ip route command you only see a default pointing to eth1.

Second, your driver seems to be having problems some where. Notice the dropped packets. Too many of these.

> 
RX packets:24 errors:0 dropped:237 overruns:0 frame:0
TX packets:10 errors:0 dropped:1 overruns:0 carrier:0


I don't know much about the ipw3945 driver and version of ubuntu you're using but make sure it's not installed and loaded causing a conflict.

run this terminal command

```

lsmod | grep ipw

```
You don't want to see any output. If you see a line showing ipw3945 then run this command.

```

sudo modprobe -r ipw3945

```

If that solves it you will have to blacklist it so it doesn't load on boot.

If you dont' see that line then my suggestion is to look at ndiswrapper troubleshooting and verify the driver you're using. It may be a valid windows driver but not all drivers work with ndiswrapper. You may have to try others. The ndiswrapper wiki has a list of devices and known drivers that work. You can see if anything is there that can help you.

[ndsiwrapper wiki]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/")

---

### Post by uconvert on 2007-11-03
I have the same problem with my Asus Z62FM. 
I had a Gigabyte (Atheros) Card working in Feisty, then upgraded to Gutsy. Card wouldn't work; and I saw alot of posts re Atheros problems. 
I switched to the Intel 3945 and it doesn't work either. I even get a successful ping for 2-way, but it won't receive!
I have been an Ubuntu fan since 6.10; but these 6-month installation woes are wearing me out!

Any help would be appreciated!!!

---

### Post by InSearchOf on 2007-11-06
Ok - done some more testing (only with ipw3945-driver).
When I configure both wired and wireless connections to use roaming profile, my wireless connection works out of the box, except for a very unstable connection when I connect to my Netgear DG824M (802.11b). Connection eventually drops out, and I have to be rather close to the accesspoint in order for any traffic to happen... On the other hand, if I connect to my neighbours Linksys WRT54G (802.11b/g) everything works swell. No hassle at all. May it be due to the fact that the two networks differ in bitrate (11Mb/s vs 24Mb/s)?

The initial problem with no traffic happening at all is still happening if I configure my wired connection (or both wired and wireless) with static IPs. I then get two default routes to gateway, and the original problem is back. So it seems that I have to live with this workaround solution with two roaming profiles. But any viewpoint on why my Netgear connection is dropping out would be appreciated. Should I get a new router? Additional question: is there any difference between roaming profile and dynamic ip?

Connected to Linksys WRT54G (802.11b/g)
ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:18:DE:7B:10:59  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe7b:1059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1615 errors:1 dropped:244 overruns:0 frame:0
          TX packets:1701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1262939 (1.2 MB)  TX bytes:507486 (495.5 KB)
          Interrupt:19 Base address:0x4000 Memory:d6000000-d6000fff 

iwconfig:
eth1      IEEE 802.11g  ESSID:"Neigbour's ID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:B1:9F:34   
          Bit Rate:24 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/100  Signal level=-72 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:244   Missed beacon:0


Connected to Netgear DG824M (802.11b) 
ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:18:DE:7B:10:59  
          inet addr:192.168.0.114  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe7b:1059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1502 errors:0 dropped:1464 overruns:0 frame:0
          TX packets:1592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1270428 (1.2 MB)  TX bytes:281447 (274.8 KB)
          Interrupt:19 Base address:0x4000 Memory:d6000000-d6000fff 

iwconfig:
eth1      IEEE 802.11b  ESSID:"MY_ID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6A:08:76   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-34 dBm  Noise level=-35 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1464   Missed beacon:0

---

### Post by Lambert on 2007-11-06
bit rate won't have anything to do with it. 

But you are both on the same frequency/channel. i would suggest changing your routers set up to a different channel to see if it helps. If the first one you try doesn't help, try another one. your routers could be causing problems for each other being on the same channel.

A sign of this is the dropped connection and both of you have invalid misc: dropped packets, (last line in iwconfig output) notice its happening more when connected to your router though.

Do you have any other devices that operate on 2.4 ghz in your house or close to your router?

---

### Post by InSearchOf on 2007-11-07
Thanks a lot!!! =D>

I changed the channel, and now my wireless connection haven't dropped a single time since i changed the channel 2-3 hours ago :-D

Still not optimal speed though, but I'll experiment a bit more with other channels the next days. And, no - I do not have any other devices on that frequency (as far as I am aware of...)

Again: thanks a lot!! :-D =D>

ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:18:DE:7B:10:59  
          inet addr:192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe7b:1059/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7716 errors:122 dropped:4069 overruns:0 frame:0
          TX packets:6211 errors:0 dropped:39 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8422830 (8.0 MB)  TX bytes:1727165 (1.6 MB)
          Interrupt:19 Base address:0xa000 Memory:d6000000-d6000fff 


iwconfig:
eth1      IEEE 802.11b  ESSID:"MY ID"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:09:5B:6A:08:76   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-33 dBm  Noise level=-34 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3841   Missed beacon:0

---

