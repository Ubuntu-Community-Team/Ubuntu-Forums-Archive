---
title: "Linux Home Server"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by Dansaycool on 2006-12-19
Hi, 
I'm trying to go about setting up a server at my home, i have used linux before and know the general workings, but i'm having a few problems tryin to sort this server out.
So far my network looks like this 

--
Broadband Modem
--

connected to

--
linux box
-- 

connected to

--
linksys router
--

connected to 

-- 
Several computers
--

when i've set up the network like that I can get the interent on the linux box but not on any of the other computers, I think its got something to do with DNS but i'm not sure. On the linux box is a newly installed ubuntu server which has two network cards. I've read somewhere I might need to install Bind9 doing the easy "apt-get install bind9" but then would I need to configure that so it does it's business thorugh the eth2.

Thanks
dan

---

### Post by sailingboarder on 2006-12-19
i may be completely wrong on this, but does the broadband connection have to go through the linux box b4 it gets to the router
on our network, though it is a windows network with the exception of my computer, the internet connection goes from modem to router then to all the computers, one wired and three wireless
im not sure if its supposed to work that way, but that's how we do it

---

### Post by Dansaycool on 2006-12-19
i dno i jst thought thats how you would set it up, kwl man nyway ill try it later tnite
thanks

---

### Post by punx45 on 2006-12-19
Both ways could be correct, but depend on settings.   the way you have the network physically configured now, the server needs to be configured for routing and possibly DHCP, and the hardware router needs to be set to act as a switch.

the other option, and more common (and so as to not treat your router as a needlessly expensive switch), is to connect the broadband modem to the router, and then connect all the computers, including the server, to the router.

option 2 will likely result in less headaches.

---

### Post by Dansaycool on 2006-12-19
ye, so also on this linux box i'm goin to run apache. Would i have to set the router to port forward  port :80 to the linux box?

---

### Post by punx45 on 2006-12-20
yes.

and while you are at it, give the linux box a static IP on your LAN.  

im not sure if it makes a difference, but i keep my static IPs outside the range of the DHCP assigned IPs:

---

### Post by Dansaycool on 2006-12-20
ye, ive just done that gave it an ip out of my DHCP range. got apache working on it too now. 
Also while i'm here do you know of any advantages of streaming music, on this linux box I've done I'm going to load all my music and Movies and I was just going to do a simple samba server setup and using WMP11 on my windows computers just play the files over the network, but i've heard that streaming is better? any1 have any ideas?

thanks for all ur help btw

---

### Post by punx45 on 2006-12-20
the simplest thing would probably be a SAMBA share that contains all your music, etc. and setting that as your default library in WMP.   I have a similar system using an NFS share from the ubuntu host, OSX and iTunes.

but if you prefer to stream, im sure a simple search in these forums will yield plenty of info.

---

### Post by Dansaycool on 2006-12-20
ye i'll do the SAMBA setup, I was going to do that oringally so i'll get on with that. 
thanks for you help again

dan

---

