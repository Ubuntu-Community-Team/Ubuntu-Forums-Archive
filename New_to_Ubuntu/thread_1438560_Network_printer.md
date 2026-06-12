---
title: "Network printer"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-25
Hi, I have Printer hooked to my ubuntu machine. I would like to be able to print from all my devices on WiFi in the house.

Is this possible, and how?


Trandre:popcorn:

---

### Post by Kenny_Larsen on 2010-03-25
Yes, or at least I managed to get it working. I went to [http://localhost:631](http://localhost:631) and clicked the share this printer button, logged off and then back on again before browsing for a printer on my XP machine which found it and it worked. This was done by trial and error so I'm not sure how generally it will work!

Kenny

---

### Post by baddnady23 on 2010-03-25
Try:

System>Administartion>Printing 

and click on new.  If it is set up properly it should be able to be chosen from there and work correctly with little or no adjustments.

---

### Post by Trandre on 2010-03-25
What is [http://localhost:631/](http://localhost:631/) do I create an acount hook the printer on that online sorce and then direct my other devices to it?

The printer is working fine on the client I am working on now, but I also what it to be a printer for all devices hooked up to my router, though it is through a linux client. 

Is it for instance possible to assign a local ip to a printer hooked to a client and not directly to the router?

Trandre

---

### Post by baddnady23 on 2010-03-25
That web address allows you to configure the CUPS printing settings for linux.  Dig into it for a while and I'm sure you'll find it very useful.  Is it possible your printer is being blocked by a closed port on your firewall?  I know with my wireless HP, it requires around 8-10 different ports to be opened up to function properly.

---

### Post by Mykk on 2010-03-25
What are the other devices mate?

If they are Windows it should (in theory) just be a case of going 

Start > Run > \\HOSTNAME\PRINTERSHARENAME

Obviously HOSTNAME and PRINTERSHARENAME are your own.


*Edit*

That is assuming of course that the printer is shared. Which i believe can be done through samba.

---

### Post by Kenny_Larsen on 2010-03-25
the localhost address links to CUPS which is essentially the print manage service, alternatively it can be done via system -> administration -> printing. But using cups is quite enlightening sometimes.

I know my printer is accessed remotely using an address like ipp://server(linuxboxname/ip)/printer

Kenny

---

### Post by Trandre on 2010-03-25
Had no Idea of neither Cups or Samba. That was Cool stuff. Diggin in to it now. Thanx guys


Trandre

---

