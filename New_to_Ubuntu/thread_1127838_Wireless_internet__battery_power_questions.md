---
title: "Wireless internet / battery power questions"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by adobrakic on 2009-04-16
I connect to the internet wirelessly, however when my computer starts up, it asks for a keyring password. Is there a way to disable this, and allow the connection to go through without having to enter the password?

Also, sometimes I run my laptop on battery, and I was wondering if Compiz eats battery usage. I heard of some app that sits in the systray and allows for switching from compiz to metacity by right clicking and going to the desired one. Anyone know what I'm talking about?

---

### Post by jbrown96 on 2009-04-16
compiz does drain your battery a bit, but from what I've seen there really isn't much of a difference. use powertop to measure you power use. Install with ```
sudo apt-get install powertop
``` and use with ```
sudo powertop
``` The options aren't permanent, but they do work.

There's a quick dirty way to fix your keyring problem, but it will delete all your passwords stored in it. You can find the keyring in System--->Preferences(or Admin?). Just delete the keyring, and then re-enter your wireless password and leave the password blank and agree to unsafe storage. It should leave you alone now. There's probably a better way to do this.

---

### Post by adobrakic on 2009-04-17
Props, I'll try it out

---

### Post by freak42 on 2009-04-17
about keyrings: yes you can get it to not prompt you for a password:

possible methods:
1) do not autologin, and have the same password for login and the keyring (secure)

2) or do not set a password in the keyring.
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/) shows you how to remove your keyring (and the stored passwords in the keyring (so make sure you have your passes somewhere else as well) and then create a new password-less keyring. (this is obviously less secure)

hth

---

