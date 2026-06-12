---
title: "Problems accessing gimp"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Ron Roy on 2011-01-03
Hi,
Earlier today I downloaded brushes for gimp and sudo chmod 700 /usr/share/gimp
and now get... "There was an error parsing the menu definition from image-menu.xml: Failed to open file '/usr/share/gimp/2.0/menus/image-menu.xml': Permission denied"
How does one reverse this command?
Thanks for your help,
Ron

---

### Post by Vaphell on 2011-01-03
owner of the /usr/share/gimp is root and you granted it full rights but none for everybody else
my guess is that this dir needs 755 (every dir in /usr/share is 755 = rwxr-xr-x)
```
sudo chmod 755 /usr/share/gimp
```

---

