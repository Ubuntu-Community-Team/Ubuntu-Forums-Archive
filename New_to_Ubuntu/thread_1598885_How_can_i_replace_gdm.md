---
title: "How can i replace gdm?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Verbeck on 2010-10-17
Since the current GDM cannot be themed, how can i replace it with an older,theme-able version? or perhaps KDM?

---

### Post by Hippytaff on 2010-10-17
You can get kde by following this tutorial - [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Verbeck on 2010-10-17
i just want to install a new login manager, not a whole desktop environment. thanx for the link though :-k

---

### Post by baraka607 on 2010-10-17
> **Verbeck said:**
> Since the current GDM cannot be themed, how can i replace it with an older,theme-able version? or perhaps KDM?

Try this may work for you:
open terminal and run the following command line

**sudo gpkg-reconfigure gdm**

Just Hit enter at the OK prompt, and then you can switch between the two easily.

All the best friend.:guitar:

---

### Post by Hippytaff on 2010-10-17
> **Verbeck said:**
> i just want to install a new login manager, not a whole desktop environment. thanx for the link though :-k

My mistake...misunderstood your post :-)

---

### Post by Verbeck on 2010-10-17
> **baraka607 said:**
> Try this may work for you:
open terminal and run the following command line

**sudo gpkg-reconfigure gdm**

Just Hit enter at the OK prompt, and then you can switch between the two easily.

All the best friend.:guitar:
thanx. i think its *dpkg* though...


when i try to install kdm thorough synaptic, its downloadding 54 mb of stuff. is it normal?
wdm downloaded less than 1 mb..

---

### Post by baraka607 on 2010-10-17
> **Verbeck said:**
> thanx. i think its *dpkg* though...


when i try to install kdm thorough synaptic, its downloadding 54 mb of stuff. is it normal?
wdm downloaded less than 1 mb..

ha ha ha yeah my bad it is 

sudo dpkg-reconfigure gdm

i have never try to install it through synaptic but i think it is normal.:guitar:

---

### Post by Verbeck on 2010-10-17
After an hour of trying different display managers [wdm, kdm, slim], i'm back to where i started.seems like there is nothing better than the current one...

thanx for the help

---

### Post by jtarin on 2010-10-17
> **Verbeck said:**
> Since the current GDM cannot be themed, 
[Au contraire.]("http://www.linuxtoday.com/news_story.php3?ltsn=2010-05-21-003-35-OS-GN")

---

### Post by Verbeck on 2010-10-17
> **jtarin said:**
> [Au contraire.]("http://www.linuxtoday.com/news_story.php3?ltsn=2010-05-21-003-35-OS-GN")
still cant use gdm themes at gnome-look :(

---

### Post by jtarin on 2010-10-17
:guitar:Nit Picker!!!

---

