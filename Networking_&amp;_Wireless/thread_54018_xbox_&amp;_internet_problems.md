---
title: "xbox &amp; internet problems"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by remin on 2005-08-03
Hi all, I've got a nice little problem after migrating from windows that has been annoying me for months now.
Basically, to connect to the net I still have to use a 56k modem, its an external connected to ttyS0 and I've got an ethernet card thats connected to my xbox.
I throw in the settings for ethernet card, after setting up my external modem perfectly and having the net run fine. Activate my ethernet card through the network settings gui, and to my annoyance the connection to the net stop workings, but my connection to my xbox works.
To get my net connection to work again, I have to deconfigure my ethernet card, and reboot my system. As you can prob tell this is extremely annoying!  ](*,)  ](*,)  ](*,) 
Is there any way to have both connections working harmoniously?

---

### Post by f76 on 2005-08-03
I had a simalar problem with 2 network cards but i think it disappeared when i created a "profile" or "location" for my network setup.

---

### Post by remin on 2005-08-04
[QUOTE=f76]I had a simalar problem with 2 network cards but i think it disappeared when i created a "profile" or "location" for my network setup.[/QUOTE]
I created two "locations", one for the xbox and one for the net.
Didn't work as ubuntu for some strange reason didnt save the settings  :?
I'll try with one location and see what happens...

...still doesnt work :-x

---

### Post by remin on 2005-08-05
Ended up fixing it, yay :)
Have to modify my firewall:

iptables -I INPUT 1 -i eth0 -j ACCEPT 
iptables -I OUTPUT 1 -o eth0 -j ACCEPT

---

