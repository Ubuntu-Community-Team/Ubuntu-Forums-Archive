---
title: "Can I get wireless card for old PC desktop?"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by cab1024 on 2005-08-06
I'm a Mac guy but just got a mid-2000 Dell P3/667 OptiPlex GX110 with 512MB RAM and a teeny 10GB HD. I joyously installed Hoary Hedgehog this morning and am loving it. So much so that I want to add a cheap wireless card to it so I don't have to have my Powerbook down here in the garage to connect it to the internet. In fact I would like to use the Ubuntu machine as the wireless signal receiver and share its signal to the old G4 tower that's also in the garage.

So, can I put a wireless card (preferably g/Extreme) in this box, and if so, which is most hassle-free?
Secondly, is there an easy way to share the signal, analogous to the Mac's Internet Sharing control pane?

Thanks!

---

### Post by cab1024 on 2005-08-07
Anyone?

---

### Post by danielhaden on 2005-08-07
A RAlink based card, such as Edimax wireless "g" will connect PCI to Wireless "b" and "g" and the drivers at RAlink (makers of the chip) have linux support.  
Actually, any card with the big RA on the big black chip will do the job, but the Edimax is particularly powerful and comes with a nicer antenna.  

I am not certain how to connect them peer to peer as I always connect PCs together through the wireless switch that is found as part of a wireless AP or a wireless router.  With both computers associated with the same wireless switch, they should be able to "talk" to each other just fine and there is no lack of security with today's wireless "g" with WPA routers and AP units.  

*An AP and a router is the same thing except that an AP does not come with a firewall.  

*If you do not already have a network, then Linksys Wrt54GS is highly recommended as well as the HyperWrt beta free add-on software for it.  These are a very complete start on a professional quality network for both wired and wireless.  If you house is outright huge, Linksys makes a pair of +7 R-TNC antennas in a single pack--that should be good for half a block.  
With a super strong HYPERwrt firewall turned all the way up, your internet service provider (Cable, DSL, DirecWay, Wildblue) will not be able to see into your network to notice that you are running more than one computer.  

*If you already have a wired network set up with adequate firewall, then the Edimax/Hawking/Jaht all-in one miniature AP unit is highly recommended.  For instance Edimax EW7203APg plus a less-than-modest upgrade antenna R-SMA such as the Linksys +7 Apple +8 (or similar) will quickly and easily add wireless into your existing wired network.  
The unit may also be used in client mode (backwards) to cause anything with an ethernet port to go wireless with no software needed. 

** If you are using a Wireless-ISP then you can use both of the above products together.  Use the Edimax AP (backwards) in client mode with a directional antenna (Hawking corner reflect or outdoor Yagi) pointed at your W-ISP.
Configure it while it is connected directly to a single computer's ethernet port.  After you have it working, providing a wireless service connection to the PC, disconnect it and put it aside.
Plug in the linksys to the PC.  Set to your own and different SSID; your own and different channel; your own and different WPA password--your own private network.
Next, plug these two units in back-to-back.  Use the linksys WAN (router) port to connect the Edimax AP!  
Log into the linksys wired or wirelessly from a PC.  
Engage all of the firewalls on the Linksys.  Lastly, log into the address you set for the small Edimax AP unit and set it to "Mac Cloning Enabled".  Your new Mac address will be from the WAN port of the Linksys.  The presence of the Edimax AP will now vanish, but it will continue to provide a wireless connection just the same as when you configured it on the PC.  
You may need to give this Mac address (as reported on status pages of both edimax and linksys)  to your W-ISP if they use MAC filtering. 
 
Now, other customers of the W-ISP cannot get into your computers and your network is private (and as large as you want without having to pay for more than one account).  
In this way, they can only see that you have connected 1 device.  That would be the Linksys (because it is a linux box) and they cannot see past its firewall to notice that it is a router.  ;)

---

### Post by cab1024 on 2005-08-08
[QUOTE=danielhaden]** If you are using a Wireless-ISP then you can use both of the above products together.  Use the Edimax AP (backwards) in client mode with a directional antenna (Hawking corner reflect or outdoor Yagi) pointed at your W-ISP.
Configure it while it is connected directly to a single computer's ethernet port.  After you have it working, providing a wireless service connection to the PC, disconnect it and put it aside.
Plug in the linksys to the PC.  Set to your own and different SSID; your own and different channel; your own and different WPA password--your own private network.
Next, plug these two units in back-to-back.  Use the linksys WAN (router) port to connect the Edimax AP!  
Log into the linksys wired or wirelessly from a PC.  
Engage all of the firewalls on the Linksys.  Lastly, log into the address you set for the small Edimax AP unit and set it to "Mac Cloning Enabled".  Your new Mac address will be from the WAN port of the Linksys.  The presence of the Edimax AP will now vanish, but it will continue to provide a wireless connection just the same as when you configured it on the PC.  
You may need to give this Mac address (as reported on status pages of both edimax and linksys)  to your W-ISP if they use MAC filtering. 
 
Now, other customers of the W-ISP cannot get into your computers and your network is private (and as large as you want without having to pay for more than one account).  
In this way, they can only see that you have connected 1 device.  That would be the Linksys (because it is a linux box) and they cannot see past its firewall to notice that it is a router.  ;)[/QUOTE]

Thanks for all the info. I even understand some of it. I think this part I quoted is the route I'll take, if I understand it correctly. 
Is this what you mean? Basically I should get another wireless router and link it wirelessly to my upstairs Airport Extreme. Then use one of the four ethernet ports on the new router to connect to the ethernet ports of the linux PC.

It seems like this would give me the easiest and best chance of success, plus it would allow me to connect my other Mac w/ OS X and link them all. This way I'm not actually putting a wireless card in the minux machine which from what I'm seeing is not too easy.

Can I do this with most wireless routers? These two are pretty cheap:
Linksys 802.11g Wireless Router Model: WRT54G -- $67US
Belkin Wireless-G Router with 4-Port Switch Model: F5D7230-4 -- $38US
I don't know what specs I'm supposed to look for to see if these models will work as receivers. Can anyone tell me?

The Belkin says its Macintosh compatible which may make it easier to set up since I do not have any windows machines.

Thanks!

---

### Post by cab1024 on 2005-08-09
Nevermind. I think I've found that both of these will work, though it may take a little hacking to use with Airport.

---

