---
title: "Can't boot GUI"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by nitinkalal on 2011-09-03
Hi...:KS
I've set automatic log in on so whenever I try to start ubuntu, it goes till ubuntu violet screen and then it stucks there. Nothing happens after that. 
I was wondering if somebody could help through this.

---

### Post by cariboo on 2011-09-04
This may not have anything to do with auto-login, but to remove auto login, start in recovery mode, and once at the meun select drop to net-root. Once at the prompt remove /etc/gdm/custom.conf:

```
rm /etc/gdm/custom.conf
```

another way to check is from recovery mode select continue from the menu, login, at the prompt and type:

```
startx
```

---

### Post by anewguy on 2011-09-04
I've seen this a few times myself.  Can you list your system specs, including the video adapter?

Sometimes if you edit the boot line from the boot menu you can try adding nomodeset to the boot line and letting it boot.  If that doesn't work, you may also want to try editing the boot line but intead putting in acpi=off.

Dave ;)

---

