---
title: "Sharing network connection through windows box."
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Danzotron on 2008-05-11
Hi guys,
I'm trying to share my internet connection with my Ubuntu box, through a windows box connected via a cross over cable. It doesn't seem to like it at the moment and I was wondering if anyone would be able to give me some ideas on what settings I should be using for all of this.

So currently my network looks like this:

DSL Modem / Wireless router (192.168.0.138 )
          |
          |
       Via wifi
          |
          |
     Windows Box(Eth interface:192.168.0.1, Wifi: Dynamic, but on the same range.) 
          |
          |   
      via crossover === Ubuntu PC (192.168.0.3), Gateway address:          (192.168.0.1)
All have a subnet mask of 255.255.0

So currently when the Ubuntu box is connected to the PC and the eth interface is enabled, the internet won't work on the windows box. On the ubtuntu box I can ping the windows machine, but not the router @ 192.168.0.138, it says destination unreachable, and the internet won't work.

Any ideas on this would be greatly appreciated, or if anyone can give me some settings to try to manually configure the whole thing with, please let me know. 

Many thanks in advance,


Daniel.

---

### Post by vorgusa on 2008-05-11
Hmm I have never really tried that configuration... but to help simplify things try setting up the Ubuntu box with a Static IP of a different network, such as 192.168.1.101 and the NIC card that goes to the ubuntu box with a similar IP 192.168.1.102 and set the Default gateway on the Ubuntu box to the IP of Windows box (192.168.1.102)  That should get the information going properly, but I think there is some configuring in Windows to get it to route the information.. You will also have manually set the DNS server on the Ubuntu box.

Another option may be to select both NICs in the Network Connections Window on the windows box and tell it to bridge the connection, which should get it to work without doing any what I mentioned before.. if that does not work try adding a static IP

---

### Post by Danzotron on 2008-05-11
> **vorgusa said:**
> Hmm I have never really tried that configuration... but to help simplify things try setting up the Ubuntu box with a Static IP of a different network, such as 192.168.1.101 and the NIC card that goes to the ubuntu box with a similar IP 192.168.1.102 and set the Default gateway on the Ubuntu box to the IP of Windows box (192.168.1.102)  That should get the information going properly, but I think there is some configuring in Windows to get it to route the information.. You will also have manually set the DNS server on the Ubuntu box.

Another option may be to select both NICs in the Network Connections Window on the windows box and tell it to bridge the connection, which should get it to work without doing any what I mentioned before.. if that does not work try adding a static IP

So you are suggesting I should have the wired interfaces on a different IP range? I'll try this when I get home from work.

Does anyone else have any more ideas?

---

### Post by vorgusa on 2008-05-11
Well the first Idea was that.. the second one keeps you on one network range

---

### Post by Iowan on 2008-05-12
I'm probably confused (again), but I don't know if the box will like two NIC's in the same subgroup. As **vorgusa** suggested (or at least similar to that suggestion), try putting the ethernet connection on a different subnet (say, 192.168.1.1 and 192.168.1.2).  Change the (Ubuntu box) gateway to the new Windows address.

I've never tried the bridging option...

---

### Post by hariprs on 2008-05-12
This is very simple.

1) Have your windows PC in two subnets

* Configure wifi interface's IP as 192.168.0.2, mask 255.255.255.0 
* And your wired interface IP as 20.0.0.1, mask: 255.0.0.0, gateway 192.168.0.2

2) Enable internet sharing in Windows PC

3) Configure 20.0.0.2 as the IP for your ubuntu with subnet mask 255.0.0.0 and gateway 20.0.0.1

Thats all, it should work now.

---

