---
title: "how to remove skype installed with wine"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by bipinbaglung on 2009-01-24
I have installed skype with the help of wine 1.0.1. Now i want to uninstal it but there in not uninstal option. I uninstall wine but it get remained. Now how can i uninstall skype

---

### Post by gandaran on 2009-01-24
go to your /home/'user'/.wine folder and delete the skype files or just delete the whole .wine folder, run configure wine again to get a new .wine folder.
go to /home/'user'/.local also to delete skype from the applications menu
or use system » preferences » main menu.

---

### Post by snowbalance on 2009-01-24
I'm unsure if you can uninstall programs you've installed via WINE the same way as ones installed otherwise, but have you tried:
```
sudo dpkg -r skype
```
I don't use WINE, so I'm sorry if that doesn't work :(

---

### Post by carml on 2009-01-24
I don't know if it works for Skype,but generally you can go in Applications->Wine->Uninstall wine software.This conduct you to a windows similare to "Uninstall Software" under MS Windows, there then select the software you want to uninstall and you've done.;)

---

### Post by daniel014 on 2009-01-24
Skype is available for Linux as a native program.

[http://www.skype.com/intl/en-gb/download/skype/linux/](http://www.skype.com/intl/en-gb/download/skype/linux/)

---

### Post by bipinbaglung on 2009-01-26
Thank You GANDARAN. Your suggestions help me.

---

### Post by bipinbaglung on 2009-01-27
How can i configure wine again?

---

### Post by gandaran on 2009-02-01
> **bipinbaglung said:**
> How can i configure wine again?
applications > wine > configure wine

---

### Post by halovivek on 2009-02-02
> **bipinbaglung said:**
> I have installed skype with the help of wine 1.0.1. Now i want to uninstal it but there in not uninstal option. I uninstall wine but it get remained. Now how can i uninstall skype
Whether the skype worked fine in wine? need to know planning to install. I have installed skype in ubuntu but still sound problem exists that why i am asking.

---

