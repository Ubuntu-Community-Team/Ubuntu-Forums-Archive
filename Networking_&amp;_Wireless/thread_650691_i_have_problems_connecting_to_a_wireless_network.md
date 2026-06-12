---
title: "i have problems connecting to a wireless network"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by boboyo on 2007-12-26
need help for the ubuntu part of my laptop

i cant connect to wireless. when i set up my connection for wireless, i says im connected but when i go on firefox, it says im not connected. i need to plug the cable from my router in my laptop if i want to go on the internet with linux. is there a way to connect without using a cable or terminal because ive already tried to do it and it doesnt work. maybe i wrote the wrong things.

does ubuntu 7.10 support linksys wireless router?


plz help me

---

### Post by reef2dive on 2007-12-26
Sorry cannot help, but I have had similar problem. In my case applications running in the terminal window could access internet, while applications running on directly could not access it. I never got around it used, I ended up using a router as a wireless card. In the current release it is gone.

What you could start is to check your routing with 

user@mu:/etc$ ip route show
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.104 
169.254.0.0/16 dev eth0  proto kernel  scope link  src 169.254.11.254 
default via 192.168.0.1 dev eth1 
default dev eth0  scope link  metric 1000 

to see that the gateway matches the expected one. As you see in my case the fixed link is down and the wireless is up. Additionally in my experience the connection to wireless is rather sluggish in Ubuntu compared to W2k and WXP.

---

