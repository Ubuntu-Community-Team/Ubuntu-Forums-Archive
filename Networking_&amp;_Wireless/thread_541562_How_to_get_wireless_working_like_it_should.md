---
title: "How to get wireless working like it should ??"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by CaptSaltyJack on 2007-09-03
Here is how most devices (generally speaking) work with wifi:

```
upon boot:
  check for wifi access points within range
  if results do not contain any visited APs then
    prompt user to choose an AP (and ask for password if needed)
    connect to specified AP
  else
    choose most recently used AP automatically
  end
```

Why Feisty's wireless (out of the box) sucks (in my opinion):

- wireless is not activated until you actually LOG in
- the damn keyring always comes up asking for the password (actually, sometimes it pops up then quickly vanishes, yet I can still see it in the taskbar.. I have to close it from there, then I get prompted for the actual WPA key)

The problem with the way Feisty works out of the box is, if I remotely reboot a wireless Ubuntu box, I'm screwed.  There's no chance of it coming back online when it has booted back up.

Can someone tell me how to set up my Feisty laptop so wireless is initiated upon boot, NOT login, AND it won't ask me for my keyring password every damn time?

Thanks :)

---

### Post by Jamie Jackson on 2007-09-03
I'm just starting to look into [wicd]("http://wicd.sourceforge.net/features.php"), but it's supposed to overcome some of these obstacles.

---

### Post by CaptSaltyJack on 2007-09-03
Cool, I'll check it out for sure. Thanks!

---

### Post by bikeboy on 2007-09-03
libpam-gnome-keyring should overcome your password prompting issue.
My wireless is activated before login, I'm guessing yours will be too with the libpam thing in action.

---

