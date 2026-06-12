---
title: "Problems configuring network"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Tosh3457 on 2008-03-21
Hi, I'm having problems configuring my two network cards. At first when I started my ubuntu I could connect to the internet but my other pc couldn't (the 2 pcs are connected by wire connection). The pc which I could connect to internet is the one with the modem.

So I chose "Network" from administrator menu. The 2 network cards were with that roam something on (I don't remember its name). So I changed one to DCHP and the other one to static IP. 
Then I saved (although I don't think I saved anything, because the dropdown menu didn't show anything and I just typed some random things on location to save (I don't really know anything about this, what does location mean in this context?). 
After this I couldn't connect to internet on any pc. I then putted it roam something  on both network cards but I still had no internet.

Any help? (I'm a total begginer using linux/ubuntu, this was the first time I used it)

---

### Post by Tosh3457 on 2008-03-21
Doesn't anybody know?

---

### Post by odius on 2008-03-21
are you using a crossover cable to connect the two computers?

---

### Post by Tosh3457 on 2008-03-21
> **odius said:**
> are you using a crossover cable to connect the two computers?

Yes, I'm using a crossover cable to connect them.

---

### Post by Tosh3457 on 2008-03-22
Anyone?

---

### Post by Tosh3457 on 2008-03-23
Ok, I tried Ubuntu again and I have internet. But what do I do so my other pc will have internet access too?

---

### Post by kevdog on 2008-03-23
Look for posts entitled bridge or ethernet bridge.  You need to create a bridge between your two physical wireless cards (its a virtual bridge -- not a physical), which will let one card pass through the other.

---

### Post by Tosh3457 on 2008-03-23
I'm not using wireless cards...

---

### Post by kevdog on 2008-03-23
Sorry I meant wired -- you still need a bridge -- that is the same utility routers use to allow multiple computers to be plugged in, yet all still access the internet.

---

### Post by Tosh3457 on 2008-03-23
Sorry but I can't understand the posts I find. I'm a newbie at networking home computers, if anyone could explain how to do it...

Linux is better than windows alright, if I want to spend days and days just to set up a god damn home network...

---

### Post by kevdog on 2008-03-23
Alright can you do me a favor

Can you provide the following:

ifconfig
sudo brctl --version

If brctl comes back blank, you may have to install the bridge utility program.  Make sure you have an internet connection and type at the command line:

sudo aptitude install bridge-utils

---

### Post by Tosh3457 on 2008-03-23
K I'll do that as soon as I can go to Ubuntu again (hopefully today).

---

### Post by kevdog on 2008-03-23
Do me a favor also

Can you draw your planned network configuration?  

Path from internet through different computers, include all routers, modems, computers, etc.

Just want to make sure we are on the same page.

---

