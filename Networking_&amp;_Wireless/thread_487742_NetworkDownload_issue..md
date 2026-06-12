---
title: "Network/Download issue."
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by Nem1976 on 2007-06-29
Situtation is this if I try and download a file from anywhere be it using the add/remove or Synaptic's I get really slow speeds.  

I tried downloading a movie file off one of my forums yesterday and If I download it on the Ubuntu box the speed is really fast like 800KBps for the first 3 sec's then it drops down to 20-40KBps and stays there or sometimes Errors our and stops the download.   The download times for this file comes out to like 2-3 hours.  

 I thought maybe it was just the site so I tried downloading it from my Windows XP workstation and I was  downloading the file at 400KBps ffffffffffffffffffffffffffand can download the file in about 10 mins.  I went back to my ubuntu box and launched my vmware thats running XP and tried downloading the same file and that gets 400KBps as well.  But If I go back to my gnome desktop and try downloading the file it gets horrible speeds.

 
Current Setup:
Ubuntu Fiesty 
Intel Motherboard w/ onboard  Marvell Technology network card. Not Connected
Intel PCI 10/100 network card.  DHCP

I have tested both network cards same issue.  I tested the internal cabling of our office and it's good.

I'm at a complete loss as what to try next.  I was going to through a cheap dlink network card in to see if that helps but I wanted to get some advice from someone that has better knowledge then myself.  I have only been using ubuntu for about a month so I'm still green to the linux world.


Thank you for any help you can provide.

Nem

---

### Post by Nem1976 on 2007-06-29
Well I figured this issue out.  Now I need to find out why it's happening.

I have a Sonicwall 3060 as our main office firewall.  I bypassed our Firewall and staticly assigned my Ubuntu an outside IP and now my download speeds are just as fast and my XP desktop.  

Now here is my ? anyone know why a sonicwall firewall would cause this problem with just linux?

---

