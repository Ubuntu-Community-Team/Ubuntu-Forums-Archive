---
title: "How do I set up a wireless network with a Windows XP computer?"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Coop on 2007-01-21
Hello

I want to set up a wireless network with a Windows XP Professional computer,which I can use to send files and chat etc.

Here's my situation:

There are two computers in our house.

One (a Windows XP Professional one) is my brother and sisters'.

The other (an Ubuntu 6.10 and Windows XP Professional dualboot) is mine.

We use Optusnet broadband (don't mind my location,I just like it like that),and we have a Siemens Speedstream adsl modem.

My brother and sisters' Windows XP Pro computer is in the same room as the Siemens Speedstream,and my Ubuntu Edgy/Windows XP Pro dualboot is in my room.

We have a Netgear WGT624 v3 wireless router connected to the Siemens Speedstream,which supplies the internet to my computer.

I [I]think[I] my brother and sisters' Windows XP Pro computer is connected directly to the Siemens Speedstream.

When I go to Network Servers in my Places menu,it shows two icons:one is the name of my wireless network,and the other says "Windows Network".

Please tell me how to set up a wireless network which I can use to send files and chat.

I will be highly obliged for your help.

Ahmed

---

### Post by rmartz on 2007-01-24
First, I would suggest both computers be connected to the router. The router will most likely have a firewall that will insulate your network from the outside. This will help stop outside attacks a little. 

When you connect both systems to the router, they will be more likely able to see each other depending on how they are set up. Since you have a router, both should be setup for DHCP.

Let me know how that works and I will give you what help I can.

---

### Post by Coop on 2007-01-26
rmartz thank you for replying.I'll try your suggestion and let you know how that goes.

---

### Post by Coop on 2007-01-28
Hello

I don't know much about hardware,so bear with me here.

rmartz,please tell me what you mean by connect both computers to the router?

The router is in the same room as the Windows XP computer.My computer is in a different room,and i receive my internet from the wireless router through a wireless card that is in the back of my computer.

My computer is in a different room than the router,so please tell me what do you mean by connect both computers to the router?

Please answer me.

---

### Post by rmartz on 2007-01-28
Coop,

It sounds like you are set up that way. Your first post sounded like you had a computer connected to the cable modem.

"I [i]think[i] my brother and sisters' Windows XP Pro computer is connected directly to the Siemens Speedstream."

The setup should be like this:

Cable Modem<-->Wireless Router<-->Computer
(Ignore these dots)..........|<--> Wireless Notework card hooked to second computer

Are you wanting your two computers to be able to share files?

---

### Post by Coop on 2007-01-29
> The setup should be like this:

Cable Modem<-->Wireless Router<-->Computer
(Ignore these dots)..........|<--> Wireless Notework card hooked to second computer
I think you are right.
btw I didnt set up the wireless network,my uncle did.I can ask him for help.
> Are you wanting your two computers to be able to share files?
Yes I want my two computers to be able to share files.
I also want my two computers to be able to chat and play multiplayer games like The Battle for Wesnoth.
Please tell me how to do that.

---

### Post by rmartz on 2007-01-29
Your Windows system is already basically set up to share. You will have to install Samba on your Ubuntu computer. Easiest way is to open the Synaptic Package Manager search for Samba. Once you find it, click the box to install it.

Once installed, you will need to search the forums for instructions as to how to set it up to allow sharing of folders.

To play games, you should be able to do that now. 

If you go to System>Administration>Network Tools then click on the Ping tab.

Type in the IP address of the Windows computer. If you get a ping response, you should be able to play games.

Well, you may have "allow" access to the game on the Windows Machine in your firewall settings.

Let me know if you need help with any of these steps.

---

