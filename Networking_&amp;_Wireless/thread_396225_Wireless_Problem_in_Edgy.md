---
title: "Wireless Problem in Edgy"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by mshale on 2007-03-29
Hi all, this is my first post to go along with my first use of ubuntu!  I have installed 6.10 (Edgy) and I believe I love everything but the networking.  I am VERY used to  windows wireless manager.  It allowed me to search for wireless networks and connect to them.  I have not had that privilage in Ubuntu :(  

Here's the question/problem:  Edgy has the required drivers for my card pre-installed, I checked it.  I have the Intel PROwireless chipset: ipw2200.  Wireless connection will work great for aobut 10 mins or so, and then loses the connection.  I cannot get it to reconnect after that.  I was downloading updates, and the manager reached "10 of 162" and the connection dropped out, and won't reconnect.

The ethernet connection is always on and ready if i choose to sit by my modem with my laptop, and unplug everything and hardwire the connection.  Can anyone help me??

---

### Post by Pizarro on 2007-03-29
I agree wireless networking seems to be the big drawback. I've struggled and got to the stage where the laptop can see my and my neighbors routers, but won't connect. It fails to get an ip address. Somewhat frustrating.

---

### Post by mshale on 2007-03-29
When you say "see" your and your neighbor's routers, do you mean that you have a program that will allow you to view the available wireless networks?  If so, what is the program called?  And if not, could you tell me where to find the pre-existing utility?  Thanks!

---

### Post by Pizarro on 2007-03-29
wifi-radar is the program name. I installed using Add/Remove it is under internet option

---

### Post by mshale on 2007-03-30
cool, thanks.  Have you tried going to system->administration->networking and configureing the wireless option?  all you have to do is input the SSID into the blank.  This is how I got mine to connect.

---

### Post by PlancksCnst on 2007-03-31
> **Pizarro said:**
> wifi-radar is the program name. I installed using Add/Remove it is under internet option

Thank you!

It was a minor nuisance to have to go upstairs and look up my ssid when I was setting up the connection.  But the real frustration came when I went to Panera (free wifi) and expected to use my laptop.  I had no idea what there ssid was.  I asked one of the workers.  She asked a manager.  Nobody knew.  I tried "Panera" and that wasn't it.  So, that was frustrating.

This needs to be included by default, and not in a seperate program; it needs to be in the network configuration tool.

---

### Post by graabein on 2007-03-31
Quick question about **wifi-radar** ... do I have to be root to start it? It won't start for me saying something about */etc/wifi-radar.conf* ... can't I just set **chmod 777** on it?

---

### Post by dougr on 2007-03-31
Not to turn this into a thread of complaint, but I can certainly empathize with you.  Unfortunately I have the RT61 chipset so I cannot be of help.  It took me a good 2 days(of course not the WHOLE day) of tweaking to get my ubuntu setup properly with wireless.  I am now at the point that I can connect to my WPA network, and any other network as long as it is not WPA as well, which isn't a problem for me, at least for the next 2 years.  THe sad part is, just to get to that took a lot of manual configuration of files, and writing small shell scripts to make it all happen at the click of a button.

I certainly can't complain, since I have not contributed to the development of ubuntu, but I would say WIFI, and especially it's handling of WPA is the biggest drawback of Ubuntu.  I really don't understand why WPA and wireless in general is so difficult to implement, but I imagine it can't be terribly easy if there is so much problem with it.

That said, Ubuntu is making major strides, and if I could just get IE6 working in Crossover(connection issues) I would never need to look at a windows pc again.

---

