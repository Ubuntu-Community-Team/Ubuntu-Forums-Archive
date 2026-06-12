---
title: "Conky Question"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by uRock on 2010-07-29
I have been plating with a couple of the themes and I was wanting to get this one to show the Public IP. The other themes I have tried were able to show this.

Thanks,
uRock

---

### Post by Apollo87 on 2010-07-29
Hello,

Looking at this thread:
[http://ubuntuforums.org/showthread.php?t=413156](http://ubuntuforums.org/showthread.php?t=413156)

It looks like you need to create a script, ie /home/user/myip.sh:
```
#!/bin/sh
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

Then put this in your conkyrc:
```
Wan IP:$alignr${execi 600 /home/user/myip}
```

---

### Post by uRock on 2010-07-29
> **Apollo87 said:**
> Hello,

Looking at this thread:
[http://ubuntuforums.org/showthread.php?t=413156](http://ubuntuforums.org/showthread.php?t=413156)

It looks like you need to create a script, ie /home/user/myip.sh:
```
#!/bin/sh
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

Then put this in your conkyrc:
```
Wan IP:$alignr${execi 600 /home/user/myip}
```

Thanx, That got it done.

---

