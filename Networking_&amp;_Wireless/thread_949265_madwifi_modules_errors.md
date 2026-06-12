---
title: "madwifi modules errors"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by lcruz007 on 2008-10-16
Hello!
I have been trying to install madwifi, however, when I type make I get some compilation errors. 

```

**...**
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode] Error 1
make[2]: *** [/home/luis/madwifi-hal-0.10.5.6/ath_hal] Error 2
make[1]: *** [_module_/home/luis/madwifi-hal-0.10.5.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
root@luis-laptop:/home/luis/madwifi-hal-0.10.5.6# 

```

What can I do to solve this problem?


Thanks in advance

---

### Post by lcruz007 on 2008-10-16
bump

---

### Post by lcruz007 on 2008-10-17
Someone knows how to solve this problem?

---

### Post by thomas228 on 2008-11-03
> **lcruz007 said:**
> Hello!
I have been trying to install madwifi, however, when I type make I get some compilation errors. 

```

**...**
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/luis/madwifi-hal-0.10.5.6/ath_hal/uudecode] Error 1
make[2]: *** [/home/luis/madwifi-hal-0.10.5.6/ath_hal] Error 2
make[1]: *** [_module_/home/luis/madwifi-hal-0.10.5.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
root@luis-laptop:/home/luis/madwifi-hal-0.10.5.6# 

```

What can I do to solve this problem?


Thanks in advance

Did you install the packages:

linux-libc-dev and libc6-dev?

They helped me compile my madwifi drivers on Hardy 8.04

Just a guess
Tom

---

### Post by eks on 2008-11-03
Try installing the latest built-in modules of the new kernel. They are on **linux-backports-modules-intrepid**. Just install and activate them on System/Administration/Hardware Drives.

There's some other stuff you can do if you find some problems here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

