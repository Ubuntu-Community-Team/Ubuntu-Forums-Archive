---
title: "Ubuntu Installation - Boots in Black Screen"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by balan_sp on 2011-08-18
Hi,

I have installed Ubuntu 10.10 desktop edition in my Acer Aspire 4741Z laptop. I used the 'Use entire hard disk' option for installing. The installation ends with a successful message.  After reboot it displays a command line and prompting me for user name and password. I couldnt see my desktop. i tried **sudo setpci -s 00:02.0 F4.B=00** but nothing happened. The screen automatically switches to a black screen when  **sudo service gdm start** command is typed.:confused:

Please help me...

---

### Post by sanderd17 on 2011-08-18
Wow, new on this forums and already got that far?

it should work if you add

```

gdm &

```

to the end of the file /etc/rc.local before the exit 0 line

---

