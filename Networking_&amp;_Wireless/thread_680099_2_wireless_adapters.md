---
title: "2 wireless adapters"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by craig88 on 2008-01-27
hey guys i have two wireless adpaters one built in and one a plug in basically the plugin is better so is it poss to disable one i dont need both running

---

### Post by hahahan on 2008-01-28
Craig88,

Open : Menu>System>Administration>Network
From there you will be able to configure or disable your networkcards.

Regards

---

### Post by craig88 on 2008-01-28
i opened the network program but i dont see a disable option anyway i just have properties and when i click them i have the option of either roaming mode or a static i.p

---

### Post by hahahan on 2008-01-28
That's for the properties of a specific network card, but in the dialog box that lists all your cards you can able and disable them one by one, at least in my case.
Should also work for you i think.

regards

---

### Post by craig88 on 2008-01-28
i think i se what u mean, the little tick box next to the connections but the only one i can click on or off is the one i want ot use and the one i dont is constantly on and i can turn it off there is just a dash next to it in the tick box

---

### Post by hahahan on 2008-01-28
I have the same situation here. This worked:
Disable roaming mode Menu>System>Administration>Network, select properties untick roaming mode.
You have to enter some config data or you can't close the dialog.
Close dialogbox and untick the desired card.

Goodluck.

---

### Post by craig88 on 2008-01-28
thanks that seems to work but how do i check for def that im on the right i.p and such is there something i can type in the terminal ?

---

### Post by hahahan on 2008-01-28
I think you don't need to but you could do :sudo gedit /etc/network/interfaces and remove all lines conserning the networkcard.

Regards

---

