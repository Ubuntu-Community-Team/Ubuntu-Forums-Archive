---
title: "Single click to open folders?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by jozmoz on 2009-04-19
hello,

Is there a way to set the cursor to open folders etc with a single click, like in windows folder options?

thanks for any help.

---

### Post by LiamWilson on 2009-04-19
Open your home folder, and click on 
Edit > Preferences

On the Behaviour Tab, click on "Single Click to open Items"

That's for ubuntu, I'm not sure about Xubuntu, but it may help.

---

### Post by theozzlives on 2009-04-19
Start gconf-editor go to apps>nautilus>preferences>change click_policy from double to single

---

### Post by jozmoz on 2009-04-19
I tried changing it to single click in home, edit, preferences, but it did not do anything? Do I need to do a system restart?


for the second suggestion, where is the gconf-editor found?

---

### Post by jozmoz on 2009-04-19
Could someone let me know where the gconf-editor is to be found?

thanks

---

### Post by gandaran on 2009-04-19
> **jozmoz said:**
> Could someone let me know where the gconf-editor is to be found?

thanks
system » preferences » main menu » system tools, enable gconf-editor
now you can find it in applications » system tools

edit: I don't know if this works for xubuntu!

---

### Post by Berserker v7 on 2009-04-19
> **jozmoz said:**
> Could someone let me know where the gconf-editor is to be found?

Enter gconf-editor in a terminal or press ALT-F2 and enter it there.

---

### Post by halitech on 2009-04-19
I don't think gconf-editor works in Xubuntu

if its the same in Debian then it should be Menu - Settings - Settings manager

in there you will see File Manager Preferences. Click that and select Behaviour. IN there is an option to use Single click to activate items.

---

