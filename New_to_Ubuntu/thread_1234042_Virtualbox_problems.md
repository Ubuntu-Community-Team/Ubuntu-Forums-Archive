---
title: "Virtualbox problems"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by tdr2009 on 2009-08-07
when i start ubuntu from virtualbox and when it gets to logon screen its really small.does any one know what is wrong?
One shows it booting then the other one shows the login screens

---

### Post by HappyFeet on 2009-08-07
Install guest additions. After you start ubuntu and get to the desktop, go to the Vbox window (the window that opens when you start vbox) and go to Machine>Install Guest Additions. After it installs, reboot ubuntu, and do Ctrl-F to get true full screen mode. Plus, with guest additions, you can move the mouse freely between guest and host without having to capture it.

---

### Post by SecretCode on 2009-08-07
The problem with the login screen being all bunched up in a thin line at the top is a known issue. 
Do you have 3D acceleration enabled? Try disabling it.
Do you have more than 64MB of video memory set in the VM? Try reducing to 64MB or less (with or without 3D acceleration).

If neither of those help you're best off going to [http://forums.virtualbox.org](http://forums.virtualbox.org)

---

### Post by tdr2009 on 2009-08-07
None of those solutions worked and i already have guest additions installed. ill try virtualbox forums now.

---

### Post by tdr2009 on 2009-08-07
> **SecretCode said:**
> The problem with the login screen being all bunched up in a thin line at the top is a known issue. 
Do you have 3D acceleration enabled? Try disabling it.
Do you have more than 64MB of video memory set in the VM? Try reducing to 64MB or less (with or without 3D acceleration).

If neither of those help you're best off going to [http://forums.virtualbox.org](http://forums.virtualbox.org)
i fixed by making the video memory go to around 20-30mb and it works now

---

### Post by Jose Catre-Vandis on 2009-08-07
So thanks to Secret Code for the solution

---

