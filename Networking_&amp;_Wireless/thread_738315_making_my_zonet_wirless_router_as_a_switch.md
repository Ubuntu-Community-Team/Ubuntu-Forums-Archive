---
title: "making my zonet wirless router as a switch"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by stellyx on 2008-03-28
hey guys im trying to setup a zonet ZSR1124WE behind a 2wire 1701 router. Im attempting to make it wireless downstairs by doing this. But im stumped.
I am able to connect the router and get local use, for instance i can use the printer pluged into the zonet ZSR1124WE but i cannot access any of the computers that run through the 2wire 1701 and i cannot get access to the internet.
I know its a setup problem so im starting this thread to get out of these weeds.

please post if you need further info

thanks in advance

---

### Post by drdrewdown on 2008-03-28
well right now you are behind DUAL NAT. so anything plugged into the first router will not be accessible if you're on the 2nd router.

in order to make a wireless router an ACCESS POINT you need to disable the DHCP server in the wireless router & then move the ethernet cable from the WAN port to one of the LAN ports.  

i would recommend giving the 2 routers ip's on the opposite ends of the network.  

eg..

router 1 = 192.168.1.1
router 2 = 192.168.1.254
router1 = port1 to router2 = port 1(not WAN)
disable DHCP in the wireless 2nd router.

this will allow DHCP to cross over the wireless as part of the original LAN which is what you're wanting to do

---

### Post by stellyx on 2008-03-29
thanks ill give it a whirl.
what should the subnet mask be you think?
should i have to change the gateway?

---

### Post by drdrewdown on 2008-03-29
if you are referring to the subnet & gw of the WAN interface, you are bypassing that interface so its irrelevant

be sure your lan interfaces on both routers match but i'd recommend giving them different LAN ip's as i described above.

lan subnet of 255.255.255.0 (default) should work fine.

cheers

---

