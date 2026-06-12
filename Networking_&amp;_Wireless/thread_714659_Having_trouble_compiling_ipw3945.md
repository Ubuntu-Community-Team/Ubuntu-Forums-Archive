---
title: "Having trouble compiling ipw3945"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by Starks on 2008-03-04
Before you berate me for even trying on a perfectly functional Gutsy install, I want to make it absolutely clear that I want to enable monitor, promiscuous, and rtap modes on my card. These are not enabled and compiled in by default.

Anyway, I'm stuck at this:

```
Makefile:54: 
Makefile:55: WARNING: $SHELL not set to bash.
Makefile:56: If you experience build errors, try
Makefile:57: 'make SHELL=/bin/bash'.
Makefile:58: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.22-14-generic /lib/modules/2.6.22-14-generic/build

You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1

```

---

### Post by lumiad on 2008-03-04
What linux kernel are you running? I might be able to provide the patches for some ipw3945 versions (though they originate from gentoo)

The problem seems to be some wrong syntax within the makefile

---

### Post by Starks on 2008-03-04
My previous post said I was running the defaul Gutsy kernel: 2.6.22-14

---

### Post by lumiad on 2008-03-04
Sorry I didn't check after lib/modules/.

I started by checking Makefile 58: 
:S


Maybe this might help:

cat ipw3945-1.2.0-Makefile.patch
```

Index: ipw3945-1.2.0/Makefile
===================================================================
--- ipw3945-1.2.0.orig/Makefile
+++ ipw3945-1.2.0/Makefile
@@ -26,20 +26,20 @@ CONFIG_IPW3945_DEBUG=y
 # NOTE:  If you have problems compiling due to IW_MODE_MONITOR not being
 #        defined then you need to update the wireless extension version
 #       installed in your kernel, or comment this line out.
-# CONFIG_IPW3945_MONITOR=y
+CONFIG_IPW3945_MONITOR=y

 # If you are interested in using radiotap headers in monitor mode,
 # simply uncomment:
 #
 # NOTE:  To use RADIOTAP you must also enable MONITOR above.
-# CONFIG_IEEE80211_RADIOTAP=y
+CONFIG_IEEE80211_RADIOTAP=y

 # The above monitor mode provides standard monitor mode.  The following
 # will create a new interface (named raw%d) which will be sent all
 # 802.11 frames received on the interface
 #
 # NOTE:  To use PROMISCUOUS you must also enable MONITOR above.
-# CONFIG_IPW3945_PROMISCUOUS=y
+CONFIG_IPW3945_PROMISCUOUS=y

 # The following, if enabled, will add a sysfs entry 'rx' that raw
 # 802.11 radiotap formatted packets can be written to.  Those packets
@@ -186,34 +186,6 @@ utils:
        @[ ! -d util ] || make -C util IEEE80211_PATH=$(IEEE80211_PATH)

 check_inc:
-       @( [ "$(IEEE80211_DUPLICATE)" ] && echo -e \
-"\n WARNING: Your kernel contains ieee80211 symbol definitions and you\n"\
-"are not using the kernel's default ieee80211 subsystem.  (Perhaps you\n"\
-"used the out-of-tree ieee80211 subsystem's 'make install' or have\n"\
-"provided a path to the ieee80211 subsystem via IEEE80211_INC.)\n\n"\
-"If you wish to use the out-of-tree ieee80211 subsystem then it is\n"\
-"recommended to use that projects' \"make patch_kernel\" facility\n"\
-"and rebuild your kernel to update the Module symbol version information.\n"\
-"\n"\
-"Failure to do this may result in build warnings and unexpected\n"\
-"behavior when running modules which rely on the ieee80211 subsystem.\n\n"\ || \
-       exit 0)
-
-       @( [ "$(IEEE80211_DUPLICATE)" ] && \
-          [ ! "$(IEEE80211_IGNORE_DUPLICATE)" ] && echo -e \
-" Aborting the build.  You can force the build to continue by adding:\n\n"\
-"\tIEEE80211_IGNORE_DUPLICATE=y\n\n"\
-"to your make command line.\n\n" && exit 1 || exit 0)
-
-       @( [ ! "$(IEEE80211_API)" ] && echo -e \
-"\n ERROR: A compatible subsystem was not found in the following path[s]:\n\n"\
-"\t$(IEEE80211_RES)\n\n"\
-"You need to install the ieee80211 subsystem from http://ieee80211.sf.net\n"\
-"and point this build to the location where you installed those sources, eg.:\n\n"\
-"\t% make IEEE80211_INC=/usr/src/ieee80211/\n\n"\
-"or use the 'make patch_kernel' within the ieee80211 subsystem to patch your\n"\
-"kernel sources.\n" && exit 1 || exit 0)
-
        @echo -e \
 " Using ieee80211 subsystem version API v$(IEEE80211_API) from:\n\n" \
 "\tBase: $(IEEE80211_BASE)\n" \

```

---

