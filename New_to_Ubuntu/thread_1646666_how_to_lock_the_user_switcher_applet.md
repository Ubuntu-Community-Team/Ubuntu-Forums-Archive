---
title: "how to lock the user switcher applet"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-16
how do i make the user switch applet always ask for a password when switching users/tks

---

### Post by owiknowi on 2010-12-16
my guess (sorry) would be:
go to system/administration/users and groups.
here you can set per user (group?) that a password is always required by emptying the check box when clicking on password next to the user name.

an other option can be found in the 'configuration editor' (search for users).
if you check 'showall' they have to give a password when trying to log in.

there is also a setting that says something like 'never allow login without password'. will look for you if i can find it.

---

### Post by yetiman64 on 2010-12-16
> **rburkartjo said:**
> how do i make the user switch applet always ask for a password when switching users/tks

On using the applet, when the new login screen is encountered a password will be required for normal account logins (with the exception of the guest account). 

If you wish to limit the use of the switcher applet in ```
gconf-editor 
```, check out the settings, desktop > gnome > lockdown, "disable user switching" and maybe "disable lockscreen" as well.

Hopefully this may be of some use to you, in preventing the switchers use, if that is what is intended.

I'm not actually aware of a means of setting a password on the switcher itself sorry.

---

### Post by rburkartjo on 2010-12-16
yet tks that is what i was looking for i just had to uncheck the disable lock screen

---

