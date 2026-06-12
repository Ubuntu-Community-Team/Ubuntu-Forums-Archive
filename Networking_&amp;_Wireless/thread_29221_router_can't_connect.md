---
title: "router can't connect"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by weekend warrior on 2005-04-23
Hello I'm new at this and need some help.  I have a fresh Hoary install and a Speedtouch 510 adsl router and can't connect to the internet. I'll describe the steps I did since this is my first router and maybe I did something wrong.

1. configured network card to 10.0.0.1, 255.0.0.0. etc  
2. sudo opened firefox, got the router setup page and uploaded the config file from my isp, Wanadoo.  (this is when the @ net symbol goes from green to amber.)
3. reset to DHCP, got the setup page back and confirmed the new config, PPoA 8/35 VC-MUX etc 
4. go to connect, enter my username/password, click connect and.... nothing  :( 

Have I missed something?

The @ light flashes green/amber and it doesn't connect. Link says "connected" but state is "down". I tried entering DNS numbers in networking but still nothing.  

Updating the firmware (currently 4.0.2.0.0) would probably help because it's supposed to have "easy setup" templates but I don't know where to get the updates/templates or how to go about upgrading. The speedtouch site doesn't offer much that I can see, [http://www.speedtouch.com/prod510.htm](http://www.speedtouch.com/prod510.htm)

Thanks in advance for helping (this looks like a great community! :) )  and just let me know what outputs you need to see.

---

### Post by ifrflyer on 2005-04-23
Hi,
Not sure if I can help, but perhaps get the thread going. 

First, can you ping the router? 

If not, can you ping localhost/127.0.0.1?

---

### Post by weekend warrior on 2005-04-23
ping 192.168.0.1 
no, network is unreachable

ping localhost  
yes

Sorry if it takes me a while to get back on here, I'm not a dual booter so I have to go back and forth from a winblows box to ubuntu and at the moment I only have one working monitor, bit of a pain *sigh* I hope to get this router working soon!

---

### Post by heimo on 2005-04-23
[QUOTE=weekend warrior]ping 192.168.0.1 
no, network is unreachable
[/QUOTE]

Is that the ip address for your router (lan side)? Then you should have ip address from the same subnet, not 10.0.0.1 as you say in first post. Probably you should be using DHCP and not entering static ip address at all.

Helpful outputs would be
 ```
ifconfig
cat /etc/network/interfaces
route -n

```

---

### Post by weekend warrior on 2005-04-23
In step 3 in my first post I switched to DHCP and it still is that way. When I reset the card to DHCP it gave me the router IP address as 192.168.0.1 and that's how I was able to reach the router setup page when I configured. Now I can't. 

I've been reading through the forum and I wonder if this is what happened. [http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

I found that through this thread which also sounds familiar. [http://ubuntuforums.org/showthread.php?t=23673](http://ubuntuforums.org/showthread.php?t=23673)

but I'm just grabbing at straws, this is new territory for  me.


Here are the outputs


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:40:F4:C0:ED:08
          inet6 addr: fe80::240:f4ff:fec0:ed08/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:6534 (6.3 KiB)
          Interrupt:5 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:167564 (163.6 KiB)  TX bytes:167564 (163.6 KiB)


route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

---

### Post by ifrflyer on 2005-04-23
Hi,
Not sure if I can help, but perhaps get the thread going. 

First, can you ping the router? 

If not, can you ping localhost/127.0.0.1?

---

### Post by ifrflyer on 2005-04-23
Just to be sure before we all go further. since eth0 seems to be xmitting but not receiving, have you confirmed the cable works and restarted the router? Sounds stupid but it's been a factor before.  

Is the subnet set correctly?

Sorry to be pedantic but often these kinds of things are the problem!

---

### Post by heimo on 2005-04-23
Couple things I'd try. Try running the dhcp request on terminal:
[i]sudo dhclient
[/i]
And simultaniously run *tail -f /var/log/messages* to see if there are errors.

If that doesn't help, change interfaces file to use static ip (hopefully that one is free?):
 ```
iface eth0 inet static
	   address			    192.168.0.100
	   broadcast			 192.168.0.255
	   netmask			    255.255.255.0
	   gateway			    192.168.0.1

``` 

And bring up the interface:
[i]ifup eth0
[/i]
Now you should see configured intercafe: *ifconfig eth0*

Restart networking
[i]sudo /etc/init.d/networking restart
[/i]

---

### Post by notzac on 2005-04-24
A few questions:

1) What is the IP address and netmask of the router itself? In Australia, the Speedtouch 510's that i've seen are 10.0.0.138/8, but yours might be different.
2) Have you tried configuring your ethernet card in Ubuntu for DHCP? Setting a static IP address on your ethernet card (especially if it's in the wrong subnet) won't achieve much. ;)

Also, if the router is doing as you say, i.e., "The @ light flashes green/amber and it doesn't connect. Link says "connected" but state is "down"." -- this usually means that you've misconfigured the router. Have you double checked your username and password? Does Wanadoo require a username in the format of user@realm, and have you put that in?

---

### Post by weekend warrior on 2005-04-24
Ok, I'll take these one at a time, btw thanks for the ideas and pedantic is fine, I'd almost rather it be something stupid than something major.  

First cables, the phone line and jack are the same I'm using now in windoze. The ethernet cable is new out of the router box but just  the same I got another yesterday (can't hurt to have a spare) and I have green LEDs on both ends.

Username and password I spent some time with because that's exactly what I thought when the @ LED was flashing green/amber. My ISP documentation says username@wanadooadsl so I entered that, then tried just my username@their regular domain name, then just my username and so on through different variations. The password I checked by going to the customer service page which requires your password and it's correct. 

But the problem is no longer that I can't get on the net, but that I can't access the  router setup page. Connections are refused, so I can't even enter my username and password anymore anyway. 

I think I need to clarify this more since it's the second time it's come up. The network card **is** currently set to DHCP. The router factory settings are IP =  10.0.0.1, subred =  255.0.0.0, gateway = 10.0.0.138 so first thing I did was set the card to those static ip values to get to the router setup page and upload the ISP config file. That's when I lose contact with the router and the @ goes amber. In fact, the page doesn't completely reload, it just says "upload result" then blank. Along the top it says something like "do you want to keep this config or restore defaults", but there's no way to confirm yes or no, just a "save all" up top left which I'm supposed to click after "connect" and (I'm assuming) state is "up". So the connection with router is gone at this point. 

Now this is when I change the network card to dynamic host, DHCP. Then I can connect with the router again at 192.168.0.1 and this is what I can't do anymore. The router is no longer at this address. Heh, the @ light is green now though  ](*,)  

Dhclient didn't work, here's the output, no errors in the message log

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:40:f4:c0:ed:08
Sending on   LPF/eth0/00:40:f4:c0:ed:08
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I didn't follow too well the second part on the static ips, that gave me the same dhcpdiscover routine  :?

---

### Post by weekend warrior on 2005-04-24
I've factory reset a couple times now and I'm going to try it again but just to be sure, what do I need to change systemwise when I reset the router to the factory default to give me a clean slate again?

---

### Post by weekend warrior on 2005-04-24
Back again, hey please ignore that part about not being able to connect to the router on 192.168.0.1 Yes I can. The last time I reset the router to factory settings and did the configuration I didn't save it correctly.  :oops: Sorry about that, I'm getting tired and a little frustrated. This time I saved it right, but I'm back to where I was at the start. I get to the last connect step, save the configuration and @ is flashing green/amber. *sigh*

---

### Post by weekend warrior on 2005-04-24
Heh, even the "oops" smiley didn't work *screams*  ](*,)

---

### Post by ifrflyer on 2005-04-24
Righto. This is actually encouraging. 

Just to confirm, when you say "connect" : are you able to surf into the router using a web browser and make the router/ISP configurations via that method? If you are, our work is done here: contact the folks at wanadoo and ask them what they're expecting in terms of login.

---

### Post by crazybill on 2005-04-24
I didn't read other replies... but if your gateway is 192.168.0.1 and you don't have a huge network.
Configure your compuer to 192.168.0.2 (not 10.0.0.1 as you stated that you did) and submask both gateway router and computer with 255.255.255.0 (not 255.0.0.0 as stated). Make sure your gateway so states 192.168.0.1

---

### Post by weekend warrior on 2005-04-25
Well I contacted Wanadoo and for the moment they only told me what I already knew, the username and password are correct. They said they'll get back to me.

So yes, to confirm I am able to surf to the router using a web browser to do the configurations but no, I'm not able to make any outside connection at all.

---

### Post by weekend warrior on 2005-04-25
The internet connection goes down as soon as I upload the wanadoo.ini so I'm  posting the contents here. It should also clear up the confusion that's come up several times now. My card is NOT set to 10.0.0.1 or 255.0.0.0, those are only the router presets. The card is currently set to DHCP and these values.

[ env.ini ]
set var="CONF_REGION" value="Wanadoo España"
set var="CONF_PROVIDER" value="PPPoA VCMUX 8/35"
set var="CONF_DESCRIPTION" value="Seleccione el tipo de encapsulamiento indicado en la carta que le hemos enviado. Deberá introducir el nombre de usuario y contraseña proporcionados por Wanadoo."
set var="CONF_SERVICE" value="Multipuesto con DHCP"
set var="CONF_DATE" value="29 Aug 2003"
set var="CONF_VERSION" value="05"
set var="HOST_SETUP" value="auto shortcut"
set var="DSL_ADDR" value="8*35"
set var="HOST_IP_ADDR" value="<dhcp>"
set var="HOST_NET_MASK" value="<dhcp>"
set var="HOST_GATEWAY" value="<dhcp>"
set var="HOST_DNS" value="<dhcp>"
set var="ST_LAN_IP_ADDR" value="192.168.0.1"
set var="ST_LAN_NET_MASK" value="255.255.255.0"

[ phone.ini ]
add name="pppoa" addr=8*35 type=pppoa

[ qos.ini ]
add name="default" class=ubr

[ oam.ini ]
config clp=1

[ bridge.ini ]
config age=300

[ pptp.ini ]

[ dhcp.ini ]
config autodhcp=off scantime=20 spoofing=off trace=off
policy verifyfirst=off trustclient=on
spoof failtime=4 errorlt=60 dodlt=10
pool add name="LAN_private"
pool config name=LAN_private poolstart=192.168.0.128 poolend=192.168.0.254 netmask=24 leasetime=86400
start

[ mer.ini ]

[ ipoa.ini ]

[ ppp.ini ]
ifadd intf="pppoa"
rtadd intf=pppoa dst=0.0.0.0/0 src=192.168.0.0/1 metric=1
ifconfig intf=pppoa dest=pppoa proto=pppoa accomp=on addrtrans=pat

[ cip.ini ]

[ pfilter.ini ]

[ pfirewall.ini ]
chain create chain="gestion"
rule create chain=gestion index=0 srcintfgrp=wan prot=udp dstport=dns action=accept
rule create chain=gestion index=1 srcintfgrp=wan prot=icmp action=accept
rule create chain=gestion index=2 srcintfgrp=wan action=deny
assign  hook=sink chain="gestion"

[ ip.ini ]
config forwarding=on firewalling=on redirects=on sourcerouting=off netbroadcasts=off ttl=64 fraglimit=64 defragmode=nat addrcheck=static mssclamping=on
apadd addr=192.168.0.1/24 intf=eth0 addroute=no
ifconfig intf=loop mtu=1500 group=local
ifconfig intf=eth0 mtu=1500 group=lan
ifconfig intf=pppoa mtu=1500 status=down group=wan
rtadd dst=0.0.0.0/0 intf=pppoa metric=1
rtadd dst=224.0.0.0/4 intf=eth0
rtadd dst=192.168.0.0/24 gateway=192.168.0.1
rtadd dst=255.255.255.255/32 gateway=192.168.0.1
rtadd dst=192.168.0.0/24 src=192.168.0.0/24 gateway=192.168.0.1

[ autoip.ini ]
ifadd intf=eth0
ifconfig intf=eth0 addr=169.254.122.26 poolstart=169.254.1.1 poolend=169.254.254.254 netmask=16
ifattach intf=eth0

[ eth.ini ]
ifconfig intf= type=

[ dnsd.ini ]
domain domain="lan"
add hostname="SpeedTouch"
start
troff

[ dhcc.ini ]
config trace=off

[ adslpots.ini ]
config opermode=multimode maxbitspertoneUS=13

[ upnp.ini ]
config maxage=1800

[ nat.ini ]
bind application=RAUDIO(PNA) port=realaudio
bind application=IRC port=irc-u
bind application=RTSP port=rtsp
bind application=FTP port=ftp
bind application=H323 port=h323

[ system.ini ]
config upnp=enabled mdap=enabled dcache=enabled

[ endofarch ]

---

### Post by weekend warrior on 2005-04-25
Here is the info from the router when I'm trying to connect.


Detailed Connections Info			   
 
Point-to-Point Protocol (PPP)	   
	   
pppoa: dest : pppoa
    Retry : 10  QoS default  encaps VC-MUX
    mode = IP routing
    flags = echo magic accomp restart mru addr route savepwd PPPOA
    trans addr = pat    mru = 1500
    route =    192.168.0.128/1 -          0.0.0.0/0 (metric 1)
    user name = ******@wanadooadsl   password = ******
    admin state = up    oper state = down    link state = connected
    LCP : state = reqsent  retransm = 9  term. reason = 
    IPCP: state = initial  retransm = 0  term. reason =

---

### Post by heimo on 2005-04-25
If your DHCP (dhclient) fails and router is not providing DHCP or DHCP relay, your network interface won't get network settings and your connection won't work. Or am I still missing something here?

When you connect the router to do configuration, are you still using the 10.0.0.1 address?

To me it looks like your routers DHCP is not enabled, but without knowledge of this configuration file format / router model, I'm a bit uncertain:

```

[ dhcp.ini ]
config autodhcp=**off** scantime=20 spoofing=off trace=off
policy verifyfirst=off trustclient=on
spoof failtime=4 errorlt=60 dodlt=10
pool add name="LAN_private"
pool config name=LAN_private poolstart=192.168.0.128 poolend=192.168.0.254 netmask=24 leasetime=86400
start

```

---

### Post by weekend warrior on 2005-04-25
I'm using 192.168.0.1 to communicate with the router, not 10.0.0.1
In the newtorking window I can see the card activated under DHCP. What can I post for you to verify if the router's DHCP is active or not?

---

### Post by weekend warrior on 2005-04-25
The datasheet for the Speedtouch 510 router

[http://www.speedtouch.com/pdf/datasheet510.pdf](http://www.speedtouch.com/pdf/datasheet510.pdf)


The user's guide

[http://www.speedtouch.co.uk/downloads/500/427/User%27s%20Guide_en.pdf](http://www.speedtouch.co.uk/downloads/500/427/User%27s%20Guide_en.pdf)

---

### Post by weekend warrior on 2005-04-25
Would it be worth trying to just upload the ini file again but changed to config autodhcp=on or better to go through the whole process again starting with a factory settings reset?

---

### Post by heimo on 2005-04-25
That's what I'd try (turning DHCP on), but sometimes my ideas are not good. :) However intuition says that that's the problem.

I haven't looked at those PDFs yet, but I will.

---

### Post by heimo on 2005-04-25
This is a bit generic answer, sorry for renduncancies with earlier posts.

Ok, I had a quick a look at the manual. Can you find the settings page on router webinterface that looks like the one on manual page 54 (pdf page 56)? The status information may be relevant.

-----------
Lecture of DHCP in ADSL routers begins

To clarify what for DHCP is used in these kind of routers (sorry if this is already clear to you, this maybe helpful for someone else reading this forum) - most ADSL boxes have DHCP client, DHCP server and DHCP relay. DHCP is used to deliver all kind of network settings for clients. Router can fetch it's configuration from ISP (internet service provider) DHCP server, it can configure local clients by providing its own DHCP server or it can relay the clients DHCP requests to ISPs DHCP server.

Pool is the range of ip addresses that can be asssigned to clients. Many times ADSL routers are used with NAT switched on - local clients will have network address from a reserved range of addresses, typically like 192.168.x.x 

DHCP router will have it's own IP address and that'll be the adress that outside world sees. In the local area network, DHCP / dynamic or static configuring can be used. Fpr DHCP to work, router must be configured to lease IP adresses - in other words, run DHCP server - or to relay DHCP requests from client to ISP.
----------------


To my understanding, you are going to use NAT and routers DHCP server, but you should as well be able to pick some valid IP from same subnet as your routers lan side interface, set other network settings (subnet mask, dns and default gateway) and be ready - if the routers connection is ok.

As you CAN connect to the router via webinterface, your local settings seem fine, but either ADSL is not connected or you're lacking some settings.

ifconfig should tell you your current ip and subnet mask, route -n tells you your default gateway. If DHCP is enabled in /etc/network/interfaces, you should be able to run dhclient - if you get no responses, DHCP server is not up. If you get settings via DHCP, you can try to ping your DNS servers (with ip), check /etc/resolv.conf


 >  Dhclient didn't work, here's the output, no errors in the message log 

Is it working now?

---

### Post by weekend warrior on 2005-04-25
I really appreciate you helping me out heimo  :)  It would be very difficult to go through this over the phone with customer service and who knows when they'll even call me. 

I took screenshots of all the router setup screens and put them in a gallery so you can see what I see. 
[http://img52.imageshack.us/gal.php?g=p1011348r0hw.jpg&cols=4](http://img52.imageshack.us/gal.php?g=p1011348r0hw.jpg&cols=4)

Yes, you're right there is a lot of missing information. I'll need help putting it all in.

---

### Post by weekend warrior on 2005-04-25
Here is what  my ifconfig looks like now

sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:40:F4:C0:ED:08
          inet addr:192.168.0.128  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fec0:ed08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:385063 (376.0 KiB)  TX bytes:169768 (165.7 KiB)
          Interrupt:5 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:857139 (837.0 KiB)  TX bytes:857139 (837.0 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by weekend warrior on 2005-04-25
and

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by weekend warrior on 2005-04-25
Yes, the dhclient is better now than before.

sudo dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:40:f4:c0:ed:08
Sending on   LPF/eth0/00:40:f4:c0:ed:08
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 3
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.128 -- renewal in 41054 seconds.

---

### Post by weekend warrior on 2005-04-25
Oh! and I almost forgot to mention, changing the wanadoo.ini file didn't help. But it seems like there's something in that file the router doesn't like. All lights are green right up to the point where I upload the file. The the @ light goes amber and stays that way. It's even amber when Ubuntu isn't even up and running yet.

---

### Post by heimo on 2005-04-25
Yes. Looks like that now your computer gets it's network settings from your router. I don't know if that ini file is so important to get uploaded to the router. It should probably be possible to enter relevant information through webinterface, or am I missing something?

Try to configure the DHCP client on the router. It should try to get it's settings from ISP. That's what I read from the ini. (<dhcp>)

Sorry for short answer - I must go sleep now. :) It's past midnight.

---

### Post by weekend warrior on 2005-04-26
Ok so I need to do the whole thing manually, sounds like fun. So where do I start? From the top right? I've reset the router to the default and set the nic to unconfigured in the network settings window. What other things do I need to reset to start from zero?

---

### Post by weekend warrior on 2005-04-26
When I look at the DHCP client setting I have to input things like the client ID, host name and lease time and need to tick or untick the NAT/PAT address translation box. Where am I going to be looking for this information? Is it in the .ini file or can I get these values elsewhere. I don't want to be entering the same info as the .ini file and cut the internet connection the same way uploading that config file did obviously.

---

### Post by heimo on 2005-04-26
I welcome all the other thread readers to post their ideas... This is a bit too much guessing of what's wrong.
 
But this line:
```
 ifconfig intf=pppoa mtu=1500 status=**down** group=wan
``` 
.. looks a bit suspicious. Maybe it's not important, maybe it needs to be this way, or maybe it's wrong.
 
DHCP client configuration you described sounds odd. It looks like it's not what I thought it was. Sometimes these interfaces are very confusing. DHCP client is something that fetches settings from DHCP server and you shouldn't need to define hostname or lease time for you client. That's servers responsibility.
>  
When I look at the DHCP client setting I have to input things like the client ID, host name and lease time and need to tick or untick the NAT/PAT address translation box. Where am I going to be looking for this information? Is it in the .ini file or can I get these values elsewhere. I don't want to be entering the same info as the .ini file and cut the internet connection the same way uploading that config file did obviously.
 
 
You probably want to use NAT (Network Address Translation), but if you want your computer to have public IP (from your ISPs DHCP server), you probably don't want to set up NAT. I'd choose enabling NAT unless you have reason not to.
 
Something that I'd try if I'd suspect that the configuration file you're uploading is flawed, would be to leave out some sections. I don't know what your router will like about it, but it'd give you some information. You could try uploading something minimal.
 
```
 
[ env.ini ]
set var="CONF_REGION" value="Wanadoo"
set var="CONF_PROVIDER" value="PPPoA VCMUX 8/35"
set var="CONF_DESCRIPTION" value=""
set var="CONF_SERVICE" value="Multipuesto con DHCP"
set var="CONF_DATE" value="29 Aug 2003"
set var="CONF_VERSION" value="05"
set var="HOST_SETUP" value="auto shortcut"
set var="DSL_ADDR" value="8*35"
set var="HOST_IP_ADDR" value="<dhcp>"
set var="HOST_NET_MASK" value="<dhcp>"
set var="HOST_GATEWAY" value="<dhcp>"
set var="HOST_DNS" value="<dhcp>"
set var="ST_LAN_IP_ADDR" value="192.168.0.1"
set var="ST_LAN_NET_MASK" value="255.255.255.0"
 
[ phone.ini ]
add name="pppoa" addr=8*35 type=pppoa
 
[ qos.ini ]
add name="default" class=ubr
 
[ oam.ini ]
config clp=1
 
[ bridge.ini ]
config age=300
 
[ pptp.ini ]
 
[ dhcp.ini ]
config autodhcp=on scantime=20 spoofing=off trace=off
policy verifyfirst=off trustclient=on
spoof failtime=4 errorlt=60 dodlt=10
pool add name="LAN_private"
pool config name=LAN_private poolstart=192.168.0.128 poolend=192.168.0.254 netmask=24 leasetime=86400
start
 
[ mer.ini ]
 
[ ipoa.ini ]
 
[ ppp.ini ]
ifadd intf="pppoa"
rtadd intf=pppoa dst=0.0.0.0/0 src=192.168.0.0/1 metric=1
ifconfig intf=pppoa dest=pppoa proto=pppoa accomp=on addrtrans=pat
 
[ cip.ini ]
 
[ pfilter.ini ]
 
[ pfirewall.ini ]
 
[ ip.ini ]
config forwarding=on firewalling=off redirects=on sourcerouting=off netbroadcasts=off ttl=64 fraglimit=64 defragmode=nat addrcheck=static mssclamping=on
apadd addr=192.168.0.1/24 intf=eth0 addroute=no
ifconfig intf=loop mtu=1500 group=local
ifconfig intf=eth0 mtu=1500 group=lan
ifconfig intf=pppoa mtu=1500 status=down group=wan
rtadd dst=0.0.0.0/0 intf=pppoa metric=1
rtadd dst=224.0.0.0/4 intf=eth0
rtadd dst=192.168.0.0/24 gateway=192.168.0.1
rtadd dst=255.255.255.255/32 gateway=192.168.0.1
rtadd dst=192.168.0.0/24 src=192.168.0.0/24 gateway=192.168.0.1
 
[ autoip.ini ]
ifadd intf=eth0
ifconfig intf=eth0 addr=169.254.122.26 poolstart=169.254.1.1 poolend=169.254.254.254 netmask=16
ifattach intf=eth0
 
[ eth.ini ]
 
[ dnsd.ini ]
domain domain="lan"
add hostname="SpeedTouch"
start
troff
 
[ dhcc.ini ]
 
[ adslpots.ini ]
config opermode=multimode maxbitspertoneUS=13
 
[ upnp.ini ]
 
[ nat.ini ]
 
[ system.ini ]
config upnp=enabled mdap=enabled dcache=enabled
 
[ endofarch ]

``` 
 
eth.ini section on original looks suspicious. I think it should contain the configuration for the routers lan side interface (eth0) and in the original, it contains couple keywords, but no values. I think it should configure the eth0 to 192.168.0.1/255.255.255.0, but for now, I don't know how to do it.
 
Hmm. Can you provide link to the place you got this ini? ISPs website?
 
](*,) I tried to print the whole usermanual so that I could read it "on road", but all I got was the pictures, text was missing.
 
EDIT: I did all kind of editing on the config file abowe - disabled firewall and stuff like that.
 
Here's another one.
```
 
[ env.ini ]
set var="CONF_REGION" value="Wanadoo"
set var="CONF_PROVIDER" value="PPPoA"
set var="CONF_DESCRIPTION" value="heimo was here"
set var="CONF_SERVICE" value="Multipuesto con DHCP"
set var="CONF_DATE" value="29 Aug 2003"
set var="CONF_VERSION" value="05"
set var="HOST_SETUP" value="auto shortcut"
set var="DSL_ADDR" value="8*35"
set var="HOST_IP_ADDR" value="<dhcp>"
set var="HOST_NET_MASK" value="<dhcp>"
set var="HOST_GATEWAY" value="<dhcp>"
set var="HOST_DNS" value="<dhcp>"
set var="ST_LAN_IP_ADDR" value="192.168.0.1"
set var="ST_LAN_NET_MASK" value="255.255.255.0"

[ phone.ini ]
add name="pppoa" addr="8*35" type=pppoa

[ dhcp.ini ]
config autodhcp=off scantime=20 spoofing=off trace=off
policy verifyfirst=off trustclient=on
spoof failtime=4 errorlt=60 dodlt=10
pool add name="LAN_private"
pool config name=LAN_private poolstart=192.168.0.128 poolend=192.168.0.254 netmask=24 leasetime=86400
start

[ ppp.ini ]
ifadd intf="pppoa"
rtadd intf=pppoa dst=0.0.0.0/0 src=192.168.0.0/1 metric=1
ifconfig intf=pppoa dest=pppoa proto=pppoa accomp=on addrtrans=pat


[ ip.ini ]
config forwarding=on firewalling=off redirects=on sourcerouting=off netbroadcasts=off ttl=64 fraglimit=64 defragmode=nat addrcheck=static mssclamping=on
apadd addr=192.168.0.1/24 intf=eth0 addroute=no
ifconfig intf=loop mtu=1500 group=local
ifconfig intf=eth0 mtu=1500 group=lan
ifconfig intf=pppoa mtu=1500 status=down group=wan
rtadd dst=0.0.0.0/0 intf=pppoa metric=1
rtadd dst=224.0.0.0/4 intf=eth0
rtadd dst=192.168.0.0/24 gateway=192.168.0.1
rtadd dst=255.255.255.255/32 gateway=192.168.0.1
rtadd dst=192.168.0.0/24 src=192.168.0.0/24 gateway=192.168.0.1
[ endofarch ]
``` 
 
;) Did you notice I'm trying to get my name on history books? (or at least one router) Those region, description, provider fields probably have no functional meaning.

---

### Post by weekend warrior on 2005-04-26
Thanks for staying with me on this heimo. I'm hoping someone else who had this problem, has this type router or similar or is just a natural linux genius ;-)  will see this and help! This is all a bit confusing for me just starting out. I got this router specifically because it's the one Wanadoo (France Telecom) offers in their adsl package and hoped it would be easy! So much for that! :-x  The .ini file comes right from their setup cd out of the box so I don't understand how it could be all wrong, but yes the two lines with autoDHCP=off and state=down look suspicious. I can try again changing the file and see what happens.

But I found this site that has me worried. [http://www.xs4all.nl/~eeuwen/speedtouch_510.htm](http://www.xs4all.nl/~eeuwen/speedtouch_510.htm)

especially this paragraph:

"All very nice and well it seemed until I found out that my Apache web server on my main computer and also my web cam server could not be 'seen' any more from the internet. At first I suspected that the Sweex 4 port broadband router with printer server was the culprit or rather poor programming capabilities. After disconnecting the router I found that the SpeedTouch 510 was blocking all access to the servers, because of the built in NAT, DHCP and firewall. So what now? Searching the internet did not bring any solutions,  except for Linux OS,  only sites where others appeared to be stuck with the same problem...."

---

### Post by weekend warrior on 2005-04-26
I just saw your edits, they look good. The firewall might be the key considering that quote I found. I'll give these a try later on tonight. I'll also take some screenshots of the manual DHCP config screens too. 

Let's see if your name goes down in history!  :smile:

---

### Post by heimo on 2005-04-26
Link to that page is great. Thank you. Those other ini files for same device may give valuable hints. I have to take a look on those.
 
I think the problem you quoted is not relevant to your situation. NAT can cause things like that, but you probably can disable NAT if neccessary. Shouldn't prevent normal internet use.
 
I'll get back to this later.

---

### Post by weekend warrior on 2005-04-26
I'll try to find more online that might be helpful. It's good though that the part I quoted shouldn't be a problem. 

Here's a site (in Dutch) with the 510 and linux setup. [http://www.xs4all.nl/helpdesk/abonnement/adsl/thomson/ethernet/linux.html](http://www.xs4all.nl/helpdesk/abonnement/adsl/thomson/ethernet/linux.html)

I don't know if it's helpful, it's very short but the numbers look similar. There are two interesting things in the screenshots. In the diagnostic shot, their DSL isn't ticked, mine was. In the configuration upgrade shot, the upload results loads completely, mine didn't. The last one is probably nothing but my DSL being ticked might be something.

---

### Post by weekend warrior on 2005-04-26
This site (in Spanish) [http://www.adslayuda.com/PNphpBB2+file-viewtopic-t-39046.html](http://www.adslayuda.com/PNphpBB2+file-viewtopic-t-39046.html) 
I understand and she's trying to use the same router with the same service I have, Wanadoo Naveghable with windoze.

But the link they gave her for the .ini file looks the same as mine.
[http://usuarios.lycos.es/imagesandwords/i510/user.ini](http://usuarios.lycos.es/imagesandwords/i510/user.ini)

I'm going to register on that site, there's a section just for the 510 router but it looks like all winblows. There is a another small linux section though.

---

### Post by heimo on 2005-04-26
The sequence of screenshots of uploading config was good. And that it hangs is a clue. When you changed the DHCP setting, did you use upload or did you change it via webinterface?

I can't understand this:
[http://www.bandaancha.st/foros.php?temid=156265]("http://www.bandaancha.st/foros.php?temid=156265")

But in the reply the configfile is otherwise identical to yours, except there are no <dhcp> values. 

We should probably believe that the ini file is actually ok, but if you want to try... I'd probably guess:

 ```
[ eth.ini ]
ifconfig intf=eth0 type=auto

``` 

I saw something like this in someone else's ini:
```
[ eth.ini ]
ifconfig intf=0 type=auto

``` 
but it doesn't look good to me. intf refers to interface.


:!: Check this: [http://www.wlug.org.nz/SpeedTouch510]("http://www.wlug.org.nz/SpeedTouch510")

---

### Post by weekend warrior on 2005-04-26
> He leido los post del tema "Abrir puertos Alcatel Speed Touch 510 ADSL RDSI". Ya hay 76. Quizas se deberia abrir un foro dedicado a este router.

No soy ningun experto pero me he "peleado" con dos de ellos, ambos multipuesto, uno con ip estatica y otro dinamica. Con el de ip dinamica no he logrado lo que queria pero con el de ip estatica si he abierto puertos.

Entrando via web hay una opcion de Upgrade y Backup desde donde podemos salvar el archivo de configuracion user.ini en el PC. Aqui podemos verlo y tocarlo.

Con respecto a NAT, decir que outside address para la configuracion con ip estatica y multipuesto corresponde a la ip publica de nuestro router. Para ip dinamica es 0.0.0.0 pues esta cambiara segun los caprichos de telefonica.

Como veis en mi user.ini no ha hecho falta tocar los filtros ni firewall que pone telefonica-quien sabe para que los pone, jejeje-: 
Good you found this cause I think it explains something. But I'm not sure because I don't know enough about routers. I'll translate.

> I've read the posts about "To open ports Alcatel SpeedTouch 510 ADSL RDSI". There are already 76. Maybe I should open a forum dedicated to this router. 

I'm not an expert but a have "fought" with two of them, both multipuesto, one with a fixed ip and the other dynamic. With the dynamic ip I didn't acheive what I wanted but with the fixed ip I did open ports. 

Entering via web there is an option for Upgrade and Backup from where we can save the config file user.ini to the PC. Here we can see it and change it.

With regards to NAT, we can say that outside address for the fixed ip configuration and multipuesto correspond to the public ip of our router. For the dynamic ip it's 0.0.0.0 as this changes according to the whims of Telefonica.

As you see in my user.ini it wasn't necessary to touch the firewall filters that Telefonica put in-who knows for what put them in, hehehe-: 
Well, that second part about the fixed and dynamic ips got me thinking. Isn't this the problem? a fixed ip? In fact, now that I look at the Wanadoo box the router came in, it says on the front "sign-up + router + fixed ip + 2 months free". 

So here's my question Is it necessary to have a fixed ip for this to work? Because in the setup directions from the ISP I've been following, it never mentions anything about putting in  **my** ip or **my**  pre-determined gateway, just 10.0.0.1 and 192.168.0.1 but that's not what I have entered under Bimbos XP. I don't have my modem set to get an ip automatically.

I could be having a dumb moment here or maybe I've been having one all along! Shouldn't I be using **my** TCP/IP settings from EX PEE somewhere?

(hehe, can you tell I really don't like M$?  :wink: )

---

### Post by weekend warrior on 2005-04-26
Oh and the config files you modified (thanks for doing that btw) didn't upload at all. I got an "ERROR: truncated file" message.

That site you found from New Zealand is starting to sound more and more correct.

"Speed Touch 510

SPAWN OF SATAN  :twisted: 

Evil, EVIL, config..."    

I don't know, I think if it's not because of the fixed/dynamic ip thing then maybe I'd be better off getting something else to connect to the web with. The router was only 27€ so it's not a big loss. 4 days is enough time wasted. 

I can get something else, any suggestions? My experience with routers hasn't been so good. But I don't really need one anyway. A modem that lots of ubuntu people have used successfully with linux drivers and good step by step documentation or even better with install routines ready made is fine by me. It'll be easier than this!

---

### Post by heimo on 2005-04-27
I'm confused. Yes, if you have been assigned, or if you should sign up (/subscribe) to get fixed (static) ip, it's most probable that your ISP is not using DHCP to do configuration and... That would cause everything to fail. You need to check these from your ISP.

ADSL router with decent webinterface (which doesn't require IE to run), should be fine - but I've read that some people have had (besides you) problems with very cheap routers. Well - I think those should be avoided for any environment.

As you are connecting with network card (ethernet) to ADSL - and this is what you want to do - you don't need drivers for Linux (for you ADSL). You only need working ethernet card and a ADSL router that is easy to set up - preferrably one that has good track record with your ISP (and good instructions to do it).

I don't see this as a Ubuntu or Linux issue. I've used probably 3 or 4 different ADSL boxes in my Linux environments, with only minor problems. Well, one major problem as the box died, but that was a clear hardware failure. Some problems with bad cables too (I shouldn't do my own cables, I guess...)

The box that died was Zyxel. I was very pleased to that device as long at it was working. Actually it was "bridge-only" device - not a router, but you can buy Zyxel routers too. The manufacturer I'd actually like to promote is Linksys. You should probably listen to your ISP (and maybe change ISP...) and not to go with their cheapest option. No need to spend fortune on these devices to get them work, but a very good reason to avoid the... evil ones.

If I were you, I would have given up long time ago. Four days fighting... Oh no. I use lots of time to help other people to fix their computer related problems, but I don't really enjoy fighting with crappy devices. Oh, and I'd avoid all the ISPs that use PPPoA/E or website logons to use internet connection. Those can cause pain. Logon sessions die - authentication can fail, passwords can change. For me: plug cable, let the devices do handshaking, autonegotiating good values. That's how smooth it can be.

EDIT: If you have choice of different ISPs, check if they use bridging or routing technology. Bridges are much simpler and easier to set up and if the ISP also uses DHCP, your computer will get network settings straight from the ISP (no DHCP relay needed). That's how my current connection is set up and it's, very, very easy.

I don't often give up or give this kind of advice, but if I were you, I'd take some gasoline, ADSL-box and an axe with me, go outside - show some axe to that plastic box and burn the remains. :D

---

### Post by heimo on 2005-04-27
Uh wait! Hold the axe. Is the firmware of that device upgradable? Check the manufacturers website for firmware upgrades (probably in support / downloads).

---

### Post by weekend warrior on 2005-04-27
I now have the latest firmware!  :)  I got it from that site I registered at yesterday.
[http://www.adslayuda.com/PNphpBB2+file-viewtopic-t-35614.html](http://www.adslayuda.com/PNphpBB2+file-viewtopic-t-35614.html)

This is what I got: Firmware 4.2.10.0.0 and inside the zip there's 42A.BIN and aq42A0es.lng (Spanish language file) 
So what do I do with this bin file?

I also got the template for "dynamic IP PPPoA Vcmux multipuesto" I was looking for like I said in my very first post. I think this will make things a lot easier. It's hard to believe they wouldn't be using DHCP if their own config file has DHCP everywhere. It doesn't make sense. But my current TCP/IP settings don't either. I haven't heard back from customer service, heh, could be tomorrow or two weeks from now. IMHO a forum like this is a much better place to sort something like this. 

I do agree though that this doesn't look directly related to ubuntu or linux but indirectly it is because linux needs to keep finding ways to cope in a M$ dominated world (for now). I blame Bill Gates! :-P  This should be required reading. 
[http://www.euronet.nl/users/frankvw/rants/microsoft/IhateMS.html](http://www.euronet.nl/users/frankvw/rants/microsoft/IhateMS.html)

So there's hope? I think I'm like you, I don't like to give up  ](*,)  ;-)   *especially* after spending time on it.

---

### Post by weekend warrior on 2005-04-27
That said, I think I'll start looking around for a Linksys router, just in case  :wink:
Which models should I look for?

---

### Post by weekend warrior on 2005-04-27
And *maybe* a different ISP too. These are my choices.
[http://www.adslayuda.com/Generico+file-datosdeconexion.html](http://www.adslayuda.com/Generico+file-datosdeconexion.html)

They all use PPoE/A. Only the first one, Arrakis doesn't have a username or password. They offer this router. [http://www.draytek.co.uk/products/vigor2500.html](http://www.draytek.co.uk/products/vigor2500.html)

But actually the reason I put the first link is for you to see the 2 configurations for Wanadoo, 1 for dynamic ip and the other fixed ip.

Would another possibility (if the firmware upgrade fails) be to try and use the fixed ip information I have already with that fixed ip configuration at the bottom of that page?

---

### Post by weekend warrior on 2005-04-27
Here is a much bigger manual, the mother of all manuals, 300 pages! :shock: for the Thomson SpeedTouch 510

[http://www.adslayuda.com/descargas/routers/thomson/manuales/userguide_en_alcatel.pdf](http://www.adslayuda.com/descargas/routers/thomson/manuales/userguide_en_alcatel.pdf)

---

### Post by heimo on 2005-04-27
Chapter 4 on your manual describes how to upgrade system software (=firmware). Bad news, it's Windows specific. Good news, it's doable (but probably not too easy) on Linux with bootp. I'd suggest using Windows machine to do this.
 
If you should use static settings, do you already know your ISP assigned ip/subnetmask? (dns settings are on the page you linked)
 
Couple linksys alternatives:
[http://www.linksys.com/international/product.asp?coid=6&ipid=181]("http://www.linksys.com/international/product.asp?coid=6&ipid=181")
[http://www.linksys.com/international/product.asp?coid=19&ipid=371]("http://www.linksys.com/international/product.asp?coid=19&ipid=371")
 
But do check other alternatives from other manufacturers. I just have been very satisfied with my WRT54G (which is NOT ADSL router):
[http://www.linksys.com/products/product.asp?prid=508&scid=35]("http://www.linksys.com/products/product.asp?prid=508&scid=35")
 
Of course many people reading this thread are frowning because we use so liberately word router. For those people nothing less than Cisco 12k series
[http://www.cisco.com/en/US/products/hw/routers/products_announcement0900aecd8027c804.html]("http://www.cisco.com/en/US/products/hw/routers/products_announcement0900aecd8027c804.html")
is considered as a toy. ;)

---

### Post by weekend warrior on 2005-04-27
Yes I can see the ip, subnet, gateway and dns numbers that my dsl modem is using right now.

---

### Post by heimo on 2005-04-27
[QUOTE=weekend warrior]Yes I can see the ip, subnet, gateway and dns numbers that my dsl modem is using right now.[/QUOTE]
 
What? :) Hmm.. the same dsl modem, the same Speedtouch 510? Does this mean it works?
 
EDIT: Or ... Or are you talking about lan side IP. You know, your adsl box needs wan side settings too, as long as it's working as a router.

---

### Post by weekend warrior on 2005-04-27
So I would have to install the router on this box right? You know I don't think that sounds very prudent, seeing the config file changes everything to dynamic host and I currently have a fixed ip setup. The last thing I want to do is mess up my only working internet connection. That would be more difficult than trying linux with bootp. Well, if that happens then "difficult" wouldn't be the word I'd use. I wouldn't even type on here the words I'd use. :twisted:  Actually, I wouldn't be able to!  

Anyway, it will be a linux learning experience! right?

---

### Post by weekend warrior on 2005-04-27
No no, sorry for the confusion, I have two modems, the newrouter and an old dsl modem I've been using with Bill Gatesware. It's a Sagem Fast 1000 winmodem, also from Wanadoo. (Too bad it wasn't 800, that one does work I've heard.) That's why I got the router. I've read one post that says it's possible to get the 1000 working in linux but very difficult. I'll see if I can dig up the site.

---

### Post by weekend warrior on 2005-04-27
Then again, "difficult" is pretty relative at this point isn't it? Maybe in fact it is easier to get this old Sagem 1000 going under linux?

---

### Post by weekend warrior on 2005-04-27
This is the Sagem F@st 1000
[http://www.chipweb.de/dsl/index.php?menu=2&id2=51](http://www.chipweb.de/dsl/index.php?menu=2&id2=51)

---

### Post by heimo on 2005-04-27
I meant that you would only do the firmware upgrade using Windows box. By the way, you do disconnect the old ADSL modem when you're trying to get that router working, do you? Those will not work at the same time, unless you have two separate dsl-connections in separate wires.

---

### Post by weekend warrior on 2005-04-27
Actually it might be possible. the modem is old, from 2002 maybe, so probably someone has got it to work.

Flashtux has a link on this page but the link (sagem.com) is broken.
[http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)

---

### Post by weekend warrior on 2005-04-27
Yes I disconnect completely, in fact since I only have one working monitor at the moment, I have to shut down one box to change to the other *sigh*.

Ok, so the firmware can be updated on this system without using the setup cd and installing the router? Just plugging it in and using the autoupgrade program will work?

---

### Post by heimo on 2005-04-27
Well... I can't guarantee. There's also always risk at making the router unusable... (which wouldn't be a big problem compared to its state at the moment).
 
Sorry for not reading this thread to find if you already mentioned, have you tried copying those settings from your Windows (adsl-modem) to your routers wan side interface?
 
EDIT: Hm.. I'm getting very confused. But if you're now using DHCP on that modem, you should have DHCP also on that router (wan side). If you're using static configuration, you should put those settings on your router (wan side). As it's going to nat your connection, you can use "reserved" addresses on lan side for both router and computer (192.168.*.*).

---

### Post by weekend warrior on 2005-04-27
Right, that's basically what I'm asking, look at page 4, post #39. I think I've been going about this the wrong way the whole time. I shouldn't have followed the directions from the ISP because I currently have my TCP/IP settings on this windows box set to a fixed ip, submask and gateway. That's why I said I felt like I was having a dumb moment, because it seems very obvious now doesn't it? Sometimes being close to the problem you can't see the forest for the trees.

>>>PLEASE! if anyone else is reading and it seems very obvious to you, then post!<<<

I think this is what I've been doing wrong. But I'm still stuck with a config file that sets everything to dynamic host. I have the firmware updates that support templates and one of those .tpl files I downloaded is for fixed ip.

I think this would do it if I can get the firmware upgraded and use the template to enter in my TCP/IP numbers. I'll try this evening to just enter in the numbers manually and see what happens.

---

### Post by weekend warrior on 2005-04-28
The saga continues....

I figured the best way to enter my fixed ip numbers would be reinstalling ubuntu. When it came to configure the network I got the same error message saying "Network autoconfiguration failed, your netowork is probably not using the DHCP protocol". So I chose configure manually. However the problem after this was ubuntu didn't have enough information to connect because the manual configuration in the install only asks for ip, netmask, and dns and not username or password. 

The ubuntu team really needs to work on this part of the install procedure. It's setup to assume the computer is on a LAN in an office environment, hence suggesting contact your network administrator. This isn't going to help home users! It's not consistent with a non-enterprise distro aiming for ease of use and/or home users. At the least it could offer more options like username and password.

Because of this missing info, the part on "testing network repository" took ages and I'm assuming here that it's trying to contact the respositories over the net? Basically it looks like the system hangs, stuck on "configuring apt 50%" There is no drive activity, no message, and of course nothing from the router to indicate the install is still going. In fact, the first time or second time I installed, I did assume the install was bad and rebooted. That's what started me going (wrongly I'm still guessing) on the DHCP path. The next time I installed I just chose "will configure network later". But this time I just left it for 10-15 minutes and came back to see 75% so it was still going.

Install finished ok, check the network numbers in ubuntu and they look the same as my windoze system so good. But how do I communicate with the router now? The only way I can find to do this is setting the nic temporarily to 10.0.0.138 and I check the router numbers, the ip, gateway and dns numbers are there but the last number of the gateway is incorrect. From the webinterface there's nowhere I can change it.  ](*,)  In ubuntu it's correct but the router has got it wrong. But it doesn't matter anyway because under the connect panel in the webinterface there is "no connection defined" and no way to enter one, which means there is no way for me to put in my username/password and click connect!  ](*,)  ](*,)  .

The only way this will work is to update the firmware and get the templates working to enter the info manually. I'm going to try the update program in winblows. If it doesn't work without actually installing the router and/or there's no way to flash the router in linux then I give up.

Take note readers, if you haven't figured out already the Thompson 510 Speedtouch is to be avoided at all costs!! It is truly :evil: SPAWN OF SATAN!!!

---

### Post by heimo on 2005-04-28
You must have understood something wrong. I did not try to suggest putting Windows network settings to your Ubuntu network settings. I'm suggesting to put those settings to routers wan side interface. 
 
You know - the ADSL-modem on your Windows box is using public IP isn't it? (not from 192.168.*.* series or 10.*.*.*-series?) Yes? That's the settings your routers outside world facing interface, wan-interface should be configured to.
 
Internet <---> (wan) Router (lan, eth0) <--->  (eth0) Ubuntu-box
Internet <---> ADSL-modem <---> Windows-box
 
It's a different scenario. When you have router between you and internet (actually, you always do, but at your home), you need to have correct settings for two interfaces on router (wan, lan) and the interface network card on your computers. Ok?
 
Hopefully this gives some ideas and wasn't completely redundant.

---

### Post by weekend warrior on 2005-04-28
Ok yes, but I still need to put something in the nic settings since it's not set to DHCP, don't I? What numbers should I be using there?

Not that it matters because the program to automatically upgarade the firmware in windows didn't work. The rourter needs to be installed first. The assistant didn't detect the device on the network and I don't have enough faith in this router or the setup files to install on this box. Everything on this system works and I'm not about to risk messing it up for just the possibility of getting a router working in linux.

Thank you for your help and guidance heimo, you were very generous.


Life is just too short for this nonsense.

I give up.

---

### Post by heimo on 2005-04-28
[QUOTE=weekend warrior]
Thank you for your help and guidance heimo, you were very generous.[/QUOTE] No problem. Sad I couldn't help better.
 
[QUOTE=weekend warrior]
Life is just too short for this nonsense.[/QUOTE] Too true. Sometimes it's just not worth it. You need to know which fights to fight.
 
[QUOTE=weekend warrior] 
I give up.[/QUOTE] The way that device is meant to be configured looks braindead. Around 1996-1997 I saved couple bucks by buying ISDN-card instead of external ISDN->Ethernet device. I used next couple years fighting with that device (for example, patching kernel, compiling, using isapnp-tools to configure, authentication and so on). For one year I had to have dual boot just for this - I only was able to use dial-up on Linux.
 
It wasn't wasted time, I believe I did learn couple things. One of them is that hardware is not so expensive after all. It's the devices that don't work which are expensive. And your time, even if you're not a lawyer or high-paid consultant, is worth a lot. And your nerves are.
 
Thanks weekend warrior. End result wasn't what we liked it to be :(, but it wasn't wasted time. :)

---

