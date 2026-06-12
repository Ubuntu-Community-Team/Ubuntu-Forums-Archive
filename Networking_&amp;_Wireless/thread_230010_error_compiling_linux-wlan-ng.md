---
title: "error compiling linux-wlan-ng"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by zjcim on 2006-08-05
```
Configuration successful.  Now type 'make' and pray.

joey@ubuntu:~/linux-wlan-ng-0.2.3$ make
set -e; for d in src doc man etc; do make -C $d ; done
make[1]: Entering directory `/home/joey/linux-wlan-ng-0.2.3/src'
set -e; for d in mkmeta p80211 prism2 shared wlanctl wland nwepgen wlancfg; do make WLAN_SRC=/home/joey/linux-wlan-ng-0.2.3/src/ -C $d ; done
make[2]: Entering directory `/home/joey/linux-wlan-ng-0.2.3/src/mkmeta'
gccgcc -E -M -I../include -I/usr/src/linux-headers-2.6.15-26-386/include -D__LINUX_WLAN__ ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetadef.c ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetastruct.c > .depend
/bin/sh: gccgcc: command not found
make[2]: *** [.depend] &#38169;&#35823; 127
make[2]: Leaving directory `/home/joey/linux-wlan-ng-0.2.3/src/mkmeta'
make[1]: *** [all] &#38169;&#35823; 2
make[1]: Leaving directory `/home/joey/linux-wlan-ng-0.2.3/src'
make: *** [all] &#38169;&#35823; 2
joey@ubuntu:~/linux-wlan-ng-0.2.3$ gcc
gcc: &#27809;&#26377;&#36755;&#20837;&#25991;&#20214;
joey@ubuntu:~/linux-wlan-ng-0.2.3$
```

console say:gccgcc :command not found
 but i do have installed the gcc 
i have no idea why it is double "gcc"

---

### Post by philippe_carlo on 2006-08-05
That's a bug in the makefile. Look for $(CC)$(CC) or something similar. Also try this prior to compiling:
```

export CC=gcc
export GCC=gcc

```

---

### Post by zjcim on 2006-08-05
thx for reply
I try your ways,but still don't work
after export CC=gcc
      export GCC=gcc,
error come up again ,same  before

the following is Makefile```
joey@ubuntu:~/linux-wlan-ng-0.2.3$ cat Makefile
# Makefile
#
# Copyright (C) 1999 AbsoluteValue Systems, Inc.  All Rights Reserved.
# --------------------------------------------------------------------
#
# linux-wlan
#
#   The contents of this file are subject to the Mozilla Public
#   License Version 1.1 (the "License"); you may not use this file
#   except in compliance with the License. You may obtain a copy of
#   the License at http://www.mozilla.org/MPL/
#
#   Software distributed under the License is distributed on an "AS
#   IS" basis, WITHOUT WARRANTY OF ANY KIND, either express or
#   implied. See the License for the specific language governing
#   rights and limitations under the License.
#
#   Alternatively, the contents of this file may be used under the
#   terms of the GNU Public License version 2 (the "GPL"), in which
#   case the provisions of the GPL are applicable instead of the
#   above.  If you wish to allow the use of your version of this file
#   only under the terms of the GPL and not to allow others to use
#   your version of this file under the MPL, indicate your decision
#   by deleting the provisions above and replace them with the notice
#   and other provisions required by the GPL.  If you do not delete
#   the provisions above, a recipient may use your version of this
#   file under either the MPL or the GPL.
#
# --------------------------------------------------------------------
#
# Inquiries regarding the linux-wlan Open Source project can be
# made directly to:
#
# AbsoluteValue Systems Inc.
# info@linux-wlan.com
# http://www.linux-wlan.com
#
# --------------------------------------------------------------------
#
# Portions of the development of this software were funded by
# Intersil Corporation as part of PRISM(R) chipset product development.
#
# --------------------------------------------------------------------


DIRS = src doc man etc

CTAGOPTS = --totals -I '__initdata,__exitdata,EXPORT_SYMBOL,EXPORT_SYMBOL_NOVERS'
ETAGS=etags
ETAGSOPTS=-a


default: all

help:
        @echo "Pick one of the following targets:"
        @echo -e "\tmake config\t\t- interactive configure"
        @echo -e "\tmake auto_config\t- automated configure"
        @echo -e "\tmake default_config\t- automated configure using default config file"
        @echo -e "\tmake all\t\t- build modules and programs"
        @echo -e "\tmake install\t\t- install modules and programs"
        @echo -e "\tmake clean\t\t- remove old binaries and dependency files"
        @echo -e "\tmake mrproper\t\t- 'make clean' + remove config file"
        @echo -e "\tmake tags\t\t- generate ctag files for source code"
        @echo -e "\tmake TAGS\t\t- generate etag files for source code"
        @echo " "

help_noconfig:
        @echo "You need to configure the source first"
        @echo "Pick one of the following targets:"
        @echo -e "\tmake config\t\t- interactive configure"
        @echo -e "\tmake auto_config\t- automated configure"
        @echo -e "\tmake default_config\t- automated configure using default config file"
        @echo -e "\tmake help\t\t- show information about other targets"

all:    config.mk
        set -e; for d in $(DIRS); do $(MAKE) -C $$d ; done

mrproper: clean
        rm -f config.out
        rm -f tags.linux tags TAGS

clean:
        set -e; for d in $(DIRS); do $(MAKE) -C $$d clean ; done
        rm -f core core.* *.o .*.o *.s *.a .depend tmp_make *~ tags
        for i in *_obj; do if [ -d $$i ]; then rm -fr $$i; fi; done
        rm -f config.mk config.new
        rm -f src/include/wlan/version.h

install:
        find . -name .depend -exec rm {} \;
        set -e; for d in $(DIRS); do $(MAKE) -C $$d install ; done

auto_config:
        @touch config.mk config.new
        @rm -f config.mk config.new
        @./Configure -d

default_config:
        @touch config.mk config.new
        @rm -f config.mk config.new
        @./Configure -d ./default.config

config:
        @touch config.mk
        @./Configure

config.mk: config.out
        $(MAKE) auto_config

config.out:
        @$(MAKE) help_noconfig
        @exit 1

tags: tags.linux dummy
        if [ -r tags.linux ]; then cp tags.linux tags; fi
        find . \
                -name '*.[ch]' -o \
                -name '*.mk' -o \
                -iname 'Makefile' | \
                xargs ctags -a $(CTAGOPTS)

tags.linux:
        if [ -h linux ]; then \
                find linux/include \
                        -type d \( -name 'asm-*' -o -name config \) \
                        -prune -o \
                        -name '*.h' -print | \
                        xargs ctags -a -f $@ $(CTAGOPTS) && \
                find linux/kernel linux/drivers linux/mm linux/fs \
                        linux/net linux/ipc linux/lib linux/init \
                        -name '*.[ch]' | \
                        xargs ctags -a -f $@ $(CTAGOPTS); \
        fi

TAGS: dummy
        rm -f TAGS
#       if [ -h linux ]; then cp linux/TAGS TAGS; fi
        { find . -name '*.[ch]' -print ; \
          find . -name '*.[ch]' -print ; \
          find . -name '*.mk' -print ; \
          find . -iname 'Makefile' -print ; } | $(ETAGS) - $(ETAGSOPTS)

dummy:

```

serch gcc,seems no problem
```
joey@ubuntu:~/linux-wlan-ng-0.2.3$ grep gcc *.*
config.mk:HOST_COMPILE=gcc
config.mk:HOST_CC=$(HOST_COMPILE)gcc
config.mk:CC=$(HOST_COMPILE)gcc
config.out:HOST_COMPILE="gcc"
config.out:HOST_CC=$(HOST_COMPILE)gcc
config.out:CC=$(HOST_COMPILE)gcc

```

---

### Post by tormod on 2006-08-29
Did you get the sources from the linux-wlan-ng-source (0.2.3-1ubuntu7) [universe] package?

---

