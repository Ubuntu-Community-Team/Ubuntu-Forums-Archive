---
title: "Google Chrome, reove from favorites and default"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Iknownothing on 2010-06-25
How do I remove Google Chrome from default and remove the same from favorites?  I think Firefox is better,

---

### Post by Rubi1200 on 2010-06-25
If you want to completely uninstall it?

Applications > Accessories > Terminal

```
sudo apt-get purge <appname>
```

---

### Post by kerry_s on 2010-06-25
> **Iknownothing said:**
> How do I remove Google Chrome from default and remove the same from favorites?  I think Firefox is better,

system-> preferences-> preferred applications

right click on the icon in favorites-> remove

---

### Post by Iknownothing on 2010-06-25
I have reset default but there is no favorites in preferred applications, still can not remove from PC

---

### Post by kerry_s on 2010-06-25
> **Iknownothing said:**
> I have reset default but there is no favorites in preferred applications, still can not remove from PC

what? i'd do pics but i have already removed the netbook-launcher.

preferred applications is to set you default browser, which you should have set to chrome.

theres only 1 option in favorites right click & that is remove.
to add to favorites you right click the launcher:
internet-> right click google chrome-> add

you can also drag & drop things on the go-home-applet(ubuntu logo) to add to favorites.

if you want to uninstall things use synaptic:
system-> administration section-> synaptic package manager

---

### Post by Iknownothing on 2010-06-26
Resolved, thank you





> **kerry_s said:**
> what? i'd do pics but i have already removed the netbook-launcher.

preferred applications is to set you default browser, which you should have set to chrome.

theres only 1 option in favorites right click & that is remove.
to add to favorites you right click the launcher:
internet-> right click google chrome-> add

you can also drag & drop things on the go-home-applet(ubuntu logo) to add to favorites.

if you want to uninstall things use synaptic:
system-> administration section-> synaptic package manager

---

