---
title: "Update manager error"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by trevc on 2009-09-29
When I use Update manager or Synaptic I get  an error message 
E: dpkg was inter--configure-arupted, you must manually run sudo dpkg--configure-a
 to correct this problem.
I have typed into terminal   sudo dpkg--configure-a  with and without the dashes  and it comes back with 
command not found.

How can I fix this without having to reinstall everthing please

---

### Post by howefield on 2009-09-29
Try, (note the spaces)

```
sudo dpkg --configure -a
```

---

### Post by trevc on 2009-09-29
When I use Update manager I get this error
E:dpkg was interrupted, you must manually run sudo dpkg--configure-a  to correct this problem

I typed this into Terminal but it comes back with command not found . How can I get Update manager to work again please

---

### Post by Michael.Godawski on 2009-09-29
```
sudo dpkg --configure -a
```Spaces are important in linux. ;)

Edit:

Please do not start many threads on the same subject in different subcategories of the forum. I have merged your other thread with this one.

---

### Post by howefield on 2009-09-29
Try the answer in your other thread...

```
sudo dpkg --configure -a
```

---

