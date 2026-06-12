---
title: "Awkward setup"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Risk_3715 on 2008-05-18
I'm green at networking so please be patient with me if I don't immediately understand what you suggest.

My setup is thus- Internet through a cable modem is hooked to a wireless router which services two machines through wireless adapters- both running XP. DHCP is running on the router. Recently I've converted my old machine to ubuntu and due to lack of money I'm forced to setup internet for my ubuntu machine through NIC's via cross over cable through my personal XP machine. That's a wireless network and a LAN subnetwork between my personal XP and the ubuntu that I'm trying to set up.

What particular setup can I configure? Do I have to specially configure the Windows Firewall? Should I use DHCP or manually configure the ip addresses on the machines?

Mostly, I'd like to know where I should begin.

If you need more info just ask I'll do my best to provide it. Help is much appreciated.

---

### Post by SpaceTeddy on 2008-05-19
let me get this straight. 

Ubuntu <--Crossover--> Windows XP <--Wireless--> Router <---> Internet 

is that your setup ? if so, sorry, i cannot help you. This would mean you have to turn the Windows machine into something that forwards pakets. I don't know how to do that or if that can even be done. Sorry :(

if you setup is 
Windows XP <--Crossover--> Ubuntu <--Wireless--> Router <---> Internet 
i can help you (mainly with this [[COLOR="Blue"]guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874"))

so, which one is it ?

---

### Post by Risk_3715 on 2008-05-19
Yes, that's correct. I was trying to set it up by connection sharing on the XP, which means I had to change the scope of my DHCP on my router. I'm coming to the realization that I may as well run the wireless adapter through my ubuntu machine- it'd be so much easier... as long as I had the drivers.

---

