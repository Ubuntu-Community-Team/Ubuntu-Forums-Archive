---
title: "Graphical Log in problems (post 9.10 upgrade)"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by suitedaces on 2009-11-12
Upgraded to 9.10, was working grand, until I restarted. When I try to log in graphically it gives me the error:

/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256

and returns me to the log in screen

I can log into terminal fine, but the chmod 1777 /tmp solution here:
[http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)

doesn't work. Also, if the solution involves logging into terminal and connecting to internet, I might need some help with that too.

---

### Post by JBAlaska on 2009-11-12
I think that command is supposed to be:
```
sudo chmod 755 /etc/gconf/gconf.xml.*
```

---

### Post by suitedaces on 2009-11-12
No joy (no such file or directory.) When I try /* instead of .* there's no output, but it doesn't work either.

I should add, at the gui log in, there's a text box saying "the configuration defaults for gnome power manager have not been installed properly"

---

### Post by suitedaces on 2009-11-12
Somehow got this sorted by booting into recovery mode and letting it fix itself.

---

