---
title: "Encrypted Remote Access"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by squimito on 2007-01-09
Hello my fellow Ubunuters
I am trying to setup an Ubuntu server to log into remotely.
Are there any encrypted remote access tools / applications that I can use for encrypted remote login. I am looking for something similar to MS Remote Desktop which has built in encryption. Thanks for everyone's help. :D

---

### Post by seuaniu on 2007-01-09
There are 2 ways to look at this:

Servers *generally* don't run a GUI.  Not that they can't, its just considered a waste of resources to have X running on a computer without a monitor.  If you're planning on running in text-only mode, SSH is the way to go.  I can't remember whether or not ssh is installed by default on the server install, but it should be.


If you plan on running a GUI, there are a couple of different options.  VNC is reliable and free.  There should be a couple of different vnc servers in the repositories.  FreeNX is another one, but i haven't been able to get it to work under Edgy.  It worked great in Dapper, but my Edgy upgrade broke it somehow.  NX boasts better performance than vnc over slow connections, so if you don't have much for a connection it might be worth working through potential problems.

Good luck!

---

### Post by tom purl on 2007-01-09
> **seuaniu said:**
> If you plan on running a GUI, there are a couple of different options.  VNC is reliable and free.  There should be a couple of different vnc servers in the repositories.  FreeNX is another one, but i haven't been able to get it to work under Edgy.  It worked great in Dapper, but my Edgy upgrade broke it somehow.  NX boasts better performance than vnc over slow connections, so if you don't have much for a connection it might be worth working through potential problems.

Please note that VNC by itself is not encrypted afaik, but you can run it over a VPN (numerous free implementations exist), or you can run it over an SSH tunnel.  

Also, you may want to consider the SSH-only option seriously.  Yeah, you can only get a terminal prompt, but it's very easy to implement and maintain, and you can do pretty much *anything* from the command line in Linux.

Good luck!

Tom Purl.

---

### Post by squimito on 2007-01-10
Thank you both for your great advice!! I did look at the VNC option previously but never thought of using SSH. I will definitely try this out. This would be great for one user, I was looking more for something like a Terminal Server, where I can have multiple user's remotely log into to a GUI session and use the server like you would in an MS Terminal Server implementation. Thank you again for the great responses!!!! :-D

---

### Post by seuaniu on 2007-01-10
> **squimito said:**
> Thank you both for your great advice!! I did look at the VNC option previously but never thought of using SSH. I will definitely try this out. This would be great for one user, I was looking more for something like a Terminal Server, where I can have multiple user's remotely log into to a GUI session and use the server like you would in an MS Terminal Server implementation. Thank you again for the great responses!!!! :-D

Well, thats different and easy.  Check out the [Linux Terminal Server Project]("http://www.ltsp.org/").  It sports the ability to run one "master computer" and many many dummy clients that act as nothing more than a networked kvm switch.  I take a similar approach to this at home with a couple of old computers that I have lying around, and its nice to be able to log into any of them and have the same desktop.  The only problem that I have is gaming and watching videos, since the screen can't refresh fast enough.  Thats not running ltsp though, just an xdmcp X server, so ltsp might behave differently.  Okay, even I'm getting a headache from all the acronyms :)

---

### Post by squimito on 2007-01-11
Hehe, thanks for the great recommendations. I think I am going to run a few virtual machines and test out both LTSP and XDMCP as viable options. Thank you again for the great help!!! :-D

---

