---
title: "Can i use Desktop edition and Netbook Remix together ?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by cantech on 2010-06-15
Have a netbook and im using Desktop edition ubuntu becouse i use my netbook with external 20"monitor at home.. But it would be great if i can select to use Netbook remix when i use netbook out of home. cant i switch between them easily.. 

&#304;s that possible ?

Thanks

---

### Post by Chesamo on 2010-06-15
I'm not certain, but I believe so. I think if you install the ubuntu-netbook-remix and the ubuntu-desktop packages, the "sessions" pull-down menu at the bottom of the GDM login window should have both the netbook session and the GNOME session.

---

### Post by bodhi.zazen on 2010-06-15
At the log in (GDM) menu you should be able to choose a standard gnome desktop.

UNR is basically just at theme for gnome.

---

### Post by cantech on 2010-06-15
so its posiible... 

How can i download it on desktop version ubuntu ?

after download how am i going to select or switch between them ?

thanks

---

### Post by Chesamo on 2010-06-15
```
sudo aptitude install -y ubuntu-desktop ubuntu-netbook
```
Then at the login screen, as I've mentioned, the "sessions" menu will be visible after clicking your name to log in (but before entering your password).

---

### Post by cantech on 2010-06-15
> **Chesamo said:**
> ```
sudo aptitude install -y ubuntu-desktop ubuntu-netbook
```
Then at the login screen, as I've mentioned, the "sessions" menu will be visible after clicking your name to log in (but before entering your password).

where am i going to put that code :(

sorry .. newbie here

---

### Post by Chesamo on 2010-06-15
> **cantech said:**
> where am i going to put that code :(

sorry .. newbie here
Applications > Accessories > Terminal

---

### Post by Tempster on 2010-06-15
**Ubuntu Netbook 2D**

I have a very interesting interface on my Compaq Laptop that is a BLEND of Ubuntu Studio and Ubuntu Netbook 2D

Originally, I loaded Ubuntu Netbook on the machine.  Then, I installed all of the Ubuntu Studio software and interfaces. I thought I would end up with a Ubuntu Studio interface but what I actually ended up with was a blend of Ubuntu Studio and Ubuntu Netbook - the interface has the top menu row of Ubuntu Studio and the Ubuntu Netbook menu items on the desktop.

At the login screen under "sessions" was the first time I ever even heard of **Ubuntu Netbook 2D**.  I have to say this blend of Ubuntu Studio and Netbook 2D is a very attractive interface, the best of both worlds.  It can be a pain selecting certain "deep" menu items on the Ubuntu Netbook interface and, conversely, it is very helpful to have frequently used menu items on the desktop.

BTW, I loaded the Ubuntu Studio software and interfaces from the Synaptic Package Manager while I was running Ubuntu Netbook.

---

