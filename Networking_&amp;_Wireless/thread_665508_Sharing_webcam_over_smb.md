---
title: "Sharing webcam over smb"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by g3brownsc on 2008-01-12
Trying to access a webcam connected to a computer in another room for a quasi-security cam type application. I've set /dev to shared on that computer, and see video0 on the network, but camorama wont recognize it. I can't link to video0, so what do I do to view that webcam from my computer?

Thanks

---

### Post by kidders on 2008-01-13
Hi there,

> **g3brownsc said:**
> I've set /dev to shared on that computer, and see video0 on the networkYou can't do that. Needless to say, Microsoft's filesharing protocols don't have any idea what a /dev node is.

Depending on what you'd like to achieve, you might want to try a conventional video broadcasting technique. There's a wide variety of different sorts of servers available for doing that sort of thing.

---

### Post by g3brownsc on 2008-01-13
I've tried unsuccessfully. I do not have a static IP, so streaming, the ideal method, is out of the question. So there's no way to get video over a network, other than that?

---

### Post by kidders on 2008-01-14
The lack of a static IP really shouldn't make any difference. :confused:

Are you doing something odd that causes a problem during/after address changes?

---

### Post by g3brownsc on 2008-01-14
> **kidders said:**
> The lack of a static IP really shouldn't make any difference. :confused:

Are you doing something odd that causes a problem during/after address changes?

Not that i know of, but both computers are behind a router. How would I set up streaming from behind a router, without a static IP? All of the how-to's I've read have led me to believe i needed a static IP, so I'm clearly missing something. 

Thanks for the feedback.

---

### Post by kidders on 2008-01-15
Hey again,
 
> **g3brownsc said:**
> How would I set up streaming from behind a router, without a static IP?

I'm starting to get the impression you want to stream video over the internet. If so, it's probably worth pointing out that exposing a Samba service to the outside world (for any reason) world is an *extremely* bad idea [SIZE=1]... just in case you're tempted to try it.[/SIZE]

Anyhow, whether your media server will operate on a LAN or over the net, all you really need is a DNS service. It's unusual for dynamically assigned IP addresses to change frequently enough to cause much of a problem.

Serving media over the net does limit your options though, in terms of what sorts of servers you can use. Many of the most commonly used ones are UPnP- or mDNS-based, so they won't be any use. If you're not too fussy about having access to sound, you could always go for a low-tech approach ... eg a Java applet or something similar.

So, where are you planning on serving your webcam to?

---

### Post by g3brownsc on 2008-01-15
Well, I don't have a website to serve it to, so the short answer is I don't know.

Any way to get video up and visible on another laptop, be it over LAN, internet, bluetooth, whatever. I'm open to ideas.

I tried and failed streaming over the internet linking to my IP, and I've lost the link.

Is there anything thats worked for anyone else?

---

