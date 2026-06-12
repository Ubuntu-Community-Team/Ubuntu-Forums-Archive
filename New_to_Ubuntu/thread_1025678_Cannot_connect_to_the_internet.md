---
title: "Cannot connect to the internet"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Hyoseke on 2008-12-30
Hi everyone!

I just installed linux 8.04 and cannot connect to the internet (through an ethernet cable). I am using dsl broadband through a d-link router and a speedtouch modem.

I inputed sudo pppoeconf in the terminal and selected yes. After it was finished scanning this came up:

"Sorry, I scanned 2 interfaces, but the accesss concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

At first I thought it was a problem with my internet so I hooked up the ethernet cable to my laptop and it worked right away.

Help would be appreciated =D!

Thanks in advance

---

### Post by handydan918 on 2008-12-30
Have you tried just doing ```
sudo dhclient
```??

I have never found it necessary to use ppoe with a router.

---

### Post by Hyoseke on 2008-12-30
Ok, I will try that !

thanks

---

### Post by Hyoseke on 2008-12-30
It didn't work.

Alot of port # and interval # started popping up.

In the end it said 

No DHCPOFFERS recieved

No working leases in persistent database - sleeping.

Any other ideas?

---

### Post by handydan918 on 2008-12-30
I'd double-check the router and make sure that it is set up to hand out addresses via dhcp. Might try unplugging power to the router for a minute, and try again.

---

### Post by Hydrid on 2008-12-30
Is your network card working?Can you see it in your hardware?Can you ping your net/card?

---

### Post by Hyoseke on 2008-12-30
Im a complete noob when it comes to computers xD.

I tried disconnecting the power to the router and reconnecting, however, it still does not work. I don't understand how to do the other thing you suggested =P.

I don't have a network card, I have a built in one i think (680i xfx mobo). I am not sure where it is located and I have no idea what it means to ping my network.

---

### Post by handydan918 on 2008-12-31
> **Hyoseke said:**
> Im a complete noob when it comes to computers xD.

I tried disconnecting the power to the router and reconnecting, however, it still does not work. I don't understand how to do the other thing you suggested =P.

I don't have a network card, I have a built in one i think (680i xfx mobo). I am not sure where it is located and I have no idea what it means to ping my network.

Open a terminal and copy and paste the output of the following commands.

```
ifconfig
lspci | grep -i net 
lsmod

```

And just for fun try ```
ping -c 4 192.168.1.1
```

If that doesn't work, you might try with a different ip address, like 192.168.0.1 or 192.168.100.1 or 10.0.0.1. Those are probably the most common defaults.If you google the make and model of the router, you can find th manufacturers site, and usually figure out what the  routers internal ip is.

---

