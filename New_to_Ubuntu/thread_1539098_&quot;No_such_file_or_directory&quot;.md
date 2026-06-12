---
title: "&quot;No such file or directory&quot;"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by headbuster on 2010-07-26
Whenever I want to install something or use a file with the terminal it tells me "No such file or directory"
For example I am installing java with this tutorial:
[http://java.com/en/download/help/linux_install.xml#selfextracting](http://java.com/en/download/help/linux_install.xml#selfextracting)
and on step 1 and 4 it says no such.... step 1 I did by going to properties and editing the permissions but on step 4 I don't know what to do. It's not only this time.... Every other thing that includes using a filename in the command in terminal fails...
and I am 1000% sure that the file exists...
strange
------

######@ubuntu:/usr/java$ ./jre-6u21-linux-i586.bin
bash: ./jre-6u21-linux-i586.bin: No such file or directory

---

### Post by Bachstelze on 2010-07-26
> **headbuster said:**
> 
and I am 1000% sure that the file exists...
strange
------

######@ubuntu:/usr/java$ ./jre-6u21-linux-i586.bin
bash: ./jre-6u21-linux-i586.bin: No such file or directory

You're probably looking in the wrong place. ;)  If the file is on your desktop, you need to do

```
cd Desktop
```

before.

---

### Post by headbuster on 2010-07-26
Well it worked...thanks
but isn't there an easier way to enable and configure it...and also I am using chrome and the tutorial is for firefox.
[http://java.com/en/download/help/linux_install.xml#enable](http://java.com/en/download/help/linux_install.xml#enable)
Thanks

---

