---
title: "Using Network Manager to easily switch between multiple predefined n/w configs"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by manojpmathai on 2008-11-18
Hi,

I need to connect  my laptop to 3 different networks and i wanted to know how it can be done using Network Manager.

1) At my work place i need to use a fixed ip,mask,gw,dns settings n mac address
2) At my home its DHCP
3) At my other work place, there is another set of fixed ip, mask, gw,dns settings and mac address.

What i want to do is to give a name to each of these settings like work1, work2, home,etc and then be able to switch to any of this config by simply clicking on the network manager menu. Is this possible ? How can this be done ?

OS = Ubuntu Intrepid 8.10 i386
network-manger version = 0.7~~svn20081018
network-manger-gnome version = 0.7~~svn20081020

What i used to do in Ubuntu 8.04 :

1) under /etc/network, i created an interface definition file for each connection e.g interfaces_work1, interfaces_home, etc with the correct definitions

2) then i wrote a small bash script, which, given the config name, copies /etc/network/interfaces_{config_name} to /etc/network/interfaces and then did an "/etc/init.d/networking restart".

It worked fine. But, for the new n/w manager in 8.10, i cant figure out how to do the same using the GUI.

Had a few questions about the GUI :

(a) In the GUI, for each wired connection i created, there are 2 checkboxes

i) Connect automatically
ii) System setting.

what do they indicate ? Hovering over them gives no tooltip.

(b) I created the 3 configs that i wanted and gave it names. But when i left click on the n/w sys tray icon, i see "Auto Ethernet" and some times i see an "Auto eth0" along with it. . What do these options mean ? Also, the other 3 that i had defined are missing. One would expect to see 3 radio buttons showing each of my custom connection config names but thats not the case. and its really confusing.

c) In the first tab, what does the grayed text to the right of each connection name indicate ? it shows strings like Now, Never, 'n' days ago,etc Does it indicate the last time the config was used/created/edited ?

---

### Post by techno91 on 2008-11-18
I'm having a similar problem as the one you listed in b. the difference is that my configurations were left alone, but the network manager refuses to use them or even recognize them. makes me wonder what the deal is.

---

