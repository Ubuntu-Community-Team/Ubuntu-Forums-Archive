---
title: "can't get ip from wireless"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by ofri on 2007-09-14
hi all,

i can't seem to get connected to my LAN using my wireless card. i used the networkmanager before, and according to the advice in some threads here i installed wicd, but same result: i can see my wireless network (and some neighbors' too). **when i try to connect, it just stalls in the "obtaining IP address" phase**.
my wireless router is ASW 530. the network uses WEP encryption. i entered the key in the appropriate place. the wireless router is connected to ADSL modem-router that also functions as my DHCP. this is a ECI BFOCuS 312+ router.
when i connect using eth0 with a cable everything works fine.

my windows XP machine (another computer. not dual boot) connects to the same network OK (both with a cable and on wireless)

i also configured my wireless network to use no encryption, but the behavior was the same. and i also noted something funny: when i use encryption, and give my wicd a wrong key, it doesn't give any warning about it - it goes through the steps of checking the key with no apparent errors, and again - just stalls in the "obtaining IP address"...

any help is welcome :)

i'm using ubuntu 7.04 with kernel 2.6.20-16-generic on a toshiba satellite A100 laptop.  here are some related outputs. if i forgot anything, let me know...

lspci
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:6A:06:46  
          inet addr:10.0.0.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2a0:d1ff:fe6a:646/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1580392 (1.5 MiB)  TX bytes:186818 (182.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:19:D2:5C:98:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3 dropped:682 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:236 (236.0 b)  TX bytes:2722 (2.6 KiB)
          Interrupt:18 Base address:0xa000 Memory:f0800000-f0800fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2112 (2.0 KiB)  TX bytes:2112 (2.0 KiB)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"hadas"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:507   Missed beacon:0

```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

iwlist eth1 scan
```
eth1      Scan completed :
          Cell 01 - Address: 00:30:54:91:F8:18
                    ESSID:"hadas"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=88/100  Signal level=-27 dBm  Noise level=-44 dBm
                    Extra: Last beacon: 1820ms ago
          Cell 02 - Address: 00:0F:66:8E:CE:40
                    ESSID:"kish"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=43/100  Signal level=-83 dBm  Noise level=-83 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 7128ms ago


```
(hadas is my network. other one is probably some neighbor's)

---

### Post by noob12 on 2007-09-14
Your setup looks fine.  (Side note: you can remove or comment the entries for wlan0 from your /etc/network/interfaces.  You don't have an interface with that name.)

My guess is you aren't reaching a full associated state possibly because of the key.  In a terminal window, while the little NM icon is rotating saying it is trying to get an IP address, can you run **iwconfig** and see if the state is Associated?  

Is there any way that you can try first connecting with the encryption disabled (temporarily)?
If you've tried that and it works, then that's sufficient.

---

### Post by dontom on 2007-09-14
Sorry to bump in on this thread, but I figured it wasn't necessary to make an own thread for the exact same problem.
So, I've got my card setup, I can find my own network, as well as some neighbours. But I can't receive any IP address, I've even turned the encryption off on the router, but that doesn't help either.
I'm using Wicd as well.

---

### Post by noob12 on 2007-09-14
dontom:  Sure.  Just note that many times the symptoms for these will look alike but the actual problems are often very different depending on what type of device you have on your client and how you have your router setup. You might want to start a different thread and people will help you diagnose your issue.

---

### Post by ofri on 2007-09-14
> **noob12 said:**
> 
My guess is you aren't reaching a full associated state possibly because of the key.  In a terminal window, while the little NM icon is rotating saying it is trying to get an IP address, can you run **iwconfig** and see if the state is Associated?  

i'm not sure i understand what a full associated state means, but here is the output when trying to connect:
iwconfig
```

eth1      IEEE 802.11b  ESSID:"hadas"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:30:54:91:F8:18   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-28 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3044   Missed beacon:0

```
and for comparison, this is the output when not trying to connect 
```

eth1      unassociated  ESSID:"hadas"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2988   Missed beacon:0


```

> **noob12 said:**
> 
Is there any way that you can try first connecting with the encryption disabled (temporarily)?
If you've tried that and it works, then that's sufficient.
as i wrote above, i already tried that, and the behavior was the same. do you want me to disable again and post iwconfig when trying to connect to unencrypted wlan?

---

### Post by noob12 on 2007-09-14
Yes, the output you showed indicates the associated state, so I think you are associating fine and it is a problem with the DHCP.

I don't see a specific problem, but here are some further things that might provide clues:

Does:
```

grep dhclient /var/log/syslog

```
show anything informative?

Do you have any MAC address-based access control rules in your router?  If so, make sure you have added the MAC address of the wireless device on your Ubuntu host to the allowed list.

Have you defined any firewall rules on your Ubuntu host?

If you configure the address, subnet, and gateway manually can you then ping the router?

---

### Post by ofri on 2007-09-15
> **noob12 said:**
>  
Does:
```

grep dhclient /var/log/syslog

```
show anything informative?

it shows a lot. whether its informative or not, i'm not sure :)
```

Sep 15 08:55:46 ofri-laptop dhclient: Listening on LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:55:46 ofri-laptop dhclient: Sending on   LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:55:46 ofri-laptop dhclient: Sending on   Socket/fallback
Sep 15 08:55:47 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 15 08:55:54 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Sep 15 08:56:03 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Sep 15 08:56:18 ofri-laptop dhclient: No DHCPOFFERS received.
Sep 15 08:56:18 ofri-laptop dhclient: No working leases in persistent database - sleeping.
Sep 15 08:57:47 ofri-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 15 08:57:47 ofri-laptop dhclient: DHCPACK from 10.0.0.138
Sep 15 08:57:47 ofri-laptop dhclient: bound to 10.0.0.4 -- renewal in 163652 seconds.
Sep 15 08:58:32 ofri-laptop dhclient: receive_packet failed on eth0: Network is down
Sep 15 08:58:43 ofri-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 15 08:58:43 ofri-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 15 08:58:43 ofri-laptop dhclient: All rights reserved.
Sep 15 08:58:43 ofri-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 15 08:58:43 ofri-laptop dhclient: 
Sep 15 08:58:44 ofri-laptop dhclient: Listening on LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:58:44 ofri-laptop dhclient: Sending on   LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:58:44 ofri-laptop dhclient: Sending on   Socket/fallback
Sep 15 08:58:47 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 15 08:58:54 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Sep 15 08:59:04 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Sep 15 08:59:16 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Sep 15 08:59:18 ofri-laptop dhclient: No DHCPOFFERS received.
Sep 15 08:59:18 ofri-laptop dhclient: No working leases in persistent database - sleeping.
Sep 15 08:59:29 ofri-laptop dhclient: receive_packet failed on eth1: Network is down
Sep 15 08:59:31 ofri-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 6493
Sep 15 08:59:31 ofri-laptop dhclient: removed stale PID file
Sep 15 08:59:31 ofri-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 15 08:59:31 ofri-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 15 08:59:31 ofri-laptop dhclient: All rights reserved.
Sep 15 08:59:31 ofri-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 15 08:59:31 ofri-laptop dhclient: 
Sep 15 08:59:32 ofri-laptop dhclient: Listening on LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:59:32 ofri-laptop dhclient: Sending on   LPF/eth1/00:19:d2:5c:98:15
Sep 15 08:59:32 ofri-laptop dhclient: Sending on   Socket/fallback
Sep 15 08:59:35 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Sep 15 08:59:41 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Sep 15 08:59:52 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Sep 15 09:00:06 ofri-laptop dhclient: No DHCPOFFERS received.
Sep 15 09:00:06 ofri-laptop dhclient: No working leases in persistent database - sleeping.
Sep 15 09:00:17 ofri-laptop dhclient: receive_packet failed on eth1: Network is down
Sep 15 09:00:19 ofri-laptop dhclient: There is already a pid file /var/run/dhclient.pid with pid 7016
Sep 15 09:00:19 ofri-laptop dhclient: removed stale PID file
Sep 15 09:00:19 ofri-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 15 09:00:19 ofri-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 15 09:00:19 ofri-laptop dhclient: All rights reserved.
Sep 15 09:00:19 ofri-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 15 09:00:19 ofri-laptop dhclient: 
Sep 15 09:00:20 ofri-laptop dhclient: Listening on LPF/eth1/00:19:d2:5c:98:15
Sep 15 09:00:20 ofri-laptop dhclient: Sending on   LPF/eth1/00:19:d2:5c:98:15
Sep 15 09:00:20 ofri-laptop dhclient: Sending on   Socket/fallback
Sep 15 09:00:22 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 15 09:00:25 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Sep 15 09:00:30 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Sep 15 09:00:35 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Sep 15 09:00:48 ofri-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Sep 15 09:00:53 ofri-laptop dhclient: No DHCPOFFERS received.
Sep 15 09:00:53 ofri-laptop dhclient: No working leases in persistent database - sleeping.

```

> **noob12 said:**
> 
Do you have any MAC address-based access control rules in your router?  If so, make sure you have added the MAC address of the wireless device on your Ubuntu host to the allowed list.

no MAC filters in my router.
> **noob12 said:**
> 
Have you defined any firewall rules on your Ubuntu host?

good question. not that i know of. how can i check that?
> **noob12 said:**
>  
If you configure the address, subnet, and gateway manually can you then ping the router?
here is what i did:
```
tail -f -n0 /var/log/syslog
```
then i used the advanced settings in Wicd to set IP to 10.0.0.2, netmask to 255.0.0.0, and gateway to 10.0.0.138 (this is my ADSL modem router that functions as a DHCP. read my first post for details). then i pressed connect. Wicd said it connected, and the output of the tail was:
```
Sep 15 09:28:09 ofri-laptop kernel: [ 1843.384000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Sep 15 09:28:10 ofri-laptop avahi-daemon[4921]: Registering new address record for fe80::2a0:d1ff:fe6a:646 on eth0.*.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.0.0.2.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: New relevant interface eth1.IPv4 for mDNS.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Registering new address record for 10.0.0.2 on eth1.IPv4.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Withdrawing address record for 10.0.0.2 on eth1.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.0.0.2.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.0.0.2.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: New relevant interface eth1.IPv4 for mDNS.
Sep 15 09:28:11 ofri-laptop avahi-daemon[4921]: Registering new address record for 10.0.0.2 on eth1.IPv4.
Sep 15 09:28:12 ofri-laptop avahi-daemon[4921]: Registering new address record for fe80::219:d2ff:fe5c:9815 on eth1.*.
Sep 15 09:28:19 ofri-laptop kernel: [ 1854.040000] eth0: no IPv6 routers present
Sep 15 09:28:21 ofri-laptop kernel: [ 1855.392000] eth1: no IPv6 routers present

```
([COLOR="DarkRed"]what does that god damn IPv6 want from me again??? when i only installed ubuntu i had problems with web and FTP until i disabled it...[/COLOR])

ping 10.0.0.138
```
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
From 10.0.0.2 icmp_seq=1 Destination Host Unreachable
From 10.0.0.2 icmp_seq=2 Destination Host Unreachable
From 10.0.0.2 icmp_seq=3 Destination Host Unreachable

--- 10.0.0.138 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4016ms
, pipe 3

```

and then i pressed the disconnect in Wicd, and got from the tail:
```
Sep 15 09:34:48 ofri-laptop avahi-daemon[4921]: Withdrawing address record for fe80::2a0:d1ff:fe6a:646 on eth0.
Sep 15 09:34:48 ofri-laptop avahi-daemon[4921]: Withdrawing address record for 10.0.0.2 on eth1.
Sep 15 09:34:48 ofri-laptop avahi-daemon[4921]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.0.0.2.
Sep 15 09:34:48 ofri-laptop avahi-daemon[4921]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep 15 09:34:48 ofri-laptop avahi-daemon[4921]: Withdrawing address record for fe80::219:d2ff:fe5c:9815 on eth1.

```

that's about it.
if you think i should really do it **manually**, can you please give me the syntax for iwconfig to set my own IP (i googled a bit, but didn't find it, so i decided to do it with Wicd)

---

### Post by kevdog on 2007-09-15
Here is how to do it

sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID In QUOTES"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

This is with an unencrypted network -- no wep/wpa

---

### Post by ofri on 2007-09-15
> **kevdog said:**
> Here is how to do it

sudo ifconfig eth1 down
sudo killall dhclient dhclient3
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID In QUOTES"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

This is with an unencrypted network -- no wep/wpa

just for the sport, i disabled encryption in my wireless router, and then:
```
ofri@ofri-laptop:~$ sudo ifconfig eth1 down
Password:
ofri@ofri-laptop:~$ sudo killall dhclient dhclient3
dhclient: no process killed
dhclient3: no process killed
ofri@ofri-laptop:~$ sudo ifconfig eth1 up
ofri@ofri-laptop:~$ sudo iwconfig eth1 essid "hadas"
ofri@ofri-laptop:~$ sudo iwconfig eth1 mode Managed
ofri@ofri-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 29007
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:d2:5c:98:15
Sending on   LPF/eth1/00:19:d2:5c:98:15
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

but i think what noob12 meant is that i try to avoid using the DHCP - give my connection its IP address manually (the equivalent of setting IP, net mask, and gateway in advanced settings in Wicd)

the command for setting the default gateway is 
```
route add default gw 192.168.0.1
```
but i'm not sure about the other 2...

i will do some man reading...

---

### Post by ofri on 2007-09-15
here are the uncommented lines from my /etc/dhcp3/dhclient.conf:
```

send host-name "<hostname>";
prepend domain-name-servers 127.0.0.1, 62.219.186.7, 208.67.222.222, 208.67.222.220;

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
timeout 30;

```



as noob12 said before, the problem is with the dhcp, but note that the same dhcp works when i connect using my cable eth0... i'm really puzzled :-k

---

### Post by noob12 on 2007-09-15
Sorry I missed all of that.  Yes, it's true that what I was suggesting is to assign everything manually on your wireless device and to try to ping your router.  

Start with the encryption disabled on the router.

First you will need to get your network information when you are attached wired on eth0.  You'll need to get the address, subnet, and gateway.

Type **ifconfig eth0** and get the subnet mask (shown as Mask) value from that.

If you type **route -n** and look for the line with a 0.0.0.0 in the first column and UG in the fourth, you will learn your default gateway.  It's not going to be a 192.168 address. It has to start with 10 (based on the logs you showed earlier).  

Your earlier address for eth0 was 10.0.0.3.  Try using 10.0.0.50 or something for your wireless.  
Then use the same subnet mask, and gateway obtained for eth0.  This assumes both eth0 and your wireless are using the same router and network.

Once you have all that information you can try entering everything for the wireless interface in the **System | Administration | Network** menu panel.  Then enable the wireless.  Check that you are associated using **iwconfig**.  See if you can ping the router (gateway) address.

If that doesn't work, then it isn't just an issue of acquiring an address; there's something more fundamental we need to fix.  If it does work, we can focus on the DHCP issues.

---

### Post by ofri on 2007-09-15
i already tried all that (read in earlier posts). i just did it using Wicd and not manually (setting the IP, mask and gateway). 

ping still fails.

---

### Post by ofri on 2007-09-16
](*,)

---

### Post by noob12 on 2007-09-16
I guess I missed all of that, but after you configured address manually via wicd, and were getting the destination host unreachable message while pinging the router, it wasn't clear where that was coming back from.

Check if you have a firewall up ```
sudo iptables -nL
```

Is the wireless access point bridged or does it have its own IP address on the LAN?  

Also, do you know if you wireless access point is also the DHCP service and router?

---

### Post by ofri on 2007-09-17
sudo iptables -nL
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
 
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

> Is the wireless access point bridged or does it have its own IP address on the LAN? 
i think it is bridged - it does have an IP but in order to ping it i have to disconnect the lan, and set my ip manually to 10.10.1.x mask to 255.255.255.0 and gateway to 10.10.1.10 and then i can ping it and access it via http at 10.10.1.10.   
also, i attached a screen shot from my wireless router's WAN info screen, that says it is bridged.

> Also, do you know if you wireless access point is also the DHCP service and router?
it is not - the DHCP server in my wireless router is DISABLED. i am using the DHCP server im my wired ADSL modem router.

---

### Post by noob12 on 2007-09-17
The firewall output says you have no blocking rules at all, so that is not the problem.

I had thought your access point was your DHCP and router, but it isn't, so that leaves another point of linkage to verify, namely between the access point and the rest of the local net.

Do you have any independent verification that your access point is properly configured?  Have you used it with any other host, or the same box booted in Windows?

When you plug in wired, are you plugging into a port on the same access point or to a different hub on the net?

---

### Post by ofri on 2007-09-17
> **noob12 said:**
> 
Do you have any independent verification that your access point is properly configured?  Have you used it with any other host, or the same box booted in Windows?

yes - my girlsfriend's computer which runs windows XP and uses the same wireless AP.


> **noob12 said:**
> 
When you plug in wired, are you plugging into a port on the same access point or to a different hub on the net?

same AP.

these 2 answers show that the AP is properly connected to the ADSL-modem-router


i am seriously thinking of re-configuring my whole network. maybe i should get rid of my ADSL-modem-router, and try to configure my wireless router to function as ADSL as well. i'm a little scared to try, because i might kill the internet connection completely. well, if i never post again, i probably did :)

---

### Post by noob12 on 2007-09-17
No. I wouldn't do that.  You're correct that if both of those are working it indicates that the AP is setup properly.

This suggests that we really aren't getting a proper association on the wireless from the Ubuntu box to the access point (despite what iwconfig is showing).  I have to look back for more ideas, but I think the idea of tearing apart the network and rebuilding would  be pointless.

---

### Post by ofri on 2007-09-17
well, pointless as it may be, i tried it. it didn't work, because i couldn't get my wireless router to connect to the ADSL (not sure why. i think its a hardware thing. maybe its ADSL port is messed up). 

but i learned something that may help solve this problem: when i disconnected my wired router, and set my wireless router to function as DHCP, i got connected with my wireless card - **i got an IP from the DHCP, but ping to the router still failed! **

does that give you any new idea as to what may be wrong?

---

### Post by noob12 on 2007-09-17
Nope. That only makes it more mysterious.   Based on what you've said/shown so far:
[LIST]
[*] The wireless AP is bridged
[*] You're getting associated to the AP.
[*] You are not getting any DHCP offers on the Ubuntu host when DHCP service is coming from elsewhere on the LAN.
[*] Windows works fine wireless with the same AP with DHCP service coming elsewhere on the LAN.
[*] Running wired to a port on the AP works fine with DHCP service coming elsewhere on the LAN.
[*] When wireless, static address assignment on the Ubuntu host doesn't let you get to other points on the LAN beyond the AP.
[*] You are getting DHCP offers when they originate from the AP, but you still can't get beyond the AP in that case.
[/LIST]

I think the answer is going to lie in understanding the AP configuration better.  I still think the problem is there, but it is something more subtle.

---

### Post by noob12 on 2007-09-17
What port do you have the AP connected to the rest of the LAN on?  Does it have multiple "internal" and one WAN port?  If so, connect the LAN to one of the internal ports.  Keep the WAN side disconnected.  Turn the DHCP service off (in the AP).

---

### Post by ofri on 2007-09-18
> **noob12 said:**
> What port do you have the AP connected to the rest of the LAN on?  Does it have multiple "internal" and one WAN port?  If so, connect the LAN to one of the internal ports.  Keep the WAN side disconnected.  Turn the DHCP service off (in the AP).

my wireless router has 4 LAN ports and an ADSL port. no WAN port. usually i just connect my computer to one of the 4 LAN ports, and the ADSL-Modem to another. the DHCP (in the AP) is already off (it is set to Disabled. maybe i should try to set in on Relay?)

---

### Post by noob12 on 2007-09-18
OK.  I'm confused about your local network topology.

I thought you said you are not using the AP as a router to the internet.  Didn't you say earlier that the AP is not your LAN's router, and that the router and DHCP server is at 10.0.0.138?

Connect the actual router that is at 10.0.0.138 to one of the LAN ports of the AP, not the ADSL port.
Keep the DHCP disabled in the AP.

---

### Post by ofri on 2007-09-18
ok, i drew you a diagram of my network. i also attached a screenshot from my AP manual, which shows its back panel. 
i hope it is clear now.

> I thought you said you are not using the AP as a router to the internet. Didn't you say earlier that the AP is not your LAN's router, and that the router and DHCP server is at 10.0.0.138?
everything you wrote here is correct. 

> Connect the actual router that is at 10.0.0.138 to one of the LAN ports of the AP, not the ADSL port
that is what i am doing. ADSL port is smaller port, which needs an RJ-11 Cable. it can be used to connect to the phone line, not to the network. it is currently not used in my wireless router. (my modem, ofcourse has an ADSL port which is used to connect to the phone line)

> Keep the DHCP disabled in the AP
it was always disabled, and i will keep it that way until ordered otherwise :)

---

### Post by noob12 on 2007-09-18
Good and bad.  Good because your setup looks exactly right.  Bad because it still suggests no cause for the problem.  I have no further ideas, but I'll keep thinking about it for awhile.

I would expect that the Relay setting you mentioned means Relaying DHCP from the ADSL side, not between the LAN and Wireless, which I would think would just be bridged.  That would seem to be confirmed by the fact that the Windows box successfully acquires an address by DHCP.  So I don't think it is going to work to try that setting, but since we're out of other options you might want to.

---

### Post by ofri on 2007-09-21
a neighbor of mine set up a new, unprotected network. i successfully connected to it with DHCP. i can ping the gateway and access the internet.
it works a bit slowly, but i guess its normal for the 45%-50% quality i'm getting.... 

i guess it confirms what noob12 sugested - that it is something in my AP configuration. where should i look for the difference between the AP that works (my neighbor's), and the one that doesn't (mine)???
just to remind you - my gf is using our AP with no problems in winXP...
and i already tried to disable encryption, so its not that (at least not ONLY that...)

---

### Post by ofri on 2007-09-21
and another thing i noticed - after i disconnected from that network, and scanned for networks again, i only see that network. i don't see my own network anymore...

---

### Post by kolslorr on 2007-09-23
I have very similar problem... of which I also tried almost everything listed here, but to no avail....

:(

---

