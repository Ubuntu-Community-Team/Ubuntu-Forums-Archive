---
title: "How to have transparent menu?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Alfx on 2009-01-15
You know like see-through menus and stuff like that.

I found this:
[I]
in ccsm - general options - opacity

(name=gnome-panel | type=Menu | PopupMenu | DropdownMenu)

and transparency = 80

in ccsm - blur - alpha blur windows

(name=gnome-panel | name=usp | type=Menu | PopupMenu | DropdownMenu)

blur = gaussian
alpha blur = true (checked)[/I]

When I try it, my menu does become see-through, except that its very faint so its near unreadable.

How do I fix this?
How do I get awesome see-through menus?

Thanks

---

### Post by Sealbhach on 2009-01-15
Hi, try changing the value of 80 down and up. Experiment till you get the right look.



.

---

### Post by Alfx on 2009-01-15
> **Sealbhach said:**
> Hi, try changing the value of 80 down and up. Experiment till you get the right look.



.

I tried messing the "Windows value" Between 0 and 100.

But by the time its actually transparent enough, its barely even readable anymore :(

---

### Post by elitenoobboy on 2009-01-21
I know that there is a way to get the taskbar to be transparent without decreasing the opacity of the text or icons (even though it's not "real" transparency or done with compiz; it's just allows you to see the wallpaper only), but I know of no way to do anything like that with the menus, whether the transparency is real or not. I'd like to see the opacity plugin updated so that it can make just the background of a menu window transparent. I don't think it can currently do anything like that.

---

### Post by neo_1in on 2009-01-21
I followed instructions from...
[http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074)
works fine for me.

---

### Post by mcduck on 2009-01-22
> **elitenoobboy said:**
> I know that there is a way to get the taskbar to be transparent without decreasing the opacity of the text or icons (even though it's not "real" transparency or done with compiz; it's just allows you to see the wallpaper only), but I know of no way to do anything like that with the menus, whether the transparency is real or not. I'd like to see the opacity plugin updated so that it can make just the background of a menu window transparent. I don't think it can currently do anything like that.

It's pretty much impossible for Compiz to do that, the support for transparency has to be added to the program you want to use real (selective) transparency, Gnome's menu, in this case..).

If the program inn question doesn't make any difference between text and background and tell which one should be transparent and which one not, Compiz can't do anything else than make everything equally transparent or opaque.

---

### Post by elitenoobboy on 2009-01-22
> **mcduck said:**
> It's pretty much impossible for Compiz to do that, the support for transparency has to be added to the program you want to use real (selective) transparency, Gnome's menu, in this case..).

If the program inn question doesn't make any difference between text and background and tell which one should be transparent and which one not, Compiz can't do anything else than make everything equally transparent or opaque.

I think it is very much possible. You just have to tell compiz to only make transparent a certain color of a window type, in this case the gray/whiteness of the menu. The only problem with that is that is that certain icons that match the color of the menu background will go transparent as well; it's also a retarded way of working around the menu's lack of built in transparency, but still very possible none-the-less.

---

