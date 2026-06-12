---
title: "Wired And Wireless"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by whitepony20054545 on 2008-09-30
This Probably sounds stupid, but i have a fully working wireless connection, (which i leech off a friend who lives 2 doors away). i have an xbox 360 connected for media share purposes using wired connection, this also works fine. on it's own. is there any way i can get both the wired connection to the xbox and the wireless internet connection running at the same time? not bothered about xbox live or anything fancy, (yet) just want to be able to listen to music on xbox while i surf the web :) 

using ubuntu 8.04 hardy with windows wireless drivers :)

---

### Post by whitepony20054545 on 2008-10-01
still looking in to this. have just found [this]("http://ubuntuforums.org/showthread.php?t=931599") thread. it talks about bypassing network manager? right sort of lines? anyone?

---

### Post by ubutufan on 2008-10-01
Hi
The /etc/network/interfaces file should look like this

auto lo
iface lo inet loopback
auto wlan0

Be carefull here. In my case the wireless card is recognized as wlan0 (0 is a zero). Yours may be the same or eth1 or eth0. Try ifconfig in terminal to identify the wireless card name.
Hope that helps. It will allow wired and wireless to work together

---

### Post by whitepony20054545 on 2008-10-01
have edited interfaces file and it does work - sort of. when ubuntu starts up it automatically connects to the wireless. but disconnects as soon as i turn my xbox on. is there any way of stopping this

---

### Post by ubutufan on 2008-10-01
I assume that your router is set to DHCP. Is that correct?

Disconnecting the ubuntu box when you turn on the xbox, in my knowledge means that the xbox demands and obtains the ip of the ubuntu box.

Check out the settings of the router for DHCP and let us know.

---

### Post by whitepony20054545 on 2008-10-01
xbox is not connected through a router. so no. it does have trouble obtaiting the ip address of the ubuntu box. but it does have messages about this when it fails the connection test. media sharing works fine anyway.

wireless router dchp is on and all is fine there. 
would a router for my xbox help this?

---

### Post by ubutufan on 2008-10-01
Mate you have me confused.
I understand that the ubuntu box now obtains wireless IP and connects fine.

Let's go to xbox. How does it connect to ineternet? Through the router or otherwise?

---

### Post by whitepony20054545 on 2008-10-01
it doesn't. that is not the point. it is wired directly to ubuntu box with crossover cable purely to stream media from pc to xbox. 

i think that i'm probably going to solve this with a proper wireless network and internet connection for my home. with xbox and pc on the same router. 

sorry to say this but i'm going to give this a go with the dreaded windows.....

---

