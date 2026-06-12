---
title: "can't ping gateway when configured to static IP"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by miles.bobby on 2008-06-03
I've been looking around and can't find an explanation for why I CAN ping my gateway when I have roaming enabled but not when I set it up as a static IP.

With DHCP (roaming) ping works ok
Set as static IP I get a message saying 'unable to resolve host'

Any help is greatly appreciated.

Thanks!

---

### Post by HalPomeranz on 2008-06-03
It sounds like you didn't configure /etc/resolv.conf when you set the static IP.  DHCP handles this for you automatically, but if you're configuring the interface statically you also have to configure your resolver.

---

### Post by Prospero2006 on 2008-06-04
That's good advice. Be sure to check resolv.conf

You could also print the output of ifconfig here.

Try this:
X=eth number
```


ifconfig ethX ip_address_of_computer
ifconfig ethx netmask 255.255.255.0
route add default gw ip_address_of_gw
ifconfig ethX up

```
ping ip_address_of_gw

---

### Post by revtds on 2008-08-09
I have just done a full install of 8.04, from Kubuntu 7.10.  I am also unable to use a static IP, which I much prefer.  I am unfamiliar with the resolver you talk  about.  Are there any helpful links about this, how to set it, etc.?  What it does.  In 7.10, I just filled in the static IP info and it ran, but 8.04 won't connect, won't ping or go anywhere.

Thanks

---

### Post by revtds on 2008-08-09
I should also have mentioned that it only seems to work if I have "Roaming Enabled" checked. If not, nothing happens.  Any info on what that is and why it seems to be exclusive of Static IP would be helpful as well

---

### Post by caljohnsmith on 2008-08-09
Revtds, the /etc/resolv.conf file holds the IP addresses for your domain name servers (DNS). Usually you can set this address to your router or DSL modem, and the router/modem will then forward your DNS requests to your ISP's DNS. 

If you can connect in roaming mode, just check what IP address it uses for DNS in your /etc/resolv.conf file, and then you can use that manually when setting up a static IP. In other words, when you are in System > Admin > Network (the network manager), there is a tab for "DNS" and this is where you would enter that address(es).

---

### Post by BruceFulton on 2009-07-09
I'm having the same difficulty in a virtual machine I've created. I'm not sure why dns or resolv.conf would impact not being able to ping the default gateway, since dns resolution is beyond the gateway. If I can't ping the gateway, there is something more basic wrong. 

I have confirmed the ip address, gateway and so on and am looking at an identical vm I've created with identical specs (except for the MAC address) that works.

I've also tried /etc/init.d/networking restart 
and I've confirmed with netstat -lnt that ssh, apache and mysql are listening.

But, I can't ping the gateway from this virtual machine, even though I can from two others.

---

