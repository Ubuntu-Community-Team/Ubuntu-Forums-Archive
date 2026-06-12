---
title: "How can I share a printer with two Ubuntu 7.10 desktop computers"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by a.v.l on 2008-01-01
I read for much of the afternoon about sharing a printer on two Ubuntu 7.10 computers but I've failed to get them to work on both machines.

Following the route 

System>adninistration>printing and selecting> server settings>"Share published printers connected to this system" - on the computer connected to the printer (server) 

Then on the other computer I wish to share the printer with I go to: 

System>administration>printing and selecting> server settings>"Show printers shared by other systems" and then add the printer and its url but this does not allow me to network the printer. 

The printer works fine on the server computer but will not on the other.

How else can I do this please?

---

### Post by iogiuseppe on 2008-01-30
You're almost there! 

Server: Make sure to enable "Allow Printing from the Internet"
Client: 
1) Click on "New Printer" it'll search for a minute for local printers and then give you the dialog where you can select an Internet Printer (IPP). 
2) Select the IPP and fill in the hostname or IP address of the server.
3) Click on the Find Queue button and you'll see the shared printer. 

You should be able to handle it from there!

---

### Post by ODF on 2008-01-30
Thank you guys !! Rep for you :D

---

### Post by a.v.l on 2008-02-01
> **iogiuseppe said:**
> You're almost there! 

Server: Make sure to enable "Allow Printing from the Internet"
Client: 
1) Click on "New Printer" it'll search for a minute for local printers and then give you the dialog where you can select an Internet Printer (IPP). 
2) Select the IPP and fill in the hostname or IP address of the server.
3) Click on the Find Queue button and you'll see the shared printer. 

You should be able to handle it from there!

After a little fiddling around I've managed to get the client computer to communicate with the server computer and print out a few pages, thanks very much. My only concern is that the printer takes several minutes perhaps fiv, before it will print out after pressing the print button. The other problem is that it won't print at all unless I switch off the Firestarter firewalls. Any ideas how to get around these problem please?

An update on the situation: ....... With a little more checking it seems that I can print from the client computer with its Firestarter firewall switched ON so long as the server computer Firestarter firewall (the one the printer is connected to) is switched OFF. I've noticed a warning icon in the task bar of the server computer which showed up in the firewall as "one serious inbound event"  I'm assuming this refered to the attempt to print from the client computer. If this is so, how do I do set-up the server Firestarter firewall so that it will allows the client computer to print on the server computer?

---

