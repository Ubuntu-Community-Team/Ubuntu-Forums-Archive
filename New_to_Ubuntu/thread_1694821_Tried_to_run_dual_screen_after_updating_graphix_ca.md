---
title: "Tried to run dual screen after updating graphix card..."
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bandhippie on 2011-02-24
Running Ubuntu 10.10. I am using a GeForce 7950 GT, I updated the driver fine.
 
When I tried to change the monitors to run as a dual screen the program told me I needed to reboot my x server, I tried doing that only to find out that I apparently turned off my ubuntu gui instead.  Now I can't get it to turn back on.  
 
I have searched the forums and tried init 2, telinit 5, startx, and ****** gnu restart (I can't remember what ****** was).  So Hopefully I can get some help here.
 
Thank you for any helpfull information and if I need to add anything I will

---

### Post by jwcalla on 2011-02-24
If you can't get X to come up you could check /var/log/Xorg.0.log for any errors, which should be indicated with (EE).

---

### Post by seawolf167 on 2011-02-25
Try

```
sudo /etc/init.d/gdm restart
```or 

```
sudo service gdm restart
```does the same thing

---

