---
title: "Edimax ew-7822ulc"
date: 2019-12-07
forum: Networking &amp; Wireless
---

### Post by suicideking on 2019-12-07
I'm running Kubuntu 18.04.3 and followed the following walkthrough:

[https://ubuntuforums.org/showthread.php?t=2392214&page=2](https://ubuntuforums.org/showthread.php?t=2392214&page=2)

```
~/rtl8822bu$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.0.0-37-generic/build M=/home/rick/rtl8822bu  modules
make[1]: Entering directory '/usr/src/linux-headers-5.0.0-37-generic'
  CC [M]  /home/rick/rtl8822bu/core/rtw_cmd.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_security.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_debug.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_io.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_ioctl_query.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_ioctl_set.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_ieee80211.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_mlme.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_mlme_ext.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_mi.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_wlan_util.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_vht.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_pwrctrl.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_rf.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_recv.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_sta_mgt.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_ap.o
  CC [M]  /home/rick/rtl8822bu/core/mesh/rtw_mesh.o
  CC [M]  /home/rick/rtl8822bu/core/mesh/rtw_mesh_pathtbl.o
  CC [M]  /home/rick/rtl8822bu/core/mesh/rtw_mesh_hwmp.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_xmit.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_p2p.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_rson.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_tdls.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_br_ext.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_iol.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_sreset.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_btcoex_wifionly.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_btcoex.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_beamforming.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_odm.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_rm.o
  CC [M]  /home/rick/rtl8822bu/core/rtw_rm_fsm.o
  CC [M]  /home/rick/rtl8822bu/core/efuse/rtw_efuse.o
  CC [M]  /home/rick/rtl8822bu/os_dep/osdep_service.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/os_intfs.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/usb_intf.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/ioctl_linux.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/xmit_linux.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/mlme_linux.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/recv_linux.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1403:4:  error: &#8216;const struct wiphy_vendor_command&#8217; has no member named &#8216;policy&#8217;
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1403:13:  error: &#8216;VENDOR_CMD_RAW_DATA&#8217; undeclared here (not in a function); did  you mean &#8216;VENDOR_CMD_MAX_DATA_LEN&#8217;?
   .policy = VENDOR_CMD_RAW_DATA,
             ^~~~~~~~~~~~~~~~~~~
             VENDOR_CMD_MAX_DATA_LEN
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1412:4:  error: &#8216;const struct wiphy_vendor_command&#8217; has no member named &#8216;policy&#8217;
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1421:4:  error: &#8216;const struct wiphy_vendor_command&#8217; has no member named &#8216;policy&#8217;
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1431:4:  error: &#8216;const struct wiphy_vendor_command&#8217; has no member named &#8216;policy&#8217;
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.c:1440:4:  error: &#8216;const struct wiphy_vendor_command&#8217; has no member named &#8216;policy&#8217;
   .policy = VENDOR_CMD_RAW_DATA,
    ^~~~~~
scripts/Makefile.build:284: recipe for target '/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o' failed
make[2]: *** [/home/rick/rtl8822bu/os_dep/linux/rtw_cfgvendor.o] Error 1
Makefile:1614: recipe for target '_module_/home/rick/rtl8822bu' failed
make[1]: *** [_module_/home/rick/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.0.0-37-generic'
Makefile:2001: recipe for target 'modules' failed
make: *** [modules] Error 2


:~/rtl8822bu$ sudo make install
install -p -m 644 88x2bu.ko  /lib/modules/5.0.0-37-generic/kernel/drivers/net/wireless/
install: cannot stat '88x2bu.ko': No such file or directory
Makefile:2007: recipe for target 'install' failed
make: *** [install] Error 1

```

Any help appreciated.

@[**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=35909")

---

### Post by chili555 on 2019-12-07
Here! Present!!

I just noticed your post. I suggest that you try this: [https://askubuntu.com/questions/1193180/rtl8822bu-fails-after-ubuntu-19-10-update/1193215#1193215](https://askubuntu.com/questions/1193180/rtl8822bu-fails-after-ubuntu-19-10-update/1193215#1193215)

---

### Post by suicideking on 2019-12-07
Thanks for your response!!

Stopped working at mod probe:

```
$ sudo apt update
[sudo] password for : 
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [816 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [624 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [143 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [355 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted i386 Packages [9,584 B]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [24.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,032 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [996 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [264 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [199 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [439 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [998 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [9,280 B]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [7,476 B]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,976 B]
Fetched 6,546 kB in 3s (1,924 kB/s)                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.



:~$ sudo apt install dkms git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.7).
dkms set to manually installed.
git is already the newest version (1:2.17.1-1ubuntu0.4).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rick@HPU:~$ git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
Cloning into 'rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959'...
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 748 (delta 1), reused 3 (delta 0), pack-reused 740
Receiving objects: 100% (748/748), 3.63 MiB | 2.31 MiB/s, done.
Resolving deltas: 100% (252/252), done.



~$ sudo dkms add ./rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959

Creating symlink /var/lib/dkms/rtl88x2bu/5.3.1/source ->
                 /usr/src/rtl88x2bu-5.3.1

DKMS: add completed.



~$ sudo dkms install -m rtl88x2bu -v 5.3.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.0.0-37-generic KVER=5.0.0-37-generic src=/usr/src/rtl88x2bu-5.3.1...............
Signing module:
 - /var/lib/dkms/rtl88x2bu/5.3.1/5.0.0-37-generic/x86_64/module/88x2bu.ko
Secure Boot not enabled on this system.
cleaning build area...

DKMS: build completed.

88x2bu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.0.0-37-generic/updates/dkms/

depmod...

DKMS: install completed.


~$ sudo modprobe -r rtl8812au
modprobe: FATAL: Module rtl8812au not found.
```

---

### Post by suicideking on 2019-12-07
Then I rebooted and was able to connect to the 5G! 

I still get that error for modprobe though. The second modprobe didn't get errors though. 

```
[FONT=monospace][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo modprobe -r rtl8812au[/COLOR]
[sudo] password for:  
modprobe: FATAL: Module rtl8812au not found.
[COLOR=#5454FF][B]

~[/B][/COLOR][COLOR=#000000]$ sudo modprobe 88x2bu[/COLOR]
[/FONT]
```

---

### Post by suicideking on 2019-12-08
I'm able to connect and it stays connected, but the speeds are worse than the 2G and seem inconsistent.

---

### Post by chili555 on 2019-12-08
Have you checked the settings in the router? See my post #2 here: [https://ubuntuforums.org/showthread.php?t=2432328](https://ubuntuforums.org/showthread.php?t=2432328)

---

### Post by suicideking on 2019-12-10
I went through that, most of the settings were already as suggested. Though I changed the wireless channel and restarted it.

Speeds have been consistent since then. Thanks for your help!!

---

