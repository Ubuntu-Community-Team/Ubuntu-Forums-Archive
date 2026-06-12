---
title: "Screen Resolution on Text Splash Screen"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-05-25
Hi there, I am new to any configuration file editing, and new to linux. I have edited  **/etc/default/grub ** so as to delete "quiet splash"  in favor of " "   so that now I have text based boot screen.  I also have changed the screen resolution
 
Problem: The text wraps right at the end of the screen and is large/unreadable. I dont see a way to change text size etc....any way to do this?
Thanks in advance.

---

### Post by -humanaut- on 2010-05-25
Are you using a Nvidia card?

---

### Post by UbuNoob001 on 2010-05-26
> **-humanaut- said:**
> Are you using a Nvidia card?

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

---

