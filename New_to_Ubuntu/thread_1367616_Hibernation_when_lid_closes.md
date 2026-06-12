---
title: "Hibernation when lid closes"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by vanhornd on 2009-12-29
Hi Ubuntu Community,

I have my Ubuntu server running on an old Dell laptop.  Apache, MySQL stuff.  How do I prevent the machine from hibernating when I shut the lid?

Thanks!   Doug

---

### Post by nerdy_kid on 2009-12-29
right click battery icon click preferences and go from there

---

### Post by Magnesium on 2009-12-29
> **nerdy_kid said:**
> right click battery icon click preferences and go from there

If he is running pure Ubuntu server, he won't have Gnome to do that. Doug, what you could do is, in the terminal, run
```
sudo mv /etc/acpi/lid.sh /etc/acpi/lid.sh.old
```
and then
```
sudo touch /etc/acpi/lid.sh
```
That should do it for you.:)

Mg

---

