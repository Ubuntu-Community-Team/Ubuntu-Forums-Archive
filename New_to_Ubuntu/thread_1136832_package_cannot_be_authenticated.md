---
title: "package cannot be authenticated"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by g2c on 2009-04-25
when trying to get-install gpicview (aprently) an image viewer) It says 

*the following packages can not be authenticated *then a list including *gpicview*

What does this mean? Can this be hasardeus?

---

### Post by Spiritous on 2009-04-25
> **g2c said:**
> when trying to get-install gpicview (aprently) an image viewer) It says 

*the following packages can not be authenticated *then a list including *gpicview*

What does this mean? Can this be hasardeus?

I had this yesterday with WINE, I just gave up on it... I would quite like to know how to fix, though :)

---

### Post by Sealbhach on 2009-04-25
It means it's not from an official Ubuntu source. It's probably quite OK but it's not certified or got a security key or anything so it's at your own risk if you download it. 

If you look in Synaptic at the Properties for gpicview it says the maintainer is

Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>

so personally, if it was me I would trust it.


.

---

### Post by Sealbhach on 2009-04-25
> **Spiritous said:**
> I had this yesterday with WINE, I just gave up on it... I would quite like to know how to fix, though :)

If you add the wine repos to your software sources and then add Scott Ritchies security key:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

You would proably not get that message when installing wine.

.

---

### Post by Bölvaður on 2009-04-25
yes when you add some repos to your list you need to varify that the packages in them have not been modified by using a key which you have to get from their website.

Look on the website you got the program or repo from and follow the instructions on how to add this special key.

---

