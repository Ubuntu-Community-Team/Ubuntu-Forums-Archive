---
title: "Internet sharing problem"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by dttk0009 on 2007-09-02
I'm having trouble sharing my internet connection from my Ubuntu (7.04) to my laptop running windows XP SP2. I have a DSL modem running into the computer, and the laptop connects to a second lan card. In Windows, I have these settings, and they work fine.

Local Area Connection 1 (Eth0)
IP - 192.168.1.136
Subnet Mask - 255.255.255.0
Default Gateway - 192.168.1.1


Local Area Connection 2 (Eth1)
IP - 192.168.1.137
Subnet Mask - 255.255.255.0
Default Gateway - 192.168.1.136
Preferred DNS - 192.168.1.136

Local Area Connection 3 (Laptop)
IP - 192.168.1.140
Subnet Mask - 255.255.255.0
Default Gateway - 192.168.1.137
Preferred DNS - 192.168.1.137

In fact, when I try to ping the computers, there's no results either. 
Can anyone give this humble newb some advice?
Much appreciated.:)

---

### Post by randomnote1 on 2007-09-02
Do you have a crossover cable going between the laptop and the computer?  Just a simple way to start the troubleshooting!

---

### Post by dttk0009 on 2007-09-02
Haha, yes I do. As posted, the current set-up works when both computers are in Winxp, but not when my main machine is in Ubuntu. I don't really have a clue how to set up the network between the two machines, despite how much I look online.

---

### Post by dttk0009 on 2007-09-02
Nevermind, I got it working. 
Uninstalled Firestarter and restarted the computer. Upon start-up, it magically fixed itself. :)

---

### Post by randomnote1 on 2007-09-02
my bad...I missed that part...glad you found the problem!

---

