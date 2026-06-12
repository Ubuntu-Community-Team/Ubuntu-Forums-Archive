---
title: "No Panel bar"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-11-07
Hello,

sometimes when I boot my computer the panel bar (the one, that is in the top of the screen) just does not appear. If the panel bar is there, the clock in the corner of the screen is just grey adn does not work. I think the problem occured first after installing the input method SCIM. Do you know, how to solve the problem?

---

### Post by P4man on 2010-11-07
Try pressing control+alt+F1. Do you get a full screen terminal? If so, log in and then try these commands:

```
sudo service gdm stop
```
(this stops the GUI)

```
sudo mv /etc/**X**11/xorg.conf /etc/**X**11/xorg.backup
```
this renames your X configuration file to a backup. Please note the UPPERCASE X's

```
sudo service gdm start
```

With some luck that helps, though you may encounter a dialogue about safe graphics depending what videocard and drivers you have.

---

