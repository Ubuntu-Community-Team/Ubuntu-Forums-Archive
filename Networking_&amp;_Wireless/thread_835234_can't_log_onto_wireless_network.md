---
title: "can't log onto wireless network"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by tzulpc on 2008-06-20
hi all, 

I installed the Ubunty 8.04 Hardy Heron a few months ago, and wireless internet worked perfectly fine. Now I've moved to stay at my parents' for the summer, but somehow I cant connect. My computer finds the network, but asks for a passphrase, which I do have but it still doesn't log on - the passphrase-box just pops up again. Does anyone have any idea what I should do? I'm new to ubuntu so please bear with me!

thanks!

---

### Post by superprash2003 on 2008-06-20
you might have to choose the right one.. like WEP or WPA, 64 bit or 128bit

---

### Post by tzulpc on 2008-06-21
i tried all of them, still doesn't work!

---

### Post by nickdbliss on 2008-06-21
Try using no authentication method for the router to see if that connects when it is open. 

Also give the output of this file
#sudo gedit /etc/network/interfaces

---

