---
title: "How do I access HP &amp; Epson printers on Windows through Ubuntu"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2007-02-14
Hi all,
       I have a friend where I have helped to set up Ubuntu **6.06** on one of the machines. He has 2 printers an HP Laserjet 2600 N & an Epson Stylus R230 , it's a small network of 5 machines & they have done networking so tht the 1st machine connects to the net the rest of the machines can also browse internet. Now my query is how can I use the printers? Also how much are these printers accessible/functional under Ubuntu. From what I've read HP seems to be in good stead, about Epson have no idea, any way people give a shot & lemme know wht to do? Thnx in advance :)

---

### Post by gradedcheese on 2007-02-14
If you are planning to connect the printers directly to your Ubuntu PC, [www.linuxprinting.org](www.linuxprinting.org) will tell you all about support status, drivers, and so on.   Printer support is actually quiet good.

If the printers are real network printers (ie: not connected to a PC, but just connect to the network), get their IP addresses and add them via System->Administration->Printing and you should be good to go.

Otherwise if the printers are connected to Windows PCs and shared that way, try browsing for them using samba.  First, use the terminal to "sudo apt-get install samba-client" and then try browsing by going to Places->Network Servers, see if you can access one of the Windows PCs and see their printers.  You may have to use the 'reload' button in the browser when icons look wrong (there are some issues...)  If you can find them that way, you should be able to work out their address/path, but I've never had to do this myself.  It would be interesting to find out how that's handled.

---

### Post by ShirishAg75 on 2007-02-14
thnx gradedcheese it would be cool if this is possible. Although I'm able to browse the net using the Windows network. Would definitely try it out :) 
            Although it's the last one, the 3rd one which I would be doing :)

Just an update, it would be the 2nd & the third which I would be doing for now. Then l8ter perhaps would try to fine-tune & see how much stuff can I get working under Ubuntu :)

---

