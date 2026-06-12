---
title: "BT Voyager 1065 driver?"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by buttyshell on 2007-02-26
does anyone know where I can get a driver for a BT Voyager 1065 Pcmcia card for Ubunto? and how do I install it?
I have just moved from Winblows XP to Ubunto

---

### Post by Metaljaz on 2007-02-27
Type the following command from the terminal window:

lspci

Look for the network controller line which should list the name of the card and the chipset. If you have to install a windows driver using ndiswrapper you need the driver for the chipset. 

Look here for further information:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by tyres on 2007-03-01
Hi buttyshell,

Follow the instructions in this link

[http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=install+ndiswrapper)

It works! I'm typing this message at the moment on a laptop using the BT 1065 adapter under Ubuntu (Edgy). 

One caveat. The script (from the link) wants internet access to install a particular version of ndiswrapper (for running Windows drivers under Linux). I got round that by having an ethernet cable link from my laptop to the router (BTHomeHub) while I was installing.

Pretty painless otherwise. Just ran the install script, and I was ready to go!

Good luck.

Colin

---

### Post by jimipop on 2008-02-20
Thinking about buying this card (BT VOYAGER 1065) for a dell  laptop. I can't connect to the net through etherne, can I still get this to work? alternatively any suggestions? Looking for as cheap as possible.

Have you got one spare?

Thanks - this is my first post here

---

