---
title: "Apple Remote Desktop"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Jugney on 2008-03-23
Hello fellow Gutsy Ubuntians (sorry, I couldnt resist)

I need to access a Tiger Machine from my ubuntu computer, but after enabling Apple Remote Desktop per the instructions here ([http://www.macminicolo.net/Mac_VNC_tutor.html](http://www.macminicolo.net/Mac_VNC_tutor.html)) I can't connect to it using either "Connect to Server" or "Terminal Server Client". TSC says "Unable to resolve host by name: Connection timed out (110)"

What am I doing wrong? Is there a guide to doing thisfrom the Ubuntu side so I could check my steps?

Thanks,
Jugney

---

### Post by Eiríkr on 2008-03-23
Since TSC noted host name problems, what happens if you try to connect by IP address instead?

---

### Post by Jugney on 2008-03-23
When I have tried that, TSC disappears and about 5 minutes later says unable to connect to host, connection timed out.

EDIT: I've been doing more Googling and found a previous post here on this issue, as well as some web tutorials, for people in the future who wander across this thread:

[http://homepage.mac.com/car1son/static_port_fwd_intro.html](http://homepage.mac.com/car1son/static_port_fwd_intro.html)

[http://ubuntuforums.org/showthread.php?t=577207&highlight=xp+mac+osx+connect](http://ubuntuforums.org/showthread.php?t=577207&highlight=xp+mac+osx+connect)

[http://72.14.205.104/search?q=cache:jI7p0gEs8hUJ:blog.gobanquet.com/index.php/how-to-use-apple-remote-desktop-from-ubuntu/+apple+remote+desktop+ubuntu&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://72.14.205.104/search?q=cache:jI7p0gEs8hUJ:blog.gobanquet.com/index.php/how-to-use-apple-remote-desktop-from-ubuntu/+apple+remote+desktop+ubuntu&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

Jugney

---

### Post by gallam on 2008-03-27
Hey Jugney,

I have the same problems when trying to use Terminal Server Client and am trying to figure out why as well.

In the meantime, if you install Krdc, it works perfectly.

I can connect to any of my Macs with no problem using Krdc (even though I run Gnome as the desktop versus KDE).

Just thought I'd pass along the tip.

---

### Post by Jugney on 2008-03-29
Thanks for the tip Gallam. 

Is setting the Mac up to allow Apple Remote Desktop the correct setting? And if so, what protocol do I use to connect to it - RDP?

Jugney

---

