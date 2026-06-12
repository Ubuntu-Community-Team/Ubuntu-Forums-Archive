---
title: "Your browser has been updated and needs to restarted."
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Coh3n on 2009-07-08
I get this every time I open Firefox, I've restarted about a hundred times, and it still keeps coming up.

Anyone have a solution to this problem?

---

### Post by Coh3n on 2009-07-08
Scratch that, I figured it out. :)

---

### Post by cariboo on 2009-07-08
There may be a problem with your profile. The best way to create a new profile is to backup the old one and restart fire. Open a terminal and type:

```
mv ~/.mozilla ~/,mozilla.bak
```

and restart firefox. Unfortunately any add-ons how have installed will need to be reinstalled. You can import your bookmarks from the backup directory you just created.

---

### Post by Coh3n on 2009-07-08
> **cariboo907 said:**
> There may be a problem with your profile. The best way to create a new profile is to backup the old one and restart fire. Open a terminal and type:

```
mv ~/.mozilla ~/,mozilla.bak
```and restart firefox. Unfortunately any add-ons how have installed will need to be reinstalled. You can import your bookmarks from the backup directory you just created.

It went away, not sure how, but I'm glad you told me that, so now I know if something goes wrong I can try that. :)

---

### Post by lovinglinux on 2009-07-08
I had this alert once while testing one of the installation methods from my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). I don't remember exactly which method of installation I used, because I already tested them more than 5 times (they all work flawlessly btw). But I guess, it was form *ubuntu-mozilla-daily* PPA (3.5.1.pre).

So I believe this issue must appear when you open a profile with a different firefox version. It's not the extension checking. It's a different alert that I never seen before.

---

### Post by amauk on 2009-07-08
there's a flag file stored in ~/.mozilla/firefox that tells firefox whether it needs restarting or not
(if file exists, app issues "needs restarting" notice)

it sometimes gets stuck

---

### Post by pavloskl on 2009-09-02
For anyone else facing this problem, just disabling the Ubuntu Firefox Modifications extention gets rid of the problem straight away.

---

