---
title: "refresh rate"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by chumley348 on 2009-11-27
Hello,

I am having a small problem.  My refresh rate on my monitor is very slow.  I can move my scroll ball 3 clicks and then wait 5 seconds for the screen to move that far and if I try to rush it, it just moves a little at a time for a long time.  How do you fix this?

---

### Post by overdrank on 2009-11-27
> **chumley348 said:**
> Hello,

I am having a small problem.  My refresh rate on my monitor is very slow.  I can move my scroll ball 3 clicks and then wait 5 seconds for the screen to move that far and if I try to rush it, it just moves a little at a time for a long time.  How do you fix this?

Hi and welcome, have you installed the drivers for your graphics card? You may start under system, Administration, hardware  drivers to see if any are available for your system.
To identify your graphics you may use the command in the terminal
```
lspci | grep VGA
``` Just copy and paste in the terminal located under applications, accessories.

---

### Post by chumley348 on 2009-11-27
thanks for the response.  Here is what comes up in the terminal widow,  Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
Also, I should add that I have a 21" monitor hooked up to a Dell netbook 10V.

---

