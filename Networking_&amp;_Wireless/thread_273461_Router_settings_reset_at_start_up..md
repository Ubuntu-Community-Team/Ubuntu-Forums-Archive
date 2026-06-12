---
title: "Router settings reset at start up."
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by -Random- on 2006-10-08
Hi, I just switched to ubuntu (from suse linux on gnome) but I have a problem. Whenever I startup my computer it changes a setting in my router, and all the computers in my house (using the same lan connection) are out of internet. How I fix it is going to my routers address everytime(192.168.2.1) and change the setting "pppoe" to "pppoa" and then it works again. Does anyone of you know how to fix this so I never have to configure my router on startup again?
thanks in advance.
P.S. I have an SMC barricade(not wireless)

---

### Post by mips on 2006-10-08
After you changed the settings on the router did you save them ?

---

### Post by -Random- on 2006-10-09
Yes, I did, after I shut down my computer it still works on al the other computers in my network, but when I start up my computer te router settings change and the whole network doesn't work any more. and if I go to 192.168.2.1 on one of the computers and change the pppoe setting to pppoa it works again. But I don't want to have to do this everytime my computer starts up ;)

---

### Post by mips on 2006-10-09
I don't see how the pc can change the router settings. In order to change the router settings you have to login to the router with a username & password. I cannot see the pc doing this.

Very strange indeed.

---

### Post by ijjz on 2006-10-09
Make sure your router user and administration accounts have strong passwords, and disable remote administration if possible.

As the other person already mentions, I'd double check to make sure the settings are being saved.

Make sure that the PC that boots up, which changes the routers configuration, that it does not have any pppoe or pppoa software on it.

---

