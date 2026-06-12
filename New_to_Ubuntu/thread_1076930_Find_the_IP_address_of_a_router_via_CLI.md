---
title: "Find the IP address of a router via CLI"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by transmition on 2009-02-21
From the command line, how would I obtain the IP address of a router, prior to connecting to it?

---

### Post by yeats on 2009-02-21
I can't think of any way to do so, except to do 

```
sudo dhclient *eth0*
```

(substituting your interface name for "eth0"), which will assign the IP and gateway automatically.

Of course, I also can't think of a graphical way to discover this either. :-)

May I ask why you need to do this?

---

### Post by transmition on 2009-02-21
Well, it is actually for dslinux (not damn small linux) which is linux on the nintendo ds. 

In order to connect to the internet, you must type the following:
```

iwconfig nds channel 6 essid SoftAP-91 key 0102031a2b
ifconfig nds 192.168.1.2 up
route add default gw 192.168.1.1

```

Where the router IP address is 192.168.1.1, Channel is 6, Essid is SoftAP-91 and the IP of the ds is to be 192.168.1.2.

However, if you are in a wifi hotspot, and all you have is the DS, you need some method of determining the IP of the router in order to determine connect to the internet.

From the dslinux wiki:

> 
Most routers hand out IP addresses to computers on the network dynamically via the DHCP protocol. DHCP does not work for most people in dslinux, so you should consider giving your DS a static IP address. 'Static' means the IP address is assigned manually without DHCP


So, you can see I am something of a difficult situation.

---

### Post by llamabr on 2009-02-21
So you want to know the ip of the router before you connect to it?  What sort of information does the ds provide before you connect?

---

### Post by chrisod on 2009-02-21
If I understand correctly, you need the IP address of a router so you can connect to it with the DS? I can't think of anyway you can do that without being connected to the network. Even if you could, there is no way to know if you are assigning yourself an IP address that is available. Also, I suspect that public wifi routers might frequently configured to not allow static IPs to connect as I can think of a couple of ways to misuse that power.

If you could get somebody else at the hotspot to tell you their IP address you could probably assign yourself something in the range and hope for the best.

---

### Post by transmition on 2009-02-22
The DS tells me nothing regarding the router prior to connection, short of ESSID, channel and MAC address.

So I have to ask people what their IP is. I can see that turning into an awkward conversation:

Me: Sir, could you please tell me your local IP?
Average User: My what?
Me: Its like a mailbox, used to, nevermind. Give me your computer/
Average User: Hey! That's mine!
Me: It's ok sir, I'm just trying to ssh from a nintendo ds...

---

### Post by llamabr on 2009-02-22
If you could look at it, you can usually tell.  dlink uses 192.168.0.100 by default, whereas linksys uses 192.168.1.100 by default, if I remember.

You could just make a list of the most common ones.  Or unfortunately, it looks like trial and error.

---

### Post by transmition on 2009-02-22
> **llamabr said:**
> If you could look at it, you can usually tell.  dlink uses 192.168.0.100 by default, whereas linksys uses 192.168.1.100 by default, if I remember.

You could just make a list of the most common ones.  Or unfortunately, it looks like trial and error.

Thanks, I guess I shall have to do that. Seems like the best solution so far.

---

### Post by rggavubt on 2009-02-22
Just enter your router via your web browser.  Just type 
[http://192.168.1.1](http://192.168.1.1) and enter if Linksys.  Look under tab that shows who's on and it will list the IP addresses.  You also have to know your name and password....usually admin, password,  Look at the manual for you router or look up your routers support page the web on how to access router via web browser.

---

