---
title: "Hibernation with swap file"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by jb_ on 2009-01-06
Hey there

I decided to delete my swap partition and use a swap file instead in Intrepid, little did I know that Linux uses the swap file for hibernation. This being a laptop (also given how long it takes to boot on a 2.5 4200 rpm drive) hibernation is pretty important.

I'd rather not move back to a swap partition, so I'd like to know if there is any reasonably simple way of getting suspend to swap file to work, I hear tuxonice supports this but I've no idea how to make it work.

I would love some help.

---

### Post by ColinPL on 2009-01-06
apt-get install uswsusp

and change
# SLEEP_MODULE="kernel"
to
SLEEP_MODULE="uswsusp"
in /etc/pm/config.d/00sleep_module

---

### Post by jb_ on 2009-01-06
Thanks, I tried that and rebooted but it doesn't work. When I try to use hibernate my screen goes black and I get presented with an unlock password box a few seconds later.

If it makes any difference, there is no hibernate option from the shut down menu. I use kpowersave (gnome-power-manager doesn't work correctly on this machine, something to do with it not supporting brightness control possibly) by right clicking the icon and choosing suspend to disk.

Edit: Can I please have this moved to general help? Absolute beginner was probably not the ideal place to have post it.

---

