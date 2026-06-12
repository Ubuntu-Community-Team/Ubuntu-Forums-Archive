---
title: "IP address never changes, problem"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by ctoaun on 2008-09-24
Greetings.

In windows, whenever, one goes online, a part of or one's entire IP address always changes. In Ubuntu, the IP address is always the same.In my mind, this creates a tracking & privacy issue.


Is there a way to correct this defect? In other words, how does one guarantee that one's IP address will change on a regular basis?

Thanks, in advance

---

### Post by Iowan on 2008-09-24
If you have a static address, it won't change.  If you get address via DHCP from ISP, it shouldn't matter what OS you run.  From **man dhclient**:>        The client normally doesn&#8217;t release the current  lease  as  it  is  not
       required  by  the DHCP protocol.  Some cable ISPs require their clients
       to notify the server if they wish to release an  assigned  IP  address.
       The  -r  flag explicitly releases the current lease, and once the lease
       has been released, the client exits.


---

### Post by ctoaun on 2008-10-01
> **Iowan said:**
> If you have a static address, it won't change.  If you get address via DHCP from ISP, it shouldn't matter what OS you run.  From **man dhclient**:

It would seem that I should begin my inquiry with my Internet Service Provider. Thanks, I'll keep all apprised.

---

### Post by superprash2003 on 2008-10-01
i hope you arent getting mixed up with internal and external ips..

---

### Post by ubutufan on 2008-10-01
The simplest of all simple ways to change the IP of your Internet provider is to unplug the router from mains. Then plug it again. That will ensure a new IP.

---

### Post by ctoaun on 2008-10-08
> **superprash2003 said:**
> i hope you arent getting mixed up with internal and external ips..

I do not believe that I am making this mistake. I will pay more attention to my ip address in the future, but I swear that it has been the same 90% of the time and appeared to be almost the same 9% of the time.

Anyway, I just searched for how to find the internal IP address. However, I could not find anything and I do not have an hour to spend in a search.

---

### Post by ctoaun on 2008-10-08
> **ubutufan said:**
> The simplest of all simple ways to change the IP of your Internet provider is to unplug the router from mains. Then plug it again. That will ensure a new IP.

Thanks for the response

I unplugged the modem for 30 seconds, yet my external ip remained the same.

---

### Post by Iowan on 2008-10-08
> **ctoaun said:**
> Anyway, I just searched for how to find the internal IP address.Internal address will be displayed by **ifconfig** - assuming you're behind a router or modem.  Internal address will probably be in range > 10.0.0.0 - 10.255.255.255
172.16.0.0 - 172.31.255.255
192.168.0.0 - 192.168.255.255
Also, IP addresses in the range of 169.254.0.0 -169.254.255.255 are reserved for Automatic Private IP Addressing.[http://www.duxcw.com/faq/network/privip.htm]("http://www.duxcw.com/faq/network/privip.htm")

If your ISP DHCP is providing the same address, you *might* modify /etc/dhcp3/dhclient.conf. Uncomment the line "#reject 192.33.137.209;", insert the address you don't want.  Dunno if there's a way to embed your current (last) address in there.

---

### Post by phillik747 on 2008-10-08
> **ubutufan said:**
> The simplest of all simple ways to change the IP of your Internet provider is to unplug the router from mains. Then plug it again. That will ensure a new IP.

True for some ISP's. For mine you have to change the MAC address of the router and power cycle the cable modem and router.  The ISP leases the IP address to a Host's [router] MAC address. You can do this by using the clone mac address feature built into most routers.

---

### Post by Bucky Ball on 2008-10-08
System->Administration->Network

Unlock and click on your wireless device then properties. Set 'Configuration' to 'Automatic DHCP' if it isn't already.

---

### Post by ctoaun on 2008-10-09
> **Bucky Ball said:**
> System->Administration->Network

Unlock and click on your wireless device then properties. Set 'Configuration' to 'Automatic DHCP' if it isn't already.

All I get from this is an "could not unexpected error has occurred."

---

### Post by ctoaun on 2008-10-09
> **Bucky Ball said:**
> System->Administration->Network

Unlock and click on your wireless device then properties. Set 'Configuration' to 'Automatic DHCP' if it isn't already.

Also, this is not a wireless issue :)

---

### Post by ctoaun on 2008-10-09
> **phillik747 said:**
> True for some ISP's. For mine you have to change the MAC address of the router and power cycle the cable modem and router.  The ISP leases the IP address to a Host's [router] MAC address. You can do this by using the clone mac address feature built into most routers.

This funny. Everyone is thinking that I am using a router. The truth is that I use a "cable modem" and "carrier pigeons." 
>
Thus far,I've yet to have a DHCP problem with the pigeons although one almost choked to its demise on bird seed, which brings up the all too familiar Ubuntu problem of getting one's "carrier pigeons" to eat slower and fly faster.

---

### Post by Bucky Ball on 2008-10-09
> **ctoaun said:**
> This funny. Everyone is thinking that I am using a router. The truth is that I use a "cable modem" and "carrier pigeons." 


Possibly because you didn't make it clear you weren't talking wireless and a router; one would assume this is a wireless problem as cable is normally picked up 'out of the box'. Odd that Ubuntu does not pick up your ethernet cable connection on boot. It is plugged in at boot I am assuming. So, you have an ethernet cable straight out of the wall plugged directly into the ethernet port on your computer? Not that I am going to be much help but am curious. :)

If it is your ISP and not your router serving the DHCP, definitely contact them and inquire about this. Maybe they are serving you a static IP which would explain everything ... therefore, not a problem. If they are secure at their end ... they are effectively your router, but also your firewall unless you implement something on your local machine. Windoze bugs are not going to effect you but that doesn't stop someone crashing in and playing. ;(

I also use a cable modem plugged into a 4 port router with another 4 port router plugged into one of the ports on the first router. The second router has 4 ports also but sends and receives wireless too. :) Be specific. :)

---

### Post by phillik747 on 2008-10-09
> **ctoaun said:**
> This funny. Everyone is thinking that I am using a router. The truth is that I use a "cable modem" and "carrier pigeons." 


Well the same still applies. If you want to force a new IP address you may need to change the MAC address of your network card.  Usually the only services that change the IP address every time you connect is dialup or a EVDO card (ie: verizon).  One quick way to test is to disconnect your current pc and power cycle the cable modem. Then connect a different pc which will register a new mac address and you *should* get a new IP address.

---

### Post by handydan918 on 2008-10-11
> **phillik747 said:**
> Well the same still applies. If you want to force a new IP address you may need to change the MAC address of your network card.  Usually the only services that change the IP address every time you connect is dialup or a EVDO card (ie: verizon).  One quick way to test is to disconnect your current pc and power cycle the cable modem. Then connect a different pc which will register a new mac address and you *should* get a new IP address.

Also, it is all too often necessary to power-cycle the pigeons...Seems like there should be an applet you could install for that...

---

