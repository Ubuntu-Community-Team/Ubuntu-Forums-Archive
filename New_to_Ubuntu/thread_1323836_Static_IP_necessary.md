---
title: "Static IP necessary"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-12
Hi Forum,

I'm setting up my sever and see that most tutorials require an edit of the connections as a first step to set the IP static.

My router provides DHCP, port forwarding and dyndns services (AWM Fritzbox). It also allows the fixing of internal IP according to MAC address so my server always has the IP 192.168.178.25, even if I re-install Ubuntu, change the OS or format the HDD. Apache is also available from the internet because port 80 is forwarded for TCP.

So do I need to change the internet settings for a fixed IP? Is there an advantage? The router fix is certainly quicker and easier. Am I missing something?

TIA

Rich

---

### Post by fromthehill on 2009-11-12
It doesn't matter how you do it as long as your internal ip doesn't change

Even if your router settings get wiped for some reason you can fix it by changing the forwarding settings in your router to the right ip

---

### Post by ukripper on 2009-11-12
need some extra info as below:

1.Why you need DHCP to serve your box? 
2.why you want router to do extra work and resolve your ip everytime to mac address? 
3.Why you don't want to use static ip?

---

### Post by RichardCL on 2009-11-12
> **ukripper said:**
> 1.Why you need DHCP to serve your box? 
I don't really need it. It was just default and works. I also use DHCP for all the other network users (mix of linux and windows machines). The other advantage is that I get network access from install or even when using a USB key.

> **ukripper said:**
> 2.why you want router to do extra work and resolve your ip everytime to mac address? 
I wasn't even aware that the router was doing anything special. Would it be faster if I used a static IP?

> **ukripper said:**
> 3.Why you don't want to use static ip?
No real reason. I'm just lazy and working on the basis "if it aint broke". Since the system runs, I've been using it as is. Now I'm learning about configuration and see that there is  another method (static IP) I'm interested in whether there would be an advantage. It is certainly more work to make a static IP and some flexibility is lost. I don't want to do it if there isn't an advantage.

---

### Post by ukripper on 2009-11-12
In that case i'd suggest you make you server to have static ip and just port forward internally on your router. Router will still be sending DHCP requests to other boxes/devices.

static ip is really easy to setup - 
just put below in your /etc/network/interfaces file:
```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.x.x
        netmask 255.255.255.0
        network 192.168.x.x
        broadcast 192.168.1.255
        gateway 192.168.x.x

```

replace x accordingly

then restart the network service
```
sudo /etc/init.d/networking restart
```

---

### Post by RichardCL on 2009-11-13
Many thanks, that is working.

Just incase anyone is trying to follow this, I used
```
route -n

```on the server to get the info that should be in the placeholder

The question is, should I expect the network to be quicker now?

---

### Post by alphacrucis2 on 2009-11-13
> **RichardCL said:**
> Many thanks, that is working.

Just incase anyone is trying to follow this, I used
```
route -n

```on the server to get the info that should be in the placeholder

The question is, should I expect the network to be quicker now?

No. The DHCP only kicks in when you first boot up and subsequently each time the DHCP lease expires, i.e it is of no real consequence. It would be a different story if you were running multiple network connections to your server and/or multiple ip addresses per interface. Then you would need a static configuration. In your case the only time that the reserved DHCP method would come unstuck would be if you changed your server ethernet hardware thereby changing the mac address. Still no big deal to sort out as you already know what to do.

---

