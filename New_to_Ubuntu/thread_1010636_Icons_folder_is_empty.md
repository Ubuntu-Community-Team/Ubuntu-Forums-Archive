---
title: "Icons folder is empty"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by WVSteelers28 on 2008-12-14
Hi all,

I was trying to change the 'start-here' icon for my current icon theme set, but now after changing it the icons folder (/usr/share/icons/) is empty.  Nothing shows up in the folder, but everything as far as the icons seem to be fine.

I changed the permissions for the /usr/share/icons folder using 'sudo chmod 766 /usr/share/icons' and then thought I had changed it back to the original using 'sudo chmod 764 /usr/share/icons'.

What did I mess up this time?  Thank you for the help.

WVSteelers28

---

### Post by taurus on 2008-12-14
It should own by root:root and has a permissions of 755.

```
sudo chmod 755 /usr/share/icons
ls -la /usr/share/icons 
```

---

### Post by WVSteelers28 on 2008-12-14
Well, that was simply enough.  I spend 30 minutes searching for a solution and you solve it in 1.  Thank you very much!

WVSteelers28

---

