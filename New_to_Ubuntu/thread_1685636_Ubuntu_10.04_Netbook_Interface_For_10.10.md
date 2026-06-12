---
title: "Ubuntu 10.04 Netbook Interface For 10.10"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by cbanakis on 2011-02-11
I had 10.04 Netbook Edition installed on my netbook and loved it.
Upgraded to 10.10 Netbook Edition, and love 10.10, but hate the new desktop interface.

I may be the only one, but does anyone know of an easy way to use the old interface on the new OS?

Thanks in advance

---

### Post by kerry_s on 2011-02-11
look in synaptic for "netbook-launcher-efl", then select the 2d version from the session menu & log in

---

### Post by zhogan85 on 2011-02-11
Another option, at the log in screen, after selecting your user name but before logging in, at the bottom of the screen there should be a drop down menu where you can select the old desktop GUI. Then log in and you should be all set.

---

### Post by cbanakis on 2011-02-12
Ah ha!!!

Thank you both, as I ended up having to do a little of both.

A Little Trial An Error, but all is well now.

Had to go into synaptic and install the following...

netbook-launcher-efl
window-picker-applet
go-home-applet

Then under administration/login screen, I changed the default session to 2D

It was pretty self explanatory after I installed netbook-launcher-efl

Because when I tried to login using 2D, it gave me errors saying window-picker and go-home were missing.

Making it pretty obvious that I needed to install them as well :)

Thanks again

Solved

---

