---
title: "lubuntu language switcher"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-06
hello everyone,

just installed Lubuntu on an old Thinkpad T42, and it's working great. 

I have an issue with AbiWord / language switcher: I can't set the language switcher (added to the taskbar) to switch between English and Arabic. In Ubuntu + OpenOffice this is easily done by adding the Arabic layout to the keyboard in Preferences + enabling Arabic in OpenOffice (in Options). 

I tried to play around with Preferences>Language Support (after adding Arabic) but all I seem to get is text in the desktop turning into Arabic when I reboot. I don't need this. All I need is to be able to type in English and/or Arabic on AbiWord at the click of the language switcher. I don't intend to install OpenOffice, as it'd probably slow down Lubuntu. 

Any idea? Thanks.

---

### Post by al.adab on 2010-10-06
as for Arabic, it works after typing this in terminal: 

*setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar*

only I can't get the language switcher on the taskbar work. To switch English from/to Arabic I have to press Alt+Shift

a little step forward :)

---

### Post by al.adab on 2010-10-06
OK - language switcher works. Only had to remove it + re-add it to taskbar. Magic :)

---

### Post by Settler on 2011-04-23
Unfortunately it needs to be re-adjusted when I roboot the system...

Any solution?

---

### Post by ActionParsnip on 2013-01-17
gksudo gedit /etc/default/keyboard

---

### Post by coffeecat on 2013-01-17
@ActionParsnip, the post you are responding to is almost 2 years old and the poster has not logged in for almost as long.

Old thread closed.

---

