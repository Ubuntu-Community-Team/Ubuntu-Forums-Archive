---
title: "Samba - Vista laptop unable to connect"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by esmurdo on 2008-09-14
Ok, I did a search and couldn't find an answer for my problem, so I'm hoping a new post will work.

I have a ubuntu 8.04 server setup with SAMBA for file and print serving (the printer issue will come later), and I can get my vista-based HP Pavilion 9910 to see it and connect to share the files.
But my problem lies in my wife's vista laptop is not even seeing the server. I've tried mapping, but I guess that doesn't work if the computer doesn't even see the server.

I have one user setup in ubuntu/samba, and the security is set to share. I've tried retracing my steps that I took to setup the first laptop, to include static ip, and WINS server. I may have missed a step, but I cannot remember what it is.

Any ideas?

---

### Post by rcormack on 2008-09-14
It might be a Windows master browser issue and not the ubuntu server.  Windows likes to be master browser.  Sometimes, vista and xp fight over that duty and can mess it up, especially if you are trying to run a wins server.  I have had to stop all the master browsers on my network to ensure all computers are seen in the network neighbourhood as provided by the wins server.

---

### Post by gregphil on 2008-09-14
You say you are using "share" security, but maybe not.  The samba default is 
   security = USER
which means it attempts to authenticate the client trying to connect.  To do this is uses a username and password  you need to enter in the samba database with the tool "smbpasswd".   You could just try adding your wife's Windows username and password with smbpasswd -a user.  Of couse there would need to be an accout with that username and password setup on the linux machine, or you need to map the Windows username to a usable linux username.  I won't go into that yet, lets wait to see if you need it.

If you are sure samba is setup to be security = SHARE, you could look into doing some command line testing from the Vista machine.  I don't remember the details right now but you can use the Windows "net" command to try and list the shares or connect to other machines on the network.  The command line error messages will probably be easier to decode than the GUI silent failure.  

The first thing you should try is to attempt to ping the linux machine from the Vista machine using the machines IP address and then using the COMPUTERNAME.  If the ping with IP works you at least have connectivity, if the ping with computer name fails you have a name resolution issue.  If both are working you probably have an authorization or firewall issue.

And (of course) make sure the Vista machine is accepting the browsing packets, i.e. turn off the Vista firewall or set it to allow the browsing packets through.  If you are behind a router you are fairly safe to being with so you can afford to briefly turn off the firewall for some testing.

Good Luck.

---

