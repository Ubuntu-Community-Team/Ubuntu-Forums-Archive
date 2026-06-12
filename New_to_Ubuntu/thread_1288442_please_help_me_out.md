---
title: "please help me out"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by tanu on 2009-10-11
i am new to linux platform...i wanted to add some path to .bash_profile ,if i open it it ll create new one every time....previously i could open the older one only but now its getting created evry time...can someone tell me how to fix it...i wanna open older one only with all previous path set...

---

### Post by bapoumba on 2009-10-11
Moved to ABT.

---

### Post by ArtLaForge on 2009-10-11
Not real sure what your trying to do, try this link:

[http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm)

---

### Post by prshah on 2009-10-11
> **tanu said:**
> i wanted to add some path to .bash_profile

I think you mean ".bashrc"; you can edit this with the command```
gedit ~/.bashrc
```

This command can be entered in the Terminal (Applications-Accessories-Terminal) or in the Alt+F2 command box.

If you want to make the path changes system wide, you will need the edit the /etc/environment file```
gksudo gedit /etc/environment
```

---

