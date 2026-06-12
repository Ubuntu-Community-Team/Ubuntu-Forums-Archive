---
title: "[SOLVED] Setting PPPoE (dynamic IP) and LAN (Static IP) on a single network card"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Sorabh Gambhir on 2008-03-18
Hi all,

I have recently installed Ubuntu 7.10 Gutsy on my desktop and am facing problem setting up two different networks on the same network card. I need to access the LAN in my institute using a static IP address and the Internet from a service provider who provides me a PPPoE connection using dynamic IP address. Earlier when I used Windows, it provided the functionality to set multiple networks on the same card. But now I can't access both the LAN and the Internet connection simultaneously, I have to change the network settings between "roaming mode enabled" and "static IP" every time I need to access the other connection. I have been searching for an answer since a whole week but to no avail. Can someone please provide me with a solution. I appreciate any help provided.

Thanks

---

### Post by Sorabh Gambhir on 2008-03-18
Let me provide some details here...First, my Internet service provider has bound my account to the MAC of my NIC.

This is how my **/etc/network/interfaces** looks like when I have configured the internet connection using PPPoE.
I used the "sudo pppoeconf" command to set up the connection.

------------------------

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider



auto eth0
iface eth0 inet manual
-------------------------

This sets the **/etc/ppp/peers/dsl-provider** as follows:

-------------------------

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
usepeerdns
user "username"

---------------------------
I am successfully able to ping websites such as "www.google.com", etc., using this setup.
And on using "ifconfig", I get the following:

eth0

          Link encap:Ethernet  HWaddr 00:15:F2:53:02:6D  
          inet6 addr: fe80::215:f2ff:fe53:26d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:502629 (490.8 KB)  TX bytes:11112 (10.8 KB)
          Interrupt:19 

lo

          Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ppp0

          Link encap:Point-to-Point Protocol  
          inet addr:125.18.174.232  P-t-P:61.246.200.13  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3810 (3.7 KB)  TX bytes:1764 (1.7 KB)



-----------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------

And when I set up a static IP to access the LAN, it looks like:
----------------------
auto lo
iface lo inet loopback



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider



auto eth0
iface eth0 inet static
address 176.12.14.174
netmask 255.255.252.0

------------------------

But using the static IP configuration as above, I don't have access to the Internet.

And on using "ifconfig", I get the following:


eth0

          Link encap:Ethernet  HWaddr 00:15:F2:53:02:6D  
          inet addr:176.12.14.174  Bcast:176.12.15.255  Mask:255.255.252.0
          inet6 addr: fe80::215:f2ff:fe53:26d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100360 (98.0 KB)  TX bytes:4657 (4.5 KB)
          Interrupt:19 


lo

          Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


-----------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------

Then I modified /etc/ppp/peers/dsl-provider as follows:

------------------------

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so **eth0:1**
usepeerdns
user "username"

------------------------

Along with modification in /etc/network/interfaces as follows:

------------------------

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig **eth0:1** up # line maintained by pppoeconf
provider dsl-provider



auto **eth0**
iface** eth0** inet **static**
address 176.12.14.174
netmask 255.255.252.0



auto **eth0:1**
iface eth0 inet manual

-------------------------

I changed the network interface for the Internet connection to eth0:1 because I need to be connected to the LAN (on eth0) 24 hours a day, whereas I connect to the Internet only when required.

But then on triggering the connection using "pon dsl-provider", I  got the following message:


Mar 19 02:39:59 desktop pppd[7200]: Plugin rp-pppoe.so loaded.
Mar 19 02:39:59 desktop pppd[7202]: pppd 2.4.4 started by sorabh, uid 1000
Mar 19 02:39:59 desktop pppd[7202]: PPP session is 436
Mar 19 02:39:59 desktop pppd[7202]:** Failed to connect PPPoE socket:** 19 No such device
Mar 19 02:39:59 desktop pppd[7202]: Exit.


-----------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------

I even tried the combination of setting the **static IP to eth0:1 and the dynamic IP to eth0** in the /etc/network/interfaces and dynamic to eth0 in /etc/ppp/peers/dsl-provider but simply got a CHAP authentication failure when trying to connect.

It is becoming quite a tedious task to switch between network configurations; every time I have to change the settings and execute the "sudo pppoeconf" command whenever I need to access the Internet.

Please help...how do I configure both the connections simultaneously on the single NIC???

---

### Post by Sorabh Gambhir on 2008-03-20
Please somebody help me. I don't want to revert back to Windows just for this...

---

### Post by netztier on 2008-03-20
> **Sorabh Gambhir said:**
> Please somebody help me. I don't want to revert back to Windows just for this...

I consider such a setup with a single NIC a "bad thing" to start with, from a networking and security perspective. 

Mixing internal and external broadcast domains like that is *asking for trouble*. The fact that Windows supports such setups is no excuse nor reason for anything, and has indeed a word or two to say about Windows' concept of "network security".

I know that my answer will be out of the scope you intended ("single NIC"), but I strongly suggest to use separate NICs for this setup. 

If that is just not an option, you could try this: get an old VLAN capable switch on which you configure two VLANs (any old Cisco Catalyst 2900XL or 3500XL will do nicely, even the 1900 series):

One port on that switch is going to be configured as 802.1q trunk, carrying the two VLANs (as tagged frames) and will connect to your NIC. 
One port is member of VLAN "internal" (untagged) and connects to your institue's LAN, 
One port is member of VLAN "external" (untagged) and connects to your ISP's modem, router or line. 

On your Ubuntu box, you configure 802.1q support on the NIC, and you map one eth0:n subinterface to each VLAN, and you then configure each eth0:n individually with PPPoE or static or dhcp or ...
Basically, this is not different from having two NICs, it's just done on a single physical one.

regards

Marc

---

### Post by Sorabh Gambhir on 2008-03-20
Thanks, I was not aware of the aspect that networking security requires managing the external and internal networks on separate NICs. I think that investing in a new NIC would be the probable choice for me, I am going to stay loyal to the Linux ideology.

---

