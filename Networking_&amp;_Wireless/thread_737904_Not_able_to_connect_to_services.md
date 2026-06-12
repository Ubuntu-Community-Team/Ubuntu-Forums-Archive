---
title: "Not able to connect to services"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by ac7ss on 2008-03-28
Within my local network I am unable to connect to one of the machines except via ssh. I have installed apache (Works locally) and am also not able to connect to the network printer or xdmcp. What do I have to enable to get these to work right?

---

### Post by Eiríkr on 2008-03-28
It sounds less like enabling something and more like disabling something -- any chance there's a firewall somwhere getting in the way?  Have a look at the process list on the problem machine and make sure the services you expect are running, and ones you don't, aren't.  ;)

Cheers,

Eiríkr

PS - Hey there Olympia!  Ever been to Le Voyeur on 4th?  :)

---

### Post by ac7ss on 2008-03-29
Duh. Firestarter didn't have the permissions for http or xdmcp. (I forget that thing.)

---

### Post by Eiríkr on 2008-03-29
Hope this means all is now working?  If so, please mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

