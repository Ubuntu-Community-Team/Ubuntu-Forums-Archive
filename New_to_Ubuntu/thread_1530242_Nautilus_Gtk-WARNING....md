---
title: "Nautilus Gtk-WARNING..."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-07-13
After using the ["Theme Applications Running as Root in Ubuntu"]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/") Tutorial on [Tombuntu]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/")

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```


I get the error below when running most programs from terminal


```
(nautilus:2960): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

(nautilus:2960): Gtk-WARNING **: Unable to locate theme engine in module_path: "crux-engine",
```

although they still run, I was just wondering how I could fix the error

Using Linux Mint 9 x86 (Ubuntu 10.04)

---

### Post by kamitsukai on 2010-07-21
Broken theme, that is all...

---

### Post by mcduck on 2010-07-21
Install the Ubuntulooks and Crux GTK2 engines from the repositories. You are using a theme that uses those engines to draw it's widgets, but the engines themselves aren't installed.

---

### Post by kamitsukai on 2010-07-21
> **mcduck said:**
> Install the Ubuntulooks and Crux GTK2 engines from the repositories. You are using a theme that uses those engines to draw it's widgets, but the engines themselves aren't installed.

Both of those GTK2 engines are available in the packages gtk2-engines and gtk2-engines-murrine in Lucid, both of which are installed. the theme is incompatible with Lucid

---

