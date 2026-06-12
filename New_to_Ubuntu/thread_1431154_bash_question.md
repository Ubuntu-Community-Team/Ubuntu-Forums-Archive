---
title: "bash question"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by doug piston on 2010-03-16
trying to setup koush's vendor tree and ive run into a snag.
 
i try to run this code with phone mounted to computer
```
. extract-files.sh
```
 
 
and i get this
```
jarvis@jarvis:~/mydroid/vendor/motorola$ mv android_vendor_motorola_sholes-open sholes-open
jarvis@jarvis:~/mydroid/vendor/motorola$ . extract-files.sh
bash: extract-files.sh: No such file or directory
```
 
my first question is what is bash exactly and why do i not know this? and secondly why i might be hitting this problem?
 
any light shedding on this would be super awesome!!
 
thanks all

---

### Post by aeiah on 2010-03-16
bash is your command line environment.

try 
```

./extract-files.sh

```

---

### Post by jacknjill111 on 2010-03-16
Bash: [http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)

> 
```
jarvis@jarvis:~/mydroid/vendor/motorola$ mv android_vendor_motorola_sholes-open sholes-open
jarvis@jarvis:~/mydroid/vendor/motorola$ . extract-files.sh
bash: extract-files.sh: No such file or directory
```


Assuming extract-files exists under "motorola" directory and if it is an executable (executable bit "x" turned on) script, you would need to run it as follows: 
```

jarvis@jarvis:~/mydroid/vendor/motorola$ ./extract-files.sh

```
or
```

jarvis@jarvis:~/mydroid/vendor/motorola$ /bin/bash extract-files.sh

```

HTH,
RS

---

### Post by doug piston on 2010-03-16
i love this forum!!!  everybody seems so nice and is willing to help complete newbs such as myself.
 
> **jacknjill111 said:**
> Bash: [http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)
 
 
 
Assuming extract-files exists under "motorola" directory and if it is an executable (executable bit "x" turned on) script, you would need to run it as follows: 
```

jarvis@jarvis:~/mydroid/vendor/motorola$ ./extract-files.sh

```
or
```

jarvis@jarvis:~/mydroid/vendor/motorola$ /bin/bash extract-files.sh

```
 
HTH,
RS
 
 
extract-files.sh is in "motorola" but turning in to and exectuable would mean to chmod the extract-files.sh with the +x correct?

---

### Post by aeiah on 2010-03-16
> **doug piston said:**
> i love this forum!!!  everybody seems so nice and is willing to help complete newbs such as myself.
 

 
 
extract-files.sh is in "motorola" but turning in to and exectuable would mean to chmod the extract-files.sh with the +x correct?

yup. you can do this under most desktop environments as well by right-clicking and going to properties

---

### Post by doug piston on 2010-03-16
one more question i have is why the phone mouted to the computer? is extract-files.sh command trying to pull from my phone?

---

