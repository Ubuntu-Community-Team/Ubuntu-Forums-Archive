---
title: "Belkin Wireless Rt61 Chipset question"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by Rocky101 on 2007-08-13
I am tryin to install my Belkin Wireless by following the steps here [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61?highlight=%28WifiDocs%2FDriver%29)

I am using Ubuntu 6.06. I am able to follow the directions and everything was going great until I issued the command

$ sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net/

 I get an error saying /kernel/drivers/net/ doesn't exist. Where do I need to go from here. thanks

---

### Post by imdano on 2007-08-14
That /lib/.../net section should be all one path.  Make sure you're using the button next to 1 (`), not a normal single quote ('). So given this command: ```
sudo cp rt61.ko /lib/modules/`uname -r`/kernel/drivers/net
```Your exact path may be a little different since you probably have a different kernel version, but for me that becomes ```
sudo cp rt61.ko /lib/modules/2.6.20-16-generic/kernel/drivers/net
```It might be helpful to just copy and paste the command from here.

---

### Post by Rocky101 on 2007-08-14
Hey Thanks alot. The full path worked

---

