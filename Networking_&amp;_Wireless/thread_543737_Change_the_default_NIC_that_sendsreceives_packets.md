---
title: "Change the default NIC that sends/receives packets"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Breathe on 2007-09-05
I've spent a lot of time trying to solve this issue. I don't like the way in which Ubuntu 7.04 manages the NICs.
My current configuration is:

eth0 : My cable network interface
eth1 : My wireless

Since i installed my wireless if I am navigating through Internet the packets are sent/received through the eth1 connection. I also have a LAN with other computers that have Windows installed (this will change very soon... XD) and when I download any file from one of these computers the packets are sent through eth0, while eth1 receives them. I presuppose that this way of working can be changed since this way of sending and receiving information is not the common thing in windows local networks... Therefore, it must exist a file that manages the different ways of working.

And i wanted to add something more ... why is the wireless activated when i start up ubuntu? I would like to have the wireless disabled on startup, and if i need the wireless, re-enable it with out a restart...

---

### Post by guardsman85 on 2007-09-05
Would you describe your network's topology in a little more detail?  Specifically, is the switch that your computers are connected to built into the wireless access point?

---

### Post by Breathe on 2007-09-05
I've got a 4-port router and a modem ADSL with one RJ45 port. In this port i connect my 4-port router so i have 3 ports free to connect my two computers and a printer.

The IP for the modem ADSL is 192.168.1.1
The IP for the 4-port Router is 192.168.1.2

So my computers have been configured like this:

Windows PC config:   Default Gateway: 192.168.1.2
                                   Private IP: 192.168.1.10 / 24
 
Ubuntu 7.04 config:   Using NetworkManager
                                   eth0:   Default Gateway: 192.168.1.2
                                              Private IP: 192.168.1.10 / 24
                                   eth1:   Roaming Moad
                                              ifconfig:
                                                             Private IP: 192.168.1.4
                                                             Broadcast: 192.168.1.255

---

### Post by guardsman85 on 2007-09-05
> **Breathe said:**
> I've got a 4-port router and a modem ADSL with one RJ45 port. In this port i connect my 4-port router so i have 3 ports free to connect my two computers and a printer.
My guess is that the issue is with your AP/router.  Since the switch is integrated into the access point, that device is picking the interface on which to send your traffic (in this case the WiFi).  You could try setting a static routes to each of your machines on your router (if it allows setting routes with specific interfaces) or you could try a second switch:

[Router/AP/Switch] o---o [Switch2] o---o [PC]

This way the second switch will see the best path to the second PC as the Ethernet connection.

---

### Post by Breathe on 2007-09-05
Thanks for your help,

I think i didn't explain well, this is my network topology:

[AP/one port (it can't be a switch because it only has one port)] o---o [router w/ AP disabled = Switch of 4 ports] o---o PC 1,2,3 because port 4 is used to connect the router with the AP/one port

---

### Post by Breathe on 2007-09-05
AH!! I forgot, the Router with the acces point disabled has wireless capabilities and has a range from port 3 to 10

---

### Post by guardsman85 on 2007-09-05
> **Breathe said:**
> has a range from port 3 to 10
sorry, not quite sure what you mean by this.  could you explain?

---

### Post by Breathe on 2007-09-05
Let's begin... XD

I've got a modem ADSL with one RJ45 port.
Configuration for this device:
  DHCP
	DHCP		                                      Server
	Client IP Pool Starting Address		  192.168.1.2
	Size of Client IP Pool                           253
 TCP/IP
	IP Address 		                            192.168.1.1
	IP Subnet Mask                                   255.255.255.0
        RIP Direction 	 	                            Both
	RIP Version 		                            RIP-2B
	Multicast                                              IGMP-V2

Connected to this device I've got a modem-router with 4 ports but i've disabled the AP so i use it as a switch
Configuration for this device:
  DHCP
	DHCP		                                      Relay
	Client IP Pool Starting Address		  N/A
	Size of Client IP Pool                           N/A
 TCP/IP
	IP Address 		                            192.168.1.2
	IP Subnet Mask                                   255.255.255.0
        RIP Direction 	 	                            Both
	RIP Version 		                            RIP-2B
	Multicast                                              IGMP-V2
 WIRELESS
        Enabled

And then i've got the computers both windows and linux configured the same way:
Default Gateway:        192.168.1.2
Ethernet Private IP:     Static Mode: 192.168.1.10 / 24 for win  192.168.1.69 / 24  for linux
Wireless:                     Roaming Mode (The DHCP configured in the first device does it for me)

---

### Post by Breathe on 2007-09-05
Let's begin... XD

I've got a modem ADSL with one RJ45 port.
Configuration for this device:

[LIST=1]
DHCP: Server
Client IP Pool Starting Address: 192.168.1.2
Size of Client IP Pool: 253
IP Address: 192.168.1.1
IP Subnet Mask: 255.255.255.0
RIP Direction: Both
RIP Version: RIP-2B
Multicast: IGMP-V2
[/LIST]


Connected to this device I've got a modem-router with 4 ports but i've disabled the AP so i use it as a switch
Configuration for this device:
[LIST=1]
DHCP Relay
Client IP Pool Starting Address N/A
Size of Client IP Pool N/A
TCP/IP
IP Address 192.168.1.2
IP Subnet Mask 255.255.255.0
RIP Direction Both
RIP Version RIP-2B
Multicast IGMP-V2
WIRELESS
Enabled
[/LIST]




And then i've got the computers both windows and linux configured the same way:
Default Gateway: 192.168.1.2
Ethernet Private IP: Static Mode: 192.168.1.10 / 24 for win 192.168.1.69 / 24 for linux
Wireless: Roaming Mode (The DHCP configured in the first device does it for me)

---

### Post by Breathe on 2007-09-05
Sorry, read the last post, i don't know how to write in a clean way in the forum... :(

---

### Post by Breathe on 2007-09-05
But don't you think my problem of who receives and who sends isn't an issue of Ubuntu???
I've played aroud with this two files:
/etc/samba/smb.conf
/etc/network/interfaces
But i don't know how to manage them confortably. I undestand a bunch of things about networks but smb.conf has much more things... :)

---

### Post by guardsman85 on 2007-09-06
First off, smb.conf won't help you with this particular problem.  That used to configure Windows shares.:)

> **Breathe said:**
>     DHCP                                              Server
    Client IP Pool Starting Address          192.168.1.2
    Size of Client IP Pool                           253
OK, this doesn't really directly fix the problem, but it's just something that I noticed; you can cut down your DHCP pool.  Since you're using a lot of static addresses on your network you don't want to run into potential addressing conflicts.  You might want to change the pool to start at .100 and have only a number of addresses equal to the number of DHCP client computers you will have on your network.

> **Breathe said:**
>  Connected to this device I've got a modem-router with 4 ports but i've disabled the AP so i use it as a switch
Configuration for this device:
  ...
 WIRELESS
        Enabled
Maybe this is a typo, there seems to be a contradiction.  Is this actually disabled?  (Sorry, just trying to make sure.:()  It still seems to me that your better bet would be to replace the 4-port router with an actual switch if possible.  Sorry if I'm not being much help, I'm still just a bit confused.:confused:

---

### Post by Breathe on 2007-09-07
Well, i've been doing some reserch and I have found something very important... I had my ideas a little bit confused... I thought till yesterday that an AP (Acces Point) was the device that made the connection between my house and my ISP (Internet Service Provider) and that's a big mistake.
I've learned that an AP is the device that you can connect to a router or switch and have the possibility of connecting wireless computers.

So, with this new concepts I can explain it much better... XD

> Connected to this device I've got a modem-router with 4 ports "but i've disabled the AP" so i use it as a switch

What I wanted to say is that i've disabled the ADSL capabilities... So, it's working as a router. I think that with this correction I've done, the contradiction you found is solved.
Ah!!! And forget the modem-router definition, i meant a router... It's a bad definition we use commonly here in spain, and i've found that, modem-router is a great mistake....

So, looking back to the original problem...

PC1   PC2    PC3
-----------------------------  R1 (Wireless Enabled)  ------------ R2 --------- WAN

You are maybe thinking... Why does this guy have two routers when he could use only one to get into the WAN... Well, the R1 isn't working very good, it doesn't synchronize with my ISP so i have to use another router that is working allright but that only has one RJ45 port... so i use it as a gateway to the WAN...

So R2 has IP: 192.168.1.1 / 24   so it's broadcast IP is: 192.168.1.255   (DHCP Enabled:  Starting at 192.168.1.2 and ending at 192.168.1.254 ***)
And R1 has:
[LIST]IP: 192.168.1.2 /24
DHCP: Relay	
Client IP Pool Starting Addres: N/A	
Size of Client IP Pool: N/A	
Remote DHCP Server: 192.168.1.1 ***
[/LIST]
 	

Does R1 have a broadcast IP??? (*** R1 doesn't assign IP's by DHCP to the wirelles or cable PC, it's R2's job... R1 relays on R2)... If the answer is yes, then, i don't know if this is a problem:

> DHCP Server
Client IP Pool Starting Address 192.168.1.2
Size of Client IP Pool 253

This info is obviously from the R2 config and as you can see the size of the pool is 253, so the last possible IP is: 192.168.1.254

(If the answer was yes, :P) Doesn't this conflict with the Broadcast IP of R1 ??? (I think that if R1 has a broadcast IP that would be 192.168.1.254, not sure)

Well, if you can help me with this, i would be grateful for your support...

Two more things, ive got one or two more routers in my storage room... if you think my topology is a mess, please tell me so... XD
And the last thing, sorry that i repeat myself, but don't you think my problem of who receives and who sends data isn't an issue of the OS, in this case Ubuntu???

Thanks a lot...

---

### Post by guardsman85 on 2007-09-08
Alright, that clears up a little of my confusion! :)  I think you still may be a little confused on your networking theory though.  Let's see if I can explain...

[FONT=Arial]First, let's look at your subnetwork (subnet) and what the addresses mean.  We will use the subnet mask 255.255.255.0 as you have.


[/FONT]      [FONT=Arial]_192.168.1_.0  - This is your network (subnetwork) address.  Since you are using 255.255.255.0, the network portion of all your addresses is the part underlined (192.168.1).  All your devices starting with the underlined part of the address are said to be in the 192.168.1.0 network.


[/FONT]       [FONT=Arial]192.168.1.1 – This is your first host address.  Since you are using this address for your ADSL modem, it is the default gateway for the other devices on the 192.168.1.0 network.  This means that in order to get to any other address not on the 192.168.1.0 network the other computers will contact 192.168.1.0.


[/FONT]       [FONT=Arial]192.168.1.2
[/FONT]   [FONT=Arial]192.168.1.253 – These are your remaining host addresses to be used for any other devices on the 192.168.1.0 network.


[/FONT]       [FONT=Arial]192.168.1.254 – The last address in the network is always the broadcast address.  Each device doesn't have a broadcast address—each *network* does.  Devices use this address to communicate with all devices on the network.  It is used when a device doesn't know exactly which device to contact or when it needs to contact everyone--like for an ARP request.  It would be like someone coming into your office and announcing, “Attention, everyone, who is Breathe?”  at which point you would respond, “I am Breathe, and I am at this address!”


[/FONT]        [FONT=Arial]Alright, now a few words about routers.

[/FONT]       [FONT=Arial]Routers are designed to separate networks, so I'd suggest setting up a separate network each side of your second router.  Right now you're trying to use a router as a switch, which is probably causing some problems.  I would use static addresses for everything but your wireless.  For that, I would use DHCP from the second router (Router B in my example--see attached picture).  In your case, the switch is built into Router B.  I think if you do it this way you'll avoid sending packets all over the place to find the proper host.[/FONT]

---

### Post by Breathe on 2007-09-08
Ok... I'm going to try that way, but i need to purchase a switch. I've got too many routers and no switch in my storage room...

So it seems you are quite sure that Ubuntu isn't causing my problems??

If your answer is yes, then, why doesn't this happen in Windows??

---

### Post by guardsman85 on 2007-09-11
> **Breathe said:**
> So it seems you are quite sure that Ubuntu isn't causing my problems??

If your answer is yes, then, why doesn't this happen in Windows??
Well, I guess I'm just looking at if from the network design standpoint that if you're using devices in ways they aren't intended and you're getting problems, then the first step is go get the proper devices.  Again, sorry if I'm not giving you the help you need :(.  Anyone else have any input?

---

