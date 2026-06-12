---
title: "Wifi to wired internet sharing"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by genericnumber1 on 2008-08-22
So I have an odd problem.. I just moved and don't have access to a wireless switch/router, so I have to make do with wired internet, no biggie right? Well, it is a fine set up for my ubuntu laptop which has an ethernet port as well as a wireless card, but it isn't so great for my wii which has no wired network capabilities, only wifi.

Is it possible to set up my ubuntu laptop as a makeshift wireless switch that I can use as an intermediary to connect my wii to the internet?

I suppose what I'm asking is A) can I accept connections via wifi as if I was a switch, and B) can I share my wired connection to connected clients?

I figure B is possible, but A I haven't been able to find any information on.

I suppose it might also important to note that DHCP is typically handled by a router I have no access to.

---

### Post by taseedorf on 2008-08-22
That is a tough one.  There IS a way to do it, but I don't think you can in Ubuntu.  At least, I don't know how.  There is a program in Windows I once used to allow the laptops in my house to connect to my one wired computer....I can't think of the name though, and this was a while back.  
If you have access to Windows... you can try

setting you're wireless connection to "access point" mode...*OR try ad-hoc mode*
 and bridging it with your wired connection...
this MAY allow your Wii to see your computer, connect to it...and so on...

---

### Post by genericnumber1 on 2008-08-22
Alrighty. Yeah, I've been trying ad-hoc with windows and the wii doesn't seem to like it :) but I'll look into access point mode.. or something. Thanks for the help!

---

### Post by SpaceTeddy on 2008-08-22
mhm... i don't think briding is right here. Since you have more than one computer and your computer is directly (?!) connected to the internet you would rather need NAT and ip_forwarding than bridging...
but that is my point of view. What i cannot help with is how you get an IP-connection established between your laptop and your wii. As soon as you have that connection (i.e. you can ping the wii from your laptop) it becomes easy - that is just a simple router/forwarding setup.

hope it helps :)

---

