---
title: "Strange Problem with the network manager"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Lieter on 2007-05-14
or maybe its very simple, anyhow. 

Ive got my laptop with ubuntu 7.04 installed now, wifi works (NDISwrapper) but to cp files between systems i prefer the wired connection,  but i need to have it plugged in at boot for it to connect using the network manager. i figure i can fix it bt i dont know how, changing options in network admin wont help. So if you guys have any advice, thanks :)

---

### Post by Floppyjoe on 2007-05-14
> **Lieter said:**
> or maybe its very simple, anyhow. 

Ive got my laptop with ubuntu 7.04 installed now, wifi works (NDISwrapper) but to cp files between systems i prefer the wired connection,  but i need to have it plugged in at boot for it to connect using the network manager. i figure i can fix it bt i dont know how, changing options in network admin wont help. So if you guys have any advice, thanks :)

Click on the little Icon with the picture of two computer screens networking along the top bar and then click on wired network to make sure it is selected. Also make sure roaming mode is enabled on the wired adapter in System/Administration/Network.

---

### Post by Lieter on 2007-05-15
that is the point, i cant select is and wifi is in roaming. its blanked out. but it is selectable when I have a cable plugged in during boot

---

### Post by NilsE on 2007-05-15
> **Lieter said:**
> that is the point, i cant select is and wifi is in roaming. its blanked out. but it is selectable when I have a cable plugged in during boot
Go into manual configuration and make sure roaming is selected for wired and wireless.  

Then You may also have to clean out the /etc/network/interfaces file if you have configured any devices manually. Just leave these 2 lines. (back it up first)



auto lo

iface lo inet loopback

---

### Post by Lieter on 2007-05-17
> **NilsE said:**
> Go into manual configuration and make sure roaming is selected for wired and wireless.  

Then You may also have to clean out the /etc/network/interfaces file if you have configured any devices manually. Just leave these 2 lines. (back it up first)



auto lo

iface lo inet loopback

done that both, but its still blanked out if i dont boot with a cable inserted

---

