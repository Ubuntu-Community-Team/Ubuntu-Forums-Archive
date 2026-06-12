---
title: "apt : command not found?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by anuj@iit on 2009-10-12
Hi 
while i am typing 'apt -get install...' on terminal window, it says 'apt : command not found'
i am giving you the window content, please have a look..

----------------------------------
root@anuj-desktop:~# apt -get install nmap
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * cacao-oj6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: apt-get install <selected package>
-bash: apt: command not found
root@anuj-desktop:~# apt -get install openjdk-6-jdk
The program 'apt' can be found in the following packages:
 * openjdk-6-jdk
 * cacao-oj6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: apt-get install <selected package>
-bash: apt: command not found
---------------------------------------------------
and so i have tried all 4 packages but didn't work. help me.
Thanks!

---

### Post by kwokyinc on 2009-10-12
There is no space in "apt-get".

---

### Post by MelDJ on 2009-10-12
and try using the sudo command more than logging in terminal as root

---

### Post by lavinog on 2009-10-12
use synaptic instead of the terminal

if you must use the terminal, you can use aptitude or apt-get:
```

sudo apt-get install packagename
sudo aptitude install packagename


```
 to search for a package
```

apt-cache search keyword
aptitude search keyword

```

You may want to limit your results when using apt-cache by piping to grep to add another keyword
```

apt-cache search keyword|grep -i otherkeyword

```

---

### Post by anuj@iit on 2009-10-12
Thanks to all

---

