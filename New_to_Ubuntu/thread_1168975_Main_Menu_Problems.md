---
title: "Main Menu Problems"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Turtleman on 2009-05-24
Ok guys, basically what I wanted to know is that if there is a better way of managing my Main Menu than the default Main Menu editor that comes with Ubuntu, because it's very weird and it has some odd glitches. So, is it possible?

---

### Post by billgoldberg on 2009-05-24
> **Turtleman said:**
> Ok guys, basically what I wanted to know is that if there is a better way of managing my Main Menu than the default Main Menu editor that comes with Ubuntu, because it's very weird and it has some odd glitches. So, is it possible?

You mean alacarte?

It shouldn't be buggy.

There are no other ways (maybe manually, but have no idea how) I can think of.

There are off course other menu's available.

---

### Post by Turtleman on 2009-05-24
Other menus available? What do you mean?

---

### Post by Sarai the Geek on 2009-05-24
You can install different kinds of menus that display the same information different ways. For example, MintMenu, which I use:

[IMG]http://farm4.static.flickr.com/3586/3560211917_04d19d8561_o.png[/IMG]

However, all of the various menus I have tried always still use the same program for menu management that you say is buggy. Perhaps you can describe the problems you are encountering so we can help you fix them?

---

### Post by Turtleman on 2009-05-24
Well, for example, I try to delete some folders and they won't disappear, and I moved some stuff around and I tried to fix it but it's just impossible the program won't allow me. For example, I moved Universal Access inside Other by accident and now it won't come off no matter what. I can't remove menus, only items. It's also very slow. I installed ubuntu very recently and added very few programs, so I don't think I crashed something in the system, because it was already like that since I've installed it. Are you sure there are no alternatives to it?

---

### Post by billgoldberg on 2009-05-24
> **Sarai the Geek said:**
> You can install different kinds of menus that display the same information different ways. For example, MintMenu, which I use:

[IMG]http://farm4.static.flickr.com/3586/3560211917_04d19d8561_o.png[/IMG]

However, all of the various menus I have tried always still use the same program for menu management that you say is buggy. Perhaps you can describe the problems you are encountering so we can help you fix them?

You can for instance install lxpanel and you can tweak the menu as much as you like.

You have total control over it.

[http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel)

---

### Post by Turtleman on 2009-05-24
> **billgoldberg said:**
> You can for instance install lxpanel and you can tweak the menu as much as you like.

You have total control over it.

[http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel)

Thanks, I'll give it a try.

---

### Post by billgoldberg on 2009-05-24
> **Turtleman said:**
> Well, for example, I try to delete some folders and they won't disappear, and I moved some stuff around and I tried to fix it but it's just impossible the program won't allow me. For example, I moved Universal Access inside Other by accident and now it won't come off no matter what. I can't remove menus, only items. It's also very slow. I installed ubuntu very recently and added very few programs, so I don't think I crashed something in the system, because it was already like that since I've installed it. Are you sure there are no alternatives to it?

You can start the app as root, that should allow you to remove menus.

```
gksu alacarte
```

Some changes might only be visible after logging out and back in.

---

### Post by Turtleman on 2009-05-24
> **billgoldberg said:**
> You can start the app as root, that should allow you to remove menus.

```
gksu alacarte
```

Some changes might only be visible after logging out and back in.

I tried logging out and then logging in, and the changes I wanted were made. I didn't do it like root though. Now the program is running fine. Thanks for the help ;-D

---

### Post by billgoldberg on 2009-05-24
> **Turtleman said:**
> I tried logging out and then logging in, and the changes I wanted were made. I didn't do it like root though. Now the program is running fine. Thanks for the help ;-D

No problem.

---

