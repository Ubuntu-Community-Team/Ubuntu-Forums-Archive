---
title: "Ubuntu, Apache, and a static IP (comcast)"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by steveschutt@comcast.net on 2008-09-29
I recently obtained five static IPs from Comcast and complete the install for a Ubuntu LAMP server. For convenience I also installed GNOME and made it optional so that I could start it whenever I wanted(via "sudo startx"), but if I got things running well it wouldn't be needed most of the time. I'm using GNOME for all my configuration activities, not the command line and VI.

Everything I've read so far about setting up Apache seems to imply that I have to put the static IP info I received from Comcast in by going to Menu|System|Administration|Network. I have set the connection with the info provided to me from Comcast; i.e., the static IP for the server, the Gateway IP, the subnet mask, and the DNS as provided by Comcast when they issued the static IP. 

But this server is not visible to the outside world; "localhost" works fine and shows the "It Works!" page when I open Firefox on the server itself, but attempting to type in the static IP from a computer that is outside my LAN gives page not found.

I have an IIS server on the same gateway and LAN inside my office, and I am using one of the five static IPs that Comcast issued to me for that server (a different IP, not the same one that I'm trying to use on the Ubuntu/Apache server). The ISS server works fine, so I believe that Comcast has done everything they need to do to register these IPs. I've double-checked my IP values (the IP to the DNS, the gateway, and the server itself) and I'm sure the numbers are right.

Am I missing something obvious? Where do you set the "outside" IP address for Apache so that entering "HTTP://123.123.12.1" in a browser that is OUTSIDE my LAN (with my IP numbers, of course) would find this computer?

---

### Post by PatricioLearner on 2008-10-03
I am interested on this... because I am getting ready to do the same.  No replies?
Thanks!

---

### Post by jones139 on 2008-10-03
Can you explain how you have things connected up please?  Do you have a single router and cable modem to connect your local network to the internet, but you ISP has set up several static IP addresses to point to it, or do you have several separate internet connections?
If it is working through a router you will need to configure your router to forward requests for your specific ip address to the correct computer?  Can you access your computer generally from the outside world?  I am wondering if it is an apache problem or a general network one?

GJ

---

### Post by gpsmikey on 2008-10-03
Comcast may be blocking port 80 - I don't remember if you are allowed to have a server on your network (have to read your AUP from Comcast).  Can you ping that address and get a response? (from the outside).

I would also suggest changing your name here - if that is indeed a valid email address, you will find yourself on the receiving end of much more junk email - there are all sorts of automated critters that scan posts and web pages looking for email addresses to "harvest" (I put my email address on my web page as a small jpg so it only is visible when viewing the web page, but scanning the HTML reveals nothing useful to the harvesters).

mikey

---

