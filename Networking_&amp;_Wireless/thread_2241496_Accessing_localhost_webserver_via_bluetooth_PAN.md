---
title: "Accessing localhost webserver via bluetooth PAN"
date: 2014-08-26
forum: Networking &amp; Wireless
---

### Post by Jo_Mesief on 2014-08-26
I have a server that is running a web server locally. I need to access that site from other bluetooth devices via bluetooth WITHOUT connecting to the internet. I was thinking of creating a bluetooth PAN and then pointing that to the server loopback interface. Then the devices would connect to the PAN and be able to access the site by punching in localhost:80 in the web browser. Is that possible/viable? If so, any references I can look at to do so? Any help is greatly appreciated!

---

### Post by SeijiSensei on 2014-08-27
I don't know anything about PAN, but regardless of what you use, you won't be able to connect directly to 127.0.0.1.  You'll need to create another interface (maybe with PAN?) and communicate with that.

If your phone has wifi and is on the same network as the web server, why not use that instead?

---

### Post by Jo_Mesief on 2014-08-27
> **SeijiSensei said:**
> I don't know anything about PAN, but regardless of what you use, you won't be able to connect directly to 127.0.0.1.  You'll need to create another interface (maybe with PAN?) and communicate with that.

If your phone has wifi and is on the same network as the web server, why not use that instead?

Yeahh. That's what I'm having trouble with, I'm not sure how to create an interface that utilizes bluetooth in order to access the site  :( :( 

I need to access this site through bluetooth somehow because there is no network in place. I need to connect to my server (just the site) even if it does not have any internet connectivity or a local network. Mainly because this server of mine is going to be portable.

---

### Post by SeijiSensei on 2014-08-27
This looks helpful: [http://www.linux.com/learn/tutorials/346552-personal-area-networking-with-bluetooth](http://www.linux.com/learn/tutorials/346552-personal-area-networking-with-bluetooth)

Seems like it creates interfaces with names like pan0 to which an IP address can be attached.

---

### Post by Jo_Mesief on 2014-08-27
Haha I was looking at that same guide. I am able to create a PAN network to a certain extent but I'm having trouble accessing anything through this network. My bluetooth device can't access any bridged connections that were made on my server. I still need to figure out how to point to my webserver still after that. So frustrating :mad:
Thanks for the help so far!

---

