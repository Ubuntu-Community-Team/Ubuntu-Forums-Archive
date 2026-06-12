---
title: "An important button has vanished"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-09-10
Hello
Im using jaunty jackalope.The button for sutdown,logout,hibernate... located on the top right corner has vanished. How can I get it?

---

### Post by wobin77 on 2009-09-10
Please verify this:
go to Menu: System -> Administration -> Login Window
 In the first tab "Local" of "Login Window Preferences", check if "Menu Bar:
Show Actions menu" is selected.
If no, check it and close the form.

---

### Post by talsemgeest on 2009-09-10
> **nayeem007 said:**
> Hello
Im using jaunty jackalope.The button for sutdown,logout,hibernate... located on the top right corner has vanished. How can I get it?
Right-click on the panel, click on "Add to Panel", then scroll down to the "Shut down" applet. Select it, then click "Add."

---

### Post by nayeem007 on 2009-09-10
it says that my gdm is stop. How can i turn it on

---

### Post by talsemgeest on 2009-09-10
> **nayeem007 said:**
> it says that my gdm is stop. How can i turn it on
Ouch, if GDM is stopped, there is probably something very wrong. Try switching to a console by pressing ctrl+alt+F1, logging in, then typing ```
sudo /etc/init.d/gdm start
```. Try switching back to the GUI by pressing ctrl+alt+F7, then try the original instructions again.

---

