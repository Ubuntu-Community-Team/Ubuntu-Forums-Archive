---
title: "home office network, mixed &quot;wired&quot; and wireless"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by nsa_767 on 2007-03-04
Hi there,

I need to setup a small home office network with internet connection, file and printer sharing. Unfortunately, it is a rather complicated setup involving:
[LIST]
[*]A wireless router, directed connected to my Telkom ADSL line.
[*]A Windows XP machine connected via a LAN cable to the router.
[*]A XUbuntu 6.10 system connected to the router via a wireless connection.
[*]A Windows XP laptop connected via wireless to the router.
[/LIST]

I've managed to get ADSL setup and all the computers have access to the internet. None of the computers, however, can see each other. Trying to ping the Windows PC from Linux doesn't work. Is because the LAN and WAN are (according to my router) on different subnet masks?

So, how do I go about setting this up? Do I need to create a VPN and then somehow run Samba ontop of that? Does anyone know of any helpful guides/tutorials which will point me into the right direction?

Oh, the printer I wish to share between these computers is connected to the Windows PC. The router is a standerd Marconi / Telkom ADSL WiFi router and I'm using WEP (it's all the router and lappy support).

Thank you in afvance for whatever help you may provide.

---

### Post by sadjack on 2007-03-04
I have a very similar setup. I find it best to turn off DHCP at the router and give everything a static IP address. In my case the router is 192.168.1.254, I have allocated each client an IP address in the range 192.168.1.10 - 50. Once you have them talking to each other you can go on from there.

At least with a static IP you can work out what is talking to what and work on it from there.

---

### Post by nsa_767 on 2007-03-04
Hmmm, I don't really want to disable DHCP. But, if I have to, I will. Thanks you for the quick reply.

I'd like to hear whether anyone else has done this with DHCP enabled.

---

### Post by sadjack on 2007-03-04
Is your router showing two different subnets or two different subnet masks? If it is the latter then just make them the same. If its two different subnets, you only really need one I would suggest unless you have a specific reason.

I now use static IP because of some problems with my ubuntu setup in which it constantly lost its dns settings when using DHCP. If you search about on the forum you will see that a few people have experienced this, because my network has only 6 computers I decided I culd easily administer static IP and it solved the problem.

I think you need to have a close look at all your seetings and decide on a network scheme.

My router came with and IP address of 192.168.1.254 and a subnet mask of 255.255.255.0. I just gave all my machines an IP in range 192.168.1.1 to 50, kept the same subnet mask and gave them a DGW of 192.168.1.254 (the router) and it works.

Readup on the DHCP issues on these forums. There are other remedies

Another issue I fell foul of was not ensuring that all wireless devices had the same WEP encryption, schoolboy error but it took a while to figure it out. 

There is no reason that your setup should not work as far as I can see. Hope you get it sorted soon.

---

### Post by nsa_767 on 2007-03-05
Yes, it is the subnet mask, not the subnet (my apologies for the mistake).

I'm going to set those the same for both LAN and WAN, and see if I have better luck then.

I will keep everyone posted on my progress.

---

### Post by misterfixit on 2008-01-19
Some good answers here, but I am still trying to work out my own network problems.  I have a home office network shared with my workshop (which is an out-building).  Right now I have it set up with the cable adaptor (modem) going to a DLINK EBR-2310 wired router.  There are 3 PC's plugged into the wired router, two Ubuntu boxes and a WinXP machine.

I have a HP C7280 attached to a DLINK WBR-2310 wireless router via the HP C7280's internal WIFI system.  No wired connections to either the C7280 multipurpose printer, scanner, copier or to the WBR-2310 wireless router.  My main Linux box has both a wireless and a wired router card in it.

Everything works fine on wired.  There are no issues or problems.

I can switch on the wireless card in my PC and print directly to the HP printer.  There are no issues or problems with that part of the function.


The HP scanner function is not seen by xsane -- but that is a challenge for another forum.

I want to extend the network by placing another Ubuntu box in the workshop along with a printer.

I have a second DLINK WBR-2310 wireless router which I can place next to the wired router and the cable modem.  I have an extended range antenna and have tested it and seen excellent signal strength all around.

So, my challenge is to perhaps make the wireless router a child of the wired router?  And I'm not sure how to do that.  I can set static IP's for each computer and for the wifi printer, but I am not sure how that will effect the cable internet connection.

Hoping someone can give me a few pointers here ...

Thanks in advance!

Dave

---

### Post by An_Dynas on 2008-01-19
I, too am new to Ubuntu and am curious about setting up a home network.  Can one avoid assigning IP addresses by dedicating the machines to the equivalent of a "group" or "domain?"  That way all look for other machines in the same group?

---

