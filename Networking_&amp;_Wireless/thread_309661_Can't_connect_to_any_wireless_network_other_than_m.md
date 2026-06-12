---
title: "Can't connect to any wireless network other than my home network."
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by Johnny_Sparx on 2006-11-29
Hello, 

I am experiencing the following problem after having had upgraded from Xubuntu 6.06 to 6.10, and my fiddling has drove me partially insane:

**I cannot connect to any wireless network other than the one specified in _network-admin_.**  Currently this is set with an SSID, fixed IP and password for the network. I was previously using *wlassistant* successfully to connect to other networks (usually open networks) but now I  cannot connect anymore.  *ifconfig* returns the following when connected  at _home_:

```
john@shark:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:48:51:FC  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe48:51fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4782089 (4.5 MiB)  TX bytes:583506 (569.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1128 (1.1 KiB)  TX bytes:1128 (1.1 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.61.1  Bcast:172.16.61.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.210.1  Bcast:172.16.210.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-48-51-FC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16250 errors:0 dropped:0 overruns:0 frame:12825
          TX packets:4550 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5997127 (5.7 MiB)  TX bytes:723117 (706.1 KiB)
          Interrupt:169 Memory:ccaa0000-ccab0000 
```

Furthermore, */etc/network/interfaces* contains the following.

```
john@shark:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid Super Sparx
wireless-key 828b4683ae
address 192.168.2.14
netmask 255.255.255.0
gateway 192.168.2.1

auto ath0


iface eth1 inet dhcp
address 192.168.2.14
netmask 255.255.255.0
wireless-essid Super Sparx
wireless-key 828b4683ae
```

Ant information would be greatly appreciated.

JS.

---

### Post by trubblemaker on 2006-11-29
QUick howto:
```
 sudo iwlist scan # lists essid's in your surroundings
```  
it will help you to set things to other essid's

to pick the closest un-encrypted network and get an ip
```

sudo iwconfig ath0 essid any
sudo dhclient ath0

```
connect to essid="linksys" un-encrypted network and get an ip
```

sudo iwconfig ath0 essid linksys
sudo dhclient ath0

```

warning:
ifup and ifdown use settings in you /etc/network/interfaces file so shouldn't be used in your case if your away from home.

Now that I've taught you all that I bet your not interested in Network Manager, a program that manages your connections for you!
Availble now! Any where Synaptic is!  Brought to you By: Ubuntu.

---

### Post by Johnny_Sparx on 2006-12-01
Thank you trubblemaker, but this is still a little weird.

I looked at your reply to my post and tried it several times on several networks.  Something is weird...:confused:   

While *iwconfig* seems to work well, *dhclient* seems to make several unsuccessful attempts before "sleeping".  Sometimes, it works right away. 

Why does this happen?  Shouldn't this be relatively consistent and reliable?  So far it does not seem to be the case.

Johnny_Sparx

---

### Post by trubblemaker on 2006-12-01
welcome to the wireless world. not always can one get a signal, hence the attempts and sleeping.(totally normal behaviour if you don't specify an ip)

the best method to connect to a network is the following 
find an un-encypted nerwork essid with

```
 sudo iwlist scan
```
then once you found one explicitly set the essid with
```

sudo iwconfig ath0 essid <found-essid>
```
then try and obtain an ip

```
sudo dhclient ath0
```

using 'any' is ok and it usually works but as your learning sometimes it has a hard time picking one.

specifying one works alot better.  now that your the man with the hardcore commandline, think about using NetworkManager availble with apt-get, or synaptic.

---

### Post by trubblemaker on 2006-12-01
oh, should say with specifying the essid you will find it alot more reliable.

---

### Post by Johnny_Sparx on 2006-12-01
Actually, that is exactly what I did... in that order.

dhclient seems to be weird.  Here's an account of what happened on one case.

```
john@shark:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:7B:84:A0
                    ESSID:"buzz"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:02:6F:07:56:2F
                    ESSID:"javau"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0D:0B:CB:5D:9F
                    ESSID:"000D0BCB5D9E"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:13:46:A4:BC:AC
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/94  Signal level=-66 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

sit0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

john@shark:~$ sudo iwconfig ath0 essid javau; sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:48:51:fc
Sending on   LPF/ath0/00:13:46:48:51:fc
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.




=======================================================



john@shark:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:13:46:48:51:FC  
          inet addr:192.168.1.112  Bcast:192.168.1.255  
Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe48:51fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5782914 (5.5 MiB)  TX bytes:1069532 (1.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6516 (6.3 KiB)  TX bytes:6516 (6.3 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.61.1  Bcast:172.16.61.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.210.1  Bcast:172.16.210.255  
Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 
00-13-46-48-51-FC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54960 errors:0 dropped:0 overruns:0 frame:22988
          TX packets:15029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9023038 (8.6 MiB)  TX bytes:1621121 (1.5 MiB)
          Interrupt:169 Memory:ccaa0000-ccab0000 

john@shark:~$ cat /etc/n
nanorc         network/       no-ip.conf     nsswitch.conf  
john@shark:~$ ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:13:46:48:51:FC  
          inet addr:192.168.1.112  Bcast:192.168.1.255  
Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe48:51fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5782914 (5.5 MiB)  TX bytes:1069532 (1.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6516 (6.3 KiB)  TX bytes:6516 (6.3 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.61.1  Bcast:172.16.61.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.210.1  Bcast:172.16.210.255  
Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 
00-13-46-48-51-FC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55200 errors:0 dropped:0 overruns:0 frame:22991
          TX packets:15029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:9037918 (8.6 MiB)  TX bytes:1621121 (1.5 MiB)
          Interrupt:169 Memory:ccaa0000-ccab0000 

john@shark:~$ clear

john@shark:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid Super Sparx
wireless-key 828b4683ae
address 192.168.2.14
netmask 255.255.255.0
gateway 192.168.2.1

auto ath0


iface eth1 inet dhcp
address 192.168.2.14
netmask 255.255.255.0
wireless-essid Super Sparx
wireless-key 828b4683ae

```


](*,)

---

### Post by trubblemaker on 2006-12-01
wow that must be frustrating, ok see a couple of things,
first you I'm pretty sure you need to use "Super Sparx" with '"' around it as space is a delimiter in your file.  That way you'll connect on boot to the correct network.  (you might want to blank out  your key that you posted. not a big deal as odds are low that they can find you but still worth it.)

hard to say what the specific issue is, is this your ap or someone else's?  (Javau could have a mac filter on it preventing you from getting an ip.)

---

### Post by Johnny_Sparx on 2006-12-02
(1) Ha ha.... Your note was well taken concerning my key.  After I first posted it, I realized the foolishness of it, and will change it after all is done... The odds are low that I'd have troubles, but still exist.](*,) 


(2) Well, I can connect at home with no problems at all... actually, I don't have to configure anything at all to get it working.  At the open network in the coffee shop(s) I actively configure as you suggested.  Again, *dhclient* goes to _sleep_ because it cannot get a lease.  What did I do?  I ran the *wlassistant* utility out of frustration, but it logs a similar failure.  I run *dhclient* again, and it works.  I am using it now.

Weird, weird, weird.  I am suspecting that it has something to do with the configuration of my card that is impeding *dhclient* from working.  I think *wlassistant* configures the card somehow, and *dhclient* subsequently works.

I ain't too religious, but am praying these days.  I have heard that divine intervention has actually happened... I mean the Red Sea parting and stuff....

Any other ideas?  There must be a simple logical way for why this is not reliable to connect to networks other than home (a very reliable connection).:-k

---

### Post by trubblemaker on 2006-12-02
so here's my long winded explanation of networking as I understand, maybe it willhelp you think of something.

when you boot, you use the setup of on "/etc/network/interfaces" if it contains specific network data, (key, essid) it will use those for connecting on boot every time.

if you run 
```
 sudo ifup ath0 
``` reads your /etc/network/interfaces file and tries to connect using those settings.

if you use 

```
sudo dhclient ath0
```it uses your current settings to try and get an ip.

so if you boot, then change anythign via any tools: iwconfig, wlassistant 
again it will use the current settings.

get my meaning? dhclient isn't smart it just uses current settings so if you changed the settings that's now what it's using, 

given your setup, in a coffee shop you will not get an ip on boot, but after changing some settings you may get an ip.

My "best practices" policy would be to *slow down* what I said before, to try and get an understanding.

so try this after a clean boot:

```

echo "before" >> output;
 iwconfig  | sudo tee -a output; 
sudo iwlist scan
sudo iwconfig ath0 essid javau
echo "changed" >> output;
iwconfig  | sudo tee -a output; 
echo "first dhclient" >> output;
sudo dhclient ath0 | sudo tee -a output; 
wlassistant | sudo tee -a output; 
iwconfig  | sudo tee -a output; 
echo "second dhclient" >> output;
sudo dhclient ath0 | sudo tee -a output; 

```

this will log all your output to a file called output.  This will hopefully show us what is changing with the settings between, the two programs that is changing it, so your connection works.

you might find that commenting out your home network entries in /etc/network/interfaces enables you to connect on the first try at a coffee shop.  That would point to some setting changes that need to happen.


Atleast from what I understand you get an ip on the second try after running wlassistant, **every time** right?

---

