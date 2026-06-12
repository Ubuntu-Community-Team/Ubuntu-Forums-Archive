---
title: "can't upgrade ICEauthority"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Someone uk on 2010-08-08
i get this error message when i boot my pc saying ICEauthroty can't be upgraded, can someone explain what ICEauthority does and what is causing this problem?

---

### Post by Shazaam on 2010-08-08
I found this...
```
Possible solution #2: This can also happen if you've somehow changed ownership of the ~/.ICEauthority file. So you can change it back by pressing Control-Alt-F1, logging in, and typing

sudo chown username:username ~/.ICEauthority

where username is your username. Then press Control-Alt-F7 and try logging into Gnome again.
```

from here...
[https://help.ubuntu.com/community/Troubleshooting](https://help.ubuntu.com/community/Troubleshooting)

---

### Post by khelben1979 on 2010-08-08
[Check this out!]("http://www.absolutelytech.com/2010/01/27/solved-unable-to-update-iceauthority-on-booting/")

(Just made a simple google search..)

---

