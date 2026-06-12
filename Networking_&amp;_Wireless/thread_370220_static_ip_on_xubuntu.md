---
title: "static ip on xubuntu"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by jordi_rc on 2007-02-25
Hi to all

I just need to know how to setup my Xubuntu to work with static ip that my isp gave me.

I have a barebone with Xubuntu installed. 
I have a static ip, given by my provider.
I use a router, thomson speedtouch 530v6.
I have my Xubuntu machine connected by ethernet to the router.

In the menu of my router I have an option to assign my ip to the computer, but it says I must change something in the os (but it doesn't tells me what).

I can also forward the ports with my router's menu.

BUT: 
1) How do I configure my Xubuntu machine so when I do all that, all goes fine?
2) In what order must I proceed?
3) I have another machine with Windows XP connected to the usb port to the same router. How must I configure it? 

Thanks for any info.

Jordi

---

### Post by n8bounds on 2007-02-25
You can edit your /etc/networing/interfaces file to assign static IPs or use the gnome networking tool...Not sure about your router.

---

### Post by jordi_rc on 2007-02-25
I saw a page:

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

It says the graphical UI to configure my connection, but... how do I know my dns values, the subnet and gateway? and my hostname and domain?

I think I am really confused with all this. And my isp providers are a bit morons, and don't know ubuntu at all, nor linux.

1)The dns values are those that appear in my router as primary dns and secondary dns??
2)The subnet mask has a standar value? Or what? 
3) the gateway is my router? Or what? 192.168.0.1 = my router = gateway???
4) what must I type in hostname? Anything I want? Or what? What is that used for?
5) and in domain name???

Thanks.

Jordi

---

### Post by chili555 on 2007-02-25
We may be mixing apples and oranges. The static IP given to you by your IP provider goes in the relevant page in the router. The router will hand an IP address to the Ubuntu computer and no one cares if it's static or DHCP. I would configure your router with it's static IP first and then make life easy for yourself and set up the Ubuntu computer with DHCP. The unknowns you asked about will be automagically provided by DHCP.

Post back if you get stuck.

---

### Post by jordi_rc on 2007-02-25
thanks chili555

I forget that I need to configure my Xubuntu machine as web server, so I must forward the ports, but also need my machine to be configured properly. And I don't know how.

For the moment I use DHCP to browse the internet, and works fine.
But for turn it into a server, I suppose I would need to configure it with my static ip and all that. Isn't it?

Jordi

---

### Post by chili555 on 2007-02-25
You probably will need a static IP on your machine to use it as a web server. Let's do it!

Open a terminal and do ifconfig. Your relevant interface will show your current IP address and netmask, as well as some other information. Like mine:

```
wlan0     Link encap:Ethernet  HWaddr 00:09:5B:E9:47:A1  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          etc.

```

Then do route -n and you will see your gateway. For example:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

Then open up System -> Administration -> Networking, select your relevent interface and click properties. Change to static and fill in the values you just found. In my case, IP address 192.168.1.106, Netmask 255.255.255.0 and Gateway 192.168.1.1. Click OK and you are all set.

---

### Post by jordi_rc on 2007-02-26
Hi chili555

I type ifconfig and it says:

> 
eth0      Link encap:Ethernet  HWaddr 00:01:80:63:67:AE
          inet addr:192.168.0.129  Bcast:192.168.0.255  Mask:255.255.255.0


With route -n it says:

> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


So I suppose I must fill:

ip: 192.168.0.129 (=the ip assigned by the router to this machine, not the public ip)
subnet mask: 255.255.255.0
gateway: 192.168.0.1 (=the router)

I have some doubts before proceed:

1) I must use the ip assigned to my pc by the router (192.168.0.1) instead of the static ip that my isp gave me (wich is another number starting in 85. and is allways the same) ?

2) what must I fill in host and domain name? Should I fill something? If I had a domain name, for example [www.domain.com](www.domain.com) I must fill domain=domain and host=what? I don't have a domain name for now. What must I fill? Or these are names of the working group or something?


Please tell me. 
Thanks chili555 for helping me in this process,

Jordi

---

### Post by chili555 on 2007-02-26
This is all you need:```
ip: 192.168.0.129
subnet mask: 255.255.255.0
gateway: 192.168.0.1

```

I'm pretty sure you can ignore all the other stuff.

Put all that in the appropriate spaces, click OK and close. You may need to restart networking. sudo /etc/init.d/networking restart and the ping -c3 [www.google.com](www.google.com). If you get a reply, you know it's all good.

The nice thing about all this is, it's not surgery: if you make a mistake, just undo it! If, for some reason, this doesn't work, go back and select DHCP and you're right back where you started.

---

### Post by jordi_rc on 2007-02-26
Hi chili 555

I writed down all the values in the GUI for Networking.

I use the networking restart comand and I get some errors, but I think I must not worry. These are:

> 
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.



Basically they seem to tell they don't find eth1 eth2 wlan0 and ath0. The last are wireless cards, and the previous ethernet. 
As I have only ONE ethernet card, named eth0, I suppose I must not worry.

I restarted all the computer and did the ping. I saw the changes to static ip remain.
I think I changed to static ip because the GUI now shows all the values I entered and says "static ip" instead of "DHCP".

The ping returns:
> 
PING [www.l.google.com](www.l.google.com) (209.85.129.147) 56(84) bytes of data.
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=1 ttl=239 time=74.1 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=2 ttl=239 time=73.3 ms
64 bytes from fk-in-f147.google.com (209.85.129.147): icmp_seq=3 ttl=239 time=73.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 73.098/73.560/74.193/0.513 ms



Is all right?

Now I must forward the ports that Apache uses to my Xubuntu machine.
I saw this website:
[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/Speedtouch530v6/Apache.htm)

I did all that.
I had a small problem, my connection was lost for some minutes, but re-inited it and after some minutes it works.

I still have Xubuntu with that static ip, and the ports are supposed to be forwaded to it.

BUT when I type the static IP my provider gave me, I get the router page, not the web in the Xubuntu machine.

Do you know why this happens? Maybe I must activate the option in the router that says this:

> 
	
Assign the public IP address of a connection to a LAN device	

This page allows you to assign the public IP address of your Internet Connection(s) to a specific device on your local network...

You might want to do this if:

    * You encounter issues with some applications through the Network Address Translation engine of your SpeedTouch.
[B]    * This device is running server applications (web server, ...) and you want it to be accessible from the internet.
[/B]    * This device has to be considered as the unique entry to your local network (DMZ).


Or why I can't visit my server? 

Thanks chili555, at last I can do all this with someone who helps!

Jordi

---

### Post by chili555 on 2007-02-26
I know nothing about setting up a publicly accessible web server. I think your settings relative to your static IP address are correct, because you are on line!

I suggest you start a new post asking for help setting up a web server. You can certainly refer to this thread in your post so responders can see where you've gotten so far.

You seem to be going in the right direction, as little as I know.

---

### Post by jordi_rc on 2007-02-26
Thanks Chili555

As we are far away, I can't invite you for a beer, so I send you a virtual beer.

[IMG]http://usuarios.lycos.es/ancientgames/xoops/beer.jpg[/IMG]

I will do a new thread, about making public a web server.

Be well, and thanks a lot!

Jordi

---

### Post by chili555 on 2007-02-26
....slurrrrrp...mmmm....thanks, Jordi! It's a tasty one! I shall look for San Miguel at the store and buy a sixer and toast to you! Good luck with your project.

Chili

---

### Post by jordi_rc on 2007-03-01
Finally that was nothing wrong.

The web is accesible from outside, but when one pc in the same house enters, it sees the router.
This is normal.

Jordi

---

