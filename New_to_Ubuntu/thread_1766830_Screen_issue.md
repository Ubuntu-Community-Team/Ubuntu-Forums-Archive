---
title: "Screen issue"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by fritz269 on 2011-05-24
Anyone help me find what the issue is on the screen here. It is now a permanent problem. I can live with it but would rather find out what is wrong. Thanks. Look at picture below

Oh, it only is happening on the left side of the screen

---

### Post by decoherence on 2011-05-24
What kind of video card do you have? Did the Additional Drivers program install any additional drivers?

You can find out specifically what video card you have if you type the following in to a terminal. Certain models have certain quirks so it'd be good to know specifically if you have, for instance, a GeForce Go 7300 or something.

```

lspci | grep VGA

```

---

### Post by wildmanne39 on 2011-05-24
> **fritz269 said:**
> Anyone help me find what the issue is on the screen here. It is now a permanent problem. I can live with it but would rather find out what is wrong. Thanks. Look at picture below

Oh, it only is happening on the left side of the screenHi, I had that problem with the cube and effects active in ubuntu classic, but I know have the cube in unity by following instructions from a thread on here and that fixed my problem.:)

---

### Post by sandyd on 2011-05-24
> **fritz269 said:**
> Anyone help me find what the issue is on the screen here. It is now a permanent problem. I can live with it but would rather find out what is wrong. Thanks. Look at picture below

Oh, it only is happening on the left side of the screen

what graphics drivers are you using?
In the past (and on certain cards), transparency when using docks + opengl don't mix properly. (demonstrated with cairodock + fglrx)

---

### Post by fritz269 on 2011-05-24
Well, it only happens sometimes and usually I can restart and not have a problem. However, this afternoon it did not help. I finally got it back to normal. My card: 

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

If its the transparency that I have to disable then I will do it but i'm hoping I don't have to.

no additional drivers were loaded

---

