---
title: "How Do I Get Linksys WRT54G Working?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by mulluysavage on 2010-01-08
I checked out a couple of other threads saying you should just plug your router into the cable modem, then plug the computer into the router, and go to [http://192.168.1.1/](http://192.168.1.1/) to configure. I get page load error when I try to do this.

---

### Post by CharlesA on 2010-01-08
> **mulluysavage said:**
> I checked out a couple of other threads saying you should just plug your router into the cable modem, then plug the computer into the router, and go to [http://192.168.1.1/](http://192.168.1.1/) to configure. I get page load error when I try to do this.

Had the same thing happen on my old WRT54G. It was fixed by doing a hard reset, unfortunately I had to do it any time I needed to access the router's web interface, so I just flashed it with DD-WRT. Been working fine ever since. ;)

---

### Post by jimmy the saint on 2010-01-08
There will be a little tiny button on the back that you will need a pen or something to press.  HOld the button in for 10 seconds.  That will restore the factory settings.

---

### Post by mulluysavage on 2010-01-08
I hit the reset button for 10 seconds, but there is no change. Maybe it's because I have it powered with a 12v 500ma adapter instead of 12v 1A. All the lights come on though.

---

### Post by mulluysavage on 2010-01-08
Interesting.. the DD-WRT Wiki lists the 54G v4 as taking a 12v 500ma power supply

---

### Post by mulluysavage on 2010-01-08
figured out the 30/30/30 hard reset on the dd-wrt forum which had no effect.

---

### Post by mulluysavage on 2010-01-08
I am trying to flash with dd-wrt. I'm trying to figure out what "setting the computer to a static IP of 192.168.1.8 or whateverthe subnet of the router is" means. I think I just go into eth0 properties in the network setting tool and set a static IP address, and leave subnet mask and gateway address blank, but how do i find out the subnet of the router?

---

### Post by pricetech on 2010-01-08
The IP you're working with sounds right for the Linksys I've worked with in the past, but check the manufacturer's website to be sure.

You can run ifconfig to determine what your router's IP is.  Your subnet mask should be 255.255.255.0 and your gateway should be the IP address of the router.  The IP you choose for your computer has to be in the same subnet.

Assuming the IP of the router is indeed 192.168.1.1 you can set the IP of your computer to 192.168.1.2 with the subnet mask and gateway numbers mentioned earlier and be able to connect.

---

### Post by RedRat on 2010-01-08
I have one of those routers and am using it right now. I hooked it up to my cable modem, plugged in my computer via the ethernet connector and can load the router's setup page. Perhaps you have a faulty router? Or perhaps your ethernet line is faulty. Sometimes those RJ-45 connectors loose a wire.

---

### Post by mulluysavage on 2010-01-09
The cable works - I put it in between the computer and the modem, and am on the internet with it. 

Here's the output of ifconfig. I don't see the gateway, and the mask looks funny... Can I determine the router address with this info? This was done with computer connected to router only.

eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:6e:f8  
          inet addr:24.45.25.91  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:fe0a:6ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64059980 (61.0 MB)  TX bytes:7208022 (6.8 MB)
          Interrupt:218 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56752 (55.4 KB)  TX bytes:56752 (55.4 KB)

---

### Post by tomcatjosh on 2010-01-09
Silly question here: do you have your computer to router cable plugged into the WAN port or LAN??

---

### Post by mulluysavage on 2010-01-09
I have the cable modem connected to the "internet" jack on the back of the router, and the "1" jack on the back of the router connected to my ethernet card on my computer.

---

### Post by CharlesA on 2010-01-09
The IP and subnet you have when connected directly to the modem is fine.

Have you tried to do a hard reset of the router? Try a different port if that doesn't work.

---

### Post by mulluysavage on 2010-01-09
I have tried a 30/30/30 reset of the router. I looked at /etc/network/interfaces and saw that there was no default gateway assigned so I added 192.168.1.1 but that had no effect How do I try a different port?

---

### Post by tomcatjosh on 2010-01-09
Have you tried playing around with the IP addressess on the router?? Say,set different IP Assignments..

---

### Post by mulluysavage on 2010-01-10
How about this: how do I determine my default gateway?

And how would I play around with the ip address of the router?

---

### Post by pricetech on 2010-01-11
> **mulluysavage said:**
> Here's the output of ifconfig. I don't see the gateway, and the mask looks funny... Can I determine the router address with this info? This was done with computer connected to router only.

eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:6e:f8  
          inet addr:24.45.25.91  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:fe0a:6ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64059980 (61.0 MB)  TX bytes:7208022 (6.8 MB)
          Interrupt:218 

You have a public IP.  Your router should be assigning private IPs.  A reset is in order.  If you have already reset and are still getting that IP from your router, something is wrong with it.

There's not much sense in attempting to "fix" anything else until the router is functioning properly.

---

### Post by running_rabbit07 on 2010-01-11
> **mulluysavage said:**
> eth0      Link encap:Ethernet  HWaddr 00:24:8c:0a:6e:f8  
          inet addr:24.45.25.91  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::224:8cff:fe0a:6ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:218547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64059980 (61.0 MB)  TX bytes:7208022 (6.8 MB)
          Interrupt:218 

The subnetting is all wrong here. The Bcast address and inet address are in different subnets. 

Please run this command in terminal.```
netstar -r
``` It should look something like this, ```
rabbit@rabbit-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
[COLOR=Red]192.168.1.8[/COLOR]     *               [COLOR=DarkOrange]255.255.255.248[/COLOR] U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
[COLOR=Blue]default         192.168.1.14[/COLOR]    0.0.0.0         UG        0 0          0 eth0

```[COLOR=Red]192.168.1.8 [COLOR=Black]Network Address
192.168.1.15 Broadcast Address (not listed with this command, but is the Bcast when using "ifconfig")
[/COLOR][/COLOR][COLOR=Blue]192.168.1.14[/COLOR] Default Gateway (the router's IP address)
192.168.1.9 Host IP (not listed with this command, but is the inet when using "ifconfig")
[COLOR=DarkOrange]255.255.255.248[/COLOR] Subnet mask which allocates that the subnet has 6 usable address 192.168.1.9-192.168.1.14

---

### Post by mulluysavage on 2010-01-15
netstat -r
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
24.45.24.0      *               255.255.252.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         ool-182d1801.dy 0.0.0.0         UG        0 0          0 eth0 
```

so this looks pretty screwed up. Anybody know how to modify this so it starts off correctly on startup?

---

### Post by mulluysavage on 2010-01-15
well I got this far using NetworkManager on manual
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.248 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         phil-desktop.lo 0.0.0.0         UG        0 0          0 eth0

```

I dont know why Destination lists 192.168.1.0 when I enter 1.8 for the address, and I don't know why gateway gives the text name of the local host, when I enter 192.168.1.1 as the gateway

route add default gw returns error operation not permitted, when i sudo it says no such process

---

### Post by sandy8925 on 2010-02-14
Can anyone help me with setting up my router ? I have a WRT54G too. The setup is as follows: I have a modem supplied by my ISP which connects to the Internet through phone lines using ADSL. I can connect to the modem using Ethernet and wireless.

Now I have connected the WRT54G 'Internet' point to the modem through an Ethernet cable. The Internet light shows green. I've setp wireless on the WRT54G and that works properly too. Now how can I access the internet through the WRT54G router i.e I want to be able to connect my laptop to the WRT54G wirelessly and be able to access the Internet.

---

### Post by mwcrowley on 2010-02-14
It this a new router, or one you bought from someone.  I have two wrt54g and they are good routers, but the hard reset does not always take on the first try.  Do it again until your sure it reset to factory defaults, and connect your laptop to the router with a cat5 cable to make sure it's working, then try wireless.  
The gateway ip and subnet mask make it look like someone else's settings and not the defaults. You don't know what else was setup, so my advice is to start from scratch.
Do a hard reset until you can log on to the router at 192.168.1.1 over a wired connection, wireless second, if you can. At that point you can select wep(ok) or wpa(better) or wpa2(best choice) for security.

---

### Post by Easy Limits on 2010-02-14
Also check Linksys website to make sure you have the latest firmware update for your model and version.

---

### Post by sandy8925 on 2010-02-15
I'm able to connect to my router through wifi and access the settings page. I'm just not able to access the internet through it. What settings do I have to change ?

---

### Post by Easy Limits on 2010-02-15
You shouldn't really have to change any settings initially.  It should be plug and play.  You can go in to the routers set up page and configure wireless security and such.  The WRT54G really has a good set up page.  You may want to call your ISP and see if they can ping your modem to make sure it is working right.  You can also power off your modem and router at the same time then power on the modem then router after about five minutes.

---

### Post by sandy8925 on 2010-02-24
I'm able to use the internet now. Just had to set the Linksys router's ip address to 192.168.2.1 instead of 192.168.1.1 (which my DSL modem was using).

---

