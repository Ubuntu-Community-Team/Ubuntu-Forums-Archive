---
title: "Intel Gigabit network card problem."
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by kalamram on 2013-12-12
Hi,
I am using ubuntu 12.10 and have two network cards.
One NIC is D-Link and other is intel with motherboard.

00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
02:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)


Both have gigabit support, but when I am using for my experiment and like NIC bonding, I got only 1.4Gbps on combined throughput of the system.

If in actual scenario, it should be 2Gbps or atleast 1.8Gbps.

Also , i observed , in Intel ethernet port side, two LED's blinking, one is in Green and one is blinking as orange.
Is this reason for throughput decrease.
But, at D-Link side, both LED's blinking as Green.

My system has e1000e driver for Intel NIC.
What is my problem, please provide suggestion on this.

Thanks,
SJ Ram

---

### Post by tgalati4 on 2013-12-12
It could be a limit at the router's end.  Just because a router is Gigabit does not mean that all ports can be driven at gigabit speeds at once.  What is the model of the router that you are using for your testing?

Are your cables rated for Gigabit speeds?  Try swapping cables or use new cables and see if throughput increases.

How is the D-Link adapter plugged in?  PCI-e?  USB?  There could be a throughput reduction due to the data bus.

The yellow flashing light on the Intel NIC could be a collision indicator--when two network cards squawk at once, one card has to sit silent for a timeout period, to let the other traffic to get through.  That would reduce throughput.  Each card has its own timeout algorithm.  

Try connecting the NIC's to two separate routers to see if you can get greater bandwidth.

---

### Post by kalamram on 2013-12-13
Hi,
thank you for the reply.

In my setup, I connected the two systems directly by Gigabit ethernet cables.

No router or switch I used.
For D-Link NIC connection, both led with green lights, only intel motherboard NIC have blinking green and orange.

My doubt is , due the intel ethernet port, the system spped reduced to 1.4Gbps instead of 1.8-2Gbps.

Is that orange light  means Mbps support for NIC.


Thank you.

---

### Post by houstonbofh on 2013-12-13
A nic on a PCI bus is limited to about 700meg to 800meg.  From your numbers, I am betting you have one, or both on PCI...

Second, nic bonding is not true load sharing.  It is load sharing by conversation...  So unless you have multiple threads, and it is set up to share that way, you will get some losses to overhead.

---

### Post by tgalati4 on 2013-12-13
You need a business-grade router to separate the traffic between the two cards.  Your test is an exercise in connectivity, but not a true trhoughput test because you would never run your system in that configuration.  As *houstonbofh* suggested, the cards could be hampered by how they are connected to the system--PCI bus or motherboard chipset limitation.  I don't know what the orange light means, but some search on the web for that specific chipset should provide some information.  It is either a packet collision or auto-speed reduction.

---

