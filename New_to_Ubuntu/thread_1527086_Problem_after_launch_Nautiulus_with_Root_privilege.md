---
title: "Problem after launch Nautiulus with Root privilege"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by losl on 2010-07-08
I have Ubuntu 10.4 for netbook installed. I used terminal to launch Nautilus with Root privilege by entering "gksudo nautilus". After 
closing both Nautilus and terminal i lost my desktop !! I have to logout and re-login to get it back. This happens when launch Nautilus with root privilege using the terminal or using "open in Administrator" in the right-click menu with "nautilus-gksu" installed.

How could i rectify this problem ??? Thank you !


For a much clear and detail info please view my screen video capture in

[http://www.youtube.com/watch?v=-Kq_QiIghFg](http://www.youtube.com/watch?v=-Kq_QiIghFg)

---

### Post by kerry_s on 2010-07-08
```
gksudo "nautilus --no-desktop"
```

nautilus script:

```
#!/bin/bash
gksudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
exit 0

```

you can use the main menu to create a launcher, i have mine under system tools.

---

### Post by losl on 2010-07-10
Thank you very much !!

Your explanation is very helpful.

---

