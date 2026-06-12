---
title: "Recommended network config for VM server?"
date: 2016-06-09
forum: Networking &amp; Wireless
---

### Post by Alvin_Fletcher on 2016-06-09
Hi there.
So I have a old IBM server running, currently it has 2 Ethernet ports and one extra port (mini BMC 2 provides industry-standard 
Intelligent Platform Management Interface).
Currently I am using the two main ports, Port 1 (enp2s0) to connect to the server to use SSH and xMing and the second one (enp3s1) set to pass through to the first VM.

So here is my first question: Should I get more Ethernet ports?[INDENT]I am wanting to use the first VM as a firewall and currently have ClearOS running, but would it be best to have two dedicated ports for this VM?
[/INDENT]

Second question: Does any one know if the port for Mini DMC would allow me to connect using SSH (PuTTY)?

To help answer the question here is the idea on how the system will be set up.[INDENT]As I am running a hobby personal server I have the internet to my house.
VDSL < Home modem < 2nd Modem < x3250 M2 server < Cisco Switch < Other servers
My Home modem will have all my home pcs and the second modem will control the server network
This allows me to set up the network as follows home: xxx.xxx.1.xxx server: xxx.xxx.2.xxx
Also the x3250 server will have another VM or possible 2 once upgraded, any advice on how to set up virtual Ethernet for them to the first VM would be great
I am using KvM to create VM, using PuTTY to program SSH remotely and xMing (or what ever its called) for x11 to my windows pc.
My networking knowledge is average, I know how to do port forwarding and setting of static IPs via Routers or OS (windows/Linux).
[/INDENT]

If I missed any useful information please let me know and Ill provide you the details

---

