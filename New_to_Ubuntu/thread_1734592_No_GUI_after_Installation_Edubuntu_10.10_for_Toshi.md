---
title: "No GUI after Installation Edubuntu 10.10 for Toshiba C660-14h"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by JackAndBlues on 2011-04-20
Hey guys,  after hours of searching Google for solutions for this problem, I'll need to ask you guys for help. I installed Edubuntu 10.10 on three new Toshiba C660-14h Laptops. The LiveCD worked great for everyone. No I am having trouble booting the GUI, this has been a common problem to Ubuntu 10.10, as Google search result show, still I don't know how to solve it.   

I tried &quot;startx&quot;, but it would not help. Further users asked for xorg.conf, but it seems to me that since version 10.04 there is no more xorg.conf in Ubuntu.  
 System: 

[LIST]
[*]Toshiba C660-14h
[*] Intel Pentium P6100 2.00Ghz 2.00Ghz (Dual-Core; it seems)
[*]2 GB Ram 32bit
[*]Intel HD Graphics
[/LIST]


If you need any further information to help, I'd be glad to serve you so.   Thanks for help,

---

### Post by JackAndBlues on 2011-04-21
bump

---

### Post by nothingspecial on 2011-04-21
You may need a restricted driver.

Boot into recovery mode with networking.

Get a wired connection and type 

```
jockey-text -l
```

If there are any drivers listed type ```
jockey-text -e <driver>
```

---

### Post by ESDEEM on 2011-04-21
I think u are on command line mode....
T install GUI....try 
> sudo apt-get install gnome-desktop
> sudo apt-get install gdm
> sudo apt-get install gnome-utils

---

### Post by JackAndBlues on 2011-04-21
I solved it. Blacklisting the intel_ips did it!

Someone should open up a collecting thread in a wiki or here in the forum, the problem has been frequent to many users and has had several causes. My was solved this way:

[http://ubuntuforums.org/showthread.php?p=9997946](http://ubuntuforums.org/showthread.php?p=9997946)

this thread helped me editing the blacklist.conf

How I did it?

1. Select the recovery mode under grub
2. Press Alt + F2
3. Enter "gksudo gedit /etc/modprobe.d/blacklist.conf" and enter your password
4. Add "blacklist intel_ips" at the bottom 
5. Save, reboot, you're ready to go.

---

### Post by JackAndBlues on 2011-04-21
> **ESDEEM said:**
> I think u are on command line mode....
T install GUI....try

Exactly. That I was .

---

