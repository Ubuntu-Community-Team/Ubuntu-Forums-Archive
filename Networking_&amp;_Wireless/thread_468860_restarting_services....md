---
title: "restarting services..."
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by BlaineM on 2007-06-09
hello.

I was curious if there was an equivalent with Ubuntu for the terminal to control the services like in CentOS.

"service network stop" -- "service network restart"

I like the service command and would like to know of an equivalent in Ubuntu.

thanks,
Blaine

---

### Post by EndPerform on 2007-06-09
These commands will do what you ask:

```
sudo /etc/init.d/networking stop
```

or:

```
sudo /etc/init.d/networking restart
```

Hope that helps. :)

---

### Post by yota on 2007-06-09
Hi, in debian you can use
```

sudo /etc/init.d/networking start|stop|restart

```

if you still like the "service" command you can put a trivial script like
```

#!/bin/bash
sudo /etc/init.d/$@

```
in /usr/local/bin

Hope this helps!

---

### Post by BlaineM on 2007-06-10
thanks alot. exactly what I was looking for.

Blaine

---

