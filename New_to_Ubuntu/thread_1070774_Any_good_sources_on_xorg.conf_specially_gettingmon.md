---
title: "Any good sources on xorg.conf specially gettingmonitors to work?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Qwertinsky on 2009-02-15
I would have to say this is the part about install Linux that always drives
me nuts.

I have several monitors here, two Samsung LCD's on standard one wide screen
and and a Viewsonic widescreen, fairly new all LCD and X always wants to
default to some obnoxiously high scan rate or resoultion that none of my
monitors work.

Being a Linux novice I tend to gravitate towards Ubuntu. The last Ubuntu to
"just work" for me was 6.06. Why don't they default X to a lower refresh
rate or resoultion on first start and let the user set it up properly?

Anyway is there a place online I can find a good decription of how to set my
xorg.conf so at least one of my monitors is usuable?

Rant=On
I think this is one of the big things that is holding Linx back from real
mainstreem adoption. I can't even run the graphical instalers on any of my
monitors because it's a jumbled mess or just flashed "out of range". So I
end up using the tesx based installers. Then spend a couple hours installing
and the first boot screen is again a jumbled mess or "out of range" it's
very disspointing. Spending a day or two figuring out how to simply display
some information on the screen is a real P.I.A, and I LIKE doing this...
Imagine the average user
Rant=Off

---

### Post by bodhi.zazen on 2009-02-15
Bad news : With the new xorg , **xorg.conf is depreciated**.

The idea is that hardware detection is improved and it should "just work". While this is great when it works, it is more difficult when it does not work.

By that, old edits to xorg.conf usually do not work as they have in the past and I am not aware of any documentation on how the new xorg.conf should work.

We need to know your video card as configuring nvidia is different from ati, etc ...

---

### Post by Qwertinsky on 2009-02-15
OK I am installing Ubuntu 8.04.1 (Xubuntu) on a [**DecTOP**]("http://www.dataevolution.com/dectop%20info%202.htm"). 

It has an AMD Geode processor and chipset.

There are a few people who got [**6.06**]("URL="http://jsco.org/dectop/") running and [**7.10**]("http://entropicblur.com/dectop/guide.html")

I can see when it boots it is loading the Geode GX Frame buffer device.

My monitor is a ViewSonic VX1962vm 
Resoultion up to 1680x1050
Horizontal 24-48Khz
Vertical 50-75Hz

---

### Post by Qwertinsky on 2009-02-16
How can I make it boot to a command line instead of the graphical login other than selecting repair mode at the grub prompt.

I really do not need X for my purpose, I just thought it would be nice to have working.

---

### Post by pgatrick on 2009-02-16
Check out 'man inittab'. I think that's what you need.

---

### Post by plucky on 2009-02-16
OK > I am installing Ubuntu 8.04.1 (Xubuntu) on a DecTOP. 


You should still be able to reconfigure your displays using in a terminal ```
gksudo displayconfig-gtk
```

Just don't use the test button after you have selected your display resolution.


Good Luck

---

### Post by Qwertinsky on 2009-02-16
> **plucky said:**
> OK 
You should still be able to reconfigure your displays using in a terminal ```
gksudo displayconfig-gtk
```


(gksudo:4256): Gtk-WARNING **: Cannot open display:

:(

---

### Post by Qwertinsky on 2009-02-16
> **pgatrick said:**
> Check out 'man inittab'. I think that's what you need.

No manual entry for inittab

:(

---

