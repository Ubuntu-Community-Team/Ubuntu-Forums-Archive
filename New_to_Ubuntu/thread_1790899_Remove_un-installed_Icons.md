---
title: "Remove un-installed Icons"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2011-06-25
I'm running Ubuntu 11.04 x64 I've install program and then removed it but when I go into 'Application' the icon is still in there. But when I click it nothing happens. How do I remove the icon?

---

### Post by inameiname on 2011-06-25
First step I suggest is to restart your computer and see if that refreshed things. I've noticed that solved the issue with me several times whenever I remove something.

If that doesn't fix it, simply open the Main Menu -> System -> Preferences -> Main Menu and find the icon that wasn't removed, and delete it. Its merely a shortcut, so no harm to anything else will come from doing it this way.

---

### Post by bdentremont on 2011-06-26
> **inameiname said:**
> ... I suggest is to restart your computer and see if that refreshed things... 

If this works, I suspect that logging out and back in (i.e. restarting X and Gnome) would have the same effect.

---

### Post by Ezlivin on 2011-06-26
I don't currently have anything I want removed to test this with

```
sudo apt-get --purge remove <packagename>
```

This removes the configuration files as well as packages and might eliminate the need to reboot / restart X. Both options are clearly sound advice though.

---

### Post by beew on 2011-06-26
> **Ezlivin said:**
> I don't currently have anything I want removed to test this with

```
sudo apt-get --purge remove <packagename>
```This removes the configuration files as well as packages and might eliminate the need to reboot / restart X. Both options are clearly sound advice though.

This is way too much. As inameinaname said just ucheck/delete the entry in the Main Menu will do.

---

