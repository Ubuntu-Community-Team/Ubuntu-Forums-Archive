---
title: "How to configure VNC for another networked computer"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by BigG123 on 2007-04-12
Hey I got a friend that has a vnc server running on one of his computer in his network (192.168.100) but he's tring to install it on another computer (192.168.0.102) so I know you need to have the second computer's VNC server to be running on a different port than the first.   But after you open the ports how do you connect to it?  When you go to the java viewer it just says 

"Connection.Exception... stuff Any idea's or any experience? 

It can't be you can only have one pc running VNC outside of LAN!

---

### Post by BigG123 on 2007-04-12
Also I just noticed when you connect to a VNC server you can say :1 after the ip to specify I guess 192.168.0.101?

---

### Post by CompShrink on 2007-04-13
First of all, please don't start multiple threads in different areas about the same thing.

Second, a little tip, if you use the edit button instead of making a second post on the same thread, you would show up when people search for "unanswered posts." Probably a small number of people do that search, but they're probably the people most wanting to help.

Third, I'll try to help you. but I know personally several people that wouldn't help you simply because the cross-posting is annoying. Anyway, the :1 in your example has nothing to do with the 4 part IP address, eg 192.168.0.102. It specifies the port VNC will use, and it is required when you use the client, and it has to match the port the server set.  generally when you start up a vncserver session, it will give you something along the lines of:

New 'HOSTNAME:10064 (username)' desktop is HOSTNAME:10064
access with: vncviewer HOSTNAME:15064
or: [http://WEBHOST:14064](http://WEBHOST:14064)

obviously, this varies depending on what server you are using.

---

### Post by BigG123 on 2007-04-13
you didn't help me at all.  All you did was tell me something that I know.

---

### Post by CompShrink on 2007-04-14
What you said in your second post contradicts what I wrote, so I don't see how I only told you things you already knew.

Example: 192.168.0.100:1 does NOT mean 192.168.0.101. It means port number 1 on 192.68.0.100, which of course would never actually be used, ports 1023 and below are reserved for root on linux.

The entire, specific error message would help. As would a better attitude, I'm sorry if I came off as having a "holier than thou" attitude in my first post.

---

### Post by joe007 on 2007-04-23
So I do vncviewer from a term window followed by the ip address I want to connect to, a Win 2k3 server, locked.  How do i send a C-A-D to allow me to enter the pwd?  Running 7.04

thanks

Can you tell I am new to Linux?

:)

---

### Post by joe007 on 2007-04-23
Got it

<shift><ctrl><alt><del>

cya

---

