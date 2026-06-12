---
title: "Picasa &quot;Error: Wrong architecture 'i386'"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by webmanoffesto on 2011-04-18
I tried to install Picasa and got the error message "Error: Wrong architecture 'i386'

I used Wubi Installer to install Ubuntu 10.04 LTS - Lucic Lynx on my Windows 7 machine. This is not a 64 bit machine. So I don't understand the error message.

What do you suggest I do?

---

### Post by falko on 2011-04-18
What's the output of ```
uname -a
```?

---

### Post by webmanoffesto on 2011-04-18
Linux ubuntu 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux

---

### Post by mastablasta on 2011-04-18
your linux is 64 bit. since you can run it on your maschine it means the maschine is also 64 bit ;-)
 
it means you need to either install the 64 bit version of Picasa or you need certian 32 bit libraries to run the 32 bit version of it.

---

### Post by webmanoffesto on 2011-04-18
[SIZE=-1]I think the below says it should work as I installed it. What do you think?

[http://picasa.google.com/linux/faq.html#2](http://picasa.google.com/linux/faq.html#2)
[/SIZE]**[SIZE=-1]Q:  Will Picasa run on             a 64-bit version of Linux?[/SIZE]**          [SIZE=-1]Yes, Picasa runs on 64-bit versions of Linux.  For           RPM-based distributions, just install the normal 32-bit RPM of           Picasa; this works on the RPM-based 64-bit distributions we tried, as           they're pretty good about letting you mix 32 and 64-bit packages.[/SIZE]          
[SIZE=-1] For Debian-based distributions, install the           amd64.deb instead of the i386.deb. This is still 32-bit, but it           knows to reference the system's 32-bit libraries. If you use apt-get           to install Picasa from our 64-bit repository, the system's 32-bit           libraries will be automatically installed if needed.[/SIZE]

---

### Post by mörgæs on 2011-04-18
[SIZE=-1]**For Debian-based distributions, install the           amd64.deb instead of the i386.deb.**

It can not be more explicit than that.
[/SIZE]

---

### Post by webmanoffesto on 2011-04-20
Successfully installed in Ubuntu by going to Applications / Ubuntu Software Center

---

### Post by mörgæs on 2011-04-20
Good, please mark the thread 'solved'.

---

