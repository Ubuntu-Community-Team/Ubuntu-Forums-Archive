---
title: "[SOLVED] I have killed my laptop !  Wrong video driver."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Robster2 on 2008-12-28
I am using Ubuntu 8.10  64K version on my Toshiba satellite L300D

Under  System>Administration> Hardware drivers

I found a hardware video driver had been downloaded for my system but had not been activated.

I activated it and now  ubuntu will not start.

In recovery mode it tries to start gnome but fails and gives me a console.

How do get rid of the driver from the console?

---

### Post by hermes0710 on 2008-12-28
> **Robster2 said:**
> I am using Ubuntu 8.10  64K version on my Toshiba satellite L300D

Under  System>Administration> Hardware drivers

I found a hardware video driver had been downloaded for my system but had not been activated.

I activated it and now  ubuntu will not start.

In recovery mode it tries to start gnome but fails and gives me a console.

How do get rid of the driver from the console?

I think you can edit as root the /etc/X11/xorg.conf and in the section that defines the g.card revert nvidia to nv in order to use the shipped in driver.Then you will be able to start in graphic to mode but with no 3d effects but at list you'll be able to search through firefox how to solve it :)

---

### Post by Michael.Godawski on 2008-12-28
hi, 

would be good to know what your graphic card is?

Is it a ATI Radeon Xpress X1270 or another Ati card?

You can try to run these in recovery mode:

```
dpkg-reconfigure xserver-xorg -phigh
```
```
/etc/init.d/gdm restart
```

---

### Post by Robster2 on 2008-12-28
Thanks for all the replies

I now know where to find the settings for the setup in xorg.conf


but this worked a treat !! :P

```
dpkg-reconfigure xserver-xorg -phigh
```
```
/etc/init.d/gdm restart
```[/QUOTE]

I would like to find out what graphics card I have.  I will look for the information.

---

### Post by halw on 2008-12-28
Type the following in a terminal and look for a line the has 'Display controller' in it. That will tell what GPU you have.

```
lspci
```

---

