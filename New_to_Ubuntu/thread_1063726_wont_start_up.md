---
title: "wont start up"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by demon_hunter on 2009-02-08
My pc gets half way through loading stops starts then stops and wont move agian

this is at the ubuntu loading screen with the bar moving across the screen

anybody help

---

### Post by gettinoriginal on 2009-02-08
At the grub splash, hit escape, then progress to shell prompt and put:
```
sudo gedit /var/log/syslog
```
That should tell you where it is failing

---

### Post by racie on 2009-02-08
This is going to sound silly, but that sounds sort of like what happens to me.  I have to hold the enter key to get the bar moving.  Does that help any?  =P

---

### Post by demon_hunter on 2009-02-09
no neither of them are working
any other ideas?

---

### Post by crazyness003 on 2009-02-09
try to boot without apic. I used to have that problem with gutsy.
Also, try turning off splash.

You can achieve both of these by doing a soft-edit to your grub by hitting "Esc" when you see a promt. Then select your kernel and hit "e" then select the kernel image (labelled "kernel") and hit "e" again.
Now just remove the "splash" and "add "noapic" to that line.
Hit "enter"
then"b" to boot.

See what happens.

---

