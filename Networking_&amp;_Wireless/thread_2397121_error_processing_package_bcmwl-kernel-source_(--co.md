---
title: "error processing package bcmwl-kernel-source (--configure):  subprocess installed pos"
date: 2018-07-25
forum: Networking &amp; Wireless
---

### Post by saurabhgangurde on 2018-07-25
while installing bcmwl-kernel-source I'm getting following error

```
##################################################################################
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-29-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
dpkg: error processing package bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
##########################################################################################

Please help. I'm also attaching corresponding logs.


Logs:
###########################################################################################################################
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.15.0-29-generic (x86_64)
Thu Jul 26 02:21:31 IST 2018
make: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c: In function &#8216;osl_os_get_image_block&#8217;:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:26: warning: passing argument 2 of &#8216;kernel_read&#8217; makes pointer from integer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                          ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected &#8216;void *&#8217; but argument is of type &#8216;loff_t {aka long long int}&#8217;
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:37: warning: passing argument 3 of &#8216;kernel_read&#8217; makes integer from pointer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                                     ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected &#8216;size_t {aka long unsigned int}&#8217; but argument is of type &#8216;char *&#8217;
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:42: warning: passing argument 4 of &#8216;kernel_read&#8217; makes pointer from integer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                                          ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected &#8216;loff_t * {aka long long int *}&#8217; but argument is of type &#8216;int&#8217;
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function &#8216;wl_init_timer&#8217;:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2359:2: error: implicit declaration of function &#8216;init_timer&#8217; [-Werror=implicit-function-declaration]
  init_timer(&t->timer);
  ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2360:10: error: &#8216;struct timer_list&#8217; has no member named &#8216;data&#8217;
  t->timer.data = (ulong) t;
          ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2361:20: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
  t->timer.function = wl_timer;
                    ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o' failed
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o] Error 1
Makefile:1552: recipe for target '_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build' failed
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'

################################################################################################################################################
```

---

### Post by chili555 on 2018-07-25
Please see post #2 here: [https://ubuntuforums.org/showthread.php?t=2397051](https://ubuntuforums.org/showthread.php?t=2397051)

---

### Post by saurabhgangurde on 2018-07-26
Thanks.. It worked.

---

