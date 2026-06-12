---
title: "New pc build slight issues . ."
date: 2010-05-30
forum: New to Ubuntu
---

### Post by DigitalDakness on 2010-05-30
HI guys i have just built a little pc to hook up to my tv.
Now i have ubuntu installed ( obviously ) everything is running fine BUT the screen usage is a bit off.
What i mean is i have black borders around my tv.
My tv is a toshiba 37" lcd with a native screen res of 1280 x 768 but can do 1080p if needed.

The gfx chip is built into the mobo.
Here is my system speccies.

Amd phenom b35 running at 3.7 ghz per core.
2gb ddr2 ram
500gb hdd
Gigabyte MA78LM-S2H Motherboard with intergrated hd radeon 3000 gfx chip.

How do i gain access to the "overscan" util what is normaly found in the windows version of catalyst.?

Many thanks in advance,

Karl

---

### Post by Ozymandias_117 on 2010-05-30
I believe it's in  the text based controls only.  the command is ```
aticonfig --tv-overscan=on
```.

---

### Post by DigitalDakness on 2010-05-30
> **Ozymandias_117 said:**
> I believe it's in  the text based controls only.  the command is ```
aticonfig --tv-overscan=on
```.


How do i do that?

---

### Post by Autodave on 2010-05-30
> **DigitalDakness said:**
> How do i do that?

Applications > Accessories > Terminal

Copy and paste that line in and hit ENTER.  It will ask for your password.  Enter your password and it will do the rest. :-)

---

