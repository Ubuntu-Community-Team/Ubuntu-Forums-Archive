---
title: "Having a problem installing ixgbe drivers Ubuntu 12.04.5 LTS"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by mike265 on 2014-11-21
[COLOR=#000000][FONT=verdana]I'm running a server with an intel x520 NIC. I am trying to upgrade the driver to latest version, and I am receiving these errors when I compile the driver
[/FONT][/COLOR][COLOR=#000000][FONT=verdana]make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/mike/ixgbe-3.22.3/src modules[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]CC [M] /home/mike/ixgbe-3.22.3/src/ixgbe_main.o[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe_main.c: In function âixgbe_get_stats64â: /home/mike/ixgbe-3.22.3/src/ixgbe_main.c:6815:5: error: implicit declaration of function âu64_stats_fetch_begin_bhâ [-Werror=implicit-function-declaration][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:6818:4: error: implicit declaration of function âu64_stats_fetch_retry_bhâ [-Werror=implicit-function-declaration] /home/mike/ixgbe-3.22.3/src/ixgbe_main.c: In function âixgbe_select_queueâ:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe*main.c:8313:3: error: implicit declaration of function â*_netdev_pick_txâ [-Werror=implicit-function-declaration][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe_main.c: At top level:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:9046:2: warning: initialization from in compatible pointer type [enabled by default][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:9046:2: warning: (near initialization f or âixgbe_netdev_ops.ndo_select_queueâ) [enabled by default][/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]cc1: some warnings being treated as errors[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]make[2]: *** [/home/mike/ixgbe-3.22.3/src/ixgbe_main.o] Error 1[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]make[1]: *** [*module*/home/mike/ixgbe-3.22.3/src] Error 2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]make: *** [default] Error 2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Also The README states that For the build to work properly, the currently running kernel MUST matche the version and configuration of the installed kernel sources. I'm not sure if this has anything to do with it. I haven't updated the kernel, so I assume everything should match. The current intel driver version is 3.15.1-k. I'm trying to update to 3.22.3. Kernel version is 3.13.0-32-generic.[/FONT][/COLOR]

---

### Post by chili555 on 2014-11-22
> Also The README states that For the build to work properly, the currently running kernel MUST matche the version and configuration of the installed kernel sources. I'm not sure if this has anything to do with it.That simply means that the kernel version, 3.13.0-32 in your case, must match the linux-headers. Yours seem to match:> /usr/src/[COLOR="#FF0000"]linux-headers-3.13.0-32-generic[/COLOR]You can check:```
sudo dpkg -s linux-headers-`uname -r`
```Those backticks are on the left side of my keyboard on the same key with ~. We hope we see, "Status: install ok installed."

`uname -r`is code for your running kernel version.

I just compiled this on my 3.13.11-03131110-generic system and it compiles with not even a single warning! I suggest you try:```
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall build-essential
cd ~/ixgbe-3.22.3/src
make clean
make
```Any errors or warnings? If not, then:```
sudo make install
```Reboot.

---

### Post by mike265 on 2014-11-22
You can check:```
sudo dpkg -s linux-headers-`uname -r`
```
Package: linux-headers-3.13.0-32-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 13008
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-trusty
Version: 3.13.0-32.57~precise1
Depends: linux-headers-3.13.0-32, libc6 (>= 2.14)
Description: Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
 This package provides kernel header files for version 3.13.0 on
 64 bit x86 SMP.

So that looks good. I proceeded to follow the rest of your instructions, but still receive errors. I ran 
```

sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall build-essential
```
and that worked fine.

```

make clean
```

returns this

make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/mike/ixgbe-3.22.3/src clean
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CLEAN   /home/mike/ixgbe-3.22.3/src/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
rm -rf ixgbe.ko ixgbe.o ixgbe.mod.c ixgbe.mod.o ixgbe_main.o ixgbe_common.o ixgbe_api.o ixgbe_param.o ixgbe_lib.o ixgbe_ethtool.o kcompat.o ixgbe_82598.o ixgbe_82599.o ixgbe_x540.o ixgbe_sriov.o ixgbe_mbx.o ixgbe_dcb.o ixgbe_dcb_82598.o ixgbe_dcb_82599.o ixgbe_sysfs.o ixgbe_procfs.o ixgbe_phy.o ixgbe_dcb_nl.o ixgbe_fcoe.o ixgbe_debugfs.o ixgbe_ptp.o ixgbe.7.gz .*cmd .tmp_versions

and then

```

make
``` 
returns these errors

make -C /lib/modules/3.13.0-32-generic/build SUBDIRS=/home/mike/ixgbe-3.22.3/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/mike/ixgbe-3.22.3/src/ixgbe_main.o
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c: In function âixgbe_get_stats64â:
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:6815:5: error: implicit declaration of function âu64_stats_fetch_begin_bhâ [-Werror=implicit-function-declaration]
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:6818:4: error: implicit declaration of function âu64_stats_fetch_retry_bhâ [-Werror=implicit-function-declaration]
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c: In function âixgbe_select_queueâ:
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:8313:3: error: implicit declaration of function â__netdev_pick_txâ [-Werror=implicit-function-declaration]
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c: At top level:
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:9046:2: warning: initialization from incompatible pointer type [enabled by default]
/home/mike/ixgbe-3.22.3/src/ixgbe_main.c:9046:2: warning: (near initialization for âixgbe_netdev_ops.ndo_select_queueâ) [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/mike/ixgbe-3.22.3/src/ixgbe_main.o] Error 1
make[1]: *** [_module_/home/mike/ixgbe-3.22.3/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [default] Error 2


Thank you for your reply!!

---

### Post by chili555 on 2014-11-22
There is this: [http://sourceforge.net/p/e1000/bugs/426/](http://sourceforge.net/p/e1000/bugs/426/)> status: open --> wont-fixHowever, you may be able to install the 3.13 kernel I have and upon which it compiles perfectly:```
make -C /lib/modules/3.13.11-03131110-generic/build SUBDIRS=/home/chili/Downloads/ixgbe-3.22.3/src modules
make[1]: Entering directory '/usr/src/linux-headers-3.13.11-03131110-generic'
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_main.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_common.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_api.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_param.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_lib.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_ethtool.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/kcompat.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_82598.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_82599.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_x540.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_sriov.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_mbx.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_dcb.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_dcb_82598.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_dcb_82599.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_sysfs.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_procfs.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_phy.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_dcb_nl.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_fcoe.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_debugfs.o
  CC [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe_ptp.o
  LD [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe.mod.o
  LD [M]  /home/chili/Downloads/ixgbe-3.22.3/src/ixgbe.ko
make[1]: Leaving directory '/usr/src/linux-headers-3.13.11-03131110-generic'
```Here is where you can get the kernel and headers: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.11.10-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.11.10-trusty/) Be certain to get the parts appropriate to your architecture; either 32- or 64-bit.

Reboot into the new kernel and compile again:```
cd ~/ixgbe-3.22.3/src
make clean
make
sudo make install
```

---

### Post by mike265 on 2014-11-22
Thank you for all that. It worked. Had to update the kernel and headers. I really appreciate all your help!! :D

---

### Post by chili555 on 2014-11-22
Glad it's working. Please use thread tools at the top to mark Solved.

---

