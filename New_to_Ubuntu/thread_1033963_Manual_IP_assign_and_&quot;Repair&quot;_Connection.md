---
title: "Manual IP assign and &quot;Repair&quot; Connection"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by gaffurabi on 2009-01-07
My Ubuntu stopped getting automatic IP from DHCP server. so how can I:

[LIST=1]
[*]assign the IP manually
[IMG]http://img.photobucket.com/albums/v185/darkrift/2-1.jpg[/IMG]

[*]"repair" connection like on windows? 

[IMG]http://img.photobucket.com/albums/v185/darkrift/1-1.jpg[/IMG]
[/LIST]

---

### Post by handydan918 on 2009-01-07
1) What is the dhcp server on your network? A router?
Check that end first. Make sure that the dhcp (software) server is up and running. If it's a router, maybe reboot it. 

2) After the above, do ```
sudo dhclient
``` and post the output back here.

---

### Post by oilchangeguy on 2009-01-07
there is no repair option that i'm aware of. but you'll need to contact your isp for the info to fill in, when configure the connection.

---

### Post by whoop on 2009-01-07
Static Ip:
Right Click your connection icon, choose edit. You can edit/add your connections there.

Repair: 
I am not sure what this button does in windows but it's probably just getting a new lease from the gateway or something. 
In that case you could try:
ifdown eth0
ifup eth0

Or just disable and the enable the network via the network icon

---

### Post by handydan918 on 2009-01-07
> **whoop said:**
> 
Repair: 
I am not sure what this button does in windows but it's probably just getting a new lease from the gateway or something. 
In that case you could try:
ifdown eth0
ifup eth0


except that it won't help if he's running on eth1...

Which is why I suggested ```
sudo dhclient
```

This is exactly the same functionlity as the window "repair" button, which just does 'ipconfig /relaease" and "ipconfig /renew".

---

### Post by gaffurabi on 2009-01-07
here is the outcome of dhclient:

```
varg@varg-desktop:~$ sudo dhclient
[sudo] password for varg: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/ca:54:b7:d8:25:b6
Sending on   LPF/pan0/ca:54:b7:d8:25:b6
Listening on LPF/eth1/4c:00:10:11:35:b4
Sending on   LPF/eth1/4c:00:10:11:35:b4
Listening on LPF/eth0/00:1d:7d:ad:ed:23
Sending on   LPF/eth0/00:1d:7d:ad:ed:23
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPREQUEST of 192.168.2.85 on eth0 to 255.255.255.255 port 67
DHCPNAK from 195.249.88.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18
DHCPOFFER of 192.168.2.85 from 192.168.2.1
DHCPREQUEST of 192.168.2.85 on eth0 to 255.255.255.255 port 67
DHCPNAK from 195.249.88.3
DHCPACK of 192.168.2.85 from 192.168.2.1
bound to 192.168.2.85 -- renewal in 2147483647 seconds.


```

[quote=whoop]Static Ip:
Right Click your connection icon, choose edit. You can edit/add your connections there.[/quote]

i did this already but ubuntu did not assign the ip i entered

~also: windows gets the IP from DHCP without any problem

---

### Post by jflaker on 2009-01-07
If I have an issue, I right click the connection icon and disable then enable networking....

---

### Post by handydan918 on 2009-01-07
> **gaffurabi said:**
> here is the outcome of dhclient:
<snip>
3
DHCPACK of 192.168.2.85 from 192.168.2.1
bound to 192.168.2.85 -- renewal in 2147483647 seconds.

[/CODE]



i did this already but ubuntu did not assign the ip i entered

~also: windows gets the IP from DHCP without any problem
So does Ubuntu. The lines above indicate that your dhcp server, at 192.168.2.1 assigned the ip of 192.168.2.85.
So what is the real problem?

---

### Post by gaffurabi on 2009-01-07
the problem is that our IPs are assigned between: 195.249.88.xxx-91.xxx

so 192.168.2.85 is not a valid IP for me and i cannot acces to internet with that.

---

### Post by daydbai on 2009-01-07
> **gaffurabi said:**
> the problem is our IPs are assigned between 195.249.88.xxx-91.xxx

so 192.168.2.85 is not a valid IP for me and i cannot acces to internet with that.

In this case, the problem is not with getting an IP - it is where you are getting your IP address from.  
192.168.***.***  looks like an address that is coming from a home router.  

Check your home network to be sure that you either don't have any devices running DCHP  (if you get all your addresses assigned from your ISP)
OR
Check to be sure that you don't have conflicting devices running DCHP (ie the broadband modem and the router and the wireless access point)

EDIT* I believe that my belkin wireless router defaults at 192.168.2.1 - if that helps any

---

### Post by gaffurabi on 2009-01-07
> **daydbai said:**
> In this case, the problem is not with getting an IP - it is where you are getting your IP address from.  
192.168.***.***  looks like an address that is coming from a home router.  

Check your home network to be sure that you either don't have any devices running DCHP  (if you get all your addresses assigned from your ISP)
OR
Check to be sure that you don't have conflicting devices running DCHP (ie the broadband modem and the router and the wireless access point)

nope for both

:(

i have only one connection way to the internet and that is through LAN (of my dormitory).
no wireless modems, home switches, bluetooth devices etc.

---

### Post by daydbai on 2009-01-07
If you type:
192.168.2.1
in your browser address bar - 
Do you get a login screen for a device?
a "page can not be displayed" error?  

The address has be getting assigned from somewhere.

---

### Post by gaffurabi on 2009-01-07
> **daydbai said:**
> If you type:
192.168.2.1
in your browser address bar - 
Do you get a login screen for a device?
a "page can not be displayed" error?  

The address has be getting assigned from somewhere.

i get :"page can not be displayed"

i believe that 192.168.2.1 is a standart IP:see [http://whois.domaintools.com/192.168.2.1](http://whois.domaintools.com/192.168.2.1) just like when you try to configure a home network you get a default IP assigned (if you dont bother assigning it manually).

---

### Post by handydan918 on 2009-01-07
Well, this is a network issue, not an Ubuntu issue. I wish we could miracle you a solution, but it's obvious that there is more going on with this network than will likely be guessed at. You ARE getting a dhcp address assigned by a dhcp server on your network. Sounds like you might need to have a chat with your netadmin.

---

### Post by gaffurabi on 2009-01-08
> **handydan918 said:**
> Well, this is a network issue, not an Ubuntu issue. I wish we could miracle you a solution, but it's obvious that there is more going on with this network than will likely be guessed at. You ARE getting a dhcp address assigned by a dhcp server on your network. Sounds like you might need to have a chat with your netadmin.

well i found a 'weird' solution:

*after the boot i cannot get the IP
*i run ```
sudo dhclient
```
*i disable/enable connection then it assigns me a 'working' IP so i can connect to internet 

i dont know the reasons for that. it was normal before but about a week ago this problem started.

---

### Post by gaffurabi on 2009-01-09
Maybe it is because i have 2 ethernet cards (one motherboard chip one external)

---

### Post by dadozgb on 2009-01-09
> **gaffurabi said:**
> Maybe it is because i have 2 ethernet cards (one motherboard chip one external)

You obviously have a windows working connection and you cannot setup it on linux? How did you set up it on windows? Maybe this is the easyest way that someone can give you a solution or at least valid hint what to to.

---

### Post by theozzlives on 2009-01-09
Are you behind a firewall?

---

### Post by gaffurabi on 2009-01-09
> **theozzlives said:**
> Are you behind a firewall?
no i am not
> **dadozgb said:**
> You obviously have a windows working connection and you cannot setup it on linux? How did you set up it on windows? Maybe this is the easyest way that someone can give you a solution or at least valid hint what to to.

both were working before fine on ubuntu, for a couple of weeks i had had this problem

---

### Post by ByteJuggler on 2009-01-09
Please, post the output of:

```
ifconfig
```

I'm wondering if your machine is somehow getting the address somehow from itself.  Do you have a dhcp server installed on your Ubuntu? You can check with:

```
dpkg --list | grep dhcp
```

Which should list any installed ("ii") packages with dhcp in the name.  The dhcp server package is likely called "dhcp3-server" so if you see that you have dhcpd installed on your machine, and it's giving itself an IP.

---

### Post by gaffurabi on 2009-01-09
```
varg@varg-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:ad:ed:23  
          inet addr:195.249.91.63  Bcast:195.249.91.255  Mask:255.255.252.0
          inet6 addr: fe80::21d:7dff:fead:ed23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:794790 (794.7 KB)  TX bytes:65001 (65.0 KB)
          Interrupt:254 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 4c:00:10:11:35:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr d6:c4:53:cf:ba:ec  
          inet6 addr: fe80::d4c4:53ff:fecf:baec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
```

and

```
varg@varg-desktop:~$ dpkg --list | grep dhcp
ii  dhcp3-client                              3.1.1-1ubuntu2                          DHCP client
ii  dhcp3-common                              3.1.1-1ubuntu2                          common files used by all the dhcp3* packages

```

my ip 195.249.91.63 after i do this 'weird' (> **gaffurabi said:**
> well i found a 'weird' solution:

*after the boot i cannot get the IP
*i run ```
sudo dhclient
```
*i disable/enable connection then it assigns me a 'working' IP so i can connect to internet 

i dont know the reasons for that. it was normal before but about a week ago this problem started.) thing.

---

### Post by gaffurabi on 2009-01-11
I am going to format ubuntu. that's the solution i found :@

---

### Post by ByteJuggler on 2009-01-12
> **gaffurabi said:**
> I am going to format ubuntu. that's the solution i found :@

Yes, I'm sorry but I'm out of ideas.  Your machine must be getting its IP from *somewhere*  -- IP assignments don't just happen out of thin air, but it's very hard to try and guess at what might be going on... :(

---

### Post by gaffurabi on 2009-01-15
right now i am using the ethernet of my mainboard gigabyte ga-m57-sli-s4 (nForce 570 sli chipset)
i am going to borrow an external ethernet card from my friend and see if it is a hardware conflict problem for ubuntu. 

meanwhile, i would like to configure the IP manually. how do we do that?

---

### Post by handydan918 on 2009-01-15
> **gaffurabi said:**
> right now i am using the ethernet of my mainboard gigabyte ga-m57-sli-s4 (nForce 570 sli chipset)
i am going to borrow an external ethernet card from my friend and see if it is a hardware conflict problem for ubuntu. 

meanwhile, i would like to configure the IP manually. how do we do that?

I think there is a fundamental lack of information here. We know nothing about your network topography. Is it an enterprise environment, or home? You say "WE get our ip addresses in 195.xx range..." who is WE? Again, I don't see this being an operating system problem. Maybe more information would help us to help you. 
What is the dhcp server on that network?
 Where does the cat5 cable go if you trace it out from your computer?
 What is the next device it connects to?
 And the next one after that?

---

### Post by gaffurabi on 2009-01-15
> **handydan918 said:**
> I think there is a fundamental lack of information here. We know nothing about your network topography. Is it an enterprise environment, or home? You say "WE get our ip addresses in 195.xx range..." who is WE? Again, I don't see this being an operating system problem. Maybe more information would help us to help you. 
What is the dhcp server on that network?
 Where does the cat5 cable go if you trace it out from your computer?
 What is the next device it connects to?
 And the next one after that?

-it is a common dormitory LAN (neither home nor enterprise, i guess), i need to connect to it first in order to connect to the internet, which is also supplied by my dormitory.

-"WE" is all the LAN users

-"What is the dhcp server on that network?" i dont know how to learn that or run a query to find out.

-cable goes to the main hub/switch of my dormitory. then mine and all the other dormitories' cables go into one major switch. i guess this helps: (i am in BMA)

[IMG]http://img.photobucket.com/albums/v185/darkrift/png_1.png[/IMG]

right now i am using manually configured IP.

---

### Post by gaffurabi on 2009-01-18
i've installed **wicd** and after couple of boots it is still working. maybe the problem was with network manager :s

---

### Post by ByteJuggler on 2009-01-18
> **gaffurabi said:**
> i've installed **wicd** and after couple of boots it is still working. maybe the problem was with network manager :s

Possibly, you seem to have a pretty interesting setup there... Glad at least you got it working!! :)

---

### Post by gaffurabi on 2009-01-19
well this networkmanager drove me crazy, damn it to hell!

---

### Post by infestor on 2009-08-01
wicd rlz :)

---

