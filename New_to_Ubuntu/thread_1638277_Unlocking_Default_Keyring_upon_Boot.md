---
title: "Unlocking Default Keyring upon Boot"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-05
Hi,

Can anyone tell me how to unlock the default keyring upon boot without having to type in my password? Currently it asks for my password, which is frustrating. 

I think it's started since I began using Ubuntu One.

Many thanks in advance

Chriss

---

### Post by lindsay7 on 2010-12-05
look under system/administration/users and groups

set the system for no password

---

### Post by Chrissd on 2010-12-05
Sorry, don't see anything of that nature in the groups...?

---

### Post by Penguin=) on 2010-12-05
Neither do i

---

### Post by lindsay7 on 2010-12-05
Do you have this menu?

[ATTACH]177506[/ATTACH]

look for change password and require password on longin

---

### Post by Penguin=) on 2010-12-05
> **lindsay7 said:**
> Do you have this menu?

[ATTACH]177506[/ATTACH]

look for change password and require password on longin


Yeh thats the menu i  have =)

---

### Post by Chrissd on 2010-12-05
Changed my user to require no password upon login, rebooted and it still asks for my password to unlock the default keyring. :(

---

### Post by Penguin=) on 2010-12-05
> **Chrissd said:**
> Changed my user to require no password upon login, rebooted and it still asks for my password to unlock the default keyring. :(


Yeah, same.

---

### Post by lindsay7 on 2010-12-05
Ok, go to systems/preferencess and then to passwords and encryptions. and open it. right click on the passwords folder you see in the box then enter your password.  Do NOT enter a new password.  LEAVE it blank and leave the confirmation blank, Save and exit.  This should take care of it.

---

### Post by Chrissd on 2010-12-05
Attached is a screenshot of my system menu and my settings menu.

Am running Xubuntu rather than Ubuntu, for what it's worth.

---

### Post by lindsay7 on 2010-12-05
Ok, you have that menu somewhere it was changed to where it is now on new versions of ubuntu it used to be under applicantion.  Can you right click on your applications menu and go to edit menus. you should be able to find it in there somewhere.

---

### Post by Old_Grey_Wolf on 2010-12-05
> **lindsay7 said:**
> Ok, you have that menu somewhere it was changed to where it is now on new versions of ubuntu it used to be under applicantion.  Can you right click on your applications menu and go to edit menus. you should be able to find it in there somewhere.

He wound need to install seahorse to get that menu, I think.

```
sudo apt-get install seahorse
```

---

### Post by Chrissd on 2010-12-05
Found it, kind of.

I had to install it from the Ubuntu Software Centre first.

Thank you very much. Do you know of anywhere I can read up to fully understand the security implications of this? I could see from the application it was just Ubuntu One that was using it.

---

### Post by Old_Grey_Wolf on 2010-12-05
> **Chrissd said:**
> ...Do you know of anywhere I can read up to fully understand the security implications of this? I could see from the application it was just Ubuntu One that was using it.

You could start reading here [http://live.gnome.org/GnomeKeyring](http://live.gnome.org/GnomeKeyring) and here [http://live.gnome.org/GnomeKeyring/SecurityFAQ](http://live.gnome.org/GnomeKeyring/SecurityFAQ).

---

