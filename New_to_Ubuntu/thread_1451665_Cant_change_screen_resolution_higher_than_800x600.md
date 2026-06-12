---
title: "Cant change screen resolution higher than 800x600"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Xavant on 2010-04-10
I'm running 8.04, i can only choose screen resolution 640x480 and 800x600, 
i'd like to change it to 1024x768 or 1280x960.  normal resolution for my screen is 1024x768, but i usually have it in 1280x960,  can anyone help?

---

### Post by Revolutionary101 on 2010-04-10
run this in terminal:

```
lspci
```

---

### Post by Xavant on 2010-04-10
> **Revolutionary101 said:**
> run this in terminal:

```
lspci
```

this code only shows my computers  components, doesn't help me making the resolution bigger. :/

---

### Post by clhsharky on 2010-04-10
HI

Well what video chip do you have and what driver are you using?
Sounds like your stuck on vesa.

> I'm running 8.04
Is not enough info on your computer for us to give much help.

Sharky

---

### Post by Revolutionary101 on 2010-04-10
> **Xavant said:**
> this code only shows my computers  components, doesn't help me making the resolution bigger. :/

Yes but we need to know what your graphics card is. Knowing that will help us fix it. Run the previous command again and post the results here.

---

### Post by Miljet on 2010-04-10
What Revolutionary101 meant was to post the results of running the command here so that someone can see what video chipset you have. It is necessary for them to have that information before they can recommend the correct video card driver.

Oops, too slow again.

---

