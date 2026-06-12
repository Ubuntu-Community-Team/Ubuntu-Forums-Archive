---
title: "Commandline Compiz reload"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Efros on 2009-03-20
Anyone know the commandline that should be used to reload compiz. I find that compiz only works satisfactorily with my setup and cairo-dock if I reload it, I would like to have this as one of my startup commands.

---

### Post by taavikko on 2009-03-20
```
compiz --replace &
```

---

### Post by arapa on 2009-03-20
Do you have the fusion-icon loading at start-up? 

If you do, there is a an option to restart compiz from the menu. 

Also make sure the start-up command in Session Preferences says "fusion-icon --no-start" otherwise compiz won't load properly and you'll have to restart it.

---

### Post by fabounet on 2009-03-20
there is also a Compiz applet in Cairo-Dock, maybe it can do the job.

---

