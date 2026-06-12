---
title: "IP address not being assigned. Can't create network."
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by Genecks on 2007-07-20
At the moment, I'm trying to create a local area network. I'm using two computers with two Ubuntu distributions: Edgy and Feisty.

I cannot get Edgy to assign my ethernet card an IP address.

WIth Feisty (on Computer 1), it seems that all I have to do is connect the wire from one computer to the other.

However, even though Feisty seems to be assigning an IP address when I connect the computers together with a cable, Edgy doesn't take any action to assign an IP address to Computer 2's ethernet card.

I don't know why nothing is really being assigned. I figure it's because Feisty uses some type of program to automatically sense a cat5 mount and then take action. Does Edgy not do this?

How do I get Edgy to assign Computer 2's ethernet card an IP address?

I'm mostly looking for a method through terminal, but if you know of a graphical way, that's ok, too.

---

### Post by alamba on 2007-07-20
In a terminal window, /etc/networking restart.

A

---

