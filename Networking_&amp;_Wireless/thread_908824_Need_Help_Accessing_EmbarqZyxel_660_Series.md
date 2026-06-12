---
title: "Need Help Accessing Embarq/Zyxel 660 Series"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by AustinMiniMan on 2008-09-02
This is a testament to why noobs messing with network settings is a bad idea. I know this isn't an Ubuntu specific question, but y'all always seem like the most helpful, so...

I have an Embarq 660 DSL Modem, with a Linksys WRT54G. I was setting up remote file access, so I needed to forward Port 80 to my desktop. I got that working alright, forwarding Port 80 to the router, then to my specific IP. Then, toying around with settings, I was under the Remote Management section, and saw the "Remote Management, Port 80" one... not sure the exact wording. Some dumb part of my brain thought that that might interfere with using my PC as a server, so I un-ticked the box next to it. Immediately after doing so, the page went to "Problem Loading Page." 

Now I realise that "Remote Management, Port 80" is what allows you to go in a change the settings. I used to be able to just go to 192.168.2.1 and access my modem, and 192.168.1.1 for the router. The router part of that works fine, but I can't access my modem any more. How do you change a setting so that you can go in to change settings? It's a catch 22 I don't know how to solve. 

I've tried the unplugging and reset for 30 seconds strategy, and have tried connecting the modem directly to my computer to no avail. Any suggestions? I need to either access the modem settings some other way, or just reset it back. Thanks for any help. -AMM

Oh... and the modem was set to router mode, not bridge... so it should be theoretically possible to change the settings if not for this issue.

---

### Post by AustinMiniMan on 2008-09-03
Anyone have any ideas? I can post more details or some screenshots if that would help...

---

### Post by AustinMiniMan on 2008-09-03
As much as I hate to do this... bump. :confused:

---

### Post by bab1 on 2008-09-03
Funny thing, I just talked to Embarq today for a friend.  The manual is available from the Zyxel web site.  I got a PDF of it

From the manual ():
> 1. Make sure the power light is on (not blinking)
2. Press and hold the reset button for 10 seconds or until the POWER light begins to blink.  
3. The defaults should be now reset.

---

### Post by AustinMiniMan on 2008-09-04
You have NO idea how much I appreciate that. I've searched for hours and no one else said that... and not something really guessable, either. 

Thanks SO much... you're the type of person who makes open source communitys like Ubuntu's great. -Ted

---

