---
title: "please help me install SoftMAC"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by ravitejac on 2008-01-19
Hello,
   I'm a newbie to linux and I need to get the SoftMAC up. I've freshly installed Ubuntu 7.10 Gutsy and here is output of uname -a

wing@laptop1:~/softmac/trunk$ uname -a
Linux laptop1 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

On following the instructions given at [https://systems.cs.colorado.edu/projects/softmac](https://systems.cs.colorado.edu/projects/softmac),

I've attempted to 'make'.

Here is the error, the reason to which I'm not able to find out. Please help me out.



wing@laptop1:~/softmac/trunk$ make
Makefile:17: WARNING: KERNELSOURCE undefined, using /usr/src/linux
for dir in cheesymac core linux_netif mactime madwifi_bsd_phy multimac nullmac rawmac remotemac remotemac/ktund fec formage; do \
                (cd $dir; make all) || exit 1; \
        done
make[1]: Entering directory `/home/wing/softmac/trunk/cheesymac'
make -C /usr/src/linux SUBDIRS=/home/wing/softmac/trunk/cheesymac modules
make[2]: Entering directory `/usr/src/linux-source-2.6.22'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: vmlinux(.text+0xc010116f): Section mismatch: reference to .init.text:start_kernel (between 'is386' and 'check_x87')
WARNING: vmlinux(.text+0xc02f3718): Section mismatch: reference to .init.text: (between 'rest_init' and 'alloc_node_mem_map')
WARNING: vmlinux(.text+0xc010d8bb): Section mismatch: reference to .init.text:trap_init_f00f_bug (between 'init_intel' and 'cmpxchg_386_u32')
WARNING: vmlinux(.text+0xc02f8fca): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fd6): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fe2): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fee): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f37e0): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'alloc_node_mem_map' and 'zone_wait_table_init')
WARNING: vmlinux(.text+0xc02f3870): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'zone_wait_table_init' and '__sched_text_start')
WARNING: vmlinux(.text+0xc02f939c): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: "cu_softmac_netif_rx_packet" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_netif_set_unload_callback" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_netif_from_dev" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_macinfo_free" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_macinfo_register" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_netif_create_eth" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_phyinfo_alloc" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_ath_set_tx_bitrate" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_netif_detach" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_layer_register" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_macinfo_alloc" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_phyinfo_free" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_phyinfo_get" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_layer_unregister" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_netif_set_tx_callback" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
WARNING: "cu_softmac_ath_set_default_phy_props" [/home/wing/softmac/trunk/cheesymac/softmac_cheesymac.ko] undefined!
make[2]: Leaving directory `/usr/src/linux-source-2.6.22'
make[1]: Leaving directory `/home/wing/softmac/trunk/cheesymac'
make[1]: Entering directory `/home/wing/softmac/trunk/core'
make -C /usr/src/linux SUBDIRS=/home/wing/softmac/trunk/core modules
make[2]: Entering directory `/usr/src/linux-source-2.6.22'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: vmlinux(.text+0xc010116f): Section mismatch: reference to .init.text:start_kernel (between 'is386' and 'check_x87')
WARNING: vmlinux(.text+0xc02f3718): Section mismatch: reference to .init.text: (between 'rest_init' and 'alloc_node_mem_map')
WARNING: vmlinux(.text+0xc010d8bb): Section mismatch: reference to .init.text:trap_init_f00f_bug (between 'init_intel' and 'cmpxchg_386_u32')
WARNING: vmlinux(.text+0xc02f8fca): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fd6): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fe2): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f8fee): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
WARNING: vmlinux(.text+0xc02f37e0): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'alloc_node_mem_map' and 'zone_wait_table_init')
WARNING: vmlinux(.text+0xc02f3870): Section mismatch: reference to .init.text:__alloc_bootmem_node (between 'zone_wait_table_init' and '__sched_text_start')
WARNING: vmlinux(.text+0xc02f939c): Section mismatch: reference to .init.text: (between 'iret_exc' and '_etext')
make[2]: Leaving directory `/usr/src/linux-source-2.6.22'
make[1]: Leaving directory `/home/wing/softmac/trunk/core'
make[1]: Entering directory `/home/wing/softmac/trunk/linux_netif'
make -C /usr/src/linux SUBDIRS=/home/wing/softmac/trunk/linux_netif modules
make[2]: Entering directory `/usr/src/linux-source-2.6.22'
  CC [M]  /home/wing/softmac/trunk/linux_netif/softmac_netif.o
/home/wing/softmac/trunk/linux_netif/softmac_netif.c: In function ‘softmac_netif_cleanup_instance’:
/home/wing/softmac/trunk/linux_netif/softmac_netif.c:255: error: void value not ignored as it ought to be
/home/wing/softmac/trunk/linux_netif/softmac_netif.c: In function ‘cu_softmac_netif_rx_packet’:
/home/wing/softmac/trunk/linux_netif/softmac_netif.c:285: error: ‘struct sk_buff’ has no member named ‘mac’
/home/wing/softmac/trunk/linux_netif/softmac_netif.c: In function ‘softmac_netif_exit’:
/home/wing/softmac/trunk/linux_netif/softmac_netif.c:469: warning: ISO C90 forbids mixed declarations and code
make[3]: *** [/home/wing/softmac/trunk/linux_netif/softmac_netif.o] Error 1
make[2]: *** [_module_/home/wing/softmac/trunk/linux_netif] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.22'
make[1]: *** [linux_modules] Error 2
make[1]: Leaving directory `/home/wing/softmac/trunk/linux_netif'
make: *** [all] Error 1
wing@laptop1:~/softmac/trunk$ 


Help me out, please, brothers.
I've tried several different stuff including compiling a kernel but didn't work and now I'm here back to square one with a fresh installation of linux.

---

### Post by peabody on 2008-01-19
could be a build dependency issue, could be that you need the linux-headers package installed for your kernel.  Could be you haven't configured the source package to build properly.  I've never installed the softmac drivers myself.

I'm interested in why you're doing this.  Is it to get your wireless adapter working?  I've been curious about the code myself.  If this doesn't work out for you, there may be other ways to get your wireless adapter working...

---

### Post by ravitejac on 2008-01-19
Actually I'm working a project where I need to modify the MAC protocols. That is why I want SoftMAC. 

Can you tell me how to check the problems you've mentioned?

---

### Post by peabody on 2008-01-20
I would simply make sure that the linux-headers package is installed.  If it isn't, install it, but if it is, you may have to do what the README file suggests and use a 2.6.11 kernel.

---

