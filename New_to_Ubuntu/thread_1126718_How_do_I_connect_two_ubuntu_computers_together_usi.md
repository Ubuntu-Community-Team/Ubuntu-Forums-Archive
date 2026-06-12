---
title: "How do I connect two ubuntu computers together using an ethernet cable (Cat5)?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by andrewwg94 on 2009-04-15
^

---

### Post by halitech on 2009-04-15
do you have a router or hub? are you wanting to share files or an internet connection?

little more details as to what you want to do would make it easier for us to help you

---

### Post by andrewwg94 on 2009-04-15
> **halitech said:**
> do you have a router or hub? are you wanting to share files or an internet connection?

little more details as to what you want to do would make it easier for us to help you

i just want to connect the two computers directly, without a router.

---

### Post by Twitch6000 on 2009-04-15
> **andrewwg94 said:**
> i just want to connect the two computers directly, without a router.

Not possible without a router or hub.

UNLESS your modem has more then one port which is not likely.

Edit: Nevermind... it seems I was incorrect...

You can use a crossover cable.

---

### Post by halitech on 2009-04-15
ok, you will need to set IP addresses, gateways, etc on both systems manually. Also, do you have a cross over cable or a patch cable?

---

### Post by halitech on 2009-04-15
> **Twitch6000 said:**
> Not possible without a router or hub.

not true, cross over cable and setting info manually will work fine.

---

### Post by mindas22 on 2009-04-15
If You use router or switch, You need normal cable.

If you are going to connect you need [Ethernet crossover cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

---

### Post by Twitch6000 on 2009-04-15
> **halitech said:**
> not true, cross over cable and setting info manually will work fine.

My mistake then... I learned something new.

---

### Post by halitech on 2009-04-15
> **Twitch6000 said:**
> My mistake then... I learned something new.

its not the fun way of doing things and can drive you crazy trying to figure out why the connection doesn't work (if it doesn't work) but it is possible.

[http://www.herongyang.com/win/crossover.html](http://www.herongyang.com/win/crossover.html)

---

### Post by llamabr on 2009-04-15
> **Twitch6000 said:**
> Not possible without a router or hub.

UNLESS your modem has more then one port which is not likely.

That's not right.  You can set up a crossover without going through a router or a switch.  It's a pain, and you have to set up static IP.  In the end, it'll be worth it to spend a few bucks on a switch.

And, most boxen come with wireless, as well as an ethernet plug, making it possible to share internet taken via wireless to a wired box.

---

### Post by jowilkin on 2009-04-15
If both computers have gigabit ethernet ports (common on newer computers) then you don't even need a crossover cable.  A regular ethernet cable will work fine.  You just need to setup the ip addresses.

---

### Post by lisati on 2009-04-15
I've read of others in this forum connecting direct NIC to NIC, but haven't done it myself.
I'd recommend that if your budget permits, you get some kind of switch or router: this can simplify things somewhat if you later want to add more machines to your home network (I currently have 4 machines networked at home, different capabilities and different roles)

---

### Post by alphacrucis2 on 2009-04-15
> **jowilkin said:**
> If both computers have gigabit ethernet ports (common on newer computers) then you don't even need a crossover cable.  A regular ethernet cable will work fine.  You just need to setup the ip addresses.


I can confirm this with my new laptop which has a gig ethernet port. The transceiver seems to be able to figure out which way round transmit and receive are and can therefore do back to back without a crossover cable.

Edit - additional info:

[QUOTE="Wikipedia"]Automatic crossover

Automatic MDI/MDI-X Configuration is specified as an optional feature in the 1000BASE-T standard[1], meaning that straight-through cables will usually work between Gigabit capable interfaces. This feature eliminates the need for crossover cables, making obsolete the uplink/normal ports and manual selector switches found on many older hubs and switches and greatly reducing installation errors. Note that although Automatic MDI/MDI-X is generally implemented, a crossover cable would still be required in the occasional situation that neither of the connected devices has the feature implemented and enabled. Prior to the 1000Base-T standard, using a crossover cable to connect a device to a network accidentally, usually meant wasted time troubleshooting the resulting lack of connection, but with this standard in place, that is no longer a concern.

Even for legacy 10/100 devices, many NICs, switches and hubs automatically apply an internal crossover when necessary. Besides the eventually agreed upon Automatic MDI/MDI-X, this feature may also be referred to by various vendor-specific terms including: Auto uplink and trade, Universal Cable Recognition and Auto Sensing.[/QUOTE]

---

### Post by mprince on 2009-04-15
I connect a Mac and ubuntu machine together with a crossover cable and share the internet connection from the mac > to the ubuntu machine. I also set up a samba share for file sharing.

It wasn't that hard to set it all up. I figure two ubuntu machines should   even play nicer together.

---

### Post by lkraemer on 2009-04-16
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1031300&page=2](http://ubuntuforums.org/showthread.php?t=1031300&page=2)
Post #15

lkraemer

---

### Post by unutbu on 2009-04-16
Use a crossover cable to connect the two machines, NIC <--> NIC.

I assume:
[list]
[*]the NIC interface on both machines is called eth0.
[*]Computer A has ip address 192.168.0.1
[*]Computer B has ip address 192.168.0.2
[/list]

On Computer A:
```

/sbin/ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.2 eth0

```

On Computer B:
```

/sbin/ifconfig eth0 192.168.0.2 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.1 eth0

```

Now on Computer A you should be able to ping Computer B:
```
ping 192.168.0.2
``` (And vice versa, B should be able to ping A.)

---

