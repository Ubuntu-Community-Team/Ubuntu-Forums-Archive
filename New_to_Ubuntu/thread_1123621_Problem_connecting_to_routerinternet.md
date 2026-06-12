---
title: "Problem connecting to router/internet"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by k10chen on 2009-04-12
hey guys, im having problems connecting to my router

this has not happened with my Linksys router, but im home from school and using a SMC Barricade SMC7004VWBR Router

here is the ifconfig result

eth0      Link encap:Ethernet  HWaddr 00:03:25:3c:2b:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3503826 (3.5 MB)  TX bytes:589301 (589.3 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7372 (7.3 KB)  TX bytes:7372 (7.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:bc:02:c6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-BC-02-C6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

the wired connection from the router works fine

Thanks

-K

---

### Post by cariboo on 2009-04-12
Do you wireless mac filtering turned on in the router?

Jim

---

### Post by k10chen on 2009-04-12
> **cariboo907 said:**
> Do you wireless mac filtering turned on in the router?

Jim

how do you check this?

-K

---

### Post by anewguy on 2009-04-12
Most routers have configuration screens that can be accessed from a browser.  Usually the address is something like 192.168.1.0 or 192.168.1.1, so to get to it you would (for example) use "http://192.168.1.1" in your browser.

Normally the router configuration is also password protected.  If you do not know the router password you will not be able to configure it.

Once you do have access to the configuration, look for something about wireless setup (it varies from manufacturer to manufacturer).  In there you will find something about granting or restricting access by device/address - you might get lucky and even just seen MAC mentioned.  The MAC is an actual hardware address assigned to the particular device, not a normal IP type address.  In my case, my Netgear router shows wireless devices and I am allowed to add them to the allowed MAC address list.

You of course will need to save the changes and perhaps reboot your router.

I'm am not familiar with your exact device so all I could give here was generic advise.

Dave :)

---

