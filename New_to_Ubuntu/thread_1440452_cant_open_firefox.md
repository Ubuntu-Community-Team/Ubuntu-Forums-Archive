---
title: "cant open firefox"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by g_baskin on 2010-03-27
Hey guys,  After updating yesterday I cant open firefox, epiphany opens fine but nothing from firefox.

---

### Post by slughappy1 on 2010-03-27
I've been having this problem too. Although for me I can get Firefox to open, but I have to open Swiftfox first, close it, and then open Firefox. Weird I know.

---

### Post by s.fox on 2010-03-27
> **g_baskin said:**
> Hey guys,  After updating yesterday I cant open firefox, epiphany opens fine but nothing from firefox.

Hello,

Can you open a terminal and enter the following:

```
firefox
```

Please post back the output.  :)

-Silver Fox

---

### Post by lovinglinux on 2010-03-27
If you have Prism installed, then remove it. It is preventing Firefox from loading recently. Otherwise, see [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by slughappy1 on 2010-03-29
> **Silver_fox_ said:**
> Hello,

Can you open a terminal and enter the following:

```
firefox
```

Please post back the output.  :)

-Silver Fox

Sorry it took me a while to get back to you. I sort of forgot and got busy. Well here is what happens when I try and boot up Firefox for the first time when it fails. I can get more information if needed. 
```
jason@Barnaby:~$ firefox
/usr/share/themes/showtime/gtk-2.0/gtkrc:89: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/showtime/gtk-2.0/gtkrc:94: Murrine configuration option "gradients" is no longer supported and will be ignored.

(firefox-bin:4703): GLib-WARNING **: g_set_prgname() called multiple times
jason@Barnaby:~$ 

```

---

### Post by JamezQ on 2010-03-29
I also have this problem. I use chrome so it's not a big deal. But I want my firefox every now and then.

---

