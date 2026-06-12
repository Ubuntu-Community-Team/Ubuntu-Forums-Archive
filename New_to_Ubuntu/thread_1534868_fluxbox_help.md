---
title: "fluxbox help"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by lolzwut on 2010-07-20
I was just thinking, how do I reset my gtk theme? I installed gtk-chtheme and put some theme on there. I just installed an online style and the color is not changing on Thunar and other things like that. It's staying with the same gtk although my menu and stuff has changed, how can I reset it?

---

### Post by lolzwut on 2010-07-20
bump..

---

### Post by lolzwut on 2010-07-21
help me please

---

### Post by rtlustyo on 2010-07-21
In fluxbox you should just be able to right click on the screen and change it from a sub-menu, no?

---

### Post by lolzwut on 2010-07-22
> **rtlustyo said:**
> In fluxbox you should just be able to right click on the screen and change it from a sub-menu, no?


I am able to change the style but that isn't the problem. The theme works fine but the gtk theme I put on earlier is stopping the color on certain windows from being changed. I'll post a screenshot if you need me to.

---

### Post by urukrama on 2010-07-22
> **lolzwut said:**
> I was just thinking, how do I reset my gtk theme? I installed gtk-chtheme and put some theme on there. I just installed an online style and the color is not changing on Thunar and other things like that. It's staying with the same gtk although my menu and stuff has changed, how can I reset it?

I am not exactly sure what your problem is. Do you have conflicting themes (ie., two themes that are somehow displayed together)? How do you normally set your Gtk theme?

Have a look at your /home/username/.gtkrc-2.0 file. Gtk-chtheme (and other such applications like LXAppearance) write the theme name in that file. If you delete any info in that file, you will have to restart your Gtk applications for the changes to take effect.

The Openbox guide linked to in my signature contains a substantial section on Gtk themeing in Openbox. All of that will apply to Fluxbox as well. You might find it helpful.

---

