---
title: "Lan can't ping Android IP within network"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by jhay2 on 2014-03-10
hi i have a problem , 
 My computer with lubuntu 13.10 cant ping any wireless IP connected with same network 

My computer IP is 192.168.1.5 
My Android WIFI IP is 192.168.1.10

i can ping my own ip but i cant ping others IP using LAN connection but if i will use WIFI i can ping my android IP , 

$ ping 192.168.1.10 gives me host unreachable

even at the Android terminal , My phone cant ping my computer's IP from the terminal

$ ping 192.168.1.5 gives me host unreachable 


but if i will use WIFI , they can ping each other ,, 


i dont know what's the problem ,


hope someone helps me, any replies are much appreciated 

Sorry for my bad english

---

### Post by rackit on 2014-03-10
Is your router/wifi device segregating wireless and wired traffic?

---

### Post by jhay2 on 2014-03-10
What do you mean sir?

---

### Post by jhay2 on 2014-03-12
:(

---

### Post by rackit on 2014-03-12
Some WiFi routers have host isolation enabled by default. This means that any wireless host can not see any other device on the network. Check your router to see if there is a setting like that.

---

### Post by jhay2 on 2014-03-13
no host isolation on my router

---

### Post by SeijiSensei on 2014-03-13
Since I can ping my Android phone from both wired and wireless devices on my network, something must be interfering.  For comparison, my router is a Buffalo  WZR-300HP with [DD-WRT]("http://dd-wrt.com/site/index") installed, but I've had the same experience with other routers like an ASUS.

How about trying to ping the other way around?  Install [Android Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en) on your phone so you can open a terminal and enter commands.  Android supports the ping command, so you can test whether the phone can ping your other machines.

Another useful tool is the "traceroute" command.  It's not installed by default in Ubuntu, so you'll need to run "sudo apt-get install traceroute" first.  Then use "traceroute -n ip.of.your.phone". (The -n switch tells traceroute to report IP addresses rather than trying to resolve their hostnames.)  You'll be able to tell where the traffic between the two machines is blocked.

---

