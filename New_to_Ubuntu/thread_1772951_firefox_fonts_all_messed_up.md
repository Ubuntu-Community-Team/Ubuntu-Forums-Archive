---
title: "firefox fonts all messed up"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by cacs on 2011-06-01
Hi.
Suddenly my FF fonts were all messed up, but not opera or system!
System fonts are smooth, but ff are barely unreadable!
How can I change those settings?
Already tried System settings > Appearance > fonts
Also tried in ff edit > preferences > fonts and colours! :(
TY.

---

### Post by ubudog on 2011-06-01
Hi there.  Is this a fresh install?  Do you have any bookmarks or anything you want to save?  If not, run this command to reset your Firefox.

```
rm -rf .mozilla
```

Then, start up Firefox, and all should be well.

---

### Post by cacs on 2011-06-01
> **ubudog said:**
> Hi there.  Is this a fresh install?  Do you have any bookmarks or anything you want to save?  If not, run this command to reset your Firefox.

```
rm -rf .mozilla
```Then, start up Firefox, and all should be well.

Hi.
I had to install all add-ons, but it's nice again! :)

Thank you!

---

### Post by ubudog on 2011-06-01
Cool, glad you got it fixed. :P

---

### Post by bbogart on 2012-06-15
FYI I solved this by just removing the "chrome" directory in:

$HOME/.mozilla/firefox/[profile].default/

keeps extensions intact.

---

