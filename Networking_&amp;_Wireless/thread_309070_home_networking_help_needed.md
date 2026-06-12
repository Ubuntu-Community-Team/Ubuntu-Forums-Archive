---
title: "home networking help needed"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by gvsrinivasan on 2006-11-29
i have two  pc's at home and and i want to put them on a network ,

 the first one is a intel celeron 850mhz system  and another one is a amd 1.06ghz system 

the intel system has a dlink ethernet controller in it . the amd system has an inbuilt nic card and a additional realtek ethertnet controller in it 

the intel system is running on kubuntu 6.06 lts and the amd system also  consists of kubuntu and winxp in it 

i want the two machines to be put on a local area network through a crossover cable 


what should i do to connect two linux pc's and use them for file and internet connection sharing and the amd system is connected to the internet through adsl  modem and one ethernet card is used for the internet  and  another one will be used for the lan connection between amd system and intel celeron pc 

i am in desperate need to establish a  lan between 2 linux pc's 

 any help on acheiving this will be great 
 thanks in advance

---

### Post by kvonb on 2006-11-29
Assuming that you already have the internet working on the AMD system, first setup your 2nd ethernet card (menu ->system->administration->network) to be 192.168.0.1 netmask 255.255.255.0.  Next do the following in a terminal:

```
sudo gedit /etc/sysctl.conf

```
uncomment the line about IPv4:

```
# Uncomment the next line to enable packet forwarding for IPv4
net/ipv4/ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net/ipv6/ip_forward=1
```

Save and exit, issue the command:

```
sudo /etc/init.d/networking restart
```

Stop, then start your internet connection.

Next change the IP address of the 2nd machine to 192.168.0.2 netmask 255.255.255.0, and set your gateway to be 192.168.0.1 (using the same network tool as above), your network should now be fully functional.

As for file sharing, use Nautilus (the file browser) to right click on the folder you wish to share (on both machines).


Done! :)

---

### Post by gvsrinivasan on 2006-11-30
thanks for the help dude 

i will try it out and then tell you how it goes ,
 i am using kubuntu and will be good if it is possible to do file sharing in konqueror also , 
this is my first networking experience between two  pc's and going  to learn networking concepts through Linux , 
i am basically a newbie in networking and server administration

---

