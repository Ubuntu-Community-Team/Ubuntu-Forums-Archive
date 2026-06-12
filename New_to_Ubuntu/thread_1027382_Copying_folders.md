---
title: "Copying folders"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2009-01-01
I want to copy /home/tim/Documents/Thunderbird Backup/lpg8fh0p.default into /etc/thunderbird/profile but I get this error message
```

Error while moving "lpg8fh0p.default".
There was an error moving the file into /etc/thunderbird/profile.
Error moving file: Permission denied
```

Help! Thanks

---

### Post by mikewhatever on 2009-01-01
Are you using sudo to write to /etc?

---

### Post by TRANQU111TY on 2009-01-01
> **mikewhatever said:**
> Are you using sudo to write to /etc?

I'm using the GUI. Sorry I'm not experienced enough with the terminal but if you could teach me what to put in there it would be great!

---

### Post by steeleyuk on 2009-01-01
Applications > Accessories > Terminal

Enter:

*sudo cp -r "/home/tim/Documents/Thunderbird Backup/lpg8fh0p.default" /etc/thunderbird/profile*
This will copy the folder, leaving the original where it is.

If you want to move the folder, deleting the original:
*sudo mv "/home/tim/Documents/Thunderbird Backup/lpg8fh0p.default" /etc/thunderbird/profile*

Alternatively, if you want to do it graphically, press Alt+F2 and type: *gksu nautilus*

This opens the file browser as root. Be careful though.

---

### Post by mikewhatever on 2009-01-01
Sure, alt+f2, type is **gksudo nautilus** and copy whatever you like.

---

