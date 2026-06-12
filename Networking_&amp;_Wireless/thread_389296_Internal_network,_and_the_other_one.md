---
title: "Internal network, and the other one"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by RichGuk on 2007-03-20
Hello,

Let me explain my setup first and what I'm trying to achieve. 

I have two PC's down stairs (one of them being my Linux box) connected to my ADSL router (100mb) and then a wire going to upstairs which connects up wireless AP and 2 other PC's (gigabit switch). What I basically want to do is go gigabit between upstairs and downstairs so I want to plug straight from up stairs into my Linux box and then plug my other Linux network card into the router and for all PC's to be able to see each other and also all access the internet.

Now a friend of mine suggested I need to have an internal network (say for the stuff upstairs) which would be on eth0 and an external network for the downstairs PC's and internet which would be on eth1 and I should use IPTables to achieve this. So I entered this:

iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o ext1 -j ACCEPT

Which seemed to allow us to ping both interfaces on the linux box from a PC (windows box) on the internal network. But we were unable to ping the router nor any of the outside world. I was wondering if anyone had a better way or any idea how to do what I want? hehe.

Router: 192.168.1.1
Linux box (external): 192.168.1.3


Thanks,

Richard

---

### Post by Mr. C. on 2007-03-20
I'm a little confused on your topology.  This is the picture I drew; tell me if this is incorrect

```

PC 1 ---- ADSL ---- PC 2     (downstairs)
           |
           |
           |
PC 3 ---- GS ---- PC 4       (upstairs)
           |
           |
           +------ WAP

```

And it sounds like you want to rewire like this:


```

PC 1 ---- ADSL ---- PC 2     (downstairs)
    \
      \     
         \  
PC 3 ---- GS ---- PC 4       (upstairs)
           |
           |
           +------ WAP

```

If this is correct ?
Which PCs have gigabit cards?

MrC

---

### Post by RichGuk on 2007-03-20
Thats correct,

and PC1 and PC3 have, but PC's second network card is only 100mb

I basically just wanted gigabit between thoese two :) without having to buy another switch :p as there is only one wire going between upstairs and down :(

---

### Post by Mr. C. on 2007-03-20
Ok, in that case you will be turning your Linux box (PC1) into a gigabit router.  You do understand this brings a fair burden to PC1 (lots of interrupts, and like putting a firehouse up to your mouth).  All internet traffic will degrade somewhat, as PC1 becomes the bottleneck (except for PC2, which is directly connected).

You do not need IP tables to do this.

You need separate networks in either side of PC1's nics (as in 192.168.0.0/24 and 10.0.0.0/24).  You simply need to enable routing.

Review Routing in the course notes and labs in week 6: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by RichGuk on 2007-03-20
I'll take a look, cheers :)

---

### Post by RichGuk on 2007-03-21
Ok, it seemed to work just enabling 

echo "1" > /proc/sys/net/ipv4/ip_forward

stuff displayed when typing "route" seemed to set its self up correctly, I think.

Works since I added a static route on the router.

Will this be ok, or do I need to open much more? :)

---

### Post by RichGuk on 2007-03-21
Also anyway to make windows hostnames stuff work over the two networks? So I can still type "firefly" instead of the IP from the external network. And and the external network's PC name from the internal network?

---

### Post by Mr. C. on 2007-03-21
> **RichGuk said:**
> Ok, it seemed to work just enabling 

echo "1" > /proc/sys/net/ipv4/ip_forward

stuff displayed when typing "route" seemed to set its self up correctly, I think.

Works since I added a static route on the router.

Will this be ok, or do I need to open much more? :)

Great!

I don't know what you mean by "open much more".  You have your router configured - thats it for basic routing.
> 
Also anyway to make windows hostnames stuff work over the two networks? So I can still type "firefly" instead of the IP from the external network. And and the external network's PC name from the internal network?

I don't think you mean "firefly" from the "external" network, as that would be the WAN, right ?  If so, you'd have to use fully qualified domain names (FQDN) such as firefly.mydomain.com, and for that, you'll have to obtain either your own DNS name, or use one of the freebie services.

For your LAN clients, the simplest way is to add lines to /etc/hosts:

```
127.0.0.1    localhost
192.168.0.1  gw
192.168.0.2  myhost myhost.mydomain.com
```

MrC

---

### Post by RichGuk on 2007-03-21
Cheer mate for all the help, life saver... *saves money for gig switch* <3.

---

