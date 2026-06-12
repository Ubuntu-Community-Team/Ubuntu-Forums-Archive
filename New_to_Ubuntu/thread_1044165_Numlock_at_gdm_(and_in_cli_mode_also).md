---
title: "Numlock at gdm (and in cli mode also)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by billgoldberg on 2009-01-19
This one has bothered me for a while. 

It's not really a problem, but I would still like to see it fixed.

When I enter my password at the gdm, I have to first disable numlock and then enable it again or else it won't accept any numbers.

This happens in Ubuntu Hardy, and Intrepid.

It also happens on my Arch box, which doesn't use the gdm. 

There I just start Gnome from the cli, but even in the cli mode, I still have to disable numlock and then enable it again when typing in my login data.

Sure this procces only takes 1 second, but still does anyone know why this happens?

I'm using a usb keyboard.

(ps, this also happens with a friend of mine running hardy and a usb keyboard)

---

### Post by gettinoriginal on 2009-01-19
I don't know if this will help, but at least check the file:
In Hardy and Gutsy, edit 
```
/etc/gdm/Init/Default
```. 

Find the line

exit 0

Add the following code above that line

      ```
if [ -x /usr/bin/numlockx ]; then
        /usr/bin/numlockx on
      fi
```

---

### Post by billgoldberg on 2009-01-19
Thanks, I'll try it out later today and see if it works.

---

### Post by arqbrulo on 2009-03-11
> **gettinoriginal said:**
> I don't know if this will help, but at least check the file:
In Hardy and Gutsy, edit 
```
/etc/gdm/Init/Default
```. 

Find the line

exit 0

Add the following code above that line

      ```
if [ -x /usr/bin/numlockx ]; then
        /usr/bin/numlockx on
      fi
```

I can't find that file in Intrepid. I had that code added when I was using Gusty, but after installing Intrepid, I just could not find that file to add it again. Can you help? Thanks.

---

