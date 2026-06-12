---
title: "change display manager"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by tdeherdt on 2008-12-27
Hey! I'm new here!

I've a little question, how do I change my display manager?

---

### Post by RomeReactor on 2008-12-27
Hi. Can you please explain what you mean? What is it exactly that you want to do?

---

### Post by tdeherdt on 2008-12-27
I've changed my display manager from gdm to kdm by accident and I don't know how I can change it back...:P

---

### Post by RomeReactor on 2008-12-27
Go to 'System->Administration->Services' and make sure **gdm** is checked (enabled). Then run this from the terminal:
```
sudo dpkg-reconfigure gdm
```
press ENTER when the 'OK' button appears in the terminal, and select gdm. Then restart Ubuntu; or log out, then press CTRL+ALT+F1 to switch to a console, and run these commands:
```
sudo /etc/init.d/kdm stop && sudo /etc/init.d/gdm start
```
If you're then not automatically returned to your login window, press CTRL+ALT+F7.

---

