---
title: "[SOLVED] Files on Desktop are not visible [Hardy]"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-12-28
All the files on my desktop are NOT visible (i dont know why). I AM ABLE to see all the files in Nautilus. I re-installed Hardy and this problem has started since then - previously everything used to work fine :(

Help!!

---

### Post by jrusso2 on 2008-12-28
1.  What Desktop are you using?

2. Do you have rights to your desktop?

---

### Post by namdung on 2008-12-28
Pls post the output 
```
ls Desktop
```

and a screenshot of ur Desktop.

Edit:
press *Alt+F2*, run *gconf-editor*

In the *Configuration Editor ---->apps--->nautilus-->preferences,* ensure that *show desktop* key is checked.

---

### Post by pirattrev on 2008-12-28
I have a slightly different issue. Whenever I drag a VIDEO (that's key, cus it only happens to them) onto my desktop the file can't be seen. Additionally I then cannot load my desktop in the nautilus browser at all (it hangs on loading).  However, if i do a quick Ctrl-H,Ctrl-H they become visible and the problem is no more. I know this is a little different, but any ideas?

---

### Post by suncoolsu on 2008-12-28
These are the files on my desktop - (can be also seen in nautilus)
> baba@sadist:~$ ls Desktop/
17895-AquaFaTux_1024.png  30670-1.jpg  45704-japanscipt.png


The picture of my desktop is attached- Notice I dont see any of these files

---

### Post by namdung on 2008-12-28
Have u tried the following as described earlier?

press *Alt+F2,* run *gconf-editor*

In the *Configuration Editor ---->apps--->nautilus-->preferences,* ensure that *show desktop* key is checked.

Also select the checkboxes in *apps--->nautilus-->desktop* to view the *Computer, Network & Thrash* icons

Also try creating a folder/file on the Desktop.

Restart GNOME by *Ctrl+Alt+Backspace*

---

### Post by suncoolsu on 2008-12-28
The show desktop icon in Nautilus Preferences was clicked :)

I just checked show icon options and Viola!! after a restart I was able to see everything :D

Notice that killing X didnt change anything 


Thanks a lot for the quick help

---

