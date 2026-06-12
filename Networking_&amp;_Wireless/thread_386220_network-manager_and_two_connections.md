---
title: "network-manager and two connections"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by malQi on 2007-03-16
hi, recently i've installed network-manager - wifi works, wired connection works too, but not at the same time. at my house i have internet from wifi (dhcp) and LAN by wire (statis) and i cannot make it to work at the same time, when i'm connected to wifi and i plug wire in i'm disconnected from internet and when i'm using LAN i cannot use wifi. is there any way to fix it?

---

### Post by Kobalt on 2007-03-17
Your thread strikes me with a question : is it possible to be connected to the net with wifi and ethernet, with two different protocols, at the same time... ?

---

### Post by Orphee on 2007-03-21
Hy I have the same problem, I have a wired connexion not connected to internet, and my wireless connexion connected to internet, I need to use both of them at the same time, How can I do ? thanks :)

---

### Post by puyi on 2007-03-21
I don't think you can do this. Under Windows and with specific server network hardware and drivers you can create redundant or bridged links between two interfaces but even in this case all bridged links must be of same type, either wired or wireless, not both.

---

### Post by XProgrammer on 2008-03-06
[FONT="Georgia"] 

Hi, You can connect to both wireless and wired at same time. You got enable the interfaces manually. 

System->Administration->Network.

In that configure both wired and wireless as enabled and mark them for DHCP. 
Execute the below commands.

ifdown eth0
ifdown eth1

ifup eth0
ifup eth1

ifconfig


Now you would see both interfaces are connected. 

ip route 

will show you the routing polices. You can change which interface needs to be dafault and more specific routes can also configurable. 


I was looking little different requirement. At home, I only connect to Wireless. 
At office, I want to connect wireless and wired because i want route some packets via wireless since that doesn't has firewall.  I was searching whether this could be done via network-manager. Otherwise, I have to write a small shell script which can do this. 
[/FONT]

---

