---
title: "How to connect to a printer on wireless router"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by captain_rob on 2009-06-26
In the archives I found that the URL to use to connect a printer with the wireless router ASUS WL-520GU (which has a printerport) in cups is:
lpd://192.168.1.1/LPRServer.

I am a newbie  :oops: and really don't know how I can print wireless using this command.  

Can someone help me out?

---

### Post by billgoldberg on 2009-06-26
> **captain_rob said:**
> In the archives I found that the URL to use to connect a printer with the wireless router ASUS WL-520GU (which has a printerport) in cups is:
lpd://192.168.1.1/LPRServer.

I am a newbie  :oops: and really don't know how I can print wireless using this command.  

Can someone help me out?

Try this:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Check the Ubuntu Client Computer part.

---

### Post by howefield on 2009-06-26
Have you tried setting the printer via System > Administration > Printing and adding a new printer selecting the Network Printer option ?

---

### Post by dka on 2009-06-26
Right, when you get to the Administration --> Printing window, search /add a network printer.  Be patient, it may take a while and the window might freeze and turn gray.  That is normal.  After that process is done, the computer should see the networked printer on the wireless router (if the printer is on).  Then it is simple to add it.  Otherwise you can manually enter the address you provided and it should find it.

I know setting up my networked printer was a pain.

Good luck.

---

### Post by captain_rob on 2009-06-27
Ok guys, thank you very much. I will experiment a little bit to see if I can get the printer work :wink:

---

### Post by prvteprts on 2009-06-27
Installing a network printer in my experience wasn't that hard. They were mostly HP printers and they were detected when I did the network search. Although, I noticed some printing features were lacking. But at the most basic level, they're intact. If you encounter any problems, post the model of your printer so the forumers would know how to help.

---

### Post by jimbop99 on 2010-03-10
I know this is an old thread but I thought I would add my experience. I have an Asus WL-520gU set up as a wireless access point with a Canon IP3000 hooked up to the USB port. I could not get the printer to install using "lpd://192.168.1.1/LPRServer" replacing the 192.168.0.1 with the IP address the router was giving it via DHCP. It finally worked once I gave the access point a static IP address. All is working great. I am really enjoying playing around with Ubuntu.

---

