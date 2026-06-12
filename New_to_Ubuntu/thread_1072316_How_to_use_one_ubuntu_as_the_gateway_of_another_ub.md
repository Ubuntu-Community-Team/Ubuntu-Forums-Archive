---
title: "How to use one ubuntu as the gateway of another ubuntu?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-17
Hi
Is it possible to use a machine with ubuntu and internet access as the gateway for another ubuntu?
I do not want to use it as proxy but some kind of internet sharing. The ubuntu with internet connection is named ubuntu1 and the other instance is named ubuntu2.

I should include that both computers are connected to a switch. Although I can use the same gateway which I used for ubuntu1 for ubunut2 but I can not because all transmissions should go through ubuntu1.

thanks

---

### Post by yoyoned on 2009-02-17
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by legolas_w on 2009-02-17
Hi
thank you for reply.
That article covers when we have one computer with two network card. in my case two comuters are connected trough a switch and first computer (which I want to use as gateway) connects to internet using that switch.

---

### Post by superprash2003 on 2009-02-17
for a gateway you need 2 network cards.. in your case , its just a typical LAN network.. you can still use your current setup for file sharing etc..

---

### Post by tarps87 on 2009-02-17
Is there a reason you want to use one of the machines as a gateway? If you are using a switch you should be able connect directly with both computers

---

### Post by Coreigh on 2009-02-17
Both computers should be able to access the internet independently throught the switch. Two possible issues preventing this are both related to IP address. If the internet service provider does not allow multiple computers on a single connection (Cable modem or DSL or whatever you have) Then you will have to replace the switch with a home router. The router appears as a single device and does the connection sharing for you. However, if the switch you indicated actually IS a router then all you probably have to do in reconfigure it to hand out IP addresses via DHCP.

---

### Post by tarps87 on 2009-02-17
> **Coreigh said:**
> Both computers should be able to access the internet independently throught the switch. Two possible issues preventing this are both related to IP address. If the internet service provider does not allow multiple computers on a single connection (Cable modem or DSL or whatever you have) Then you will have to replace the switch with a home router. The router appears as a single device and does the connection sharing for you. However, if the switch you indicated actually IS a router then all you probably have to do in reconfigure it to hand out IP addresses via DHCP.

You could also fix the computers IP's relative the the routers IP, if it is a router.

---

### Post by donkyhotay on 2009-02-17
Yes you can so long as you have at least 2 network cards. I did this myself awhile back as part of building a small personal DHCP/webserver. As a headless system the hardest part was configuring iptables manually but if you're using a GUI you can just use firestarter. Admittedly this was really more for learning how to do it then any practical application since it's usually easier to just use a hardware router/switch instead.

---

### Post by legolas_w on 2009-02-17
The problem is:

Machine 1- has ubuntu 8.10
Machine 2- has OpenSolaris 2008.11

Machine 1 can connect to VPN while machine 2 can not connect to VPN because OpenSolaris has no simple way to configure its VPN

I thought I can somehow use machine 1 as the gateway for machine 2 therfore it can use the VPN connection without requiring a long and possibly hard time to setup the connection.

It looks like that I can not do it with one network card, I should either find a way to setup the vpn or buy another network card.

Thanks.

---

### Post by handy on 2009-02-18
Have a look at [*_IPCop_*]("http://www.ipcop.org/")?

It is a tiny Linux based firewall router with a range of other services available often via add-ons (I only use the [*_Copfilter_*]("http://www.copfilter.org/") add-on).

It is simple to set up, has a brilliant browser based GUI for configuration & reference that is only accessible from a client machine.

It runs brilliantly on PII's (I am using a PIII) which use little electricity.  An 8Gb HDD & 256Mb of RAM will sort out all but the most unusual home LAN, bigger installations can benefit from a larger HDD for the proxy caching & more RAM.

Following is a link to page in a thread I started when I was setting IPCop initially:

*_[http://ubuntuforums.org/showpost.php?p=6303994&postcount=29](http://ubuntuforums.org/showpost.php?p=6303994&postcount=29)_*

If you read through that thread, you will find that I am no network wizard, I had good help because I needed it.  Knowing what I know now, it is such an incredibly easy system to set up. As they say, 20 minutes when you know what you are doing. :D

By the way, the machine I'm using as my headless IPCop/Copfilter box cost me $5- at the rubbish dump.

---

