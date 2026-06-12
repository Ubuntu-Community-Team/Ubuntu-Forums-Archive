---
title: "Peer to peer bet. Linux and Windows for viewing website"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by cocotu on 2007-01-24
Hi, I have installed apache, mysql, php on my linux box in order to run Joomla and practice a few things.  I don't have a router yet, I want to know if I can view the website connecting peer to peer to the linux box from a Windows machine. I know with Samba you are able to share files, etc. But for viewing this website by typing the linux box IP address on my browser I'm not sure how or if this can be accomplish.  Thanks for your help.

---

### Post by spd106 on 2007-01-24
Yeah, that's fine. You should see the same that you get at [http://127.0.0.1](http://127.0.0.1), just be sure to set up the network. If ping works then http should.

---

### Post by cocotu on 2007-01-24
Right now I'm not home. But lets say I type 127.0.0.1 at my Win machine wouldn't I get the localhost from the Win machine NOT the linux machine? Thanks...

---

### Post by spd106 on 2007-01-24
Sorry, that was very confusing of me.

You are correct, it will show the localhost's webserver, I meant try that on the ubuntu machine. 

From the windows machine just type [http://192.168.0.1](http://192.168.0.1) or whatever the address of the ubuntu machine is.

---

### Post by cocotu on 2007-01-24
ok, thanks spd106. So I just need to connect my win box to my linux box and they would be able to see each other? I have only done this in a network and by typing the linux machine IP I'm able to see the website running in the Linux box.  I will try tonight. Thanks again!

---

