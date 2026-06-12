---
title: "help please black screen"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by rx8bob on 2009-06-09
hi i have a webbook  i can load up and login hear the drums but the screen is black after the ubuntu logo. i have NO internet at the moment. i did also get a wristband usb from elonex to restore factory settings but need the screen on first
thanx

---

### Post by dileepm on 2009-06-09
Does this happen exactly for the first time after you install Ubuntu?

---

### Post by rx8bob on 2009-06-09
hi ubuntu is already in thw webbook. the other day i tried ti restore factory settings but it didnt work. now when i turn on i get ubuntu logo then screen goes black. i get drum sound and still with black screen i pu username and password in, get more drums but screen still black
bob

---

### Post by timjohn7 on 2009-06-09
> **rx8bob said:**
> hi ubuntu is already in thw webbook. the other day i tried ti restore factory settings but it didnt work. now when i turn on i get ubuntu logo then screen goes black. i get drum sound and still with black screen i pu username and password in, get more drums but screen still black
bob

After you hear the 2nd drum roll, push Alt Ctrl + F1, Alt Ctrl + F2 and Alt Ctrl + F7.  This will take you through tty1, tty2 and restart tty7 which should take you to your Desktop.  This may or may not fix your problem permanently.  I have a similar problem using an Intel Graphics card and sometimes the fix remains in place for months, but occasionally seems to reset back to the black screen.  Its bothersome, but not serious.

---

### Post by dileepm on 2009-06-09
Couldn't excatly figure out the problem. I had a similar one. I tried the following it worked.

Go to boot menu --> then to recovery mode --> drop to root shell

```
apt-get remove compiz-core compiz
```

```
init 6
```

Login again

Sometimes there might be a issue with your graphics card support with compiz.

---

