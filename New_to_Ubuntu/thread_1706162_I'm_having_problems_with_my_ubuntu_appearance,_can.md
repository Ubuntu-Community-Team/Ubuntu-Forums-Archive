---
title: "I'm having problems with my ubuntu appearance, can anyone help?"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by aknolidge on 2011-03-13
Hey guys, just downloaded ubuntu and I must say I like it !!!! lol:D..

However I have an issue trying to change my appearance, on the visual effect I'm trying to put it on EXTRA rather than have it on simple but, it's giving me a desktop driver cannot be enabled  or some sort, has anybody had similar problems ?

---

### Post by coffeecat on 2011-03-13
This depends on your video card. Some can support visual effects with the default driver, some with a proprietary driver and some not at all. What graphics card do you have? If you are not sure, open a terminal (Applications > Accessories) and run this command:

```
lspci | grep -i VGA
```Post the output; it will tell us which graphics chipset you have.

---

### Post by oldos2er on 2011-03-13
What video card do you have? Check menus System, Administration, Hardware Drivers (or Additional Drivers, I forget the exact menu name) to see if there are any proprietary drivers available for your video card.

---

### Post by aknolidge on 2011-03-13
Hey just downloaded the new ubuntu on my desktop along with my windows 7 ultimate. I'm running the 64-bit on my monitor with 1920x1080 resolution. why is it that my desktop look big? I've been trying to switch my desktop to look normal and not big? Can anybody help with this?

---

### Post by Copper Bezel on 2011-03-13
Big how? Do you mean that the fonts and controls are oversized (or undersized?) You could look into changing the theme to find something with bigger controls, and system font sizes can be changed under the Appearance settings.

---

### Post by overdrank on 2011-03-13
Hi and welcome, please do not create multiple threads on the same issue. Threads merged and moved to Absolute Beginner Talk. :)

---

