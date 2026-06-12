---
title: "Can't activate Desktop Effects."
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-12-23
My desktop effects were working for a while there then they just wont turn back on. I cant activate my Driver hardware ether. it comes up with the install window then it closes without going up any percent. Anyone know how to fix this?

---

### Post by pizza-is-good on 2009-12-23
That happened to me on my first install of Karmic.

I did a clean install after that and it was fixed.

---

### Post by Gone fishing on 2009-12-23
What card is it? 
Can you install the drivers using synaptic?

---

### Post by Rave Gloves on 2009-12-23
> **Gone fishing said:**
> What card is it? 
Can you install the drivers using synaptic?

I dont think i can install from synaptic,

its an NVIDIA 9200 i think

Edit, my home folder is a partion on my laptop if i want to do a clean install i can save the partion and keep the data right?

---

### Post by HereInOz on 2009-12-23
Provided you do a manual partitioning (not guided) and ensure that you DO NOT format the /home partition, the data should still be there.

---

### Post by Taijitu on 2009-12-23
Hi there.

Try to open up synaptic (System -> Administration -> Synaptic) and search for the package called **nvidia-glx-185** and see if it is intalled, and if it isn't, install it and try a reboot.

If it is installed already, then I'm kinda lost...

---

### Post by Rave Gloves on 2009-12-23
> **Taijitu said:**
> Hi there.

Try to open up synaptic (System -> Administration -> Synaptic) and search for the package called **nvidia-glx-185** and see if it is intalled, and if it isn't, install it and try a reboot.

If it is installed already, then I'm kinda lost...

```
nvidia-glx-180:

Package nvidia-glx-180 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

```

Error im getting, go for the fresh install?

---

### Post by Taijitu on 2009-12-23
I most definately think this is fixable without doing a fresh install... I have had this problem too and fixed it. However, I am unable to recall excactly how >.<.

But it could seem something is wrong with your repositories. If you open up Software Sources under Administration and under the options to pick a download server, pick the main server and try to install the nvidia-glx-185 again.

---

### Post by Trisket on 2009-12-23
i had this problem last week.. just delete all the nvidia software you have loaded in synaptic, then reboot and go back into system>administration>hardware drivers these proprietary drivers seem a bit skittish at times..

---

### Post by Rave Gloves on 2009-12-25
After a clean install the problem is still ongoing, i tried the suggestion above but now i cant find nvidia-glx-185 in the synpatic. Please help. i want to be able to use compiz again!

This time, my driver installs for my graphics card but i still cannot activate the extra effects on the appearance menu

---

### Post by Gone fishing on 2009-12-26
Thats odd I'm using nvidia-glx-185
What happens if you 

sudo apt-get install nvidia-glx-185

You should probably install nvidia-settings too

sudo apt-get install nvidia-settings

After edit their is a program called envyng which will install the latest drivers for you if you want it graphical you need to install all the packages but envyng-core will give you a text interface with the command envyng -t not tried it myself but mint comes with the program by default.

---

