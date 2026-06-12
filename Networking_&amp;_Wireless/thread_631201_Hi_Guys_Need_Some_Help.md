---
title: "Hi Guys Need Some Help"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by benji12 on 2007-12-04
I have 3 pcs in my house we will call the 1st pc-a second pc-b third pc-c ok pc-a has win xp running and has the direct link to the internet and has to network cards installed pc-b is my server running ubuntu that has two network cards installed and pc-c has win xp also with 1 network card pk the problem is i cant get the internet on pc-b but pc-a and pc-c are fine ill try a little diagram    
cable--------pc-a---------pc-b----------pc-c
and the other thing i cant do from ubuntu is get all the pcs to share files i have samba installed on pc-b as well its all getting quite confusing as well im starting to get used to the command line as well
thankyou for any help it would be most welcome

---

### Post by SteveHillier on 2007-12-04
The diagram you posted looks like a bus type network which I find difficult to comprehend in this day and age.  
What is your modem type?  Are you connecting Cat5?  Have you got a switch in the system?
How about using an arrangement such as

pc a       pc b       pc c

         switch

         modem

I have had no problem getting Ubuntu to connect.  You might like to check your gateway address and make sure Ubuntu is seeing it.   You might like to check which of your network adapters is connecting.

Hope this might be some help

---

### Post by benji12 on 2007-12-04
lol thanks mate for your reply i had ubuntu on the net but i unpluged the network cables from pc-b to pc-c and now i cant get the net and the modem is a dsl modem

---

### Post by webdr on 2007-12-04
ok, hopefully I understand this correctly.
You have:

Internet <----> Router w/ DHCP/switch

Router/switch <---->PCA
Router/switch <---->PCB (interface: eth0 or eth1?)
Router/switch <---->PCC

Is that right?

-WebDr

---

### Post by benji12 on 2007-12-04
Yep thats right mate minus the switch just using network cards

---

### Post by benji12 on 2007-12-04
yep and im using the eth0 and eth1 interface

---

### Post by benji12 on 2007-12-04
eth0 is set to dhcp and eth1 is using a static ip address for local network

---

### Post by SteveHillier on 2007-12-05
> **benji12 said:**
> Yep thats right mate minus the switch just using network cards

Can I quiz?  Does your router have an integrated switch.  Perhaps you can post the model number.  For example a Netgear DG834 has 4 LAN sockets which are the computer side of a switch.  Internally there is a gateway that will route stuff between the LAN and the WAN.  And further in than that is the DSL modem (all in one neat little box eh!)

Next, are you using fixed IP addresses on all machines or is your router running DHCP and allocating addresses.  If so what address range is it setting and does your fixed IP fit in with that scheme.  Perhaps you can do an IPCONFIG /ALL on your windows machines and check the ip addresses, the mask and the gateway address.  The similar command on Ubuntu is IFCONFIG and that will tell you how your local adapters are set up.

My gut feeling at this point is that your IP addresses are not matching.  Can you ping between the machines?

Have a go at that and come back again.

---

### Post by webdr on 2007-12-08
Benji,

Are you connecting PCB eth0 AND eth1 to the same physical layer (switch) and
allocating them both to the same subnet? 

Internet <----> Router w/ DHCP/switch

Router/switch <---->PCA
Router/switch <---->PCB -eth0 (dhcp; 192.168.1.0/24)
Router/switch <---->PCB -eth1 (Static; 192.168.1.0/24)
Router/switch <---->PCC

-webdr

---

### Post by SteveHillier on 2007-12-10
> **webdr said:**
> Benji,

Are you connecting PCB eth0 AND eth1 to the same physical layer (switch) and
allocating them both to the same subnet? 

Internet <----> Router w/ DHCP/switch

Router/switch <---->PCA
Router/switch <---->PCB -eth0 (dhcp; 192.168.1.0/24)
Router/switch <---->PCB -eth1 (Static; 192.168.1.0/24)
Router/switch <---->PCC

-webdr

Yes, that might give a problem, but....
if eth0 is allocated by DHCP and eth1 statically, then surely the router would recognise the static address on eth1 and then allocate a different address via DHCP to eth0??
I suspect things would be better if only one of the interfaces were to be used.  It seems that there is no requirement for PCB to act as a gateway as there is only one local network.  The modem/router would act as the internet gateway.

I think Benji12 needs to feed back before this can go further.

---

