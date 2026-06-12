---
title: "Help Help Help"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by ethanubutnumaker on 2007-06-17
I am a new linux user. i love linux and everything about it. but listen to my setup so you can better understand my problem. 

I have a two computers. one PMG4 "Quicksilver" and a Dual boot Win XP/Ubuntu "Feisty Fawn".

now i have a usb wireless nic on the windows/linux computer. but i dont have a wireless nic on the mac. but when i boot windows XP i can share the internet connection over a lan connection between my windows and mac. under ubuntu i can only have one active connection at a time. so i cant connect to the wireless router and the PMG4 at the same time. Ive searched the internet and came across different solutions that involved IP forwarding and masquerading. but i do not have a complete understanding on how this all works and i want to be able to share my internet connection to my mac so i can use my linux more often.

one thing that was interesting was that my wireless nic is eth1. then there are two other interfaces, eth0 and lo (loopback -which is?). im guessing the eth0 is the lan connection between my two computers. I have already tried different solutions but i cant remember just what  i did. so any help would be apprecated. 

Linux forever,
ethan - ATL, GA, USA

---

### Post by trak87 on 2007-06-17
I'm not a networking guru so I should probably shut up, but you say you have a router. All the ip masquerading / nat forwarding and networking between local computers should be handled by the router, so you shouldn't need to set up a Linux based router. Is your router handling the internet feed like this:

```
internet cable or dsl or dialup --->  router  |---> box 1 via wireless
                                              |---> box 2 via wired connection
```

All each computer needs to know is how to reach the router. After that the router will connect all the computers together.

---

### Post by ethanubutnumaker on 2007-06-17
Hi thanks for your reply. but to clarify my setup. my home network is like this:

1. Cable router >
2. Wireless router>
     -another hub>
          -other computers
     -my stepmother's computer
     -wireless connection to my windows/linux>
          -windows ICS to my mac (only on windows, i dont know how to share an internet connection          
            on ubuntu)


I have two connections on my ubuntu

1. LAN (connects linux to mac)
2. WLAN (connects linux to wireless router)


Linux Forever,
Ethan

---

### Post by ethanubutnumaker on 2007-06-18
Basically i have two networks that connects to another network. one of those networks consists of my Win/Linux PC and my Mac. Again, i cant run a cable up a story to my mac. so what i usually do is boot up windows and share my wireless connection with my LAN connection. then set the windows IP in the router field on my mac. that works great. 

however, when i boot ubuntu. i can either have my wireless or my LAN connection active, but not at the same time. so my question is, can i bridge these two connections? or can i have two connections simulatenously connected? or is there a way of broadcasting my wireless internet connection in effect, making my linux box become a router?

ive tried using nat and ipmasqurading but i dont know exactly how this works and there is a huge possibility i missed a step or did it improperly.

I appreciate any help. thanks.

Linux forever,
Ethan

---

