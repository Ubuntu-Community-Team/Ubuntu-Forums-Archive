---
title: "Dropbox issue permission denied"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by patchido on 2011-08-14
I've got my dropbox folder inside a partition called DATA wich is always mounted at boot time, i did this via storage device manager, and recently my dropbox isnt syncing, it gives me an "cannot sync presmission denied"
so i wanted to try and manually insert the files downloading them from the site, and when i get them to that folder i get this 

```
fchmod (file attributes) error: Operation not permitted
 (warning) cannot set modif./access times
          Operation not permittedfchmod (file attributes) error: Operation not permitted
 (warning) cannot set modif./access times
          Operation not permittedfchmod (file attributes) error: Operation not permitted
 (warning) cannot set modif./access times
          Operation not permittedcaution: filename not matched:  Hunter/Planeaciones de cargos Ago\-Dic/Planeaci\?\?n de Cargos pancho2011.docx

```

thanks

btw, the folder is shared

---

### Post by LowSky on 2011-08-15
Check the folder permissions, maybe they were accidentally changed. If you turn off dropbox can you access the folder, if yes, it could possibly be a issue with file space or maybe even your connection, try re-adding your pc to your dropbox account

---

