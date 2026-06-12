---
title: "Inbound network connections timeout"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by gwyneth on 2007-06-15
I have setup Apache and SSH on Feisty. I opened ports 80 & 22 on my Dlink (DI-624) Router. I have a dyndns account liked to my routers IP to access from outside.

WWW: Within the local network i can access my website but from outside, like from work, i cannot. The page eventually timesout.

SSH: Using Putty to SSH in from work... Sometimes it'll let me login and hang at the user prompt and sometimes it'll hang halfway though login. 
When I try to ping the machine (through remote administration of the router) it says that the ping timed-out. 
If I retry immediately it'll hang (with a black screen & no login options) but if i wait like 5-10 minutes it'll allow me to login again and then hang again. 

I'm sure the router configs work coz 3 weeks ago it worked with my old machine (with dapper) which i recently replaced with a new machine and feisty. Also I did try SSH from work with the older machine at the time and it worked fine. 

Any ideas on how to troubleshoot this?

---

### Post by gwyneth on 2007-06-15
Also.. I have GNUMP3d installed on port 8888. I just tried it from work and it loaded the main page fine. When i tried to navigate to another page it gave me a timeout error..

It seems like any remote connection to the machine goes through initially and then hangs and refreshes/resets itself after a while and then again hangs after initial connection... 

Halp!!!!!!!!!!!

---

### Post by gwyneth on 2007-06-17
cmon... someone help.. dont make me resort to a reinstall or distro change... please!!!

---

### Post by paranoid times on 2007-10-07
I ran into the same problem. It turned out that it was an issue with the firewall. There were a collection of ports open. however one of them was not port 8888. I modified the firewall script (On the computer that I am using to host gnump3 it is a custom script by I don't know who, so I imagine that if this is your problem it will be held in a different place.)

You can probably just check on it by doing an nmap from the outside to your server computer while gnump3 is running to make sure that the port is open. If it doesn't show up when you know it is running it is probably a firewall issue.

Cheers,
Michael

---

