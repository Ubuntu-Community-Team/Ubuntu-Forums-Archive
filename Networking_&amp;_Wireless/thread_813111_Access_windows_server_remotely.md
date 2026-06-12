---
title: "Access windows server remotely"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by sp0nge on 2008-05-30
:confused:

Okay, here is my situation:

I have recently been given the task of designing and implementing a server which will host a website that allows employees to log in and upload specific files, and will allow customers to log in and purchase the right to view and/or print these files. 

My main question at this point is what is the best way for me to allow myself remote access to this windows server from my Ubuntu machine in my home office? I have used terminal services to access windows machines on my local network, but is this something that can be done (efficiently and securely) remotely?

---

### Post by bluefrog on 2008-05-30
thru VPN wouldn't be a problem I guess.

---

### Post by EvilMarshmallow on 2008-05-30
I installed VNC Server on all my Servers at work.  Then using VPN, I can access them remotely with ease.

I wasn't responsible for setting up the VPN, so I'm not sure how it works or if there's a free/cheap way to do it.  I think it requires a router that's capable of supporting VPN, from the little bit I've read about it though.

---

### Post by jimv on 2008-05-30
RDP is fine.  Just forward a port through your router to 3389 on the server.  I would make the external port something other than 3389 so that someone who's port sniffing won't see it and immediately know it's RDP.  So maybe forward 12345 or something to 3389.

---

### Post by sp0nge on 2008-05-30
Thanks for the input. I will try using RDP first, as this has served me fairly well. If there are complications, I'll try VNC next. 

Thanks to jimv for the suggestion of changing the port number.. the main concern in this endeavor is security so I truly want to make it as hard as possible to gain unauthorized access to the machine.

---

