---
title: "Network problems"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by Gustav Haraldsson on 2005-04-15
I just installed Ubuntu hoary 5.04-amd64 and im having some DHCP problems, im connected via my ISP with a DHCP. Works great in windows, but when i try e.g dhclient it tries to send DHCP request but without any luck (see dhclient output below). Now i can see my netcard trying to send out the DHCP request (via lights each time DHCPDISCOVER is sent). So the hardware is responding. 

dhclient output

machine@ubuntu:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/xx:xx:xx:xx:xxf:xx
Sending on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping

Ifconfig output :

machine@ubuntu:~$ /sbin/ifconfig
eth0 Link encap:Ethernet HWaddr 00:08:A1:25:9F:C7
inet6 addr: some::crazy::IPv6::address:xxx/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:59 errors:0 dropped:0 overruns:0 frame:0
TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:9015 (8.8 KiB) TX bytes:8226 (8.0 KiB)
Interrupt:17 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1033 errors:0 dropped:0 overruns:0 frame:0
TX packets:1033 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:89221 (87.1 KiB) TX bytes:89221 (87.1 KiB)

Netstat outcome

machine@ubuntu:~$ /bin/netstat -rn
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt
Iface

Dmesg gives some crazy results :

eth%d: -- ERROR --
Class : Internal Software error
Nr: 0x2bd
msg: TWSI : transfer does not exists.


Mii-tool says : SIOCGMIIPHY on 'eth0' failed: Operation not supported.

My system ran fine before on fedora Core 2

My dhclient.conf is fine.

Each time i try dhclient my dmesg shows some fun results eth0: no IPv6 router present. Could it be that IPv6 is screwing it up, that it is actually just trying to connect with IPv6 instead of IPv4 ?

I've tried basicly everything, but i think the problem lies deeper then just us user stupidity because on the boards u can find variety of simular DHCP problems.

Well i hope someone has a good solution.

With Regards,

Gustav Haraldsson

---

### Post by don bohrer on 2005-04-16
Gustav,
What jumps out at me is the subnet mask (255.255.255.255). If your machine is indeed requesting an IP and you believe your hardware is ok then I would reset the cable modem then the computer. You might also call and have your provider flush and  reset  the modem. When I was with road runner I had to  do this when I connected different computer with another mac address. I would also double check that the machine is set to dhcp and there  is no old information (ip/mask/gateway) still hanging out.   

Windows handles many network environments easily I am beginning to think most linux distros do not. Ubuntu is my first experience  with any distro other than SUSE. I'm running on an old dell  laptop pentium 500mhz. Network and the totem player are the only things  that  did not work from the start. BTW I like Ubuntu much better  than Suse.

I have my networking running perfectly, but would like to autorecognize different networks on the fly. At home I use pppoe, dhcp at work, and at favorite coffee house dhcp. On  several networks I have WEP enabled but I couldn't get connected wireless so I turned it off. Thats my next project. Run on multiple networks with WEP enabled and not have to jump through hoops to do so.

Let me know how things go.

don (el paso)

---

### Post by crane on 2005-04-16
Are you on a cable modem or DSL?
Have you tried setting using static instead of dhcp?
Also, are you behind a router or is the computer connected directly to the modem?

---

### Post by Gustav Haraldsson on 2005-04-16
Hi and thx for a fast reply,

> I would reset the cable modem then the computer. 
I'm dual booting, so i reset everytime to go to windows which has a fine connection and no problem receiving IP, so i dont really see how restarting the modem will help. But for the sake of science i'll try :)

> When I was with road runner I had to do this when I connected different computer with another mac address. 
I connect other computers to the modem with no problem :)

> Are you on a cable modem or DSL? 
Im connected to my ISP via DSL

> Have you tried setting using static instead of dhcp? 
Well my isp hands me my static IP via DHCP, that is to say i dont receive dynamic ip's from the DHCP :). Do you whant me to try to force my network card to use the IP i should be getting from my ISP? Im not sure that will work.

> Also, are you behind a router or is the computer connected directly to the modem?  Im connected directly to the modem.

Hope this helps anyone to see the errors in my ways :).

With ragrds,

Gustav

---

### Post by wherethebibawi on 2005-06-28
i see them.... ](*,)

i have an intel 8255/7/8/9 ethernet pro. 
i was reading  that the problem it seems, has somthing to do the the e100 module, in my case anyway.

[http://www.ubuntuforums.org/showthread.php?t=35857&highlight=e100](http://www.ubuntuforums.org/showthread.php?t=35857&highlight=e100)

i also tried reverting to the prior eepro100 module but ther was no change.

[http://kernaltrap.org/node/2567](http://kernaltrap.org/node/2567)

i feel that you may have this problem as well.

And for arguments sake i have had trouble with another fresh install of ubuntu on the same box with another brand card also using the e100 module. 

The difference here is that i am on a corp. LAN with an IP proxy.

---

### Post by abisko00 on 2005-07-10
Hi!
Sorry, I don't have to offer a solution. I am just another victim of this annoying problem.

At work, where I have a direct connection with static IP, internet works just fine. Even my wireless card has not problems to connect to a router. However at home on my cable connection, Ubuntu does not get connected. I see that it gets an IP from the DHCP server and a DNS server is also configured, but no application reaches the outside world. 

In network statistics I see that I receive a lot of packages, but send only a few.
The dmesg report is the same as in the initial post: "eth0: no ipv6 routers present"

I was guessing that this has to do with the DCHP capabilities of my provider's server. However I did not manage to switch-off the use of ipv6. Does anyone have an idea how I can switch to good-old ipv4? 

Whenever I try to unload the ipv6 module, I get a 'in use' message (even force doesn't help). I uncommented all ipv6 related lines in /etc/modprobe.d/aliases, but still ipv6 is used.  

BTW: I am using the 8139cp driver (Realtek).

---

### Post by abisko00 on 2005-07-16
Found my solution:

After having tried a huge number of different solutions unsuccessfully, mostly involving changes in dhcp.conf, aliases and resolv.conf, I found a solution that helped me to connect through my provider:

I exchanged dhcp-client for dhcpcd. According to the description, dhcpcd is for ipv4 only, but I don't care as long as it works.

---

### Post by horndude77 on 2005-08-07
I think I'm having a similar problem. It's weird because when I initially boot up it seems to get an IP just fine, but then when I try to do anything on the internet it just doesn't work.

Could you describe in more detail your fix. From your description I don't know how to replace dhclient with dhcpcd. I like what I'm seeing from ubuntu so far, but without the internet it's useless to me. Thanks!

-----horndude77

---

### Post by zachtib on 2005-08-21
[QUOTE=abisko00]Found my solution:

After having tried a huge number of different solutions unsuccessfully, mostly involving changes in dhcp.conf, aliases and resolv.conf, I found a solution that helped me to connect through my provider:

I exchanged dhcp-client for dhcpcd. According to the description, dhcpcd is for ipv4 only, but I don't care as long as it works.[/QUOTE]
 how did you do this? I tried to remove dhcp3-client but it wanted to remove ubuntu-base also

---

### Post by TeleTommy on 2005-08-22
I have the same problem. But configuring manually doesn't work too.
How can I get rid of this IP6 stuff at all?

---

### Post by Motomouse on 2005-09-21
I commented the Ip 6 lines in /etc/hosts. Until now this solved my dhcp and loosing connection to the router problems

```
127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
# ::1 ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts
```

# In other words: 
# The preceding lines are undesirable for me and quite a few other people  ;-)

---

