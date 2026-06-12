---
title: "Creating Wireless Network at School"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by bjb.butler on 2008-08-05
Hello all

I am going to be going to university in the fall, and wanted to set-up my own wireless network in my dorm. I was thinking of purchasing an Apple Airport to set up my network, so I could have a printer and hard drive access wirelessly. But it says that I need to connect my dsl or cable modem to the router first, and I am unsure if each room has a cable modem in it. If my room doesn't have a modem, what are my options of setting up a wireless network?

---

### Post by tamoneya on 2008-08-05
When it says modem it really just wants to be connected to the internet so you can just plug it into your ethernet jack.  It is pretty standard for universities to have one per student in the dorms.  Also check with your campus IT to make sure that you are allowed to do this.  I dont know of any places where they wont let you but i wouldnt be surprised if one did.  Also make sure you have strong encryption (at least WPA).  If you are at a university that is at all technical people will most likely try to crack it just for the fun of it.

---

### Post by Moridin333 on 2008-08-05
I believe that the main thing to be considered is what devices you will have physically connected to the router.  To access the internet you will have to have the cable modem.  to use the printer you will have to have that.  To use the hard drive you will have to have that.  All of these will have to be in the same room with the router.

Another thing to consider is compatibility with apple products.  I have no knowledge of this.  Maybe someone behind me can help.

Also something you might not be aware of is speed.  As far as I know wired is always faster than wireless.  So if you will be transferring files between the hard drive and a wireless laptop it will take longer.  You shouldn't have much slowdown with the internet using wireless.

Let me know if you have any more questions.

---

### Post by loboc on 2008-08-05
The cable modem is just the WAN (Wide Area Network) source.  The ethernet jack in your room will do the same thing.  One problem you might run into is someone else using a router in close proximity to yours.  I have a couple of suggestions.

I agree you should turn WPA on. 

I would also change the channel to 1 or 11 to avoid interference. Most people leave their routers on the default 6.

I would also change the router settings so it uses a IP number set different from the uni.  Such as 10.1.1.* for computers on your local network. You wont know what numbers to avoid til you get to uni.  Plug your laptop in the jack first and run 
ifconfig to see what the have setup for DHCP

---

### Post by loboc on 2008-08-05
> **Moridin333 said:**
> I believe that the main thing to be considered is what devices you will have physically connected to the router.  To access the internet you will have to have the cable modem.  to use the printer you will have to have that.  To use the hard drive you will have to have that.  All of these will have to be in the same room with the router.

Another thing to consider is compatibility with apple products.  I have no knowledge of this.  Maybe someone behind me can help.

Also something you might not be aware of is speed.  As far as I know wired is always faster than wireless.  So if you will be transferring files between the hard drive and a wireless laptop it will take longer.  You shouldn't have much slowdown with the internet using wireless.

Let me know if you have any more questions.

Apple Routers work fine with ubuntu thats the point of 802.11b g n standards.  

Plug the laptop in to the router when you run your backups to your networked hard disk.

---

### Post by bjb.butler on 2008-08-05
Thanks everyone for the replies

Good info!

---

