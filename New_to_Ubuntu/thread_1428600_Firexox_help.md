---
title: "Firexox help"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by JoeGoe on 2010-03-13
Hi,

A few months ago I deleted firefox 3.5 from my system, and installed chrome.

Now, I when I try to reinstall firefox, it won't show ip under Applications~Internet.  Where did it go?

---

### Post by asmoore82 on 2010-03-13
Are you installing from the package manager?

---

### Post by tshrinivasan on 2010-03-13
Hi,

How you deleted firefox?

How you reinstalled again?

Is the firefox opens, when you type "firefox" in terminal?I

---

### Post by lovinglinux on 2010-03-13
Go to "System >> Preferences >> Main Menu" and create a new launcher under Internet using the following command:

```
firefox %u
```

---

### Post by JoeGoe on 2010-03-13
> **asmoore82 said:**
> Are you installing from the package manager?
I am installing it from the package manager.

---

### Post by Phrea on 2010-03-13
Try the suggested  Main Menu, and add it from there.

---

### Post by JoeGoe on 2010-03-14
Thanks for the help, I got it working.  One more thing though, where is the image of the fox surrounding the globe stored?

---

### Post by mikewhatever on 2010-03-14
/usr/lib/firefox-3.5.8/icons/mozicon128.png
The menu editor will direct you to /usr/share/pixmaps/firefox-3.5.png, which is a simlink to the actual icon.

---

