---
title: "Help!!! No login screen!!!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by HypnoSquid on 2009-01-07
i changed my login screen to match my theme and now when i boot up it just sits loading at the login screen (spinning cursor thing) and NEVER loads up!!!

i donno what i should do other than un-install ubuntu and reinstall, which i REALLY do not want to do.

is there a way i can boot up to a command line and what would i use in the command line to set the login screen back to default???

---

### Post by dccrens on 2009-01-07
Try to hit "Alt and F4" or one of the other "F" keys to see if you can get to ca console. If you can log in from there and try to figure out what you changed. Change it back. You will be operating at the command line. You can also try to hit CNTL-ALT-BKSP together and restart the x server to see it that works.

---

### Post by Michael.Godawski on 2009-01-07
hi

you can try to boot into recovery mode and run these:

```
update-alternatives --config usplash-artwork.so
```

found [here]("http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/"), never had done it for myself though.

---

### Post by HypnoSquid on 2009-01-07
I FIXED IT!!!!

```
ctrl+alt+f2 at the loading screen

login

cd /usr/share/gdm/themes

ls

sudo rm -rf *problem folder here*

exit


```



thanks so much for your help guys

---

