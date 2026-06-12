---
title: "how to monitor network traffic"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by sn0m on 2008-07-07
Hi guys
There's some strange activity on my network, theres uploading, while I have not any programs that i know off uploading any stuff, ie deluge is closed??
Is there any program that will tell me whats sending what or downloading what before I freak out and reset my house wireless network.
Ta 
Sokol

---

### Post by pytheas22 on 2008-07-07
A little bit of uploading is normal, so there's not necessarily any reason to worry.  You can take a look at the information going out and its destination with Wireshark:
```

sudo apt-get install wireshark
```

Make a packet dump of the traffic and you can see everything that's going on.

---

### Post by sn0m on 2008-07-07
Thanks for you quick answer mate. I'm quite newbe so would appreciate a bit more help. How do I find my interface?
ta 
Sokol

---

### Post by pytheas22 on 2008-07-07
No problem.  Once you install Wireshark (using the apt-get command above or Synaptic), open it by pressing F2 and typing "gksudo wireshark" (you can run as a normal user from the Applications>Internet menu, but it's better to run as root).  In the top-left corner of Wireshark, click the button that says "List the available capture interfaces" when you hover the mouse over it.  From there, you choose the interface you want to capture on (probably the one connected to the Internet) and you can begin a packet capture.

Once you start capturing, you can see all the packets going into and out of your computer, and their origin and destination.  For some kinds of packets, you can right-click and select "view TCP stream" (or something close to that) and view the information inside them.  This information can give you a big clue as to whether the traffic is legitimate or not.

If you have any more trouble, feel free to ask.

---

