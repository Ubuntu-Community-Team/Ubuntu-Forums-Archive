---
title: "long shot"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by MizikeJulian on 2008-03-10
right so ive, had ubuntu on a couple of different machines, right now its running smoothly, if not a little choppy, on an old dell with a pentium 3 in it, i also have an old imac g3 400mhz, anyways i was wondering if there was a way to use my ubuntu machine as a gateway, currently it is connecting to the internet through a wireless pci card dealy a wifi router and a cable modem, oh i dont know if this makes a difference but the imac is running osx 10.2 right cool thanks in advance

edit: thats a little unclear, what i mean to say is that i wish to connect to the internet on the imac through the ubuntu machine, i tried fire started to no avail, also strangely while i only see one ethernet connection on the back of the ubuntu machine im showing 3 different connections, ath0 wifi1 eth0, also strangely the connection that goes to my wifi router is ath0 not wifi0, right a peculiar situation, it might be important to note that i used the alternative installation disk of ubuntu 7.10. right ok, any thoughts or suggestions and redeemable for good karma, in the astrological realm.

---

### Post by dmizer on 2008-03-11
what you want to do is called "internet connection sharing".  i've used the following howto on multiple occasions to enable internet connection sharing:

[https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)

that said, in most situations it is preferable to use a router with a built in firewall for many reasons (not limited to the following):
1) ease of setup
2) better security
3) maintenance free
4) better local network response

good reasons for using internet connection sharing include
1) internet connection is dail up
2) fine tuned packet and routing control via iptables
3) multiple subnets

ath0 is your wireless card's "managed mode" <- this is your active internet connection
wifi0 is your wireless card's "[monitor mode](http://en.wikipedia.org/wiki/Monitor_mode)"

to make use of wifi0, you would actually have to configure ubuntu to use the card in monitor mode which in most cases is undesirable.

---

### Post by MizikeJulian on 2008-03-11
hmm first off thanks,
hmm it seems that not all of the commands listed in the tutorial fit exactly right with the darwin command prompt 
in darwin
sudo ifconfig dumps 4 returns 
lo0

gif0
stf0
en0
i tried the commands in the client section using the en0 tag in darwin on the imac,
but i was unable to use the first command in the list, the one that unconfigure's the network interface,
and if you could clarify, the gw address im pointing the imac at is the same as the lan adress of my wireless ubuntu box? in this case 192.168.1.4, as that is the address that is curently reserved for the wireless ubuntu machine in the router, also is the ip address i give to my imac arbitrary? just like setting another ip address in the router, or must i also point my ubuntu box at the imac?

again thanks

this was the command i used in the ubuntu box
user@ubuntu:~$ sudo iptables -A FORWARD -i eth0 -o ath0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT

there must be something im missing, still no connection with the imac.
right thanks

---

### Post by dmizer on 2008-03-11
on the ubuntu box, post the output of:
```
sudo ifconfig
```
also, your physical layout should now look something like this:

cable modem -> ubuntu pc eth0 ~ ubuntu pc ath0 -> router (in hub mode/no NAT) -> mac

which means that you'll have to turn off NAT translation in your router for this to work.

---

### Post by MizikeJulian on 2008-03-12
ok
sudo ifconfig dumps 

ath0      Link encap:Ethernet  HWaddr 00:C0:A8:C1:5D:F2  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fec1:5df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11559232 (11.0 MB)  TX bytes:1490297 (1.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:B0:D0:CA:B2:48  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:60 (60.0 b)
          Interrupt:5 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-C1-5D-F2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44088 errors:0 dropped:0 overruns:0 frame:293
          TX packets:10063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:14754777 (14.0 MB)  TX bytes:1716393 (1.6 MB)
          Interrupt:9 

user@ubuntu:~$ 

right so right now my physical setup goes as follows

cable modem -- wifi router -- Ubuntu ath0 -- Ubuntu eth0 -- mac en0 or something,,,

also i suppose it is important to note that currently the mac is not capable of connecting to the internet, nor have i been able to get either computer to ping the other, nor have i been able to achieve any sort of file sharing,, right so it would seem that this physical setup is not capable of what i would like, unfortunately, this seems to be the only physical layout that fits my budget, 
also it may be important to note that from time to time there are as few as one other computer connecting to the wireless network and as many as three, 
so i guess my question goes as follows
is there a way to share a wireless connection locally?
or am i on a wild goose chase backwards through a cornfield? to use a local colloquialism.
right thanks it advance for your input.

---

### Post by dmizer on 2008-03-13
that physical setup should work.  don't know a thing about geese.

so you should set up your mac with the following network system preferences:

ip address = 192.168.0.2
subnetmask = 255.255.255.0
router = 192.168.0.1

then you should be able to ping to your ubuntu machine (at ip address 192.168.0.1)

---

