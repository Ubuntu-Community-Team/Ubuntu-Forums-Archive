---
title: "wireless access point behind router-cant see wired network now?"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by e1ektrob0y on 2008-01-19
I have recently set up a wireless access point behind my router for my media center running mythtv. I now have wireless internet on the media center but it can no longer see or be seen by samba, nor can i ssh in or out from the other computer (most importantly the file server).
The adsl router is 192.168.1.1 and the wireless access point is 192.168.0.1. all my other pc's have 192.168.1.- addresses and the media center is now 192.168.0.100. What have i done wrong here? 
the main goal is to hook up nfs for mythtv from the file server to the media center...

---

### Post by kevdog on 2008-01-19
Did you turn off the dhcp server on the access point??  You probably dont want two separate subnets  dot you?  Are you using dd-wrt on the Access Point?

---

### Post by e1ektrob0y on 2008-01-19
> **kevdog said:**
> Did you turn off the dhcp server on the access point??  You probably dont want two separate subnets  dot you?  Are you using dd-wrt on the Access Point?
if i turn off DHCP on the access point, the internet stops working...and what is dd-wrt?

---

### Post by kevdog on 2008-01-19
Hmm, you havent described your situation fully.

Do you require separate subnets?

Can you provide a drawing or something that describes the way you want to setup your network.  I may be making some incorrect assumptions.

---

### Post by e1ektrob0y on 2008-01-20
> **kevdog said:**
> Hmm, you havent described your situation fully.

Do you require separate subnets?

Can you provide a drawing or something that describes the way you want to setup your network.  I may be making some incorrect assumptions.
hopefully this will help. i want the other two pc's to be able to see the media center behind the wireless access point and vice versa if that makes sense. its not that complicated i'm sure its just something simple that i haven't done...

[IMG]http://i74.photobucket.com/albums/i247/dales618/routing.jpg[/IMG]

---

