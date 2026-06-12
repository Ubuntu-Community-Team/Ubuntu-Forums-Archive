---
title: "Speedtouch 110 Installation"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Chianti on 2008-08-31
Hello everybody.:)

I tried to install a Speedtouch 110 PCMCIA card to an old Thinkpad after installing Hardy and updating it. Since I'm not an experienced user I searched the forum/google for information and I only found this thread:

[http://ubuntuforums.org/showthread.php?t=45311]("http://ubuntuforums.org/showthread.php?t=45311")

which redirects me to the french forum where a guy posted a script which sould do the job. The script seems outdated and it did't work. So I tried to do each pass manually. Here is waht I did:

```

sudo apt-get update

sudo apt-get -y install build-essential linux-source

cd /usr/src/

sudo tar -xvf ./linux-source-2.6.24.tar.bz2

sudo ln -s ./linux-source-2.6.24 ./linux

cd linux

sudo make oldconfig

sudo make modules_prepare

sudo TEMPDIR=speedtouch-$(date +%H%M%S)

sudo mkdir /tmp/$TEMPDIR

cd /tmp/$TEMPDIR

sudo wget http://www.xs4all.nl/~pptp/agere/wlags49.tar.bz2

sudo tar -xvjf ./wlags49.tar.bz2

cd wlags49 
```

Until this point everything seemed perfect! But when I do:

```

sudo ./Build

```

I get this:

```
make: Entering directory `/usr/src/linux-source-2.6.24'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.24/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      /tmp/wlags49/built-in.o
  CC [M]  /tmp/wlags49/wl_profile.o
  CC [M]  /tmp/wlags49/wl_sysfs.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_sysfs.c:15:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
/tmp/wlags49/wl_sysfs.c: In function \u2018show_tallies\u2019:
/tmp/wlags49/wl_sysfs.c:40: warning: initialization from incompatible pointer type
/tmp/wlags49/wl_sysfs.c: In function \u2018register_wlags_sysfs\u2019:
/tmp/wlags49/wl_sysfs.c:124: warning: unused variable \u2018lp\u2019
/tmp/wlags49/wl_sysfs.c: In function \u2018unregister_wlags_sysfs\u2019:
/tmp/wlags49/wl_sysfs.c:132: warning: unused variable \u2018lp\u2019
/tmp/wlags49/wl_sysfs.c: At top level:
/tmp/wlags49/wl_sysfs.c:116: warning: \u2018wlags_group\u2019 defined but not used
  CC [M]  /tmp/wlags49/wl_priv.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_priv.c:90:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
  CC [M]  /tmp/wlags49/wl_main.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_main.c:112:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
/tmp/wlags49/wl_main.c: In function \u2018wl_insert\u2019:
/tmp/wlags49/wl_main.c:1115: warning: comparison is always true due to limited range of data type
/tmp/wlags49/wl_main.c: In function \u2018wl_process_mailbox\u2019:
/tmp/wlags49/wl_main.c:4016: warning: unused variable \u2018lt_rsp\u2019
  CC [M]  /tmp/wlags49/wl_enc.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_enc.c:84:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
  CC [M]  /tmp/wlags49/wl_util.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_util.c:105:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
  CC [M]  /tmp/wlags49/wl_netdev.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_netdev.c:111:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
/tmp/wlags49/wl_netdev.c: In function \u2018wl_init\u2019:
/tmp/wlags49/wl_netdev.c:169: warning: unused variable \u2018lp\u2019
/tmp/wlags49/wl_netdev.c:168: warning: unused variable \u2018flags\u2019
/tmp/wlags49/wl_netdev.c: In function \u2018wl_device_dealloc\u2019:
/tmp/wlags49/wl_netdev.c:1390: warning: unused variable \u2018lp\u2019
  CC [M]  /tmp/wlags49/wl_cs.o
In file included from /tmp/wlags49/hcf.h:81,
                 from /tmp/wlags49/wl_cs.c:115:
/tmp/wlags49/include/hcf/hcfcfg.h:786:5: warning: "_BLDTYPE" is not defined
/tmp/wlags49/wl_cs.c: In function \u2018wl_adapter_insert\u2019:
/tmp/wlags49/wl_cs.c:332: error: implicit declaration of function \u2018SET_MODULE_OWNER\u2019
make[1]: *** [/tmp/wlags49/wl_cs.o] Error 1
make: *** [_module_/tmp/wlags49] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.24'
```


If I continue:

```
sudo mkdir /lib/modules/$(uname -r)/extra/

sudo cp ./wlags49_h2_cs.ko /lib/modules/$(uname -r)/extra/
```

it tells me that the file **wlags_h2_cs.ko** does not exist...


What I'm doing wrong???:confused:


Thanks in advance...

---

### Post by Chianti on 2008-08-31
OK, it seems that the previous solution works only on older kernel. I found another solution here:

[http://huitsix13.free.fr/new.php?new=12]("http://huitsix13.free.fr/new.php?new=12")

which made my card work.

---

