---
title: "How to make a theme effective for all users?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by exziton on 2009-01-17
Hello!

I have to configure some Ubuntu 8.10 computers which will be used by a large number of users (>100). For several reasons I would like to have the same theme for all users. Is there any way to make the theme configuration under my account the standard theme for all other users (including users which may be added in the future)?

Thank you very much!

---

### Post by binbash on 2009-01-18
you can link all users .theme file (icon fonts also) to your user's (theme icon fonts).

---

### Post by exziton on 2009-01-18
Thank you for the answer, but that is not what I need. The themes, icons and fonts are already available for all users (they are in the /usr/share/... folders). What I am looking for is a possibility to apply a theme with its icons and fonts and all the configurations I made (dock, ...) to all users, so that their desktop will look exactly the same like mine. I would know how to do this manually, but as there will be more than 100 users on the system, I am looking for a possibility to do this automatically.

---

### Post by cmay on 2009-01-20
> **exziton said:**
> Thank you for the answer, but that is not what I need. The themes, icons and fonts are already available for all users (they are in the /usr/share/... folders). What I am looking for is a possibility to apply a theme with its icons and fonts and all the configurations I made (dock, ...) to all users, so that their desktop will look exactly the same like mine. I would know how to do this manually, but as there will be more than 100 users on the system, I am looking for a possibility to do this automatically.
i was fetching some packages for my debian lenny install last night. i saw a package called user-settings in synaptic. that was sounding as what you need from the description. the program should be able to set the user wall papers and generel settings from one account. i have not tried it and i am not sure if it works or if it is in the ubuntu respotires. as said i am working on debian lenny right now. i have a jaunty jackalop install also but i did not check in synaptic there yet. the respotories from there would also be updated as intrepid or hardy. i hope it could help somehow. good luck .

---

### Post by exziton on 2009-01-29
... could not find any package named user-settings

---

### Post by 3rdalbum on 2009-01-29
Pessulus can set mandatory settings in gconf for a subset of users. I expect this should do almost everything you want. Incidentally, you can put the invisible settings files from your home directory (do "Show Hidden Files" in Nautilus to see them) into /etc/skel and they will be copied automatically to any new user accounts that get created.

---

### Post by exziton on 2009-01-29
Thank you so much, that is exactly what I needed!

---

