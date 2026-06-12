---
title: "CCSM brightness problem"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-02-03
After getting ccsm running the way I like, I cant adjust my screen brightness anymore.  I dont think I changed anything in CCSM about the brightness.  Help please.

---

### Post by DarrenMR415 on 2011-02-03
Please help, the brightness is giving me a headache.

---

### Post by maphilli14 on 2011-03-18
Seems to work for me.  I'm wondering how to turn it back to default when done.  I can turn it up and down.

---

### Post by rupak447 on 2011-03-18
I was also a victim of this problem. Finally, I reduce ma CCSM brightness and now feel relax. Hope, you would find your solution on ma way.

---

### Post by DarrenMR415 on 2011-06-11
Ive tried everything I can think of.  I cannot get my brightness down.

---

### Post by DarrenMR415 on 2011-06-11
This got the brightness slider working again.

> If you&#8217;re running Ubuntu 10.10 or 11.04 on laptop, you might get a problem that fn key combination to change screen brightness is not working. Here&#8217;s a solution for nvidia laptop with this problem:

First edit xorg.conf in terminal with the command:
sudo gedit /etc/X11/xorg.conf

And then find the Section &#8220;Device&#8221; and add the bold line.

Section &#8220;Device&#8221;
 Identifier &#8220;Default Device&#8221;
 Option &#8220;NoLogo&#8221; &#8220;True&#8221;
**Option &#8220;RegistryDwords&#8221; &#8220;EnableBrightnessControl=1&#8243;**
 EndSection

And now your brightness control is working in next login!

---

