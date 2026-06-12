---
title: "hostap drivers injection patch in feisty"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by Softcox on 2007-07-19
Hello,

I'm trying to get the patched hostap drivers working as per the instructions on [this site/]("http://asndotone.blogspot.com/") (click link)

Everything goes fine until this step:

```
make O=../OutputDir outputmakefile[
```

Which gives:

```
x@y:~/HostApInjection/linux-source-2.6.20-2.6.20$ make O=../OutputDir outputmakefile
scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
N*** "make menuconfig" or "make xconfig").
***
make[3]: *** [silentoldconfig] Error 1
make[2]: *** [silentoldconfig] Error 2

```

If I run 
```
make O=../OutputDir oldconfig
```

It seems to run fine

Now, running:
```
make O=../OutputDir outputmakefile
```

Seems to be OK with no errors

Running:
```
make O=../OutputDir archprepare
```

Gives an error about build not being clean and to run make mrproper, so running:

```
make O=../OutputDir mrproper
```

Works fine

Now again running:
```
make O=../OutputDir archprepare
```

Gives an error with
```
GEN     /home/x/HostApInjection/OutputDir/Makefile
scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[3]: *** [silentoldconfig] Error 1
make[2]: *** [silentoldconfig] Error 2
make[1]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make: *** [archprepare] Error 2


```

What do I do next?  Any ideas would be appreciated, thanks!

---

### Post by drjunior on 2007-10-18
I have the same problem... I don't  know what to do now..

---

### Post by waraey on 2007-10-22
why not use my guide on doing it in gutsy

[http://ubuntuforums.org/showthread.php?t=583868](http://ubuntuforums.org/showthread.php?t=583868)

-waraey

---

### Post by waraey on 2007-10-22
The problem here is the .config file is not properly created. first then build 

```
make O=../OutputDir menuconfig 
```

you may need the ncurses libraries installed. save the .config file


> **Softcox said:**
> Hello,

I'm trying to get the patched hostap drivers working as per the instructions on [this site/]("http://asndotone.blogspot.com/") (click link)

Everything goes fine until this step:

```
make O=../OutputDir outputmakefile[
```

Which gives:

```
x@y:~/HostApInjection/linux-source-2.6.20-2.6.20$ make O=../OutputDir outputmakefile
scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
N*** "make menuconfig" or "make xconfig").
***
make[3]: *** [silentoldconfig] Error 1
make[2]: *** [silentoldconfig] Error 2

```

If I run 
```
make O=../OutputDir oldconfig
```

It seems to run fine

Now, running:
```
make O=../OutputDir outputmakefile
```

Seems to be OK with no errors

Running:
```
make O=../OutputDir archprepare
```

Gives an error about build not being clean and to run make mrproper, so running:

```
make O=../OutputDir mrproper
```

Works fine

Now again running:
```
make O=../OutputDir archprepare
```

Gives an error with
```
GEN     /home/x/HostApInjection/OutputDir/Makefile
scripts/kconfig/conf -s arch/i386/Kconfig
***
*** You have not yet configured your kernel!
***
*** Please run some configurator (e.g. "make oldconfig" or
*** "make menuconfig" or "make xconfig").
***
make[3]: *** [silentoldconfig] Error 1
make[2]: *** [silentoldconfig] Error 2
make[1]: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'.  Stop.
make: *** [archprepare] Error 2


```

What do I do next?  Any ideas would be appreciated, thanks!

---

