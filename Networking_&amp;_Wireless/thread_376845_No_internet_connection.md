---
title: "No internet connection"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by xTonyx on 2007-03-05
Sorry guys, I'm another newbie having problems setting up the internet in ubuntu.
Help would greatly be appreciated. My hardware config is

cable connection to internet via a cable modem connected to ethernet of computer. Basically I'm typing this on my Mums shiny new vista machine with ubuntu booted off the live cd. When hooked up in this set up the internet is available immediatly with no extra set up required. IP etc set up through DHCP. 

However when I plug the ethernet cable into either of the two nic in my computer, which is running ubuntu,  I get no connection.
```
xtonyx@xtonyx-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:E3:1E:7C:D8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:62:4B:5D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2201966 (2.0 MiB)  TX bytes:12996 (12.6 KiB)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10184 (9.9 KiB)  TX bytes:10184 (9.9 KiB)
```

Both network cards are different types, tho I forget now what eth0 card is, however eth1 is rtl3189d with ubuntu running the 8139too module. I can't help but think it is a striking resemblence to [dbauer3851's problem]("http://www.ubuntuforums.org/showthread.php?t=376737") (due to similar problem and similar chipset on NIC) so I'm keeping an eye it however  they seem to be approaching the problem by disabling DHCP and configuring it as a static IP which I don't think would work with my setup as I don't think I have much control over the cable, or do I?

Couple of things about my ISP; cable connection, don't need to input a password or username to access internet and I don't think it's a informing them about a MAC address problem as apparently they stopped limiting MAC addresses and I've never had to register the MAC address of the NIC in the computer I'm using now.

Go easy on me, I'm new!!!!

---

### Post by wesley_of_course on 2007-03-05
Wesley here ;

   I'm  a noob but maybe disabl'in one of your 'Nic's  so Ubuntu sees only ????

        Shot in the dark from me . Good Luck and don't give up , I'm sure someone a whole lot knowledgable will come up with a solution .Or point in the right direction .

---

### Post by Mr. C. on 2007-03-05
You have two NICs on your system, one connected to the cable modem, one not, correct?

For the one that is connected, do you have a Link light (the light on the back of the NIC, if there is one, will indicate that the hardware - NIC and Modem - are communicating).

If you have these lights, but they are unlit, try the other interface.

I see that there have been 38 packets sent out via ETH1, nothing on ETH0.

MrC

---

### Post by xTonyx on 2007-03-06
> **Mr. C. said:**
> You have two NICs on your system, one connected to the cable modem, one not, correct?

For the one that is connected, do you have a Link light (the light on the back of the NIC, if there is one, will indicate that the hardware - NIC and Modem - are communicating).

If you have these lights, but they are unlit, try the other interface.

I see that there have been 38 packets sent out via ETH1, nothing on ETH0.

MrC

Yeah you're right. I have tried both interfaces (in the instance I copied the ifconfig it was eth1 that was connected, as you rightly spotted). Both cards light up when connected, they just seem to be unable to set up and IP etc. 

As for disabling one of the cards, I will try however I suspect it might not be the solution as I originally only had one card in and was unable to connect, suspecting it might have been a hardward problem I inserted a second NIC I had of different chip set to see if that solved it.

---

### Post by Mr. C. on 2007-03-06
Ok, set lights on tells us the modem - nic are communicating with each other (i'm presuming those lights go off when you unplug that cable, right ? )

This means you have established Link.

Now, looking at your output from earlier.  I see that there is NO IP address assigned.  This is required before anything else will work.  If your broadband provider only gives dynamically assigned addresses, you must use that.  Don't use a static IP, as that will likely conflict with someone elses.

Are you SURE they are not doing MAC address filtering ?  It is possible that they auto-register the first device connected.

It might be possible for you to change the MAC address of your system to be the same as your moms.  This will confirm MAC address filtering.

If you have a crossover cable, you could try a connection between your mom's PC and your system.   You will need static IPs, but it might just work on its own, as Windows will assign a private local address, and Ubuntu may also (not sure of the later).  If this connection works, you know you have MAC filtering issues.

Do you have a switch, so that both computers can be connected at the same time?  This would greatly aid in debugging.

MrC

---

### Post by xTonyx on 2007-03-06
Don't think it's MAC filtering, the card I'm trying to get working (eth1) is out of my mum's old computer and has the only MAC address we have ever registered (and the new computer worked without registering).

I agree with the no IP address is my problem, I'm just banging my head against the screen trying to find out why its not accepting an IP through dchp. 

I have a router on its way and a wireless card, was hoping to set up my machine ina wireless network. Looking at this forum wireless networking is going to be an absolute sod lol. It might worth seeing if I can get the 2 computers connected through ethernet using the router.

I've got some more complex diagnostic tools for my chipset to see if that can be enlightening, which I will post up tomorrow. One strange thing I've noticed is that using the diagnostic tools its saying it's "rtl3189C" chipset. Yet clearly stamped on the chip is "rtl3189D". Ubuntu is using driver rtl3189too for the card, which says its for rtl3189a/b/c/+ or something like that. Could it be possibly a driver problem? I found a winxp driver for rtl8139d which can be used with ndiswrapper, and has been used apparently to get rtl3189d card to work. I tried this but I don't know how to get ubuntu to use the ndiswrapper driver instead of the 8139too. 

I

---

### Post by Mr. C. on 2007-03-06
The driver has recognized and accepted the card.  This is probably a minor chip revision; happens all the time.

If the changes were more fundamental, Realtek would have changed a value in the PCI configuration params.

Its not that your system isn't "accepting an IP through dchp"; rather, your card is broadcasting a request on the wire to anyone that will listen.  One of two things is happening: a) nothing is reaching the DHCP server, or b) nothing coming from the DHCP server is finding its way to your card.  In otherwords, something is blocking the traffic.

Do you know how to run wireshark or tcpdump ?  You can run these to see every pattern of traffic to/from the NIC. 

MrC

---

