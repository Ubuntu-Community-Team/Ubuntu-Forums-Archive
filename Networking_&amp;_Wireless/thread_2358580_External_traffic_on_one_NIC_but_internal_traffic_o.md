---
title: "External traffic on one NIC but internal traffic on another?"
date: 2017-04-14
forum: Networking &amp; Wireless
---

### Post by djtrainr3k on 2017-04-14
Hello Ubuntu Forums, I have a question I cannot seem to figure out as my Google-Fu is failing me.

Let me explain the setup:


[LIST]
[*]1 Server PC
[*]2 Network interfaces;
[*]enp2s0 (Built In Gigabit)
[*]enp4s2 (100Mbit external NIC)
[/LIST]


[LIST]
[*]Ubuntu OS Version: 17.04
[/LIST]

The Built-in interface (enp2s0) is connected via gigabit switch to an ASuS RT-AC68U router which is the center of the home network.

The External NIC (enp4s2) is connected via an old Netgear FR328S Firewall which is then connected to the same switch and (subsequently) the same network.

What I want to accomplish is to have all ***internal*** network traffic to go through the ***built in*** interface and have ***external*** traffic from port forwarding to go through the ***external NIC*** with the firewall. My main plan so far is to port forward samba and possibly FTP and have all traffic for those services from my public IP go through the firewalled NIC, while still allowing internal network traffic to go through the built in (enp2s0) interface. Any help or alternate networking ideas are welcome and thank you all in advance.

---

### Post by gordintoronto on 2017-04-15
You might want to have a look at pfSense, which would replace your router and firewall, and vastly simplify your network setup.

---

