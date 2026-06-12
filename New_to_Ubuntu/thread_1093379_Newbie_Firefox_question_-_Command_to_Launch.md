---
title: "Newbie Firefox question - Command to Launch?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Pa100ka on 2009-03-11
Hi,

This is probably a daft question, but I've Googled and searched the forum, and can't find an answer.

Firefox 3.0.7 on Intrepid with Gnome.

I note that my menu launcher says "firefox %u" (without the quotes). What does the %u signify please? In a terminal, if I just type "firefox", up it comes. If I type "firefox %u" it thinks I am looking for [www.%u.com](www.%u.com) (expected, since the argument is supposed to be a URL).

So what's with the %u in the launcher, please?

Thanks,
Pa100ka

---

### Post by stanz on 2009-03-11
I believe this is the 'present working users directory'...yo[COLOR=Red]u[/COLOR]....
I've forgotten the full details...sry

[https://wiki.ubuntu.com/BasicTroubleshooting?highlight=(\%25u](https://wiki.ubuntu.com/BasicTroubleshooting?highlight=(\%25u))

---

### Post by LowSky on 2009-03-11
well -u usually refers to the current user's version; in the case you may have a centralized install with multiple users. Kinda dumb point as the current program will open to what ever user is currently logged on even without the -u


dont really know why they use the % symbol

---

### Post by Pa100ka on 2009-03-11
Thanks. Actually, I found the answer here:

[http://library.gnome.org/users/user-guide/stable/launchers-properties.html.en](http://library.gnome.org/users/user-guide/stable/launchers-properties.html.en)

In other words, it is a special code used by the Gnome Launcher, but since nothing follows the %u, as far as I can see it is in effect silently dropped.

Cheers,
Pa100ka

---

