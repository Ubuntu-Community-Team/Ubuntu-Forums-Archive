---
title: "Unintalled Unity now cant see anything? Also keyring password wrong???"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by Suitsuke on 2011-08-20
So I installed ubuntu on my old laptop.

Uninstalled Unity via Software manager because I think it's basically the worst thing ever created.

Now I cant see anything. Just my desktop wallpaper like it's a picture and nothing more. No menus no nothing.

I can right click and make new folders etc. but that's it.

The only way I can turn the laptop off is with a 'CTRL-ALT-DEL' :/

How do I get the old Gnome desktop back?

Also when I log in, it tells me to input my keyring password. I've never had any problems entering it before but now it's always like *'invalid'.*

Why did all of this suddenly stop working? I thought uninstalling Unity just removed the annoying sidebar etc.

---

### Post by sanderd17 on 2011-08-20
At login time (where you have to fill in your password), can you select gnome-classic?

---

### Post by Suitsuke on 2011-08-20
I cant select anything. I get asked a password for my wireless which I cant put in. So I have to put the key for my wireless in all over again. After that, I get my desktop and nothing.

---

### Post by sanderd17 on 2011-08-20
Did you perhaps activate automated login?

you can reinstall unity with the terminal:

CTRL+ALT+T or CTRL+ALT+F1

```

sudo apt-get install unity

```

Then you will have a normal interface again, and be sure to disable automatic login before you try removing unity again.

---

### Post by Suitsuke on 2011-08-20
Is there any way I can remove the need for passwords altogether? I really don't need them.

Ok I'll try that and see what happens but I really want my default Gnome desktop back and no Unity.

Thanks for the help.

---

