---
title: "Need Insight into Network Connection Problem"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by emf on 2006-12-05
I recently moved into a new apartment where there is a cable connection.  The system they have uses a cable to connect the router to wireless router D-Link DI-514.  I have a G3 IMac without a wifi card so I'm directly linked to the DI-514 router through a cable.  ](*,) I am not good with network issues and really have no idea how to proceed.  Any suggestions would be greatly appreciated.

1. All cables are properly connected and all lights are on.

2. I ran the following commands as root.  Let me know if you need anything else.  

**~$ lshw -C network  **                  #Shortened output
description : Ethernet connection
product: UniNorth GMAC (Sun GEM)
bus info: pci@20:0f.0
logical name: eth0
serial: 00:30:65:be:fe:34
configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half **link=no** multicast=yes port=MII speed=10MB/s

(Since I cannot cut & paste, this is shortened output.  Also, command was run when I was connected to a neighbors wifi.  Other than speed, info is the same.)

**~$ lspci-v|grep Ethernet**
0002:20:0f.0 Ethernet controller: Apple Computer Inc UniNorth GMAC (Sun GEM) (rev01)


**~$ dhclient eth0**
DHCPACK 192.168.0.1 bound to 192.168.0.100

**~$ route -n **
Kernel IP routing table
Destination	Gateway	Genmask	Flags	Metric	Ref	Use	Iface
192.168.0.0	0.0.0.0		255.255.255.0	U	0	0	0	eth0
0.0.0.0		192.168.0.1	0.0.0.0		UG	0	0	0	eth0


3. My **/etc/network/interfaces** file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


4. It fails when I try to ping an external ip address. 

ANY SUGGESTIONS?  Is there a file I need to correct?  It's been a long time since I last set up my connection, but I may have had a static IP address previously.  Is there a file I should correct?  I'm not at home to check this, but would this be in my /etc/iftab or /etc/resolv.conf files?

---

### Post by stream303 on 2006-12-05
The following might help since it appears you have no access to the router.  Pinging might be disabled by the owner of the router too.

If you know your isp's dns servers, and you are running dhcpclient (looks like you are and I'll bet the router owner is running dhcp) you might be interested in the following:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

If you can find out what your dns servers are, you might be interested in the PREPEND line-edit in the howto referenced above.

---

### Post by emf on 2006-12-06
Stream303 - Thank you for the suggestion.  I will try it when I get home tonight.

Since I was at a loss as to what was wrong I ran the following commands last night.  Maybe they'll give someone more insight into my problem.  

[COLOR="#ff0000"]**$ cat /etc/resolv.conf**[/COLOR]
search socal.rr.com
nameserver 192.168.0.1


[COLOR="#ff0000"]**$ ifconfig**[/COLOR]
eth0 Link encap: Ethernet HWaddr 00:30:65:BE:FE:34
inet addr: 192.168.0.100
Bcast: 192.168.0.255
Mask: 255.255.255.0
inet6 addr: fe80::230:65ff:febe:fe34/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric 1
... # No errors, no drops, overruns, etc.



**And I reran the lshw -C network:**
[COLOR="Red"]**~$ lshw -C network**[/COLOR]
description : Ethernet connection
product: UniNorth GMAC (Sun GEM)
bus info: pci@20:0f.0
logical name: eth0
serial: 00:30:65:be:fe:34
configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half **link=yes** multicast=yes port=MII speed=100MB/s

**# In the above, link switched from "link=no" to "link=yes"**


I also modified [COLOR="#ff0000"]**/etc/modprode.d/aliases**[/COLOR] with the following lines:
      alias net-pf-10 ipv6 off
      alias net-pf-10 off
      alias ipv6 off
      #alias net-pf-10 ipv6

I took this from the [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

I did this beacause I noticed the following in dmesg:

[COLOR="#ff0000"]**$dmesg**[/COLOR]
eth0: no IPv6 routers present

I would like to change this back if I can, but I don't think I'm hurting anything by leaving this file commented for the moment.

AGAIN, SUGGESTIONS ARE GREATLY APPRECIATED. IF THERE IS A SPECIFIC LINE IN DMESG I SHOULD LOOK FOR, PLEASE LET ME KNOW.

Thank you.

---

### Post by gitargr8 on 2006-12-06
Have you tried to ping your gateway? Run netstat -rn and ping the IP listed under gateway. This IP should be the address of your router. If you can't ping the router, you're either being blocked access to the router, or you're plugged into the wrong Ethernet jack.

If you do have access to the router, type the router IP address into a web browser, you can find out what DNS server the router is using, and try pinging the DNS server. 

If you can ping the DNS server, try running nslookup [www.yahoo.com](www.yahoo.com) to see if you can resolve IPs through the DNS server.

Let me know what step fails.

~Ryan

---

### Post by emf on 2006-12-06
Thanks Ryan.  I will try your suggestions tonight and let you know the results.  I'll feel pretty dumb if I discovered I'm plugged into the wrong ethernet jack.

Question: You mention the router IP address can be found under Gateway when i give the command netstat -rn.  Would this be the same IP address found under Gateway when I run route -n?  This is found in my first post.

If thats the case I pinged 192.168.0.1 with 0% packet loss.

---

### Post by gitargr8 on 2006-12-07
Yes, that should be the address. You own the router you're connecting to, correct? You should be able log onto the router with your web browser then, and find out what DNS server it is connecting to.

~Ryan

---

### Post by emf on 2006-12-07
I attempted the suggestions of both stream303 and gitargr8.  Still no connection.  Here are the steps I took:

stream303:
> If you know your isp's dns servers, and you are running dhcpclient (looks like you are and I'll bet the router owner is running dhcp) you might be interested in the following:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

If you can find out what your dns servers are, you might be interested in the PREPEND line-edit in the howto referenced above.

1. [COLOR="#ff0000"]**Uncommented and edited the PREPEND line of /etc/dhcp3/dhclient.conf**[/COLOR] with the ISP's dns nameserver.  I probably did this wrong.  My landlord hasn't got back to me on my request for my ISP's primary and secondary dns server addresses, but I was able to connect to the router and I found the address of **0.0.0.0** for my primary dns address.  So 0.0.0.0 is what I entered in the dhclient.conf file.  I then did ifdown eth0 && ifup eth0.  This didn't solve anything.

Can 0.0.0.0 possibly be correct?  This seems wrong, but I really don't know anything about networking.

2. Next I ran the command 
```
[B]ip a |grep inet6
inet6 ::1/128 scope host
inet6 fe80:230:65ff:febe:fe34/64 scope link[/B]
```

so I guess its still possible I'm having trouble with IPV6.  I will review the page [http://www.ubuntuforums.org/showthread.php?t=87798]("http://www.ubuntuforums.org/showthread.php?t=87798")

Now gitargr8's suggestions:
> Have you tried to ping your gateway? Run netstat -rn and ping the IP listed under gateway. This IP should be the address of your router. If you can't ping the router, you're either being blocked access to the router, or you're plugged into the wrong Ethernet jack.

If you do have access to the router, type the router IP address into a web browser, you can find out what DNS server the router is using, and try pinging the DNS server. 

If you can ping the DNS server, try running nslookup [www.yahoo.com](www.yahoo.com) to see if you can resolve IPs through the DNS server.

Let me know what step fails.

1. ```
netstat -rn
``` gives the address of **192.168.0.1** listed under gateway.  I successfully pinged this address.

2. I typed 192.168.0.1 into my web browser.  Here is some of the info I copied down.  Let me know if there's anything else you need to see.

LAN
IP Address  192.168.0.1
Subnet Mask  255.255.255.0
DHCP Server Enabled

WAN
Connection  DHCP Client Disconnected
IP Address  0.0.0.0
Subnet Mask  0.0.0.0
Default Gateway  0.0.0.0

Dynamic IP
Host Name  DI-514
Primary DNS Address  0.0.0.0


Using this information I pinged 0.0.0.0 successfully.

3.  I attempted 
```
nslookup www.yahoo.com
noservers could be reached
```

So this failed.  Any suggestions?

Like I said at the beginning of this post I've requested my landlord to give me the ISP dns server primary and secondary addresses, but I don't know if I can rely on him.  Do you have any other suggestions?  I really don't know what to do.

---

### Post by mips on 2006-12-07
> **emf said:**
> 
2. I typed 192.168.0.1 into my web browser.  Here is some of the info I copied down.  Let me know if there's anything else you need to see.

~snip

WAN
Connection  DHCP Client Disconnected
IP Address  0.0.0.0
Subnet Mask  0.0.0.0
Default Gateway  0.0.0.0


There is your problem, you are barking up the wrong tree.

The WAN port of your D-Link is not receiving any IP information from your cable modem. Maybe reset your cable modem & d-link router (power off and back on again) and see if things change. Alternatively call the ISP and ask them why your d-link is not getting an IP address from their modem.

Did you connect your cable modem to the D-Links WAN port or it's normal ethernet ports ??? It should be connected to the WAN port.

---

### Post by emf on 2006-12-07
Mips,

Thanks for the advice.  I'll reset everything, check connections and see what happens.

---

### Post by stream303 on 2006-12-07
Maybe a friendly neighbor can tell you what the dns addresses are?

You might also want to look into the OpenDNS option if no isp server info is forthcoming....

---

### Post by mips on 2006-12-07
> **emf said:**
> Mips,

Thanks for the advice.  I'll reset everything, check connections and see what happens.

Good luck, I'm off to bed.

The problem is not with Ubuntu. You have no IP config on the D-link WAN side and that is why things are not working.

---

### Post by gitargr8 on 2006-12-10
I know whenever I'm having DNS issues, I use 4.2.2.2 because it is so easy to remember. The more pressing issue is that you're not receiving an IP address from your ISP. Have you tried calling your ISP? They can dial in to your modem and make sure that it is connecting properly. Also, can you try plugging directly into your modem (bypass the router) and try running ifconfig -a?

---

