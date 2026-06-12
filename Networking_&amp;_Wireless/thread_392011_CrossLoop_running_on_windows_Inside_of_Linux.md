---
title: "CrossLoop running on windows Inside of Linux"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by XstatyK on 2007-03-24
This is directed to CrossLoop and not about other types of remote connectivity. (although there are lots like VNC, TightVNC, Ultra... etc. etc.)

After seeing this thread
[http://techrepublic.com.com/5208-6230-0.html?forumID=102&threadID=213785&messageID=2187517](http://techrepublic.com.com/5208-6230-0.html?forumID=102&threadID=213785&messageID=2187517)
and trying out the program I thought it was a very helpful program to help others (friends and family) with their problems on the computer.

But since I mainly use Linux I thought it was bothersome to have to boot into windows just to use this tool.
So since I've been using a program called Virtualbox that lets you install other Operating Systems inside of Linux and Windows, I thought well lets see if it works inside of the virtual Windows that is actually running inside of my Linux system. It did work perfectly and I thought it was cool to say the least.
So If you would like to see a screenshot of it here it is
[http://www.filehive.com/i.php?i=0323/crossloop.jpg](http://www.filehive.com/i.php?i=0323/crossloop.jpg)

So crossloop is a cool tool for those end users who don't know enough about computers to set up a vnc server. And Virtualbox is a cool tool for both Windows users and Linux users. I'm just sharing this with you guys hoping you will find it as useful a tool as I have.

Cheers

---

### Post by vinces1979 on 2008-01-05
Just a note to other users trying to run crossloop on Ubuntu.  Crossloop will run on wine with a few missing features.  Crossloop is nice program for assisting users behind a firewall easily.

I'm running:
Ubuntu Gutsy 7.10
wine-0.9.51
2.6.22-14-generic

Access Works 100% ( All I really need )
File transfer works prefect from host
tranfsering files to the host:
-- When you connect the original window shrinks to about 100x100 window
drag and drop your files onto this smaller window to send file to client.

Share (Doesn't worka at all)
Options Menu (Doesn't work, weird cursor flashing)

But if your like me and need to help out family and friends who are on windows, this is a great little tool and via wine, no virtual machines are needed. 

Thanks Crossloop
Thanks Wine 
And of course all hail Ubuntu

Screenshots:

[http://vinces.ca/shots/crossloop_wine_1.png](http://vinces.ca/shots/crossloop_wine_1.png) < the app running
[http://vinces.ca/shots/crossloop_wine_2.png](http://vinces.ca/shots/crossloop_wine_2.png) < connected :-)

---

### Post by P4man on 2008-04-21
> **vinces1979 said:**
> 
Thanks Crossloop
Thanks Wine 
And of course all hail Ubuntu


and thank you for pointing this out :)

However, I really need something like crossloop under Linux that allows you to **share** a desktop. A friend of mine is migrating to Ubuntu, but she is behind multiple NATs at least one of which she can't control.

Under windows, it works great with crossloop (amazing little app!), and I can connect under Ubuntu  (I use virtualbox anyhow). But when she boots Ubuntu, there is no way I can help her, and thats when she needs it most heh.

Has anyone found a way ? Should we petition Crossloop to make a Linux client too (its based on VNC, so it shouldn't be that hard) ?

Any thoughts ?

---

### Post by vinces1979 on 2008-04-21
Hey there, 

I use Krfb to invite users to vnc into my deskop ( works similar to crossloop) however I don't believe that NAT controls are there.

---

