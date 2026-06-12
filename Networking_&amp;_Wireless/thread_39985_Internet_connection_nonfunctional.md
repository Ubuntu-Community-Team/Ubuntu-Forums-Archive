---
title: "Internet connection nonfunctional"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by hbchrist on 2005-06-07
I can't believe I'm the only one to ask this *particular* question, so if another thread has discussed it, please point me to it. I did look before posting, but I found most discussions concentrated on wireless connectivity.

I have an older Celeron 700 tower computer that I have loaded with U5.04. The install was flawless, and all components, including the network config, installed without a hitch.

Upon reboot, the system receives an IP from the DHCP (Windows) server. The default gateway and subnet mask are also correct. However, I absolutely cannot get out to the internet.

The most frustrating thing about it is that I have two other U5.04 systems, both wireless laptops, that connect to my WEP APs and access the net with no problems. Because all of the hardware on the tower is recognized and working correctly, I am bamboozled as to why it cannot access the net.

Here is the setup: Tower computer --> 10/100 switch --> 10MB hub --> Linksys router --> Cable modem --> Internet. I have a WinXP system in the same room as the tower, and it also uses the 10/100 switch. The XP system access the net without issue.

I have not taken the tower down to the data center (my basement  ;-) ) and plugged it into the router directly, yet. I will try this tonight when I get home, but I wanted to post this issue in the morning in the hopes that the Ubuntu community can provide some insights. 

Lastly, the user name I assigned myself for the U5.04 tower is identical to the name I've given to my laptops. I have not placed the tower into any special domains or workgroups, and the network config is exactly the same as the laptops in all respects.

TIA,
hbchrist

---

### Post by lt_kije on 2005-06-07
Well, that's weird. Have you tested the network at various levels?

1. Try pinging 127.0.0.1 (just to verify that your TCP/IP stack isn't dead)
2. Try to ping the IP of the DHCP server (eg 192.168.0.1)
3. Try to ping a highly available IP, eg Google (216.239.37.99)
4. Try to ping google.com by domain name (eg google.com)

Each of the above steps moves you one level higher in your network, so to speak. Do they all work? Which, if any, fails? How?

Also, and I assume this isn't the case, but I have to ask: are there any special authentication mechanisms on the router/dhcp server?

HTH,
lt_kije

---

### Post by hbchrist on 2005-06-07
[QUOTE=lt_kije]Well, that's weird. Have you tested the network at various levels?

1. Try pinging 127.0.0.1 (just to verify that your TCP/IP stack isn't dead)[/QUOTE]

Yes, this works.

[QUOTE=lt_kije]2. Try to ping the IP of the DHCP server (eg 192.168.0.1)[/QUOTE]

This fails, as do steps 3 and 4 with the "destination unreachable" message. For the record, I am on a 10.x.x.x subnet, so I'm not using any public IPs.

And that is why it is so bizarre. Upon boot, the system *successfully* broadcasts for an IP and the W2K3 server responds and leases it a correct IP.


[QUOTE=lt_kije]Also, and I assume this isn't the case, but I have to ask: are there any special authentication mechanisms on the router/dhcp server?[/QUOTE]

None. It is WEP protected which only matters to the wireless laptops, of course. The wired systems should have no issues. 

Thanks,
hbchrist

---

### Post by hbchrist on 2005-06-10
*bump*

Does anyone else have any ideas on this issue?

I moved the server into the data center, but it still refuses to access the internet. I have connected the NIC to the SMC hub, and I have connected it to the Linksys router. Despite the fact that the NIC card gets an IP lease from my W2K DHCP server, it cannot ping the DHCP server, the router, or any addresses on the internet. 

I have set up numerous laptops without issue, but this workstation is mindboggling.

TIA,
hbchrist

---

### Post by voidlogic on 2005-06-11
Try making sure your ethernet is the deafult connection to the net. I had a problem after an upgrade where I had to set eth0 to be default using the route command. Hope that helps.

voidlogic

-----------------------
I need Help!
[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)
 ](*,)  ](*,)  ](*,)

---

### Post by kleeman on 2005-06-11
What do the following commands show?

ifconfig

and

dmesg | grep eth

---

### Post by hbchrist on 2005-06-12
[QUOTE=kleeman]What do the following commands show?
ifconfig[/QUOTE]

I will have to post this later. I can't find a good floppy to write a text file to so I can sneaker net the results. For now, the output looks OK.

[QUOTE=kleeman]dmesg | grep eth[/QUOTE]

This part I copied by switching between monitors and typing:

e100: eth0: e100_probe: addr 0xd8101000, irq 10, MAC addr 00:08:C7:AA:A0:B6
e100: eth0: e100_watchdog: link up: 10Mbps, half-duplex
eth0: no IPv6 routers present
NETDEV WATCHDOG: eth0: transmit timed out

The NIC in the workstation connects physically to an SMC Elite 3512TP 10Base-T hub which connects to a Linksys Cable/DSL VPN router 10/100 switch, model # BEFVP41. The cable/dsl router is *not* wireless, but it is updated with the latest firmware.

---

### Post by kleeman on 2005-06-12
You appear to be having nic driver problems judging from this line:

NETDEV WATCHDOG: eth0: transmit timed out

(this is the network dropping out for some reason)
I searched on this error in google and the threads it showed suggested driver problems. I would suggest you report this as a bug:

 [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

The developers will answer from my experience......

---

### Post by hbchrist on 2005-06-12
I will do that. I will also root around for another card, maybe one that is more standard, although I am pretty sure that I have a 3Com 905 in there. 

Thanks for all the help.

hbchrist

---

### Post by hbchrist on 2005-06-13
Update..

The previous NIC was a Compaq labeled card that I redeployed from an old Compaq workstation. The current tower is *not* an old Compaq, it is a white box I built on my own some years ago.

I replaced the problem NIC with a Linksys LNE100TX. Ifconfig still shows the card receiving an IP from the DHCP server but the system still is denied access to the net. However, when I do 'dmesg | grep eth', the NETDEV WATCHDOG message has disappeared and I am left with:

eth0: Lite-On 82c158 PNIC rev 32 at 0001e400 <the card's MAC address>, irq 10
eth0: no IPv6 routers present

I'm guessing the IPv6 has to be disabled. I can Google that as well as the error msg pertaining to the routers, but I still welcome some insight as to what is going on here.

Thanks,
hbchrist

---

