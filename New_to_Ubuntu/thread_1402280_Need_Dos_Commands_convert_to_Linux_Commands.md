---
title: "Need Dos Commands convert to Linux Commands"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Sugi on 2010-02-09
> @ echo off
ipconfig /flushdns
ipconfig /release
ipconfig /renew
exit

How do I convert this to Linux commands in a bash file?

#!/bin/bash
echo ifconfig /flushdns
echo ifconfig /release
echo ifconfig /renew
exit

Is that correct or am I totally wrong?

Thanks,
Sugi

---

### Post by mikechant on 2010-02-09
ifconfig does not have any of those options or equivalent functions (nb options are usually specified with a - or -- in Linux)

ipconfig /flushdns:
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=156577](http://ubuntuforums.org/showthread.php?t=156577)
Particularly comments 7 and 8

ipconfig /release
ipconfig /renew
Have a look at this:
[http://ubuntuforums.org/showthread.php?p=2032997](http://ubuntuforums.org/showthread.php?p=2032997)

I think it's the dhclient command you want

---

### Post by oldfred on 2010-02-09
I thought it was:

ifconfig eth0 down
ifconfig eth0 up

but I do not know if you need a delay between them?

---

### Post by mushwars on 2010-02-09
```
man nscd
```

Name server caching daemon. 

Basically you just need to restart it

```
sudo /etc/init.d/nscd restart
```

this will flush dns, you can ask for a renew from your router though I dont know why you would want to do that when you can just restart networking

```
sudo /etc/init.d/networking restart

-or-

sudo service networking restart
```

---

### Post by lisati on 2010-02-09
Another one:
```

sudo ifdown eth0 && sudo ifup eth0

```

---

