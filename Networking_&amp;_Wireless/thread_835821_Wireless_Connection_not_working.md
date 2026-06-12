---
title: "Wireless Connection not working"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by sudo get-info learn on 2008-06-20
I have just installed ubuntu 8.04 on my laptop.  Things are looking good except I can't manage connect to the internet neither by cable nor by wireless.  The wireless, it tells me that it is connected to the network and shows two bars but Firefox can't find any websites that I enter in.  Is this an IP issue?  How might I resolve this?

---

### Post by secondstage on 2008-06-20
Welcome to the forums. I'm just about as new as you are, buy I will try my best to help.

First check if the wireless card is supported.Check out [this wiki]("http://https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see if it is. 

Second, Put in the Live CD, and see if you can connect to the internet that way. If so , then you probably did something, and messed up the settings, which would lead me to asking you to type one thing in terminal (In the top bar, Applications > Accessories > Terminal). Open it up, and type...
```
iwconfig
```
press ENTER and Copy-Paste the output into a post

---

### Post by nickdbliss on 2008-06-21
Give the output of
#lshw -c network
#ifconfig and #ping [www.google.com](www.google.com) -c 5
also 
#sudo gedit /etc/network/interfaces
#iwlist scan
Along with #iwconfig
Use those commands in the terminal. Applications>Accessories>Terminal
Thanks

---

