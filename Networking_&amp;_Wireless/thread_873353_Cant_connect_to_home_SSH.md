---
title: "Cant connect to home SSH"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by uberlube on 2008-07-28
Ok so I recently set up a home SSH server that works for me with no issues as long as its with my internal IP range. I went to no-ip.com and signed up for an account and made a new host using my homes external IP. I then logged into my router and activated dynamicDNS and entered the host address and all other info in the fields and double checked to make sure the info was saved. I am currently on a road trip and Im trying to log in from my hotels wireless connection without much luck. I am attempting to log in using the 'connect to server' option under places in my gnome menu with my host address from no-ip.com with port 22 and my usual username and its returning this message:

> Cannot display location "sftp://***@********.no-ip.***/"
Connection refused by server


I thought that I set everything up correctly but i guess not. Am I not entering the correct info to connect or is this a problem with my ISP? Can you think of any way I can make this connection from here?

Thanks :)

---

### Post by tamoneya on 2008-07-29
you most likely need to setup port forwarding.  That IP is the IP of your router not your computer.  Therefore what ssh is telling you is that the router is not doing anything on port 22.  By forwarding you tell the router that whenever it gets stuff for port 22 send it to your computer at port 22.

---

