---
title: "A question about duplex"
date: 2018-04-28
forum: Networking &amp; Wireless
---

### Post by sandman887 on 2018-04-28
I've been reading about full and half duplex ethernet, and even studying my NIC manuals, various depictions and diagrams, but there is still one thing that I wasn't able to glean from those, and it involves the number of cables. Does full-duplex require two cables with a computer requiring one ethernet NIC for transmit, and a second NIC for receiving, and half-duplex one? You would think this would be something easy, but I guess I'm just missing something here :lolflag:
Thanks!

---

### Post by TheFu on 2018-04-28
no.

---

### Post by sandman887 on 2018-04-30
> **TheFu said:**
> no.

No to what?

1. Does full-duplex require two cables with a computer requiring one ethernet NIC for transmit, and a second NIC for receiving?

or

2. Does half-duplex use one NIC and one cable?

Thanks for your response.

---

### Post by Yellow Pasque on 2018-04-30
As long as the NIC and the cable you are using support full duplex, you only need one NIC. You can check with ethtool:
```
$ sudo ethtool <interface name> | grep Duplex
Duplex: Full
```

---

### Post by SeijiSensei on 2018-04-30
Full-duplex means that the adapter uses separate channels for upstream and downstream traffic. An Ethernet cable uses two of its four pairs of wires for this task, one for transmission and the other for reception.  [Only two pairs are used for 10/100BaseT]("http://www.hardwaresecrets.com/how-gigabit-ethernet-works/").  Gigabit Ethernet uses all eight wires.

Half-duplex technologies like wifi must "turn the line around," sending then waiting for a reply.  Obviously that makes them slower than full-duplex connections which can send and receive simultaneously.  Half-duplex especially takes a toll on TCP connections, which require the receiver to ACKnowledge each packet sent.

---

### Post by TheFu on 2018-04-30
Full duplex over a single ethernet cable has been standard since around 2000 for 100base-tx and faster connections over CAT5 or better cables.  Works fine with CAT3, if supported by the HW. I would be surprised if anyone actually had less than CAT5 anymore.
[https://en.wikipedia.org/wiki/Ethernet_over_twisted_pair](https://en.wikipedia.org/wiki/Ethernet_over_twisted_pair) has lots of background.

---

### Post by The Cog on 2018-04-30
Same answer but with slightly different wording:
With both half-duplex and full-duplex, you only need one Ethernet cable. The difference is that in half-duplex the behaviour is changed, and the computer is not allowed to simultaneously transmit and receive data: it has to wait until nothing is being received before beginning to send, and will abort its current transmission if it sees someone else's transmission start. In full-duplex the computer is allowed to send and receive that the same time. This difference is behavioural only, and derives from the days when Ethernet used coaxial cable (like TV aerial cable) instead of multiple twisted pairs of wires. Coax could not support two simultaneous transmitters.

---

### Post by sandman887 on 2018-04-30
Thanks for the replies. The reason I was confused was actually because of diagrams showing it, which is funny, since they probably thought making diagrams of it would make it easier to understand if one saw it. The reason was because of images like these:
[IMG]https://i.imgur.com/IEhvn4d.png[/IMG]
[IMG]https://i.imgur.com/gEyQPBL.jpg[/IMG]
[IMG]https://i.imgur.com/LEnwNdhh.png[/IMG]

From your answers, the middle one makes the most sense, showing only one NIC on both sides. However, I didn't know if the arrows were supposed to be cables or not. So from what you guys are saying, both of the "arrows" can be inside just one cable.

The reason I started researching this to begin with was to see whether I could increase bandwidth within my LAN by dedicating one cable for sending and another cable for receiving, therefore hypothetically doubling the bandwidth to and from each of my computers.

---

### Post by sandman887 on 2018-04-30
> **The Cog said:**
> Same answer but with slightly different wording:
With both half-duplex and full-duplex, you only need one Ethernet cable. The difference is that in half-duplex the behaviour is changed, and the computer is not allowed to simultaneously transmit and receive data: it has to wait until nothing is being received before beginning to send, and will abort its current transmission if it sees someone else's transmission start. In full-duplex the computer is allowed to send and receive that the same time. This difference is behavioural only, and derives from the days when Ethernet used coaxial cable (like TV aerial cable) instead of multiple twisted pairs of wires. Coax could not support two simultaneous transmitters.

Thank you, that explains it better. I didn't see your message before I posted my previous one. But it still makes me wonder if I can double the bandwidth by using one cable for sending and another cable for receiving. For example, I have two identical gigabit ethernet cards. Their manual says that they can both be 1000 Mbps full-duplex or 2000 Mbps full-duplex, which added to the confusion.

---

### Post by The Cog on 2018-04-30
You should always use full duplex these days, in which case the cable will be fully utilised. Beware that for 10 and 100M, the default if you use auto configuration they will probably settle on half-duplex which is the safe but slow option. 

It is possible to increase the speed by using two (or more) NICs and this is called NIC bonding. Both the computer and the switch it's connected to must know about the bonding. Bonding also provides some resilience in that the loss of one cable still leaves the other cable working.

---

### Post by sandman887 on 2018-05-01
Thanks for your info

---

