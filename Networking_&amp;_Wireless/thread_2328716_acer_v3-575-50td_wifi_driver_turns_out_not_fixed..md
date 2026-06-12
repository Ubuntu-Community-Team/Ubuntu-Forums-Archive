---
title: "acer v3-575-50td wifi driver turns out not fixed."
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by rev-matthewagilmore on 2016-06-23
[thread=2328063]http://ubuntuforums.org/showthread.php?t=2328063[/thread] 
I thought it was solved but it was not. every thing seemed to work fine with  just the .deb. but then I noticed it if i disconnected from  wifi some times it would not let me reconnect  not showing anything. so i when did the shell commands in  ran into errors please help.
```
 matti@matti-Aspire-V3-575:~$ cd backports-20150313bash: cd: backports-20150313: No such file or directory
matti@matti-Aspire-V3-575:~$ ls
backports-20150313.tar.xz  examples.desktop              Public
Desktop                    linux-firmware_1.158_all.deb  Templates
Documents                  Music                         Videos
Downloads                  Pictures                      VirtualBox VMs
matti@matti-Aspire-V3-575:~$ cd backports-20150313
matti@matti-Aspire-V3-575:~/backports-20150313$ make defconfig-ath10k
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
In file included from zconf.tab.c:2503:0:
menu.c: In function &#8216;get_symbol_str&#8217;:
menu.c:561:18: warning: &#8216;jump&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]
     jump->offset = r->len - 1;
                  ^
menu.c:515:19: note: &#8216;jump&#8217; was declared here
  struct jump_key *jump;
                   ^
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
matti@matti-Aspire-V3-575:~/backports-20150313$ make
make[5]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/matti/backports-20150313/compat/main.o
  CC [M]  /home/matti/backports-20150313/compat/lib-average.o
  LD [M]  /home/matti/backports-20150313/compat/compat.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/main.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/regd.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/hw.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/key.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/dfs_pattern_detector.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/dfs_pri_detector.o
  LD [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/mac.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/debug.o
/home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/debug.c: In function &#8216;ath10k_debug_register&#8217;:
/home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/debug.c:2081:9: warning: passing argument 4 of &#8216;debugfs_create_bool&#8217; from incompatible pointer type [-Wincompatible-pointer-types]
         &ar->dfs_block_radar_events);
         ^
In file included from /home/matti/backports-20150313/backport-include/linux/debugfs.h:3:0,
                 from /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/debug.c:19:
include/linux/debugfs.h:96:16: note: expected &#8216;bool * {aka _Bool *}&#8217; but argument is of type &#8216;u32 * {aka unsigned int *}&#8217;
 struct dentry *debugfs_create_bool(const char *name, umode_t mode,
                ^
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/core.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/htc.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/htt.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/htt_rx.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/htt_tx.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/txrx.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/wmi.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/wmi-tlv.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/bmi.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/hw.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/spectral.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/thermal.o
  LD [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/ath10k_core.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/pci.o
  CC [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/ce.o
  LD [M]  /home/matti/backports-20150313/drivers/net/wireless/ath/ath10k/ath10k_pci.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/main.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/status.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/sta_info.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/wep.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/wpa.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/scan.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/offchannel.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/ht.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/agg-tx.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/agg-rx.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/vht.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/ibss.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/iface.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/rate.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/michael.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/tkip.o
  CC [M]  /home/matti/backports-20150313/net/mac80211/aes_ccm.o
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_ccm_encrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:28:28: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct aead_request&#8217;
  char aead_req_data[sizeof(struct aead_request) +
                            ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:29:7: error: implicit declaration of function &#8216;crypto_aead_reqsize&#8217; [-Werror=implicit-function-declaration]
       crypto_aead_reqsize(tfm)]
       ^
In file included from include/linux/compiler.h:56:0,
                 from /home/matti/backports-20150313/backport-include/linux/compiler.h:3,
                 from include/linux/linkage.h:4,
                 from include/linux/kernel.h:6,
                 from /home/matti/backports-20150313/backport-include/linux/kernel.h:3,
                 from /home/matti/backports-20150313/net/mac80211/aes_ccm.c:12:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:30:25: error: invalid application of &#8216;__alignof__&#8217; to incomplete type &#8216;struct aead_request&#8217;
   __aligned(__alignof__(struct aead_request));
                         ^
include/linux/compiler-gcc.h:118:46: note: in definition of macro &#8216;__aligned&#8217;
 #define __aligned(x)  __attribute__((aligned(x)))
                                              ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:41:2: error: implicit declaration of function &#8216;aead_request_set_tfm&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_tfm(aead_req, tfm);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:42:2: error: implicit declaration of function &#8216;aead_request_set_assoc&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_assoc(aead_req, &assoc, assoc.length);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:43:2: error: implicit declaration of function &#8216;aead_request_set_crypt&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_crypt(aead_req, &pt, ct, data_len, b_0);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:45:2: error: implicit declaration of function &#8216;crypto_aead_encrypt&#8217; [-Werror=implicit-function-declaration]
  crypto_aead_encrypt(aead_req);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:28:7: warning: unused variable &#8216;aead_req_data&#8217; [-Wunused-variable]
  char aead_req_data[sizeof(struct aead_request) +
       ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_ccm_decrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:53:28: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct aead_request&#8217;
  char aead_req_data[sizeof(struct aead_request) +
                            ^
In file included from include/linux/compiler.h:56:0,
                 from /home/matti/backports-20150313/backport-include/linux/compiler.h:3,
                 from include/linux/linkage.h:4,
                 from include/linux/kernel.h:6,
                 from /home/matti/backports-20150313/backport-include/linux/kernel.h:3,
                 from /home/matti/backports-20150313/net/mac80211/aes_ccm.c:12:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:55:25: error: invalid application of &#8216;__alignof__&#8217; to incomplete type &#8216;struct aead_request&#8217;
   __aligned(__alignof__(struct aead_request));
                         ^
include/linux/compiler-gcc.h:118:46: note: in definition of macro &#8216;__aligned&#8217;
 #define __aligned(x)  __attribute__((aligned(x)))
                                              ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:73:9: error: implicit declaration of function &#8216;crypto_aead_decrypt&#8217; [-Werror=implicit-function-declaration]
  return crypto_aead_decrypt(aead_req);
         ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:53:7: warning: unused variable &#8216;aead_req_data&#8217; [-Wunused-variable]
  char aead_req_data[sizeof(struct aead_request) +
       ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_key_setup_encrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:83:8: error: implicit declaration of function &#8216;crypto_alloc_aead&#8217; [-Werror=implicit-function-declaration]
  tfm = crypto_alloc_aead("ccm(aes)", 0, CRYPTO_ALG_ASYNC);
        ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:83:6: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  tfm = crypto_alloc_aead("ccm(aes)", 0, CRYPTO_ALG_ASYNC);
      ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:87:8: error: implicit declaration of function &#8216;crypto_aead_setkey&#8217; [-Werror=implicit-function-declaration]
  err = crypto_aead_setkey(tfm, key, key_len);
        ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:89:9: error: implicit declaration of function &#8216;crypto_aead_setauthsize&#8217; [-Werror=implicit-function-declaration]
   err = crypto_aead_setauthsize(tfm, mic_len);
         ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:93:2: error: implicit declaration of function &#8216;crypto_free_aead&#8217; [-Werror=implicit-function-declaration]
  crypto_free_aead(tfm);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/matti/backports-20150313/net/mac80211/aes_ccm.o' failed
make[6]: *** [/home/matti/backports-20150313/net/mac80211/aes_ccm.o] Error 1
scripts/Makefile.build:403: recipe for target '/home/matti/backports-20150313/net/mac80211' failed
make[5]: *** [/home/matti/backports-20150313/net/mac80211] Error 2
Makefile:1402: recipe for target '_module_/home/matti/backports-20150313' failed
make[4]: *** [_module_/home/matti/backports-20150313] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[3]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
matti@matti-Aspire-V3-575:~/backports-20150313$ sudo make install
[sudo] password for matti: 
  CC [M]  /home/matti/backports-20150313/net/mac80211/aes_ccm.o
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_ccm_encrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:28:28: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct aead_request&#8217;
  char aead_req_data[sizeof(struct aead_request) +
                            ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:29:7: error: implicit declaration of function &#8216;crypto_aead_reqsize&#8217; [-Werror=implicit-function-declaration]
       crypto_aead_reqsize(tfm)]
       ^
In file included from include/linux/compiler.h:56:0,
                 from /home/matti/backports-20150313/backport-include/linux/compiler.h:3,
                 from include/linux/linkage.h:4,
                 from include/linux/kernel.h:6,
                 from /home/matti/backports-20150313/backport-include/linux/kernel.h:3,
                 from /home/matti/backports-20150313/net/mac80211/aes_ccm.c:12:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:30:25: error: invalid application of &#8216;__alignof__&#8217; to incomplete type &#8216;struct aead_request&#8217;
   __aligned(__alignof__(struct aead_request));
                         ^
include/linux/compiler-gcc.h:118:46: note: in definition of macro &#8216;__aligned&#8217;
 #define __aligned(x)  __attribute__((aligned(x)))
                                              ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:41:2: error: implicit declaration of function &#8216;aead_request_set_tfm&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_tfm(aead_req, tfm);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:42:2: error: implicit declaration of function &#8216;aead_request_set_assoc&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_assoc(aead_req, &assoc, assoc.length);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:43:2: error: implicit declaration of function &#8216;aead_request_set_crypt&#8217; [-Werror=implicit-function-declaration]
  aead_request_set_crypt(aead_req, &pt, ct, data_len, b_0);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:45:2: error: implicit declaration of function &#8216;crypto_aead_encrypt&#8217; [-Werror=implicit-function-declaration]
  crypto_aead_encrypt(aead_req);
  ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:28:7: warning: unused variable &#8216;aead_req_data&#8217; [-Wunused-variable]
  char aead_req_data[sizeof(struct aead_request) +
       ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_ccm_decrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:53:28: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct aead_request&#8217;
  char aead_req_data[sizeof(struct aead_request) +
                            ^
In file included from include/linux/compiler.h:56:0,
                 from /home/matti/backports-20150313/backport-include/linux/compiler.h:3,
                 from include/linux/linkage.h:4,
                 from include/linux/kernel.h:6,
                 from /home/matti/backports-20150313/backport-include/linux/kernel.h:3,
                 from /home/matti/backports-20150313/net/mac80211/aes_ccm.c:12:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:55:25: error: invalid application of &#8216;__alignof__&#8217; to incomplete type &#8216;struct aead_request&#8217;
   __aligned(__alignof__(struct aead_request));
                         ^
include/linux/compiler-gcc.h:118:46: note: in definition of macro &#8216;__aligned&#8217;
 #define __aligned(x)  __attribute__((aligned(x)))
                                              ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:73:9: error: implicit declaration of function &#8216;crypto_aead_decrypt&#8217; [-Werror=implicit-function-declaration]
  return crypto_aead_decrypt(aead_req);
         ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:53:7: warning: unused variable &#8216;aead_req_data&#8217; [-Wunused-variable]
  char aead_req_data[sizeof(struct aead_request) +
       ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c: In function &#8216;ieee80211_aes_key_setup_encrypt&#8217;:
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:83:8: error: implicit declaration of function &#8216;crypto_alloc_aead&#8217; [-Werror=implicit-function-declaration]
  tfm = crypto_alloc_aead("ccm(aes)", 0, CRYPTO_ALG_ASYNC);
        ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:83:6: warning: assignment makes pointer from integer without a cast [-Wint-conversion]
  tfm = crypto_alloc_aead("ccm(aes)", 0, CRYPTO_ALG_ASYNC);
      ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:87:8: error: implicit declaration of function &#8216;crypto_aead_setkey&#8217; [-Werror=implicit-function-declaration]
  err = crypto_aead_setkey(tfm, key, key_len);
        ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:89:9: error: implicit declaration of function &#8216;crypto_aead_setauthsize&#8217; [-Werror=implicit-function-declaration]
   err = crypto_aead_setauthsize(tfm, mic_len);
         ^
/home/matti/backports-20150313/net/mac80211/aes_ccm.c:93:2: error: implicit declaration of function &#8216;crypto_free_aead&#8217; [-Werror=implicit-function-declaration]
  crypto_free_aead(tfm);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/matti/backports-20150313/net/mac80211/aes_ccm.o' failed
make[5]: *** [/home/matti/backports-20150313/net/mac80211/aes_ccm.o] Error 1
scripts/Makefile.build:403: recipe for target '/home/matti/backports-20150313/net/mac80211' failed
make[4]: *** [/home/matti/backports-20150313/net/mac80211] Error 2
Makefile:1402: recipe for target '_module_/home/matti/backports-20150313' failed
make[3]: *** [_module_/home/matti/backports-20150313] Error 2
Makefile.build:6: recipe for target 'modules' failed
make[2]: *** [modules] Error 2
Makefile.real:88: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:40: recipe for target 'install' failed
make: *** [install] Error 2

```

---

### Post by howefield on 2016-06-23
Moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by jeremy31 on 2016-06-23
Try this for that wireless
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb

sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make
sudo make install
```

Reboot

---

### Post by rev-matthewagilmore on 2016-07-02
works  so  fare  says its instilled let you know if problem is solved in  a few days need to test drive it  because last time i thought it was  solved

---

### Post by jeremy31 on 2016-07-02
It will work until the next kernel update then just
```
cd backports-4.4.2-1
make clean
make defconfig-wifi
make
sudo make install
```

Reboot

---

### Post by rev-matthewagilmore on 2016-07-05
what  does -zxvf  do

---

### Post by X-RED_Tech on 2016-07-05
> **rev-matthewagilmore said:**
> what  does -zxvf  do

[http://www.linuxcommand.org/man_pages/tar1.html](http://www.linuxcommand.org/man_pages/tar1.html)

---

