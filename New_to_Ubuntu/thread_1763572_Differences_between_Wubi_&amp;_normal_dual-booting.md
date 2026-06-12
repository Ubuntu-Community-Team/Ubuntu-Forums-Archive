---
title: "Differences between Wubi &amp; normal dual-booting?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-05-20
How much difference is there between Ubuntu installed inside Windows by Wubi & Ubuntu installed alongside Windows by typical dual-boot methods?

I didn't manage to find any decent list or explanation of such differences.

Thanks for any indications!

---

### Post by jerrrys on 2011-05-20
this may help
[U]
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+vs+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911)
[/U][ ]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Differences+between+Wubi+%26+dual-booting&as_qdr=all&sa=Google+Search&lang=en#911")

---

### Post by JRV on 2011-05-20
Wubi is started from the Windows boot loader which then chainloads grub to start Ubuntu.

Instead of being in it's own partition the Wubi file system is on a file in the Windows partition.

Wubi can be uninstalled through the Add/Remove programs in the Windows control panel.

Wubi is for someone who is not committed to using Linux, but wants to give it a try.  A Wubi installation is usually temporary.  People usually try it, then delete it and do a regular install, or not.

Wubi often has trouble handling updates.

---

### Post by s3a on 2011-05-20
In short, Wubi is worse since, if I'm correct, it suffers from whatever problems Windows would have such as a fragmented filesystem since it is installed in it. I would definitely dual-boot if I were you. If you want to change the sizes of the partitions, you can choose to do so later with a Ubuntu Live CD so it's not like your making a decision that you can't change.

---

### Post by beew on 2011-05-20
Or you can make a full install into an external hard drive and boot from it.

WUBI is just a demo in a way and it also makes trouble shootings unnecessarily complicated. If you want to have a realistic picture of Linux give it its full due.

---

