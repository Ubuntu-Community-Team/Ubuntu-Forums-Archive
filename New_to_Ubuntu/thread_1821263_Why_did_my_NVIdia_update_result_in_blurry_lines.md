---
title: "Why did my NVIdia update result in blurry lines?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-08-08
I've had my nvidia video card since 2003. I didn't know what driver updates were nor that they existed until yesterday so today I went to the nvidia website to install the update. Everything seems the same as before except when I go to this website

[http://www.chess.com/play/computer.html](http://www.chess.com/play/computer.html)

I get a box that's full of red and blue lines and dots nonsense. When I uninstall the update, I get the chessboard as usual. I already have Java installed so why is this happening?

Since it's fine without the update, why would nvidia choose to make the user experience worse?

---

### Post by wildmanne39 on 2011-08-08
Hi, it is just trial and error with nvidia and ati drivers some work in one system and not in others.

---

### Post by brawnypandora0 on 2011-08-08
> **wildmanne39 said:**
> Hi, it is just trial and error with nvidia and ati drivers some work in one system and not in others.

What! So whether it works on any particular computer depends upon pure chance with relation to the motherboards? What incompetence!

---

### Post by wildmanne39 on 2011-08-08
Hi, for instance the nvidia drivers are having trouble with 11.04 not a particular piece of hardware. 

As far as I know all nvidia card can work with 11.04 but you have to try different ones sometimes to find the one that works best for you.

---

### Post by CatKiller on 2011-08-09
You don't generally need to install things from random websites to get updates in Ubuntu.

---

### Post by beew on 2011-08-09
> **wildmanne39 said:**
> Hi, for instance the nvidia drivers are having trouble with 11.04 not a particular piece of hardware. 


Well it works out of the box for me. I have upgraded the driver many times too using ppa (now at 280.13)

---

### Post by beew on 2011-08-09
> **brawnypandora0 said:**
> What! So whether it works on any particular computer depends upon pure chance with relation to the motherboards? What incompetence!

Not in my experience. However, if your card goes back to 2003 then chances are Nvidia may not be keeping up the support. I have a 2003 machine which I have installed Ubuntu 10.10, but the Nvidia96 driver was not delivered by Nvidia til a few months later so I ended up downgrading xorg to the 10.04 version and for it the nvidia96 driver did work.

It is not recommended to install driver from the Nvidia site because it is not patched for Ubuntu and also you have to reinstall the driver everytime you upgrade your kernel. You should use Additional Drivers to install it and use something like the x-swat ppa to upgrade it (though I think you should just stick with whatever works as your card is really old)

---

