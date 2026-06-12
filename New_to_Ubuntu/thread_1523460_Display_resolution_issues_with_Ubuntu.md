---
title: "Display resolution issues with Ubuntu?"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by dmitchell1981 on 2010-07-03
I have an old dell m140 xps laptop that I am using temporarily but I can not get the laptop to display my 20" monitor's native resolution. the specs on located here [http://reviews.cnet.com/laptops/dell-xps…](http://reviews.cnet.com/laptops/dell-xps…) Can this laptop even reach 1680 x 1050 resolution? my ubuntu version is 10.04

Additional Details
my monitor is an ACER 2016W

---

### Post by josephellengar on 2010-07-03
Your link is broken.

---

### Post by dmitchell1981 on 2010-07-03
[http://reviews.cnet.com/laptops/dell-xps-m140-notebook/1707-3121_7-31565934.html](http://reviews.cnet.com/laptops/dell-xps-m140-notebook/1707-3121_7-31565934.html)

---

### Post by josephellengar on 2010-07-03
> **dmitchell1981 said:**
> I have an old dell m140 xps laptop that I am using temporarily but I can not get the laptop to display my 20" monitor's native resolution. the specs on located here [http://reviews.cnet.com/laptops/dell-xps…](http://reviews.cnet.com/laptops/dell-xps…) Can this laptop even reach 1680 x 1050 resolution? my ubuntu version is 10.04

Additional Details
my monitor is an ACER 2016W

This laptop can reach that resolution.  Located at this link is the details of your graphics chipset: [http://www.intel.com/products/chipsets/gma950/index.htm](http://www.intel.com/products/chipsets/gma950/index.htm)  It appears that you can go up to 2048x1536.  However, your problem may lay in the fact that the chipset is set up for a 4:3 ratio while your monitor is 16:10.  That's my best guess, no guarantees.  What is the highest resolution that you can use?

---

### Post by dmitchell1981 on 2010-07-04
1024 x 768 4:3

---

### Post by josephellengar on 2010-07-04
> **dmitchell1981 said:**
> 1024 x 768 4:3

Yeah, so that's probably your problem.  You have to be in a 4:3 resolution.  It's only my best guess though; I'm not an expert on this.

---

### Post by Cypress421 on 2010-09-05
Can you enter
 
```
lspci -v > output && gedit output &
```
 
into the Terminal and then when the text editor appears, search for Intel or Nvidia to find the GPU chipset.

---

### Post by Elfy on 2010-09-05
This got bumped by a spammer - the OP has not been back since July 4th.

Closing - if OP comes back and want's it opening they should use the report button to ask.

---

