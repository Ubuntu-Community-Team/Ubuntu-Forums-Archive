---
title: "Weird PuTTY problem on fresh Gutsy install"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Contess on 2008-03-09
I can connect to remote proxy server doing this in a terminal window:

sudo ssh -D 88 -p 22 myusername@proxy_IP

..subsequently I am able to tunnel firefox though this connection, all works fine.

However though, If I do the same using putty Firefox does not find nor connect to the tunnel. 
The terminal window opens ok, I type in username and password and the proxy server returns the confirmation but no application can be tunneled. Using EtherApe I can see that the connection to the proxy server is established.

Any ideas

---

### Post by Eiríkr on 2008-03-09
I've never used tunneling myself, but when you first open PuTTY, in the left-hand pane, click Connection -> SSH -> Tunnels, and poke around with the options there.  

HTH,

Eiríkr

---

### Post by frankos44 on 2008-03-09
I dont know why there is a need for putty on Linux? I have always used the normal BASH shell to tunnel.

Obtain shell on remote computer:
$ ssh [email]me@mydomain.com[/email]

Copy files to remote computer:
$ scp *.php [email]me@mydomain.com[/email]:/var/www/mysite

Port redirection using secure tunnel:
$ ssh -L 3307:127.0.0.1:3306 [email]me@mydomain.com[/email]

Does putty do anything else?

---

### Post by Eiríkr on 2008-03-09
Well blow me over, I had no idea it even existed for Unix platforms until just now -- I'd assumed that Contess was talking about PuTTY on Windows.  Heck, that's where the name comes from -- because you use putty to fix windows.  Ba dum, tish!  But now I wander over to the PuTTY page, and lo, it's on Unix now too.  I'm not sure *why*, but okay.  

Cheers,

Eiríkr

---

### Post by Contess on 2008-03-15
well, I like putty because it is user friendly. The command line is too cryptic for my liking. 
I am no CL user. I used windows all my life and I am glad that I now have an alternative user friendly linux version. See, I am not so smart and I don't wan't to spend too much time learning the command line in depht.
This is why I LOVE GUI's

Maybe, I am the only one.

---

### Post by frankos44 on 2008-03-15
> **Contess said:**
> well, I like putty because it is user friendly. The command line is too cryptic for my liking. 
I am no CL user. I used windows all my life and I am glad that I now have an alternative user friendly linux version. See, I am not so smart and I don't wan't to spend too much time learning the command line in depht.
This is why I LOVE GUI's

Maybe, I am the only one.

Once you use the command a few times over it you will remember. It's worth getting used to the command line because it is extremely powerful tool and you can do often do things the GUI cant. Microsoft prompt is rubbish in comparison.

---

### Post by kevdog on 2008-03-15
You can use putty on linux if you wish (no shame in that), however remember putty's keys are slightly different than OpenSSH keys, so if you want to use putty you need to import your private key and convert it to putty's format to work.

---

### Post by TechMansoor on 2008-04-29
> **kevdog said:**
> You can use putty on linux if you wish (no shame in that), however remember putty's keys are slightly different than OpenSSH keys, so if you want to use putty you need to import your private key and convert it to putty's format to work.

Would this have anything to do with putty port redirection and the connection being refused? I tried doing just like in windows where you can specify the local port as well as the redirecting port(rdp 3389 in my case) but the connection always gets refused by terminal client. If I do the same thing in windows, everything works fine.....

---

