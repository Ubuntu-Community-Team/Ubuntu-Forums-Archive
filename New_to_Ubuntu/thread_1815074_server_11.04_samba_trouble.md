---
title: "server 11.04 samba trouble"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by zurplfoo on 2011-07-30
Hey guys, 
I'm an absolute beginner and try to setup a ubuntu server as a home file server. I got here a lot useful information, but I still have trouble with setup of samba...  

Network: 
1 Laptop   
   - Windows 7 
1 PC
   - Windows 7
   - VMWare (Ubuntu Server 11.04)  

While installation I was following the instruction from the ubuntu pages, howtoforge (setup simple file server) and some helpful information from this board.

Well the thing is, that after installing and configure the samba I put the setting on the lowest security -> 0777 for the folder with nogroup and nouser (also samba has nouser/nogroup in the config for this share) to make sure that I get access at all. Well that works perfectly with the laptop, but not on the PC. Even I see the Server in the "Network" view, I can't access.  

I tried everything: I find in the samba log file with the name of the PC "getpeername failed. error was transport endpoint is not connected samba". But this says nothing to me...  
Also the print of smbtree is not showing the PC, but the laptop.  

In my desperation I tried to change the samba to samba4... and went back to samba 3.4.7  

I think it got worse after that... :(  
I hope someone can help me...  

Best regards, Z

---

### Post by gordintoronto on 2011-07-30
It's much, much easier to install Desktop Ubuntu (perhaps the long-term release, 10.04), then use the Nautilus file manager to create and share (under the right-click menu) some folders.

"Server" is really meant for "headless" computers hosting high-volume web sites, or other applications where performance is an issue.

---

