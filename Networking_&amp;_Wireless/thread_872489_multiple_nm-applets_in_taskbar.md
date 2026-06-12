---
title: "multiple nm-applets in taskbar"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by spice_vs on 2008-07-28
Hi,
i have a small trouble with networkmanager. I once found some trouble with nm-applet so i killed it and started another one using 

```
nm-applet
```
It worked fine. But after that i find 2 nm-applets running after every restart. i guess it makes an entry in the autostart applications list. i am not able to configure it. can anyone help me where is this list of autostart apps is. 
my system is Xubuntu 7.10

thanks
spice

---

### Post by caljohnsmith on 2008-07-28
Take a look in your ~/.config/autostart directory, and you'll probably see multiple instances of nm-applet there. Just delete all except one.

---

