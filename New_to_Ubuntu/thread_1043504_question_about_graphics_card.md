---
title: "question about graphics card"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-01-18
hi everyone,i am presently using ubuntu8.04,on a system that has 2 gigs of RAM,a 2GHz core2duo,and an nvidia Geforce 6200(256 MB).the eyecandy on my system is not that snappy.so,i am upgrading to a new graphics card,may be Geforce XFX 8400GS 256MB.how smoother the graphics will be in the latter case.also,tell me if ubuntu would recognize on its own the changed hardware configuration,and do with the present nvidia driver?

---

### Post by Crafty Kisses on 2009-01-18
I think it will make a difference, that card does work with Ubuntu. This card should do you well.

---

### Post by jimmy the saint on 2009-01-18
Just to be on the safe side, I would go the the hardware drivers app (system>administration>Hardware Drivers) and disable the restricted driver in use first.  then swap the cards and let Ubuntu recognize the new card then go back to the Hardware driver app and use the one that becomes available.  Probably not neccessary but I find that its better to eliminate the possiblitiy of issues than to deal with them as they come.

---

### Post by o.besner on 2009-01-18
You might wanna have a look at your xorg.conf once the card is installed

sudo gedit /etc/X11/xorg.conf

but you'll probably have to change nothing at all, and everything should work fine. As for speed... it will depend on how much bling you use on your desktop, but if you like the cube, transparency and 3D effects you'll notice a good boost.

---

### Post by nhasian on 2009-01-18
i have almost the same system as you but i have an nvidia 8600m and the graphics are pretty snappy.  

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201305520548%20106792522&name=GeForce%209%20series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048%201305520548%20106792522&name=GeForce%209%20series)

---

### Post by Prospero2006 on 2009-01-18
Have you run ```

envyng -t

```
?

---

