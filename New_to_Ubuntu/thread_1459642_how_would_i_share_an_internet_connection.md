---
title: "how would i share an internet connection?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by cpu_medic on 2010-04-21
hi all, i have a real quick question.
right now i have an agreement with my neighbor that we share his internet. (details aren't applicable) anyhoo i have an old laptop running xp pro, and it is taking the wifi signal and porting it to my router so i have internet in my house. i was wondering if ubuntu had features like this. and if it does how would i get to them. cant wait to be windows free!

---

### Post by cpu_medic on 2010-04-21
so i think i may have found the answer. it lies [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
so i guess this prob is solved.

---

### Post by cuberts on 2010-04-21
> **cpu_medic said:**
> hi all, i have a real quick question.
right now i have an agreement with my neighbor that we share his internet. (details aren't applicable) anyhoo i have an old laptop running xp pro, and it is taking the wifi signal and porting it to my router so i have internet in my house. i was wondering if ubuntu had features like this. and if it does how would i get to them. cant wait to be windows free!How to use Internet Connection Sharing
To use Internet Connection Sharing to share your Internet connection, the host computer must have one network adapter that is configured to connect to the internal network, and one network adapter or modem that is configured to connect to the Internet.

On the host computer
On the host computer, follow these steps to share the Internet connection:
Log on to the host computer as Administrator or as Owner.
Click Start, and then click Control Panel.
Click Network and Internet Connections.
Click Network Connections.
Right-click the connection that you use to connect to the Internet. For example, if you connect to the Internet by using a modem, right-click the connection that you want under Dial-up.
Click Properties.
Click the Advanced tab.
Under Internet Connection Sharing, select the Allow other network users to connect through this computer's Internet connection check box.
If you are sharing a dial-up Internet connection, select the Establish a dial-up connection whenever a computer on my network attempts to access the Internet check box if you want to permit your computer to automatically connect to the Internet.
Click OK. You receive the following message:
When Internet Connection Sharing is enabled, your LAN adapter will be set to use IP
address 192.168.0.1. Your computer may lose connectivity with other computers on
your network. If these other computers have static IP addresses, it is a good idea to set them
to obtain their IP addresses automatically. Are you sure you want to enable Internet
Connection Sharing?
Click Yes.
I hope that this helped

---

