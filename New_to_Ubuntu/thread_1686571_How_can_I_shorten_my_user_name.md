---
title: "How can I shorten my user name?"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Daanii on 2011-02-12
Using the terminal, my command line always begins "edward@edward-Presario-V6700-Notebook-PC:"   So I guess that is my user name. How can I change that to simply "edward"

Thank you.

---

### Post by sffvba[e0rt on 2011-02-12
> **Daanii said:**
> Using the terminal, my command line always begins "edward@edward-Presario-V6700-Notebook-PC:"   So I guess that is my user name. How can I change that to simply "edward"

Thank you.

The part after the @ is actually your systems name... and I am not sure myself how to change that :)



404

---

### Post by kn0w-b1nary on 2011-02-12
> **Daanii said:**
> Using the terminal, my command line always begins "edward@edward-Presario-V6700-Notebook-PC:"   So I guess that is my user name. How can I change that to simply "edward"

Thank you.

in edward@edward-Presario-V6700-Notebook-PC, before the "@" is your username, and after is the name of the computer (hostname). I know you can change it with Ubuntu Tweak.
[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb)

Hope this Helps!

---

### Post by Hippytaff on 2011-02-12
try doing
```

sudo nano /etc/hostname

```then change the name on this file, save it. It won't take effect until you reboot :-)

---

### Post by sffvba[e0rt on 2011-02-12
Also found this link [http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/) which might do the trick :) *edit: and seeing the post above mine this link will do the trick :D*


404

---

### Post by Daanii on 2011-02-12
Thanks all. I did use the sudo nano /etc/hostname command to change my system name to PC. Then rebooted. Looks a lot better now, edward@PC:

---

### Post by Hippytaff on 2011-02-12
Glad you sorted it ;-)

---

