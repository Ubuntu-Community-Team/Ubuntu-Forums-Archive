---
title: "Makefile driver error"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by manudo on 2013-12-20
Ok, here's the deal, I've using Ubuntu 12.04 LTS and always installed the Wireless driver with no problem, can make file, run modules, everything's fine.
Now I've updated to Ubuntu 13.10 and gives an error with the "make" command, tried different directories but it's the same.
Tried to install build-essentials linux-headers-generic, gcc, g++.
Still the same, any help?

Trying to install [this driver]("http://www.broadcom.com/support/802.11/linux_sta.php").
Here's the [installation manual]("http://www.broadcom.com/docs/linux_sta/README.txt"), followed it all and still giving error.

Here's the prompt when running the "make clean" command:
```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
make[1]: *** No rule to make target `driver/hybrid_wl'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [clean] Error 2

```

An here's for the "make" command:

```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/carmona/hybrid_wl/built-in.o
  CC [M]  /home/carmona/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/carmona/hybrid_wl/src/wl/sys/wl_linux.o
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_reg_proc_entry’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:2: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:22: warning: assignment makes pointer from integer without a cast [enabled by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;
                ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->write_proc = wl_proc_write;
                ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->data = wl;
                ^
cc1: some warnings being treated as errors
make[2]: *** [/home/carmona/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/carmona/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [all] Error 2

```

Thanks in advance! :)

---

### Post by manudo on 2013-12-20
Ok, here's the deal, I've using Ubuntu 12.04 LTS and always installed  the Wireless driver with no problem, can make file, run modules,  everything's fine.
Now I've updated to Ubuntu 13.10 and gives an error with the "make" command, tried different directories but it's the same.
Tried to install build-essentials linux-headers-generic, gcc, g++.
Still the same, any help?

Trying to install [this driver]("http://www.broadcom.com/support/802.11/linux_sta.php").
Here's the [installation manual]("http://www.broadcom.com/docs/linux_sta/README.txt"), followed it all and still giving error.

Here's the prompt when running the "make clean" command:
```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
make[1]: *** No rule to make target `driver/hybrid_wl'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [clean] Error 2

```

An here's for the "make" command:

```

KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/carmona/hybrid_wl/built-in.o
  CC [M]  /home/carmona/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/carmona/hybrid_wl/src/wl/sys/wl_linux.o
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7:  warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from  incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4:  warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from  incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_reg_proc_entry’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:2:  error: implicit declaration of function ‘create_proc_entry’  [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:22:  warning: assignment makes pointer from integer without a cast [enabled  by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;
                ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->write_proc = wl_proc_write;
                ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->data = wl;
                ^
cc1: some warnings being treated as errors
make[2]: *** [/home/carmona/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/carmona/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [all] Error 2

```

Thanks in advance! :smile:

---

### Post by mörgæs on 2013-12-20
Please stop multiposting.
Merged.

---

### Post by chili555 on 2013-12-21
These kind of errors:> /home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7:  warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from  incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3246:7: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4:  warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from  incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3249:4: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_reg_proc_entry’:
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:2:  error: implicit declaration of function ‘create_proc_entry’  [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3470:22:  warning: assignment makes pointer from integer without a cast [enabled  by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/home/carmona/hybrid_wl/src/wl/sys/wl_linux.c:3475:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;...generally indicate that the file is not quite suitable for the kernel, gcc version, etc., in Ubuntu 13.10.

I suggest you simply install the version that *is* customized for 13.10:```
sudo apt-get install bcmwl-kernel-source
```Broadcom provides a one-size-maybe-fits-all package that works with most but not all Linux distributions, gcc versions, etc. Welcome to 'not all!'

---

### Post by manudo on 2013-12-23
> **chili555 said:**
> These kind of errors:...generally indicate that the file is not quite suitable for the kernel, gcc version, etc., in Ubuntu 13.10.

I suggest you simply install the version that *is* customized for 13.10:```
sudo apt-get install bcmwl-kernel-source
```Broadcom provides a one-size-maybe-fits-all package that works with most but not all Linux distributions, gcc versions, etc. Welcome to 'not all!'

Simply wow, dude! You're awesome! I just have to install that package to make wireless work?
Without all the make clean, make, modprobe method?

---

### Post by chili555 on 2013-12-23
> **manudo said:**
> Simply wow, dude! You're awesome! I just have to install that package to make wireless work?
Without all the make clean, make, modprobe method?Yessir! Exactly.

---

