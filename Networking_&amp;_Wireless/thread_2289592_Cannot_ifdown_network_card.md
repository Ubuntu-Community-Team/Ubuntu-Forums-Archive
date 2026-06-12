---
title: "Cannot ifdown network card"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by blazeag on 2015-08-05
Hi, I'm on Ubuntu Server 14.04.2. My server has two network cards: p5p1 and p4p1. All is working fine.

My /etc/network/interfaces:

```

auto p5p1 p4p1

iface p5p1 inet static
        address 10.11.12.100
        netmask 255.255.255.0
        broadcast 10.11.12.255
        gateway 10.11.12.1

iface p4p1 inet static
        address 92.93.94.68
        netmask 255.255.255.248
        broadcast 92.93.94.71

# Static routes
up route add -net 10.0.0.0/8 gw 10.11.12.1 dev p5p1
up route add -net 0.0.0.0/0 gw 92.93.94.65 dev p4p1

```


The problem is: how can I restart a network card without having to reboot server? I tried:

```
ifdown p4p1 && ifup p4p1
```

but the result is:

```

ifdown: interface p4p1 not configured
RTNETLINK answers: File exists
Failed to bring up p4p1.

```

I'm sure I'm doing wrong some way, but what?

---

### Post by steeldriver on 2015-08-18
It looks to me more like you can't bring the interface *up* - the

```
RTNETLINK answers: File exists
```

error is often related to trying to specify multiple gateways with the same metric, I think (but I don't understand what you are trying to do here).

---

### Post by blazeag on 2015-08-20
Hi,

thank you for your reply. I'm trying to make all requests for 10.0.0.0/8 go through p5p1 card, and all other traffic through p4p1 card. I specified only one gateway (in p5p1) so it can act as default gateway.
I read a lot about this kind of error, and the fact it commonly derives from specifying two gateways, but as you can see I specified only one.

Strangely "interface p4p1 not configured" is still here. I do not know which way to turn.

---

### Post by blazeag on 2015-08-28
Bump. Obviously it is a bigger problem than I though :)

---

### Post by The Cog on 2015-08-28
It would help to try to do the ifdown and ifup as separate commands so you can see which command the error messages are coming from.

I have sometimes seen an issue where ifdown refuses with a "not configured" error but iful refuses with "file exists". I haven't invedtigated in detail, but I think the scripts are trying to control two states which have got out of sync.

After issuing ```
ifdown p4p1
```, try then issuing ```
ifconfig p4p1 down
```. See if ifup works after that.

P.S.
I think it's more normal to add the static routes as the relevant interface comes up, more like this:
```

auto p5p1 p4p1

iface p5p1 inet static
        address 10.11.12.100
        netmask 255.255.255.0
        broadcast 10.11.12.255
        gateway 10.11.12.1
        up route add -net 10.0.0.0/8 gw 10.11.12.1 dev p5p1

iface p4p1 inet static
        address 92.93.94.68
        netmask 255.255.255.248
        broadcast 92.93.94.71
        up route add -net 0.0.0.0/0 gw 92.93.94.65 dev p4p1


```

---

### Post by blazeag on 2015-09-30
Ok, I finally resolved, it was the default gateway: I changed it to the server address itself, and now it works like a charm. I also moved static routes as you suggested.

This is the working configuration:

```

auto p5p1 p4p1

iface p5p1 inet static
        address 10.11.12.100
        netmask 255.255.255.0
        broadcast 10.11.12.255
        gateway 10.11.12.100
        up route add -net 10.0.0.0/8 gw 10.11.12.1 dev p5p1

iface p4p1 inet static
        address 92.93.94.68
        netmask 255.255.255.248
        broadcast 92.93.94.71
        up route add -net 0.0.0.0/0 gw 92.93.94.65 dev p4p1

```

Thank you very much, I can put a SOLVED in the thread title

---

