---
title: "Firefox Freezes When Restarting"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2009-12-11
Just recently, when I restart Firefox it doesn't open Firefox up again, and when I try to open Firefox manually it says "Firefox is already running but not responding". I have to use pkill in the terminal to open Firefox again.

Please help, as I don't want to have to close the Firefox process every time I upgrade an add-on.

(I said "Firefox" a lot.)

---

### Post by kmac on 2009-12-12
> **LegendarySandwich said:**
> Just recently, when I restart Firefox it doesn't open Firefox up again, and when I try to open Firefox manually it says "Firefox is already running but not responding". I have to use pkill in the terminal to open Firefox again.

Please help, as I don't want to have to close the Firefox process every time I upgrade an add-on.

(I said "Firefox" a lot.)

Create a launcher on your toolbar to run the terminal command:

```
killall firefox
```

Give it a clever icon and click when necessary

---

### Post by lovinglinux on 2009-12-12
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by frenchn00b on 2009-12-12
type in the console:

```
killall -e firefox-bin firefox ; sleep 5s ; killall -e firefox firefox-bin -9 ; firefox -safe-mode
```

---

### Post by LegendarySandwich on 2009-12-12
Nevermind, I seemed to fix it. I will post later if the problem happens again.

---

