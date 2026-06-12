---
title: "Startup script"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by c0nrad on 2010-07-14
Hey,

I was wondering if anyone could point me in a direction for this script I was thinking of making.

I want to make a script that'll open a terminal in each "Desktop" when I login.

I know a bit of bash, and I'm guessing i'd jsut use the command gnome-terminal a few times. But, how do I run this script on startup and how do I put them in specific desktops.

Thanks,
c0nrad

---

### Post by Ctrl-Alt-F1 on 2010-07-14
Don't know about specific desktops but an easy way to run bash commands on startup is just to put them in the /etc/rc.local file.  Another way is to make a script and then via the menu add it to startup applications (can't remember exactly what it is called).

---

