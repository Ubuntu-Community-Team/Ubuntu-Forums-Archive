---
title: "Can't configure PPPoE connection.."
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by BasiliusCarver on 2008-07-30
I'm confused haha. I have installed ubuntu and have an atheros wireless card which I have got working with ubuntu and although I can connect to the routers in my hostel, (I can see the other computers in the network in "Windows networks" when I am connected (using wicd)) I cannot connect to the internet. The way I connect to the internet is normally through PPPoE through my wireless but I can't configure this through any of the network setup programs I can find in the preferences and admin prefs. My mate told me that the connection I'm trying to create is PPPoEoA and I cant figure out how to do this. The closest I can find is in the network preferences with the point to point connection where you can choose PPPoE but in the next tab I can only select eth0 as the place it's trying to connect through. I imagine this would work if I could set that to be wifi0 or ath0.

---

### Post by superprash2003 on 2008-07-30
i think you mean you want to create a dialer.. for this go to the terminal and type sudo pppoeconf

---

### Post by pranavk_uict on 2010-05-06
But, in that case, you don't actually get WiCD to connect to the internet....
Is there any GUI to connect to internet (using PPPOE)?

---

### Post by khushalb on 2010-07-19
Well friends I am new to ubuntu and I have managed to make a PPPOE connection using what u said sudo pppoeconf. through this i could connect to the internet.

But my issue is that can I create a dialer just like in Windows. In windows I can create a PPPOE connection and Create a dialer. In Ubuntu where is the Dialer where I can use to connect to internet.

---

