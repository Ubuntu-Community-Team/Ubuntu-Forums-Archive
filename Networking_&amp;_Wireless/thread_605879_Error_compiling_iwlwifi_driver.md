---
title: "Error compiling iwlwifi driver"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by info2 on 2007-11-07
Hi,

I am using kernel 2.6.24 rc2.

With this kernel the ieee802 subsystem and the new intel iwlwifi drivers are included and working (ok - not very well)

Now I want to compile the newest drivers which are not yet included within the kernel   (kernel has 1.1.17, newest is 1.1.21) 

I get the following error:

```

fallen@beowulf:~/Desktop/iwlwifi-1.1.21$ make SHELL=/bin/bash
make -C /lib/modules/2.6.24-rc2/source O=/lib/modules/2.6.24-rc2/build M=/home/fallen/Desktop/iwlwifi-1.1.21/compatible/ EXTRA_CFLAGS="-DCONFIG_IWLWIFI_DEBUG=y -DCONFIG_IWLWIFI_SPECTRUM_MEASUREMENT=y -DCONFIG_IWLWIFI_SENSITIVITY=y -DCONFIG_IWLWIFI_QOS=y" modules
make[1]: Betrete Verzeichnis '/usr/src/linux-source-2.6.24-rc2'
Makefile:119: *** Output directory (O=...) specifies kernel src dir.  Schluss.
make[1]: Verlasse Verzeichnis '/usr/src/linux-source-2.6.24-rc2'
make: *** [modules] Fehler 2

```

Nice error, isnt it? And very informative... good to know that O= specifies the kernel source dir. 

#sarcasm off#

But the directory is ok I think:

```

fallen@beowulf:~/Desktop/iwlwifi-1.1.21$ ls -Al /usr/src/linux-source-2.6.24-rc2

lrwxrwxrwx 1 root root     32 2007-11-07 12:56 build -> /usr/src/linux-source-2.6.24-rc2
...
lrwxrwxrwx 1 root root     32 2007-11-07 12:56 source -> /usr/src/linux-source-2.6.24-rc2

```

I don't know whats wrong with that. 
I hope you can help me.

Thanks in advance.

---

### Post by Lambert on 2007-11-07
you mention iee802 but the iwlwifi driver is built for the new mac80211 wireless stack. Just want to make sure you're aware of that.

Try to specify the path to kernel.

```

make KSRC=/path/to/kernel

```

---

### Post by info2 on 2007-11-08
Thank you, you are right, mac80211 , thats what I wanted to write. I'm sorry.  :)

But that error still occurs even if there is some more output now:

```

fallen@beowulf:~/Desktop/iwlwifi-1.1.21$ make SHELL=/bin/bash KSRC=/usr/src/linux-source-2.6.24-rc2
Checking kernel compatibility in:
        /usr/src/linux-source-2.6.24-rc2
 * Kernel requires compatibility version:
   - Requires IEEE80211_CONF_CHANNEL_SWITCH compat.
   - Remove CONFIG_IWLWIFI_HT option if defined
   - Remove CONFIG_IWLWIFI_HT_AGG option if defined
Building compatibility version in 'compatible/' directory:
Copying compatible/ from origin/...done
 + Applying: patches/06-csa.patch
        diff -urp old/iwl-helpers.h origin/iwl-helpers.h
make -C /usr/src/linux-source-2.6.24-rc2 O=/usr/src/linux-source-2.6.24-rc2 M=/home/fallen/Desktop/iwlwifi-1.1.21/compatible/ EXTRA_CFLAGS="-DCONFIG_IWLWIFI_DEBUG=y -DCONFIG_IWLWIFI_SPECTRUM_MEASUREMENT=y -DCONFIG_IWLWIFI_SENSITIVITY=y -DCONFIG_IWLWIFI_QOS=y" modules
make[1]: Betrete Verzeichnis '/usr/src/linux-source-2.6.24-rc2'
Makefile:119: *** Output directory (O=...) specifies kernel src dir.  Schluss.
make[1]: Verlasse Verzeichnis '/usr/src/linux-source-2.6.24-rc2'
make: *** [modules] Fehler 2


```

---

### Post by kevdog on 2007-11-08
Are you certain you dont have to recompile the kernel with certain options selected:

 * Kernel requires compatibility version:
   - Requires IEEE80211_CONF_CHANNEL_SWITCH compat.
   - Remove CONFIG_IWLWIFI_HT option if defined
   - Remove CONFIG_IWLWIFI_HT_AGG option if defined

When compiling the kernel there is a configuaration process prior to compiling, that you can select various options for your kernel (there are like 1000 options).  Anyway it would seem that these options would have to either selected/deselected based on the output you gave

---

### Post by info2 on 2007-11-08
Thank you for the answear.

But the problem I can not solve is this one:

Makefile:119: *** Output directory (O=...) specifies kernel src dir.  Schluss.

---

### Post by Lambert on 2007-11-08
You are running make as a normal user it looks like.

> 
$ make


Try running your command with sudo in front of it

```

sudo make

```

The make file explains this output as...

> 
# Check that OUTPUT directory is not the same as where we have kernel src


I'm not sure if it has to do with file permissions with root/sudo user or an output directory other then source needs to be specified.

---

### Post by info2 on 2007-11-08
Hey Lambert,

your last hint solved the problem.

I forced the KSRC_OUTPUT to point to somewhere else and now it is working.
Nevermind, thanks a lot.
Strange that the Makefile didn't recognized it.

---

