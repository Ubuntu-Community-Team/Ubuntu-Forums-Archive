---
title: "Wireless / Wired File Sharing"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Captain_Falafel on 2008-11-05
For the record, I'm a n00b. I need to move all my files back to my Intrepid box from my Vista box either with a wired ethernet cable or through my wireless network. However, I tried connecting with an ethernet cable through a router with both computers and niether seem to connect or see each other. I'm absolutely clueless about wirless file sharing/networking, and even more clueless about the way Vista runs things.
Can someone point me in the right direction because I really don't want to resort back to transfering all my files via USB drives (which is what I did to move them from Hardy to Vista) :P

---

### Post by Captain_Falafel on 2009-01-05
bump

---

### Post by grappler on 2009-01-05
There are various ways - including samba - but I guess the way I'd go (for simplicity) is to install an openssh server on the ubuntu machine - install openssh-server and openssh-client using synaptic. On the windows machine install putty. 

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

Since I don't run a windows machine I can't help much here. 

Then from the windows machine you can scp <files> to the linux machine on your local network.

---

