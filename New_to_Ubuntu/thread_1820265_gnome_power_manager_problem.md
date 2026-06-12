---
title: "gnome power manager problem ?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by mj360 on 2011-08-07
i'm having a problem, it say gnome power manager at the log screen, can someone help me with this ?

---

### Post by HunterDX77M on 2011-08-07
I am not sure what you are asking. Could you kindly clarify or provide a screen shot?

---

### Post by mj360 on 2011-08-07
this the picture. this what happen when i get to the login screen. it say install problem the configuration defaults for gnome power manager have not been installed correctly. please contact your computer administrator. this what it keep saying when i put my password it, it goes back to the login screen, i can't login in ?

---

### Post by mj360 on 2011-08-07
here the picture

---

### Post by mj360 on 2011-08-07
hello ? any body ?

---

### Post by omelette on 2011-08-07
Have you tried booting in safe-mode?

---

### Post by maxar6 on 2011-08-07
You could try and re installing ubuntu.

---

### Post by mj360 on 2011-08-08
i tried safe-mode but i really don't know what to do in safe-mode to fix this ?

---

### Post by Paqman on 2011-08-08
> **mj360 said:**
> i tried safe-mode but i really don't know what to do in safe-mode to fix this ?

Try:
```
apt-get install --reinstall gnome-power-manager
```

Then give it a reboot and see if that sorts it.

---

