---
title: "Wireless Card Houdini"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by bconover on 2008-06-01
I am sort of new to Ubuntu, so perhaps this is obvious.

For a while, my wireless card (I have a an HP dv6000 series laptop) wasn't working, so I kept my computer hardwired. Just today, I little icon popped up in the top right bar, a picture of a hardware card thing. It said "new drivers available". So, I clicked it, and my hardware window popped up, asking to install a new wireless driver. I did, and my wireless worked! (as in, the little orange light went blue, and I could receive and send data). Of course, things went bad. I restarted my computer, and BAM! No more wireless driver. It even disappeared  from the hardware list, as if the update never took place. 

My question:
How can I run this update again? I tried running the update manager, but it said my computer was up to date. 

And, if I do get the driver installed again, how can I prevent this frome happening anymore?

I don't remember the name of the driver. I am 95% sure it began with a B. If you need anymore info, ask, and I'll do my best to provide you with what I know. 

All help is greatly appreciated, thanks!

---

### Post by bconover on 2008-06-03
Any suggestions are highly appreciated.

---

### Post by bconover on 2008-06-27
Okay.

I reinstalled Ubuntu. The Driver Update didn't show up. But now, after several weeks, IT DID. And my wireless is working again (I'm posting this reply over wireless). Here's exactly what happened:

My computer appeared to have shut down by itself. I rebooted, and after my desktop came up, in the top right corner (in the notification bar) a little picture of a computer card with a lock on it popped up saying "New Drivers Available: Click here to install new drivers". I clicked, and my Hardware Drivers list popped up, showing my already installed Nvidia card, and a new Broadcom B43 Wireless card! 

I'm scared to restart, as last time I did this, the driver went away. Please, PLEASE reply to this, I need some help! Even if you are not sure what to do, just reply with any comments or vague ideas!

Thanks!

---

### Post by bconover on 2008-06-27
Here, a picture of the Hardware Drivers list, with newly placed Broadcom B43 Wireless Driver. The icon next to my name (Brian L. Conover Jr.) is the driver icon that popped up upon login completion saying that new drivers were available.

[IMG]http://i172.photobucket.com/albums/w35/bjincs002/Screenshot-2.png[/IMG]

---

### Post by bconover on 2008-06-27
HELP

My computer wants to update, but I'm afraid that will kill my wireless! What should I do?

---

### Post by bconover on 2008-06-27
The updates appear only to be for security encryptions and Samba (the connect-over-the-internet-to-a-printer thing, which I do use). Is it safe?

---

### Post by zeller on 2008-06-27
You should be good to go then when you restart. That's odd that it didn't hold over through a reboot.

In case you have to get back to that little icon and you don't want to wait for weeks, search in the menus for the Restricted Driver Manager. Click that and you should be able to install the driver again for the b43xx chipset you have.

Hope that helps.

---

### Post by zeller on 2008-06-27
> **bconover said:**
> The updates appear only to be for security encryptions and Samba (the connect-over-the-internet-to-a-printer thing, which I do use). Is it safe?

Should be. It uses the network but doesn't control the network to my knowledge. Network Manager does that and it uses the Restricted Driver for the B43xx chipset. Completely unrelated. So, should be.

---

### Post by bconover on 2008-06-27
YES!

I rebooted, and my wireless still works!

Thanks for the advice!

---

### Post by bconover on 2008-06-28
I recently restarted again.

Driver disappeared, wireless not working.

Thanks Ubuntu >:(

---

### Post by bconover on 2008-06-28
BTW, I have nothing in my menus called Restricted Drivers Manager. I have something called Hardware Drivers, which looks suspiciously similiar, but there is no way to install a driver with it, its just a list.

---

