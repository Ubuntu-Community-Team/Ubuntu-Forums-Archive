---
title: "Looked everywhere, need wireless set up help."
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by crimlaw on 2008-11-08
I am running Ubuntu 8.04, and I have never been able to get wireless to work.  I have a Compaw Presario F700 with an atheros card.  When I am in windows, my wireless works great, so I have the drivers there.  Also, my laptop has a hard switch on the front that allows me to turn wireless on and off.  When I am in Ubuntu, the light next to the switch is orange, which to me means it is not functioning.  

I looked in system -> administration -> Hardware Drivers, and it says "Atheros Harware Access Layer (HAL)" with the box checked and the green light next to "in use".  It was says "Support for Atheros 8.02.11 wireless LAN cards" with the box checked and the green light next to "in use."  

Can anyone walk me through getting my wireless to finally work.  That is the only thing that is keeping me from making the full switch from windows.  

Thanks!!!

---

### Post by TenPlus1 on 2008-11-08
If your Atheros driver is working ok you should be able to go into Network Connections (or Network in Hardy) and setup your wireless card same as you did in XP (essid, wep/wpa key, dchp or static ip addy etc.)

---

### Post by crimlaw on 2008-11-08
When I click on Places->Network, the only thing that comes up is "windows network."  If I had to guess, from my limited knowledge, I would say that Ubuntu does not recognize the wireless card at star up, so my wireless light never turns blue, and Ubuntu then does not find my wireless as an option to connect to.  How do I change this?  How do I get ubuntu to see my wireless, and then allow me to connect to it?

Oh, you meant System->Admin->network.  When I go there, my only listed options are wired and point to point connection.  I have tried to manually set up my wireless before, but it just does not seem to work.

---

### Post by crimlaw on 2008-11-08
I tried following the Ubuntu setup and when I typed iwconfig in the terminal, I received the following:  

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by crimlaw on 2008-11-08
ALL RIGHT, GOT IT TO WORK!!!  I followed the help option in Ubuntu itself to find the exact name of my card with iwconfig.  Then I googled the name of the card and found a Ubuntu forum post from a few months ago that gave a step to step.  I would post the link, but I had to restart my computer, and did not save it.  Just google the name of the Atheros card if you are wondering.  

Ha, time to finish the full move away from windows.

---

