---
title: "Pixelated Display"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by moonshyne222 on 2009-05-09
Hello all,

So this is my first time using Linux, so bare with me please! I'm a windows native, Frank-er installed Ubuntu on my laptop, saying its better than windows. We'll see about that...here we go!

The display is all pixelated, and weird. Its almost like glowing, and a screenshot really doesn't show what i'm talking about. Anyone able to give me a heads up?

Started with ubuntu 8.10 and than upgraded to 9.04. The display shows colors almost like negatives.

I'm on an Acer Aspire 4000 series...I think?

---

### Post by freak42 on 2009-05-10
what video driver are you using?

if you don't know post the contents of the /etc/X11/xorg.conf file (gedit /etc/X11/xorg.conf)

---

### Post by ashmew2 on 2009-05-10
If its an Nvidia/Ati Graphic Card , you SHOULD install the proprietary hardware drivers which the companies provide. If you have an integrated Intel graphic card  , I think you are better off reverting to 8.10 (or any other previous version) because as far as ive heard , there are problems with Intel on Jaunty (Ubuntu 9.04 i mean).

---

### Post by moonshyne222 on 2009-05-10
Honestly, i think this board is using onboard graphics. The display has always been like this...pixelated and such. No drivers available, i've tried to look.

---

### Post by pauna on 2009-05-10
> **moonshyne222 said:**
> Honestly, i think this board is using onboard graphics. The display has always been like this...pixelated and such. No drivers available, i've tried to look.

Could you please output the parts of "lspci -v" that talk about graphics controllers. That will help us tell you what drivers you need.

---

### Post by moonshyne222 on 2009-05-10
> **pauna said:**
> Could you please output the parts of "lspci -v" that talk about graphics controllers. That will help us tell you what drivers you need.
  
And what exactly is that? A terminal command im guessing? If so, can you tell me EXACTLY what to type. Im horrible with the terminal and always fail with it.

---

