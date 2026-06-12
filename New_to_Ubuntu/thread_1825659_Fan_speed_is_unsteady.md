---
title: "Fan speed is unsteady"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Zuoi on 2011-08-15
Hello everyone :)

I've made the switch to Ubuntu recently, and the first thing I noticed is the speed difference. It has taken some time, some wondering and I've had a lot of "a-ha"-moments. There is a lot of great things to say about Windows, but Ubuntu. I love you....

Except for one little thing that has started to annoy me. In Windows the speed of my CPU Fan, on my Asus Z35F was at steady speed. Of course it would spin faster or slower, but the changes between the speed were much more fluent, than they are in Ubuntu. Ubuntu will spin the fan up at a speed I've never heard before for about 3-4 seconds, and then back down to almost silent. The happens when I use something that requires a lot of CPU power of course, and when I do that, the fan's speed just keeps bumping between really fast and loud, and then down to nothing the next moment.

I actually didn't know that the OS had anything to do with adjusting the fan speed. I've always thought that it was the BIOS/Motherboard that did so.

Can I, in anyway control the speed of the fan, or make the speed-switches more fluent, in Ubuntu?

Thank you. :)

---

### Post by grahammechanical on 2011-08-15
Ubuntu is only affecting the CPU fan speed indirectly by running processes that use the CPU.

Install xsensors from the Ubuntu Software Centre. That has a graphical display of temperature and fan speeds. This is better than basing the assessment on how loud the fan noise seems to be. You may have an overheating issue that causes the fans to increase speed until the temperature drops.

Regards.

---

