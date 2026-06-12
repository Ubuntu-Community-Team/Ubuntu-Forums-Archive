---
title: "How can i recognize my ieee1394 card?"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by ilios on 2007-03-25
I installed Ubuntu 6.10 in my desktop computer.
I also use a laptop computer with windows XP. 

I want to share my files and internet connection between my desktop and laptop computer. 


Before installing Ubuntu, i used XP. 
So It was easy to detect my 1394 card, 
and set local network connection between them. 

But now, I can't recognize my 1394 card. 

How can i recognize my card? and how can i establish the network connection between my desktop and laptop computer for sharing files, and internet connection? 

I'm beginner of linux. And i can't write english well. T.T 
Please someone help me. Thank you.~

---

### Post by steefjeqv on 2007-03-25
Hi,

I'm trying to establish a connection between two computers using firewire.

For me it's not 100% working at the moment. I can ping to my DNS server but not to the other PC. It can be done though. There's another (small) thread on this forum which was succesful.

Anyway, the answer to your question is the following :

Open terminal and type the following command :

sudo modprobe eth1394

Your firewire port will now be recognized as a network device (eth0 or eth1....).

If I'm not mistaken you'll have to use this command every time you boot.
If this is the case you can do this :

click on system>preferences>sessions and add : modprobe eth1394

I hope this will help you establishing a working connection.

Greetings,
steefjeqv

---

### Post by ilios on 2007-03-25
Thx a lot!

Now i can see another Wired connection  in Network Settings.
But, how can i find shared folders of my laptop using this connection? 
I don't know how to configure this new network connection.


I tried to find my laptop's shared doc 
with browsing all Network Servers i can see,
but i couldn't find.  

What should i do more to access my shared docs in laptop?
Also, what should i do to use internet service in my laptop?? 

i will really appreciate for any little help. Thank you.

---

### Post by steefjeqv on 2007-03-25
Hello again,

First of all, I'm not a network specialist. So any help from fellow forum users would be nice.

You can configure your network interfaces through : System>Administration>Network.

I would suggest to try pinging to your other PC with Network Tools : System>Administration>Network Tools. Click on the Ping tab and fill in the network adress. If this works then you can start installing and configuring Samba.

The networking software you need when connecting between Ubuntu and Windows is called Samba. It's available for install through Synaptic.
Some (a lot) info on Samba : [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

I'm really just getting to know this myself, so it's quite difficult for me to help you. 

Greetings,
steefjeqv

---

### Post by ilios on 2007-03-26
Thank you very much~ 

Now i can access my laptop's share folder

using file brower with location "smb://192.168.0.2". 


And i can use internet in my laptop too!! 

[http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+share](http://ubuntuforums.org/showthread.php?t=91370&highlight=internet+share) 
Above thread was very helpful. 


Thank you for helping me. ~~

---

### Post by steefjeqv on 2007-03-26
Hi ilios,

Glad to hear everything is working !

Greetings,
Steven

---

