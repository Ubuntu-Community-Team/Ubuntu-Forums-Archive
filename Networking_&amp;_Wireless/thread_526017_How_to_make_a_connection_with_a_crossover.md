---
title: "How to make a connection with a crossover?"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by pacsum on 2007-08-15
Hi, I want to move 20GBs from a desktop to a laptop with a crossover cable but I don't know what to do to see the other computer, what do I have to configure? 
BTW both are running feisty.

---

### Post by chewearn on 2007-08-15
First, make sure both computers are in the same subnet.  Assign them with static IP, e.g.
desktop 192.168.1.1
laptop 192.168.1.2

Open a terminal, and ping one computer from another.  E.g. (using the IP address above) from the desktop:
```
ping 192.168.1.2
```

If you see something like this, then the connection should be ok:
```
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=2.91 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.198 ms

```

Press CTRL+C to terminate the ping command.

Next, enable folder sharing on one of the computer:
System > Administration > Shared Folders

Follow the instructions from the GUI (should be straightforward, else you can followed up with your questions here :))

Once you have shared a folder, you can browse it from the other computer, via Places > Network (note: give it a minute or two, for the second computers to see the shared folder).

---

### Post by pacsum on 2007-08-15
Ok I see the computers on the network but when I try to access  the desktop it says "the folder contents could not be displayed. Sorry, couldn't display all the contents of windows network: <name>-desktop."

---

### Post by pacsum on 2007-08-15
now I can't even see the other computer (desktop) :confused:

---

### Post by pacsum on 2007-08-15
Any Ideas?

---

### Post by chalewa on 2007-09-20
is this possible with a windows box and an ubuntu one?

---

