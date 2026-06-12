---
title: "POWERLINK configuration problem"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by andrea-miclausig on 2018-08-30
Hi everybody! So, for my job I need to setup a powerlink test network. To get confident and since we don't have a Linux machine at work, I'm working on a Ubuntu VM in VirtualBox. I know the whole concept of timing goes away, but I'm just trying to get confident. Anyway, while trying to compile the kernel for the network card I get the following errors. Since I'm quite new to compiling and things like that, I have no idea where to start from. Any help is appreciated.

Thank you!

```
andrea@andrea-VirtualBox:~/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build$ cmake -DCFG_OPLK_MN=TRUE -DCFG_POWERLINK_EDRV_82573=TRUE ..
-- The C compiler identification is GNU 7.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- CMAKE_SYSTEM_NAME is Linux
-- CMAKE_SYSTEM_PROCESSOR is x86_64
-- Configuring done
-- Generating done
-- Build files have been written to: /home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build

andrea@andrea-VirtualBox:~/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build$ make
Scanning dependencies of target oplk82573mn
[  2%] Generating oplk82573mn/src/main.c
[  5%] Generating oplk82573mn/src/trace-printk.c
[  8%] Generating oplk82573mn/src/edrvcyclic.c
[ 10%] Generating oplk82573mn/src/ctrlk.c
[ 13%] Generating oplk82573mn/src/ctrlkcal-direct.c
[ 16%] Generating oplk82573mn/src/dllk.c
[ 18%] Generating oplk82573mn/src/dllkfilter.c
[ 21%] Generating oplk82573mn/src/dllkstatemachine.c
[ 24%] Generating oplk82573mn/src/dllkevent.c
[ 27%] Generating oplk82573mn/src/dllkframe.c
[ 29%] Generating oplk82573mn/src/dllknode.c
[ 32%] Generating oplk82573mn/src/dllkcal.c
[ 35%] Generating oplk82573mn/src/dllkcal-circbuf.c
[ 37%] Generating oplk82573mn/src/eventk.c
[ 40%] Generating oplk82573mn/src/eventkcal-linuxkernel.c
[ 43%] Generating oplk82573mn/src/eventkcalintf-circbuf.c
[ 45%] Generating oplk82573mn/src/nmtk.c
[ 48%] Generating oplk82573mn/src/pdok.c
[ 51%] Generating oplk82573mn/src/pdokcal.c
[ 54%] Generating oplk82573mn/src/pdoklut.c
[ 56%] Generating oplk82573mn/src/pdokcal-triplebufshm.c
[ 59%] Generating oplk82573mn/src/pdokcalmem-linuxkernel.c
[ 62%] Generating oplk82573mn/src/timesynck.c
[ 64%] Generating oplk82573mn/src/timesynckcal-linuxkernel.c
[ 67%] Generating oplk82573mn/src/errhndk.c
[ 70%] Generating oplk82573mn/src/errhndkcal.c
[ 72%] Generating oplk82573mn/src/errhndkcal-local.c
[ 75%] Generating oplk82573mn/src/veth-linuxkernel.c
[ 78%] Generating oplk82573mn/src/circbuffer.c
[ 81%] Generating oplk82573mn/src/circbuf-linuxkernel.c
[ 83%] Generating oplk82573mn/src/bufalloc.c
[ 86%] Generating oplk82573mn/src/debugstr.c
[ 89%] Generating oplk82573mn/src/target-linuxkernel.c
[ 91%] Generating oplk82573mn/src/amix86.c
[ 94%] Generating oplk82573mn/src/edrv-82573.c
[ 97%] Generating oplk82573mn/src/hrestimer-linuxkernel.c
[100%] Generating oplk82573mn/oplk82573mn.ko
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c: In function ‘powerlinkOpen’:
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c:311:5: error: implicit declaration of function ‘init_timer’; did you mean ‘init_timers’? [-Werror=implicit-function-declaration]
     init_timer(&heartbeatTimer_g);
     ^~~~~~~~~~
     init_timers
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c: In function ‘executeCmd’:
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c:671:9: error: implicit declaration of function ‘copy_from_user’; did you mean ‘raw_copy_from_user’? [-Werror=implicit-function-declaration]
     if (copy_from_user(&ctrlCmd, (const void __user*)arg_p, sizeof(tCtrlCmd)))
         ^~~~~~~~~~~~~~
         raw_copy_from_user
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c:679:9: error: implicit declaration of function ‘copy_to_user’; did you mean ‘raw_copy_to_user’? [-Werror=implicit-function-declaration]
     if (copy_to_user((void __user*)arg_p, &ctrlCmd, sizeof(tCtrlCmd)))
         ^~~~~~~~~~~~
         raw_copy_to_user
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c: In function ‘startHeartbeatTimer’:
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c:900:31: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
     heartbeatTimer_g.function = increaseHeartbeatCb;
                               ^
/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.c:901:21: error: ‘struct timer_list’ has no member named ‘data’
     heartbeatTimer_g.data = 0;
                     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.o' failed
make[4]: *** [/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn/src/main.o] Error 1
Makefile:1552: recipe for target '_module_/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn' failed
make[3]: *** [_module_/home/andrea/Scaricati/opp/drivers/linux/drv_kernelmod_edrv/build/oplk82573mn] Error 2
CMakeFiles/oplk82573mn.dir/build.make:96: recipe for target 'oplk82573mn/oplk82573mn.ko' failed
make[2]: *** [oplk82573mn/oplk82573mn.ko] Error 2
CMakeFiles/Makefile2:99: recipe for target 'CMakeFiles/oplk82573mn.dir/all' failed
make[1]: *** [CMakeFiles/oplk82573mn.dir/all] Error 2
Makefile:129: recipe for target 'all' failed
make: *** [all] Error 2
```

---

### Post by andrea-miclausig on 2018-09-06
Solved: it's a kernel problem. I needed to use a real time kernel before version 4.0.8 in order for this to work.

---

