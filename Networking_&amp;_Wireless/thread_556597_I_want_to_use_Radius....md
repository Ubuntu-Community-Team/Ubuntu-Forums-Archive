---
title: "I want to use Radius..."
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Usta_AsH on 2007-09-21
Hello I want to use Radius and I want to set up Load balancing system too.
Can I do that thing on 1 computer which uses Ubuntu server edition?
If you know that how to install radius&load balancing system please tell me!!!

---

### Post by wirelessmonkey on 2007-09-21
What exactly are you trying to do? Do you have enough traffic to justify load balancing? What is your network infrastructure?  

The simple answer to your question, is Yes, you can do load balancing.  I use radiator as a radius server, and the configuration is quite simple.  I know FreeRadius can do it, but I have not configured it for load balancing, just authentication.  

What do you need to know? What experience do you have?

---

### Post by Usta_AsH on 2007-09-22
I'd like to combine my dsl+cable+leased line+satellite connection and I want to share those connection with radius system.
Note: I haven't bought a server. If I am sure to do this I will buy server.

---

### Post by HermanAB on 2007-09-22
This may help: [http://aeronetworks.ca/radius.html](http://aeronetworks.ca/radius.html)

Cheers,

H.

---

### Post by Usta_AsH on 2007-09-22
> **HermanAB said:**
> This may help: [http://aeronetworks.ca/radius.html](http://aeronetworks.ca/radius.html)

Cheers,

H.

This article dedicated for Mandrake.

---

### Post by Usta_AsH on 2007-09-22
Up!

---

### Post by Usta_AsH on 2007-09-23
Up again

---

### Post by wirelessmonkey on 2007-09-23
If you're just load balancing outgoing connections, you probably don't want to user RADIUS, as it's primarily for balancing incomming connections.  

Here's a bunch of links on the topic of load balancing for you:
[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)
[http://tetro.net/misc/multilink.html](http://tetro.net/misc/multilink.html)
[http://www.the-scream.co.uk/forums/showthread.php?s=&postid=62416](http://www.the-scream.co.uk/forums/showthread.php?s=&postid=62416)


Good Luck

---

