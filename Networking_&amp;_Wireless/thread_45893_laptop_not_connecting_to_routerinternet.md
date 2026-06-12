---
title: "laptop not connecting to router/internet"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by matawang on 2005-07-02
I m a noobie. Trid to run ubuntu on my laptop which is running on centrino. but not able to connect even to the wireless router. tried ping to 192.168.2.1; result: ping:unkbnown host.

wireless connection in menu network settings says it is connected. msg: interface eth1 is active. but still can't connect. 

pls help
 ](*,)

---

### Post by defkewl on 2005-07-02
Did you filled in the router ip address as gateway ip address?

---

### Post by jshein on 2005-07-02
What does ifconfig tell you?

#ifconfig

Is the connection active? 
Did it get an IP? 
Try statically assigning an IP to the connection and see if that fixes the problem.

---

### Post by alastair on 2005-07-02
Output of :

ifconfig -a
iwconfig
route -n
cat /etc/network/interfaces

Plus any details of your network - DHCP? etc.

---

### Post by matawang on 2005-07-03
[QUOTE=alastair]Output of :

ifconfig -a
iwconfig
route -n
cat /etc/network/interfaces

Plus any details of your network - DHCP? etc.[/QUOTE]

ok here is the output:
ifconfig -a

eth0  Link encap:Ethernet HWaddr  00:0B:5D:4E:FD:95
         BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b) TX bytes:0 (o.o b)
         Interrupt:11 Bse address:0x3000

eth1  Link encap:Ethernet HWaddr  00:0C:F1:3A:C8:76
         inet6 addr: fe80::20c:f1ff:fe3a:c876/64 Scope:Link
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b) TX bytes:0 (o.o b)
         Interrupt:11 Memory:d0202000-d0202fff

lo     Link encap:Local Loopback
         inet addr: 127.0.0.1  Mask:255.255.255.255
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:3790  errors:0 dropped:0 overruns:0 frame:0
         tx PACKETS:3790 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:0
         RX bytes:340448 (332.4 kib)) TX bytes:340448 (332.4 KiB)
       

sit0  Link encap:IPv6-in-IPv4
        NOARP MTU:1480 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 b) TX bytes:0 (o.o b)



#iwconfig

lo      no wireless extensions

eth0  no wireless extensions


eth1  unassociated ESSID:"pasta"  Nickname:"ipw2100"
         Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
         Bit Rate=0 kb/s  Tx-Power:off
         Retry:on   RTS thr:off   Fragment thr:off
         Encryption  key:off
         Power Management:off
         Link Quality:0 Signal level:0  Noise level:0
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0   no wireless extensions


route -n
Kernel IP routing table
Destination   Gateway  Genmask   Flags Metric Ref Use  Iface



cat /etc/network/interfaces

#The loopback network interface
auto lo
iface lo inet loopback

#This is a list of hotpluggable network interfaces

mapping hotplug
               script grep
               map eth1

iface eth1 inet dhcp
wireless-essid pasta
wireless-key saysukamakan

autoeth1

-----------------------------------------------------------------------------------------

i am using SMC Barricade g : SMC2804WBR wireless router

i have no problem with wired connection.


please help!!!!

---

### Post by matawang on 2005-07-03
[QUOTE=defkewl]Did you filled in the router ip address as gateway ip address?[/QUOTE]

Yes. IP for router : 192.168.2.1

---

### Post by matawang on 2005-07-03
[QUOTE=jshein]What does ifconfig tell you?

#ifconfig

Is the connection active? 
Did it get an IP? 
Try statically assigning an IP to the connection and see if that fixes the problem.[/QUOTE]


tried to statically assign IP but not possible.
i am running live cd

---

### Post by jshein on 2005-07-03
try

#ifconfig eth1 ssid pasta chan 0
#ifconfig eth1 192.168.2.123

#ping 192.168.2.1

What does that get you?

---

### Post by alastair on 2005-07-04
Yes - wireless is a pain sometimes. As is networking occasionally ....

You have not got an IP address from the router (DHCP) on your wireless device eth1.
No IP address, no play. You are "unassociated".

The "interfaces" file is really for use at boot, or using "ifup eth1" and "ifdown eth1" stages.

You could try and manually set things, like "jshein" says above. Play with things like :

iwconfig eth1 ap <MAC address of AP>
iwconfig eth1 key restricted <WEP key>

(where <WEP key> == 26 HEX digits for a 128 bit WEP)

ifconfig eth1 192.168.2.123
route add default gw 192.168.2.1

Check via :

ifconfig eth1
route -n
iwconfig

---

### Post by matawang on 2005-07-05
Ok....i managed to solve my problem....
wat i did was to do dual boot installation for my notebook. but i have to do manual configuration for the IP address and gateway address.
everything is working fine at the moment. 
Thanks to everyone who tried to help. really appreciate that.

---

### Post by topoftheworld on 2005-07-05
Hello guys, first post here, I am having the same problem.
I manually put in my info, and have been able to connect to the net and stuff.
I shouldn't have to though, my router supports DHCP. 
Also, I am not sure if this is related to that issue, but I have really bad ping times to most websites, and I am having trouble pinging locally as well. 

thanks for any help

---

### Post by jshein on 2005-07-05
I have frequently had this kind of problem on numerous machines. It has to do with your combination of card + dhcp server ( router or whatever ).

Sometimes it can be solved by changing the DHCP client  from dhcp3-client ( default ) to dhcpcd

#sudo apt-get install dhcpcd

---

