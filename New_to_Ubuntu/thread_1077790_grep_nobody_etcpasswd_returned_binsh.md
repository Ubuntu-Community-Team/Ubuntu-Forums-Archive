---
title: "grep nobody /etc/passwd returned bin/sh"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by grewolf on 2009-02-22
Returned bin/sh Is this a concern?  I was searching trying to understand system logs and came across this page
[HTML]http://ubuntuforums.org/archive/index.php/t-578172.html[/HTML]

It seems that this is bad as per the posts on the page.

---

### Post by llamakc on 2009-02-22
> **grewolf said:**
> Returned bin/sh Is this a concern?  I was searching trying to understand system logs and came across this page
[html]http://ubuntuforums.org/archive/index.php/t-578172.html[/html]It seems that this is bad as per the posts on the page.

/bin/sh is the default on Ubuntu.

---

### Post by ibuclaw on 2009-02-22
[PHP]
$ grep "nobody" /etc/passwd
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
[/PHP]

Not a concern really ... they have a nonexistant home directory, no sudoers rights, and are limited to only writing data in the /tmp directories...

Regards
Iain

---

### Post by ikonia on 2009-02-22
you can change this to a non-interactive shell such as nologin, or a true/false shell


```

sudo usermod -s /bin/nologin nobody

```

or 

```

sudo usermod -s /bin/false nobody

```

for examples.

---

