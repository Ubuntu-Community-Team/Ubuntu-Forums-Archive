---
title: "About making Ubuntu 22.04 an access point"
date: 2024-10-08
forum: Networking &amp; Wireless
---

### Post by noa221 on 2024-10-08
Hello.
I am currently using a Raspberry Pi4 (OS: Ubuntu 22.04).
I would like to experiment with data transmission.
The experimental system is,
PC(172.20.x.x)-wired hub(172.20.x.0)
Wired hub (172.20.x.0)-router (172.20.x.x)
Router(192.168.x.x)-Raspberry Pi(192.168.x.x)&#8592;eth0
Raspberry Pi(10.1.1.1)-wlan0-connected terminal(10.1.x.x)
I assume that the Raspberry Pi is an access point, and I want to experiment with sending data from the connected terminal to the PC.
Initially, I had set wlan0 on the Raspberry Pi to 192.168.x.x to make it an access point, but I could not send data to the PC and thought I needed to change the IP address.
However, when I try to make it an access point while setting it to 10.1.x.x, it does not work.
I would appreciate if someone could tell me how to do this.
Thank you in advance.

---

