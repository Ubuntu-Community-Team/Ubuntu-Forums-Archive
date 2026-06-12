---
title: "Crossover  xp&lt;-&gt;buntu"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by iAlta on 2006-11-18
Hi!

I just bought a crossover cable to connect my Xubuntu and xp machine. Or is it machine**s**?

But I don't acctually know how to use it. 

Could anyone help to set up a ftp service? (And also how tp say the previous sentence propperly.)


And if I could get the internet sent to my Xubuntu would be awsome!


Thanks in advance
iAlta

---

### Post by PilotJLR on 2006-11-18
XP has a feature called "internet connection sharing"... I think it's in the programs | accessories folder.
You need to run that...
I'm assuming you have 2 NIC's in the xp machine... so when you run the ICS wizard, it will basically turn one NIC into a LAN port, and will provide DHCP and NAT to the ubuntu machine.

---

### Post by MrFSL on 2006-11-18
A crossover ethernet cable requires that you have a network interface card (NIC) or network interface adapter in each machine.

Plug in the cable in each machine. Then you have to setup your network connections so that the two computers are on the same network. You do this with static ip addresses. Here is an example:

machine #1
IP Address 192.168.0.1
Subnet Mask: 255.255.255.0

machine #2
IP Address 192.168.0.2
Subnet mask: 255.255.255.0

At this point the two computers will be able to access the resources and servers by referencing the IP address of the other machine.

To share internet between the 2 machines (in the configuration where you are using a crossover cable) requires that one of the machines has 2 network interface cards - 1 for the crossover cable, and 1 for your internet service provider. Next, the computer with 2 NICS needs to be setup to share the internet (commonly called Internet Connection Sharing or ICS). This feature is available in both Linux and Windows. In windows there is a wizard that can help you setup your settings or you can go to your network connections, right click, go to properties, and check a box to share this connection. In my mind it is easiest in Linux which has this functionality built into the kernel. 

There are several ways to make this work but I suggest (in ubuntu) to install firestarter which is a graphical interface to your Ubuntu firewall. Firestarter has an easy way to setup ICS so that your Ubuntu box shares its internet connection with other computers.

NOTE - If you have the required number of network adapters and plan on using ICS you do NOT need to use static IP addresses. You can install DHCP in linux and your Ubuntu box can hand out IP addresses to your XP box. This functionality is the same in Windows.

Hope this gets you started.

MrFSL

---

### Post by iAlta on 2006-11-18
Thanks for the inmormative posts.

I might just say this now: networking, not my speciallity.

My xp has 2 networks cards, one wireless connected to the router and one wired connected to my xubuntu. And xubuntu only has one.

One question: how do I set-up the static ip's?

Also, Firestarter refers me to apt-get, which I beleive requires an internet connection, which I don't have,  yet atleast.

---

### Post by iAlta on 2006-11-19
OK, I found out how to set a static ip on ubuntu.

But I still don't know how to do it on xp though.... (and since this is the ubuntu forums, maybe I should go elsewhere:rolleyes: )

---

### Post by PilotJLR on 2006-11-19
Go to Control Panel, then Network Connections.
Right click the connection you are using, then click properties. Then click the protocol entry for "TCP/IP" and click properties again.

Check the radio buttons for "manually assign" on your IP / mask / gateway and also DNS.

---

### Post by iAlta on 2006-11-21
I don't have GNOME, but Xfce...

---

