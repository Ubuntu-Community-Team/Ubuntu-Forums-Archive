---
title: "LAN with Apache /etc/network/interface quesiton"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by darkwave80 on 2007-10-08
I have ubuntu 7.04

and sometimes i can see the files on xp and sometimes it dosent work if i have a PPP going on with ubuntu and then try to access apache files on ubuntu....

So i edited the /etc/network/interfaces file to set the lan on a static ip with fixed settings and now i cant even get xp to see shared apache files at all and i cant ping either ip address

this is how i have my /etc/network/interfaces file

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.80
netmask 255.255.255.0
gateway 192.168.1.1

i wanted to put the ip address of the ubuntu eth0 card 192.168.0.80

and in the past this set up seemed to work.

but now i cant get it to work at all...

What i have is a verizon wirless internet which can connect and its under the PPP when im connected but htis is what i see when im connected to verizon and have eth0 up.

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:4C:8C:6D  
          inet addr:192.168.0.80  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe4c:8c6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139031 (135.7 KiB)  TX bytes:26203 (25.5 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:886295 (865.5 KiB)  TX bytes:886295 (865.5 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.220.12.164  P-t-P:166.74.38.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:7754714 (7.3 MiB)  TX bytes:831903 (812.4 KiB)


on the eth0 it seems to look configured im not sure why the broadcast is the number it lists but it always was "odd" number.....

ive tryed using the terminal to manually configure the network becuase using the "dummy interface for network the "network-admin" to do it the GUI way dosent seem to work all the time reguardless of DHCP or setting a fixed static address..

I just dont get why this doesnt work with all the information manually typed out....

Ive read tons of posts like this but alls I want is to be able to connect to the net on my ubuntu box without causing apache to not work or visa versa..

I always want the eth0 to run with fixed settings and if i use my PPP connection to not affect anything going on with the eth0 settings..

---

### Post by darkwave80 on 2007-10-08
Here is more information...this might be a issue with XP being dumb....

but i booted up my other ubuntu machine and set both to just both the Ubuntu and the Ubuntu apache machine to use DHCP and i can pull up the apache ip and folder just fine in both...

but if this is working then my PPP is dead.....i can connect with the apache machine and here is what it looks like when im on the internet with PPP and apache WORKS....



Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
96.176.38.5     *               255.255.255.255     UH      0         0        0 ppp0
192.168.1.0     *               255.255.255.0            U       0       0          0 eth0
link-local          *               255.255.0.0                  U     1000   0        0 eth0
default         192.168.1.1       0.0.0.0                  UG      0         0        0 eth0

but if i do a sudo ifconfig eth0 down

and then disconnect from the PPP dialer then redial it looks like this and i can browse the internet

[Blo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XX.XXX.41.190  P-t-P:66.174.38.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 b)  TX bytes:97 (97.0 b)
[/B]
[CENTER]
and when i do a route now it looks like this....[/CENTER].

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
5.sub-XX-174-38 *               255.255.255.255 UH    0      0        0 ppp0
default         *                            0.0.0.0                   U     0      0        0 ppp0




so that just shows that i can run PPP or turn on the eth0 with no internet and which ever one is running first works....

what can i change to make both work reguardless of which one is running.....

i got a feeling it has something to do with making a "default route" but when the PPP is on and off from time to time how can i tell the computer to always make the PPP connection the main one?

---

