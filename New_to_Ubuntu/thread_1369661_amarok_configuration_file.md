---
title: "amarok configuration file"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Matt26 on 2010-01-01
can anyone tell me where i can find the xine-config file for amarok in ubuntu 9.10?  i've read that it is located at ~/.kde/share/apps/amarok/xine-config but i can't find it there.

i've also searched for the file using ubuntu's search function but that didn't find anything.

---

### Post by SuperSonic4 on 2010-01-01
```
[15:40:53] sonic ~ $  locate xine-config
/usr/bin/xine-config
/usr/share/man/man1/xine-config.1.gz
```

looks like it's /usr/bin/xine-config

---

### Post by Matt26 on 2010-01-01
> **SuperSonic4 said:**
> ```
[15:40:53] sonic ~ $  locate xine-config
/usr/bin/xine-config
/usr/share/man/man1/xine-config.1.gz
```

looks like it's /usr/bin/xine-config

thanks, i tried the locate command and it didn't return any results, so i guess that means that i don't have an xine-config file.

i have amarok installed and i have used it, so shouldn't there be an xine-config file to go with it?  i'm assuming that amarok uses the xine engine by default.

---

### Post by SuperSonic4 on 2010-01-01
It is possible you've not updated the database recently. Amarok usually uses xine but it can use gstreamer or even mplayer and vlc.

You can either update the database and try again ```
sudo updatedb
``` or use find ```
find / -name xine-config
```

The second command will bring up a lot of error messages (permission denied) unless ran as root but it will not be in a non-readable folder

---

### Post by Matt26 on 2010-01-01
> **SuperSonic4 said:**
> It is possible you've not updated the database recently. Amarok usually uses xine but it can use gstreamer or even mplayer and vlc.

You can either update the database and try again ```
sudo updatedb
``` or use find ```
find / -name xine-config
```

The second command will bring up a lot of error messages (permission denied) unless ran as root but it will not be in a non-readable folder

still no results- i've also confirmed that amarok is using the xine engine, so i'm not sure why i can't find the xine-config file.

any other suggestions?

---

