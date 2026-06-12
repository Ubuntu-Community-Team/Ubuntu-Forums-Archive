---
title: "shut down"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by old_dope on 2009-08-02
Have just installed the latest version of Ubuntu on a spare computer and everything is working fine. But when i clicked on "log-off" and then selected "shut-down" the computer is still running?

---

### Post by theozzlives on 2009-08-02
> **old_dope said:**
> Have just installed the latest version of Ubuntu on a spare computer and everything is working fine. But when i clicked on "log-off" and then selected "shut-down" the computer is still running?

How old is the computer?

---

### Post by old_dope on 2009-08-02
The computer is about two year old

---

### Post by x33a on 2009-08-02
press ctrl+alt+f1

then type:
```
sudo shutdown -h now
```

see what message is displayed (if any) and post it here.

---

### Post by cariboo on 2009-08-02
Do you have apci disabled?

---

### Post by x33a on 2009-08-02
> **cariboo907 said:**
> Do you have apci disabled?

you mean acpi :)

---

### Post by old_dope on 2009-08-02
When the Ubunutu OS loaded i typed "ctrl + alt + f1" and i was taken to a screen with a lot of text. I had to type my username and password. When i clicked on enter even more text appeared. So i clicked on "Esc" and was taken back to the GUI screen.

I then opened a terminal and typed: sudo shutdown -h now
and the computer shutdown immediately

---

### Post by jacklinux on 2009-08-02
> **old_dope said:**
> When the Ubunutu OS loaded i typed "ctrl + alt + f1" and i was taken to a screen with a lot of text. I had to type my username and password. When i clicked on enter even more text appeared. So i clicked on "Esc" and was taken back to the GUI screen.

I then opened a terminal and typed: sudo shutdown -h now
and the computer shutdown immediately
All is good then right?

---

