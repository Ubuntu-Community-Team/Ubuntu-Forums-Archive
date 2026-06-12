---
title: "Constant Network Activity"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by ux5b2 on 2005-07-25
Hello,

I recently installed gdesklets with a network monitoring app to show my incoming and outgoing traffic.  I noticed that when Im connected to the intered but am not doing anything (no browsers open) I still have in and out traffic.  Is this normal.  I did a netstat and found a bunch of connections that I have no idea what they are (like /tmp/.X11-unix/...).  What should I do to effectively control my incoming and outgoing traffic?

Thanks

---

### Post by cwaldbieser on 2005-07-25
Try "netstat --tcp" to monitor TCP level connections.  You are probably just seeing a lot of UNIX domain sockets which is pretty normal.  They are just used for inter process communication by some programs.

---

### Post by go_bears on 2005-07-29
I added the Network Monitor to my Gnome panel and it shows that i'm constantly receiving packets.  Is this normal?

---

### Post by cwaldbieser on 2005-07-29
I don't have the applet installed, so I am not in a good position to interpret it.  I typically don't receive packets all the time, but my PC is behind my router.  You could get a program like ethereal or tcpdump and capture the packets in real time and see if they make sense.

---

