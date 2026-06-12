---
title: "boots to cmd  not desktop"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by jd-white on 2009-09-26
My new install starts in the command prompt. How do I get it to boot to the desktop.  TIA jd

---

### Post by j7%&lt;RmUg on 2009-09-26
Are you using the desktop edition or the server edition?

---

### Post by MelDJ on 2009-09-26
does it say busybox and initramfs?

---

### Post by jd-white on 2009-09-26
> **MelDJ said:**
> does it say busybox and initramfs?
it is a login usr name i enter then asks for password and i am in at a cmd line

ty

---

### Post by jd-white on 2009-09-26
> **nisshh said:**
> Are you using the desktop edition or the server edition?
desktop....it is a login usr name i enter then asks for password and i am in at a cmd line

ty

---

### Post by MelDJ on 2009-09-26
try typing gnome-session

---

### Post by jd-white on 2009-09-26
ty i will

---

### Post by jd-white on 2009-09-26
when I logoff it says     stopping gnome but i was not at the desktop i logged off from a cmd screen

---

### Post by MelDJ on 2009-09-26
did the desktop come up?

---

### Post by fela on 2009-09-26
At the command prompt, type in:

```
sudo /etc/init.d/gdm start
```

It will ask for a password. Now I'm guessing that it'll give you errors and not start the login manager (as that command should). If it does output errors, please post them here.

---

### Post by credobyte on 2009-09-26
[LIST=1]
[*]Enter your username and password
[*]Type in: [COLOR=Green]startx[/COLOR]
[*]Let us know the outcome ( in case of errors, let us know them ).
[/LIST]

---

### Post by diskotek on 2009-11-07
> **MelDJ said:**
> does it say busybox and initramfs?

i have this problem exactly. and i can not start x or something else from the busybox command line.

as i read many same troubleshot, but no solution found yet i the forum

---

