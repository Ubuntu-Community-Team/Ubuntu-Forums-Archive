---
title: "How to install Edimax EW-7811UTC AC600 Wireless USB with no internet (no ethernet)"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by leo18 on 2014-06-06
Hi Guys, 

I've recently bought a new USB wireless adapter from EDIMAX model EW-7811UTC AC600 Dual-Band. Works like a charm on Win7, however I'm having trouble installing it on my Ubuntu 14.04 LTE.  In the instruction manual it states that "An active connection is required for Linux driver installation" 
Having no access to wired network I'm unable to follow the steps in manual and was wondering whether there's an alternative way of installing it without the internet connection. 

**Installation Manual for Linux:**

[http://www.edimax.com/images/Image/QIG/Wireless/EW-7811UTC/EW-7811UTC_QIG_EN%28English%29.pdf](http://www.edimax.com/images/Image/QIG/Wireless/EW-7811UTC/EW-7811UTC_QIG_EN%28English%29.pdf)

**With my purchase I have received a cd with drivers:**

rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_fix_led.tar.gz

**lsusb**

Bus 001 Device 005: ID 7392:a811 Edimax Technology Co., Ltd

Would like to add that I'm an absolute newbie and would appreciate if anybody could advise what steps needs to be taken to successfully install this USB adapter.

---

### Post by chili555 on 2014-06-06
Here is how you install it in about five minutes.

Leo: "Hey, friend, can I borrow your ethernet connection for just a few minutes? I brought along six of your favorite beverage."

Friend: "Sure, Leo, glad to help you! Let me put a couple of those beverages on ice."

You then open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

Your wireless should now be working. Detach the ethernet, thank the friend and enjoy!

Here is how to do it in about five days...maybe.

Go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Select Trusty in the drop-down box. Search for linux-headers-generic, build-essential and git. Be sure to locate their dependencies and the dependencies of the dependencies. Be sure to download the correct version, either 32- or 64-bit. Once you've download about fifteen or so packages on another computer, transfer them with a USB stick or similar to the desktop of your Ubuntu computer. Open a terminal and install them:

```
cd ~/Desktop
sudo dpkg -i *.deb
```

It may complain that a package is missing a dependency. If so, download that and add it to the desktop and try again. 

Write many posts on the forum to tell old Chili how you're stuck. Rinse and repeat.

Once that's all done, get this: [https://github.com/gnab/rtl8812au/archive/master.zip](https://github.com/gnab/rtl8812au/archive/master.zip)  Download it and then transfer it to your desktop, too. Right-click it and select 'Extract Here.' Now, back to the terminal.

```
cd ~/Desktop/rtl8812au-master
make
sudo make install
sudo modprobe 8812au
```

Your wireless should now be working.

Questions? Concerns??

---

### Post by leo18 on 2014-06-07
Hi Chili, many thanks for comprehensive response. I'd prefer 5 min option with a friend over 5 days solution. Too bad that all of my friends consider ethernet cables as ancient technology. Easy fix as I've ordered a cheap ethernet cable over ebay I don't mind waiting bit longer to get this running smooth. Will post back next week once the cable arrives. Thanks

---

### Post by chili555 on 2014-06-07
> **leo18 said:**
> Hi Chili, many thanks for comprehensive response. I'd prefer 5 min option with a friend over 5 days solution. Too bad that all of my friends consider ethernet cables as ancient technology. Easy fix as I've ordered a cheap ethernet cable over ebay I don't mind waiting bit longer to get this running smooth. Will post back next week once the cable arrives. ThanksI look forward to your post and please spend as much on the beverages as on the cable! Good luck!

---

### Post by leo18 on 2014-06-15
Chili you probably heard it not once, not twice but you are a lifesaver !!! I've tried the first solution with ethernet cable and it worked perfect. I'm now able to connect to 5Ghz wifi network over my EDIMAX EW-7811UTC AC600 Wireless dual band mini USB Adapter. Highly recommend this device previously on Win7 with different 2Ghz usb dongle was getting download speeds between 40-45 Mbps, now on 5Ghz connection gettin download speeds over 60 Mbps!!!

For those that have a freshly installed copy of 14.04 LTE before applying the steps suggested by chili555 make sure to go to "Software & Updates" and under ubuntu software tab tick all downloadable options and select download from Main Server, otherwise like in my case you may get "Package build-essential is not available" type of error.

Once again Many Thanks for your help Chili!

---

### Post by chili555 on 2014-06-15
Awesome! Glad it's working.

You have compiled the driver only for your currently running kernel. When Software Updater installs a newer linux-image, after the requested reboot, you will need to re-compile:```
cd ~/rtl8812au
make clean
make
sudo make install
sudo modprobe 8812au
```Please retain the files and these instructions for that time.

---

### Post by leo18 on 2014-06-15
Hi Chili, thanks for bringing this up certainly it will come useful after installing the updates :)

---

### Post by harmkuiper on 2014-07-14
Thanks Chili555 and Leo18 for giving me hope that i can resolve this. I spend quite some time yesterday to USB move 9 packages to get build-essential installed on my 12.04 box. I thought i had it working but then the make failed using the official driver. I am going to see if i can use that git based driver :)

Keywords for others so they can find this thread
Sitecom AC600, no internet, offline instructions, USB Hell, installation instructions, build-essential not installed

---

### Post by chili555 on 2014-07-14
> **harmkuiper said:**
> Thanks Chili555 and Leo18 for giving me hope that i can resolve this. I spend quite some time yesterday to USB move 9 packages to get build-essential installed on my 12.04 box. I thought i had it working but then the make failed using the official driver. I am going to see if i can use that git based driver :)The git based driver also requires build-essential and linux-headers-generic and *all* their dependencies.

---

### Post by harmkuiper on 2014-07-14
> **chili555 said:**
> The git based driver also requires build-essential and linux-headers-generic and *all* their dependencies.

Hey Chili555,

So far a bit more luck, but still no luck getting the driver to work. The make clean > make > sudo make > modprobe work fine but the adopter doesnt work. (listed in lsusb)

Build-Essential is installed and Linux-Header-Generic (3.2.0-65._3.2.0-65.99_all, 3.2.0-65-generic_3.2.0-65-99_amd64, 3.2.0.65.77_amd64) installed as well. 

During the make (without sudo) i do get some errors, though in your other post ([link]("http://ubuntuforums.org/showthread.php?t=2215827")) you resolve by using the git archive. Which i am also using (June 11th 19:17 version).

Could you please help? Also: hijacking thread :)

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-15-generic/build M=/home/harm/rtl8812au-master  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /home/harm/rtl8812au-master/core/rtw_cmd.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_security.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_debug.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_io.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_ioctl_query.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_ioctl_set.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_ieee80211.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_mlme.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_mlme_ext.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_wlan_util.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_vht.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_pwrctrl.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_rf.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_recv.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_sta_mgt.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_ap.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_xmit.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_p2p.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_tdls.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_br_ext.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_iol.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_sreset.o
  CC [M]  /home/harm/rtl8812au-master/core/efuse/rtw_efuse.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/osdep_service.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/os_intfs.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/usb_intf.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/ioctl_linux.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/xmit_linux.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/mlme_linux.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/recv_linux.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/harm/rtl8812au-master/os_dep/linux/rtw_android.o
  CC [M]  /home/harm/rtl8812au-master/hal/hal_intf.o
  CC [M]  /home/harm/rtl8812au-master/hal/hal_com.o
  CC [M]  /home/harm/rtl8812au-master/hal/hal_com_phycfg.o
  CC [M]  /home/harm/rtl8812au-master/hal/hal_phy.o
  CC [M]  /home/harm/rtl8812au-master/hal/led/hal_usb_led.o
  CC [M]  /home/harm/rtl8812au-master/hal/HalPwrSeqCmd.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/Hal8812PwrSeq.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/Hal8821APwrSeq.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_xmit.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_sreset.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_hal_init.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_phycfg.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_rf6052.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_dm.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_rxdesc.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_cmd.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/usb/usb_halinit.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/usb/rtl8812au_led.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/usb/rtl8812au_xmit.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/usb/rtl8812au_recv.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/usb/usb_ops_linux.o
  CC [M]  /home/harm/rtl8812au-master/hal/rtl8812a/rtl8812a_mp.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/odm_debug.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/odm_interface.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/odm_HWConfig.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/odm.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/HalPhyRf.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_MAC.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_BB.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_RF.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.o
  CC [M]  /home/harm/rtl8812au-master/hal/OUTSRC/rtl8821a/odm_RegConfig8821A.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_mp.o
  CC [M]  /home/harm/rtl8812au-master/core/rtw_mp_ioctl.o
  LD [M]  /home/harm/rtl8812au-master/8812au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/harm/rtl8812au-master/8812au.mod.o
  LD [M]  /home/harm/rtl8812au-master/8812au.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'

```

oops, the error code doesnt show. Will update later

---

### Post by chili555 on 2014-07-14
> **harmkuiper said:**
> Hey Chili555,

So far a bit more luck, but still no luck getting the driver to work. The make clean > make > sudo make > modprobe work fine but the adopter doesnt work. (listed in lsusb)

.....Let's see:```
lsusb
modinfo 8812au
```It would list in lsusb whether it has a working driver or not; what's more relevant is *iwconfig*.

Thanks.

---

### Post by harmkuiper on 2014-08-16
I downloaded the 14.04 iso and gave that a try. Still no luck! perhaps i am using the wrong drivers. I bought a Sitecom AC600 Dual Broadband.. which came with linux drivers but those cant be downloaded or something only on the CD.

Current iwconfig
```

harm@harm-MS-7680:~/rtl8812au$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```

When compiling your drivers:
```

harm@harm-MS-7680:~$ cd rtl8812au/
harm@harm-MS-7680:~/rtl8812au$ make clean
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
harm@harm-MS-7680:~/rtl8812au$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-34-generic/build M=/home/harm/rtl8812au  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-34-generic'
  CC [M]  /home/harm/rtl8812au/core/rtw_cmd.o
  CC [M]  /home/harm/rtl8812au/core/rtw_security.o
  CC [M]  /home/harm/rtl8812au/core/rtw_debug.o
  CC [M]  /home/harm/rtl8812au/core/rtw_io.o
  CC [M]  /home/harm/rtl8812au/core/rtw_ioctl_query.o
  CC [M]  /home/harm/rtl8812au/core/rtw_ioctl_set.o
  CC [M]  /home/harm/rtl8812au/core/rtw_ieee80211.o
  CC [M]  /home/harm/rtl8812au/core/rtw_mlme.o
  CC [M]  /home/harm/rtl8812au/core/rtw_mlme_ext.o
  CC [M]  /home/harm/rtl8812au/core/rtw_wlan_util.o
  CC [M]  /home/harm/rtl8812au/core/rtw_vht.o
  CC [M]  /home/harm/rtl8812au/core/rtw_pwrctrl.o
  CC [M]  /home/harm/rtl8812au/core/rtw_rf.o
  CC [M]  /home/harm/rtl8812au/core/rtw_recv.o
  CC [M]  /home/harm/rtl8812au/core/rtw_sta_mgt.o
  CC [M]  /home/harm/rtl8812au/core/rtw_ap.o
  CC [M]  /home/harm/rtl8812au/core/rtw_xmit.o
  CC [M]  /home/harm/rtl8812au/core/rtw_p2p.o
  CC [M]  /home/harm/rtl8812au/core/rtw_tdls.o
  CC [M]  /home/harm/rtl8812au/core/rtw_br_ext.o
  CC [M]  /home/harm/rtl8812au/core/rtw_iol.o
  CC [M]  /home/harm/rtl8812au/core/rtw_sreset.o
  CC [M]  /home/harm/rtl8812au/core/efuse/rtw_efuse.o
  CC [M]  /home/harm/rtl8812au/os_dep/osdep_service.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/os_intfs.o
/home/harm/rtl8812au/os_dep/linux/os_intfs.c: In function ‘create_proc_read_entry’:
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:328:2: warning: initialization from incompatible pointer type [enabled by default]
  };
  ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:328:2: warning: (near initialization for ‘fops.read’) [enabled by default]
/home/harm/rtl8812au/os_dep/linux/os_intfs.c: In function ‘create_proc_read_write_entry’:
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:339:3: warning: initialization from incompatible pointer type [enabled by default]
   read: read_proc,
   ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:339:3: warning: (near initialization for ‘fops.read’) [enabled by default]
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:341:2: warning: initialization from incompatible pointer type [enabled by default]
  };
  ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:341:2: warning: (near initialization for ‘fops.write’) [enabled by default]
/home/harm/rtl8812au/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:389:3: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
   entry = create_proc_read_entry("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);
   ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:438:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_write_reg, dev, proc_set_write_reg);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:438:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_write_reg, dev, proc_set_write_reg);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:445:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_read_reg, dev, proc_set_read_reg);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:445:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_read_reg, dev, proc_set_read_reg);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:452:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_fwstate, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:459:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_sec_info, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:466:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mlmext_state, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:473:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_qos_option, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:480:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ht_option, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:487:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_info, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:494:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ap_info, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:501:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_adapter_state, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:508:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_trx_info, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:515:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump1, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:522:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump2, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:529:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump3, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:536:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump1, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:543:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump2, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:550:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump3, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:557:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_reg_dump1, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:564:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_reg_dump2, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:573:9: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
         dir_dev, proc_get_rf_reg_dump3, dev);
         ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:580:9: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
         dir_dev, proc_get_rf_reg_dump4, dev);
         ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:590:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_all_sta_info, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:608:8: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_best_channel, dev);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:616:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_signal, dev, proc_set_rx_signal);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:616:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_signal, dev, proc_set_rx_signal);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:623:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ht_enable, dev, proc_set_ht_enable);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:623:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ht_enable, dev, proc_set_ht_enable);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:630:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bw_mode, dev, proc_set_bw_mode);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:630:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bw_mode, dev, proc_set_bw_mode);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:637:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ampdu_enable, dev, proc_set_ampdu_enable);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:637:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ampdu_enable, dev, proc_set_ampdu_enable);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:644:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_stbc, dev, proc_set_rx_stbc);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:644:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_stbc, dev, proc_set_rx_stbc);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:652:6: warning: passing argument 4 of ‘create_proc_read_entry’ from incompatible pointer type [enabled by default]
      dir_dev, proc_get_two_path_rssi, dev);
      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:321:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:655:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rssi_disp, dev, proc_set_rssi_disp);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:655:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rssi_disp, dev, proc_set_rssi_disp);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:671:8: warning: passing argument 4 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_sreset, dev, proc_set_sreset);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:671:8: warning: passing argument 6 of ‘create_proc_read_write_entry’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_sreset, dev, proc_set_sreset);
        ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:333:38: note: expected ‘ssize_t (**)(struct file *, const char *, ssize_t,  loff_t *)’ but argument is of type ‘int (*)(struct file *, const char *, long unsigned int,  void *)’
 static inline struct proc_dir_entry *create_proc_read_write_entry(const char *name,
                                      ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c: At top level:
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:1053:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/harm/rtl8812au/os_dep/linux/os_intfs.c:1053:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /home/harm/rtl8812au/os_dep/linux/usb_intf.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/ioctl_linux.o
/home/harm/rtl8812au/os_dep/linux/ioctl_linux.c: In function ‘rtw_mp_efuse_get’:
/home/harm/rtl8812au/os_dep/linux/ioctl_linux.c:8887:65: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseInitMap[i+j]);
                                                                 ^
/home/harm/rtl8812au/os_dep/linux/ioctl_linux.c:8875:3: note: containing loop
   for (i = 0; i < EFUSE_MAP_SIZE; i += 16)
   ^
/home/harm/rtl8812au/os_dep/linux/ioctl_linux.c:9301:69: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseModifiedMap[i+j]);
                                                                     ^
/home/harm/rtl8812au/os_dep/linux/ioctl_linux.c:9295:3: note: containing loop
   for (i=0; i<EFUSE_MAP_SIZE; i+=16)
   ^
  CC [M]  /home/harm/rtl8812au/os_dep/linux/xmit_linux.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/mlme_linux.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/recv_linux.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/harm/rtl8812au/os_dep/linux/rtw_android.o
/home/harm/rtl8812au/os_dep/linux/rtw_android.c: In function ‘rtw_android_priv_cmd’:
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:356:30: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  if (copy_from_user(command, (void *)priv_cmd.buf, priv_cmd.total_len)) {
                              ^
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:548:4: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast [enabled by default]
    pwfd_info->rtsp_ctrlport = ( u16 ) get_int_from_command( priv_cmd.buf );
    ^
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:307:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command( char* pcmd )
     ^
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:568:4: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast [enabled by default]
    pwfd_info->wfd_device_type = ( u8 ) get_int_from_command( priv_cmd.buf );
    ^
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:307:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command( char* pcmd )
     ^
/home/harm/rtl8812au/os_dep/linux/rtw_android.c:592:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
   if (copy_to_user((void *)priv_cmd.buf, command, bytes_written)) {
                    ^
  CC [M]  /home/harm/rtl8812au/hal/hal_intf.o
  CC [M]  /home/harm/rtl8812au/hal/hal_com.o
  CC [M]  /home/harm/rtl8812au/hal/hal_com_phycfg.o
  CC [M]  /home/harm/rtl8812au/hal/hal_phy.o
  CC [M]  /home/harm/rtl8812au/hal/led/hal_usb_led.o
  CC [M]  /home/harm/rtl8812au/hal/HalPwrSeqCmd.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/Hal8812PwrSeq.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/Hal8821APwrSeq.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_xmit.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_sreset.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_hal_init.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_phycfg.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_rf6052.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_dm.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_rxdesc.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_cmd.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/usb/usb_halinit.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/usb/rtl8812au_led.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/usb/rtl8812au_xmit.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/usb/rtl8812au_recv.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/usb/usb_ops_linux.o
  CC [M]  /home/harm/rtl8812au/hal/rtl8812a/rtl8812a_mp.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/odm_debug.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/odm_interface.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/odm_HWConfig.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/odm.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/HalPhyRf.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_FW.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_MAC.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_BB.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalHWImg8812A_TestChip_RF.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8812a/odm_RegConfig8812A.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_MAC.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_BB.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalHWImg8821A_TestChip_RF.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.o
  CC [M]  /home/harm/rtl8812au/hal/OUTSRC/rtl8821a/odm_RegConfig8821A.o
  CC [M]  /home/harm/rtl8812au/core/rtw_mp.o
  CC [M]  /home/harm/rtl8812au/core/rtw_mp_ioctl.o
  LD [M]  /home/harm/rtl8812au/8812au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/harm/rtl8812au/8812au.mod.o
  LD [M]  /home/harm/rtl8812au/8812au.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-34-generic'
harm@harm-MS-7680:~/rtl8812au$ sudo make install
[sudo] password for harm: 
Sorry, try again.
[sudo] password for harm: 
install -p -m 644 8812au.ko  /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.13.0-34-generic
harm@harm-MS-7680:~/rtl8812au$ sudo modprobe 8812au
harm@harm-MS-7680:~/rtl8812au$ 


```

---

### Post by praseodym on 2014-08-16
Please show the outputs of:
```

lsusb
lsmod
iwconfig
```

---

### Post by harmkuiper on 2014-08-17
praseodym here is the output. I made some stuff bold


```

**harm@harm-MS-7680:~$ lsusb**
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 046d:081b Logitech, Inc. Webcam C310
Bus 001 Device 008: ID 18a5:0238 Verbatim, Ltd 
**Bus 001 Device 010: ID 0df6:0075 Sitecom Europe B.V. **
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 005: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 1532:0029 Razer USA, Ltd 
Bus 001 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**harm@harm-MS-7680:~$ lsmod**
Module                  Size  Used by
nls_iso8859_1          12713  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
usb_storage            62209  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
snd_usb_audio         153525  1 
snd_usbmidi_lib        29215  1 snd_usb_audio
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  5 
intel_rapl             18773  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
crct10dif_pclmul       14289  0 
snd_seq_midi           13324  0 
crc32_pclmul           13113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13216  0 
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
radeon               1522422  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
snd                    69238  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
lpc_ich                21080  0 
drm                   303102  3 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
shpchp                 37032  0 
i2c_algo_bit           13413  1 radeon
mei_me                 18627  0 
mei                    82276  1 mei_me
ppdev                  17671  0 
parport_pc             32701  1 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
video                  19476  0 
mac_hid                13205  0 
psmouse               106678  0 
r8169                  67581  0 
mii                    13934  1 r8169
**harm@harm-MS-7680:~$ iwconfig**
eth0      no wireless extensions.

lo        no wireless extensions.

harm@harm-MS-7680:~$ 

```

---

### Post by praseodym on 2014-08-17
[https://wikidevi.com/wiki/Sitecom_WLA-3100](https://wikidevi.com/wiki/Sitecom_WLA-3100)

Obviously, a brand new one. There is a driver recommended which is too large for attaching.

[http://www.mediatek.com/en/downloads/?sort=os](http://www.mediatek.com/en/downloads/?sort=os)

Download the driver **mt7610u** and unpack it to your home-folder. Then open the file **~/mt7610u_wifi_sta_v3002_dpo_20130916/common/rtusb_dev_id.c ** and add the device ID like this:
```

#ifdef MT76x0
	{USB_DEVICE(0x148F,0x7610)}, /* MT7610U */
	{USB_DEVICE(0x0E8D,0x7610)}, /* MT7610U */
[COLOR="#FF0000"]     	{USB_DEVICE(0x0DF6,0x0075)}, /* MT7610U */[/COLOR]
	{USB_DEVICE_AND_INTERFACE_INFO(0x0E8D, 0x7630, 0xff, 0x2, 0xff)}, /* MT7630U */
	{USB_DEVICE_AND_INTERFACE_INFO(0x0E8D, 0x7650, 0xff, 0x2, 0xff)}, /* MT7650U */
```

Then open the file **~/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/confik.mk** and change the content to:

```
# Support Wpa_Supplicant
# i.e. wpa_supplicant -Dralink
HAS_WPA_SUPPLICANT=[COLOR="#FF0000"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
# i.e. wpa_supplicant -Dwext
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="#FF0000"]y[/COLOR]
```

Save, close the editor and try to compile:

```
cd ~/mt7610u_wifi_sta_v3002_dpo_20130916/
make
sudo make install
```

Load the module and replug the stick:
```

sudo modprobe -v mt7650u_sta
dmesg | grep mt7
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by harmkuiper on 2014-08-17
Dear praseodym, thanks for your fast response. I cant successfully compile and im just not home enough to understand the problem. Thanks for pointing out that i need other drivers. If you have time to help me further that be great otherwise i can give it a go for the next couple of days.

here is the make log. Note: in the USB_ID file i tried both upper and lower case for the additional device id (not sure of that mattered)
```

harm@harm-MS-7680:~$ cd mt7610u_wifi_sta_v3002_dpo_20130916/
harm@harm-MS-7680:~/mt7610u_wifi_sta_v3002_dpo_20130916$ make
make -C tools
make[1]: Entering directory `/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/tools'
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/tools/bin2h
chipset = mt7650u
chipset = mt7630u
chipset = mt7610u
cp -f os/linux/Makefile.6 /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/Makefile
make -C /lib/modules/3.13.0-34-generic/build SUBDIRS=/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-34-generic'
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c: In function ‘announce_802_3_packet’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:334:16: warning: unused variable ‘pAd’ [-Wunused-variable]
  RTMP_ADAPTER *pAd = (RTMP_ADAPTER *)pAdSrc;
                ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c: In function ‘STA_MonPktSend’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_profile.c:443:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/assoc.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/auth.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/sync.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/sanity.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/connect.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/wpa.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../mgmt/mgmt_vht.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/vht.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_md5.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_aes.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_aes.c:1459:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Wrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainTextLength));
      ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_aes.c:1554:6: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘long unsigned int’ [-Wformat=]
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/mlme.o
In file included from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/mlme.c:28:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/mlme.c:538:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:471:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/mlme.c:539:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:471:76: note: in definition of macro ‘NdisZeroMemory’
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_wep.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/action.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_data.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c: In function ‘NICReadEEPROMParameters’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘UCHAR *’ [-Wformat=]
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
   ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 5 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 7 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 8 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 9 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 10 has type ‘UCHAR *’ [-Wformat=]
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:1061:9: warning: unused variable ‘i’ [-Wunused-variable]
  USHORT i;
         ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c: In function ‘NICInitializeAsic’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:1684:1: warning: the frame size of 2048 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
In file included from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:28:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c: In function ‘NICReadEEPROMParameters’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:27: warning: array subscript is above array bounds [-Warray-bounds]
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
                           ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:660:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
   ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:27: warning: array subscript is above array bounds [-Warray-bounds]
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
                           ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:660:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
   ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:27: warning: array subscript is above array bounds [-Warray-bounds]
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
                           ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:660:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
   ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:27: warning: array subscript is above array bounds [-Warray-bounds]
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
                           ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:660:16: note: in definition of macro ‘DBGPRINT_RAW’
         printk Fmt;               \
                ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init.c:716:3: note: in expansion of macro ‘DBGPRINT’
   DBGPRINT(RT_DEBUG_TRACE,("E2PROM: A Tssi[-4 .. +4] = %d %d %d %d - %d -%d %d %d %d, step=%d, tuning=%d\n",
   ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_aes.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_sync.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/eeprom.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_info.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_info.c: In function ‘Set_DebugFunc_Proc’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_info.c:1084:2: warning: format ‘%x’ expects argument of type ‘unsigned int’, but argument 2 has type ‘ULONG’ [-Wformat=]
  DBGPRINT_S(RT_DEBUG_TRACE, ("Set RTDebugFunc = 0x%x\n", RTDebugFunc));
  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_info.c: In function ‘set_rf’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_info.c:5960:3: warning: format ‘%x’ expects argument of type ‘unsigned int *’, but argument 5 has type ‘UCHAR *’ [-Wformat=]
   rv = sscanf(arg, "%d-%d-%x", &(bank_id), &(rf_id), &(rf_val));
   ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_cfg.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_cfg.c: In function ‘RTMP_COM_IoctlHandle’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_cfg.c:705:32: warning: unused variable ‘ppINTF’ [-Wunused-variable]
                         VOID **ppINTF = (VOID **)pData;
                                ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_radar.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/spectrum.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/spectrum.c:1972:3: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rt_channel.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_profile.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_asic.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_asic.c: In function ‘AsicUpdateProtect’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_asic.c:330:2: warning: large integer implicitly truncated to unsigned type [-Woverflow]
  UCHAR i, PhyMode = 0x4000;
  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_asic.c:384:2: warning: large integer implicitly truncated to unsigned type [-Woverflow]
  PhyMode = 0x2000; /* Bit 15:13, 0:Legacy CCK, 1: Legacy OFDM, 2: HT mix mode, 3: HT green field, 4: VHT mode, 5-7: Reserved */
  ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/scan.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/uapsd.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/ps.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/rtmp_chip.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/rtmp_chip.c: In function ‘RtmpChipOpsHook’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../chips/rtmp_chip.c:910:30: warning: assignment from incompatible pointer type [enabled by default]
  pChipOps->ChipSwitchChannel = Default_ChipSwitchChannel;
                              ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/txpower.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/txpower.c: In function ‘AsicGetAutoAgcOffsetForExternalTxAlc’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/txpower.c:164:23: warning: assignment from incompatible pointer type [enabled by default]
    pTssiMinusBoundary = &pAd->TssiMinusBoundaryA[0];
                       ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/txpower.c:165:22: warning: assignment from incompatible pointer type [enabled by default]
    pTssiPlusBoundary = &pAd->TssiPlusBoundaryA[0];
                      ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rtmp_phy.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c: In function ‘rtmp_bbp_get_temp’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c:68:9: warning: unused variable ‘bbp_val’ [-Wunused-variable]
  UINT32 bbp_val; 
         ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c: In function ‘rtmp_bbp_tx_comp_init’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c:83:8: warning: unused variable ‘rf_val’ [-Wunused-variable]
  UCHAR rf_val;
        ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c:82:9: warning: unused variable ‘bbp_val’ [-Wunused-variable]
  UINT32 bbp_val;
         ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c: At top level:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_phy.c:153:14: warning: ‘vht_prim_ch_val’ defined but not used [-Wunused-variable]
 static UCHAR vht_prim_ch_val[] = {
              ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../rate_ctrl/alg_grp.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/ba_action.o
In file included from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rt_config.h:33,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/ba_action.c:30:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:929:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(__pRxPkt, __pData, __DataSize);      \
  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/ba_action.c:1569:2: note: in expansion of macro ‘RTMP_OS_PKT_INIT’
  RTMP_OS_PKT_INIT(pRxBlk->pRxPacket,
  ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../common/rt_os_util.o
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:56:0,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/sta_ioctl.c:30:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_giwscan’:
include/net/iw_handler.h:542:9: warning: array subscript is below array bounds [-Warray-bounds]
   memcpy(stream + point_len, extra, iwe->u.data.length);
         ^
  CC [M]  /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.o
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsUsDelay’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:176:8: warning: unused variable ‘i’ [-Wunused-variable]
  ULONG i;
        ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:500:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:31,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:31:
/usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:502:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:31,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:31:
/usr/src/linux-headers-3.13.0-34-generic/arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:653:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_os.h:44:0,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/rtmp_comm.h:75,
                 from /home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:31:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOsPktInit’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:672:2: note: in expansion of macro ‘SET_OS_PKT_DATATAIL’
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:698:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘__RtmpOSFSInfoChange’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:1109:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:1110:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpDrvAllRFPrint’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:2032:4: warning: passing argument 2 of ‘file_w->f_op->write’ from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:2032:4: note: expected ‘const char *’ but argument is of type ‘UINT32 *’
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:2017:22: warning: unused variable ‘macValue’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:2017:9: warning: unused variable ‘macAddr’ [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRelease’:
/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.c:2153:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/harm/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-34-generic'
make: *** [LINUX] Error 2
harm@harm-MS-7680:~/mt7610u_wifi_sta_v3002_dpo_20130916$ 


```

---

### Post by praseodym on 2014-08-17
Obviously, the driver from 2013 is not working anymore. Try the latest Windows driver with Ndiswrapper:
```

sudo apt-get install --reinstall ndisgtk ndiswrapper-dkms dkms build-essential
```
Unpack the EXE via right-klick and copy all of its content to a new folder. Install the respective *.INF file via
```

gksudo ndisgtk
```

---

### Post by harmkuiper on 2014-08-17
> **praseodym said:**
> Obviously, the driver from 2013 is not working anymore. Try the latest Windows driver with Ndiswrapper:
```

sudo apt-get install --reinstall ndisgtk ndiswrapper-dkms dkms build-essential
```
Unpack the EXE via right-klick and copy all of its content to a new folder. Install the respective *.INF file via
```

gksudo ndisgtk
```

cant get the INF files from the .exe file. :| tried to install it on a windows computer but cant really find the driver file. I am on a 64 bit system if that helps

---

### Post by praseodym on 2014-08-17
Scroll down to the driver page there is the Win driver. Check the Wiki for extracting, too:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers)

---

### Post by harmkuiper on 2014-08-18
> **praseodym said:**
> Scroll down to the driver page there is the Win driver. Check the Wiki for extracting, too:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Downloading_Windows_Drivers)
Alright this isnt worth my time. Looked online for a native supported wifi adapter and bought that , 10 euro's including shipping. My time is worth enough to justify a 4th adapter for my PC.

Not working on linux (or w. lots of effort):
Cisco AE2500
SItecom AC600

Praseodym and Chille555 you guys are awesome and i really and truely appreciate all the effort you put into this community. It is easy to complain that some linux drivers are tricky but you guys more then make up for it.

---

### Post by praseodym on 2014-08-18
You could have a frequent look at that download page or check the mainline kernels like 3.16 or the kernel log release notes if there's a new driver available

---

### Post by JohnMac on 2014-09-18
Hi,

I cannot get my EW-7811UTC driver to install on my PC running 12.04. I do have internet connected. This is the code I get culminating with "No such file or directory.

Any hints


j```
ohn@john-OptiPlex-755:~$ cd ~/rtl8812au
john@john-OptiPlex-755:~/rtl8812au$ make clean
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
john@john-OptiPlex-755:~/rtl8812au$ sudo make install
[sudo] password for john: 
install -p -m 644 8812au.ko  /lib/modules/3.2.0-68-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `8812au.ko': No such file or directory
make: *** [install] Error 1
john@john-OptiPlex-755:~/rtl8812au$ sudo apt-get update
Hit http://au.archive.ubuntu.com precise Release.gpg                           
Get:1 http://au.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://au.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://au.archive.ubuntu.com precise Release                               
Get:2 http://au.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://au.archive.ubuntu.com precise-backports Release
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://au.archive.ubuntu.com precise/main Sources                          
Hit http://au.archive.ubuntu.com precise/restricted Sources
Hit http://au.archive.ubuntu.com precise/universe Sources
Hit http://au.archive.ubuntu.com precise/multiverse Sources
Hit http://au.archive.ubuntu.com precise/main i386 Packages
Hit http://au.archive.ubuntu.com precise/restricted i386 Packages
Hit http://au.archive.ubuntu.com precise/universe i386 Packages
Hit http://au.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://au.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://au.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://au.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://au.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://au.archive.ubuntu.com precise-updates/main Sources [478 kB]       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                   
Get:6 http://security.ubuntu.com precise-security/main Sources [110 kB]      
Get:7 http://au.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:8 http://au.archive.ubuntu.com precise-updates/universe Sources [110 kB]   
Get:9 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:10 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]  
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,785 B]
Get:12 http://security.ubuntu.com precise-security/main i386 Packages [450 kB] 
Get:13 http://au.archive.ubuntu.com precise-updates/multiverse Sources [8,886 B]
Get:14 http://au.archive.ubuntu.com precise-updates/main i386 Packages [862 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_AU                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [103 kB]
Get:17 http://au.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:18 http://au.archive.ubuntu.com precise-updates/universe i386 Packages [254 kB]
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,638 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:20 http://au.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://au.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://au.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://au.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://au.archive.ubuntu.com precise-backports/main Sources                
Hit http://au.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://au.archive.ubuntu.com precise-backports/universe Sources            
Hit http://au.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://au.archive.ubuntu.com precise-backports/main i386 Packages   
Hit http://au.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://au.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://au.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://au.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://au.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://au.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://au.archive.ubuntu.com precise/main Translation-en_AU                
Hit http://au.archive.ubuntu.com precise/main Translation-en                   
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://au.archive.ubuntu.com precise/restricted Translation-en_AU          
Hit http://au.archive.ubuntu.com precise/restricted Translation-en             
Hit http://au.archive.ubuntu.com precise/universe Translation-en               
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en_AU        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://au.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en_AU  
Hit http://au.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://au.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://au.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://au.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://au.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 2,608 kB in 8s (320 kB/s)                                              
Reading package lists... Done
john@john-OptiPlex-755:~/rtl8812au$ sudo apt-get install linux-headers-generic build-essential git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.
john@john-OptiPlex-755:~/rtl8812au$ git clone https://github.com/gnab/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Counting objects: 398, done.
remote: Total 398 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (398/398), 1.44 MiB | 244 KiB/s, done.
Resolving deltas: 100% (155/155), done.
john@john-OptiPlex-755:~/rtl8812au$ cd ~/rtl8812au
john@john-OptiPlex-755:~/rtl8812au$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-68-generic-pae/build M=/home/john/rtl8812au  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic-pae'
  CC [M]  /home/john/rtl8812au/core/rtw_cmd.o
  CC [M]  /home/john/rtl8812au/core/rtw_security.o
  CC [M]  /home/john/rtl8812au/core/rtw_debug.o
  CC [M]  /home/john/rtl8812au/core/rtw_io.o
  CC [M]  /home/john/rtl8812au/core/rtw_ioctl_query.o
  CC [M]  /home/john/rtl8812au/core/rtw_ioctl_set.o
  CC [M]  /home/john/rtl8812au/core/rtw_ieee80211.o
  CC [M]  /home/john/rtl8812au/core/rtw_mlme.o
  CC [M]  /home/john/rtl8812au/core/rtw_mlme_ext.o
  CC [M]  /home/john/rtl8812au/core/rtw_wlan_util.o
  CC [M]  /home/john/rtl8812au/core/rtw_vht.o
  CC [M]  /home/john/rtl8812au/core/rtw_pwrctrl.o
  CC [M]  /home/john/rtl8812au/core/rtw_rf.o
  CC [M]  /home/john/rtl8812au/core/rtw_recv.o
  CC [M]  /home/john/rtl8812au/core/rtw_sta_mgt.o
  CC [M]  /home/john/rtl8812au/core/rtw_ap.o
  CC [M]  /home/john/rtl8812au/core/rtw_xmit.o
  CC [M]  /home/john/rtl8812au/core/rtw_p2p.o
  CC [M]  /home/john/rtl8812au/core/rtw_tdls.o
  CC [M]  /home/john/rtl8812au/core/rtw_br_ext.o
  CC [M]  /home/john/rtl8812au/core/rtw_iol.o
  CC [M]  /home/john/rtl8812au/core/rtw_sreset.o
  CC [M]  /home/john/rtl8812au/core/efuse/rtw_efuse.o
  CC [M]  /home/john/rtl8812au/os_dep/osdep_service.o
  CC [M]  /home/john/rtl8812au/os_dep/linux/os_intfs.o
/home/john/rtl8812au/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/john/rtl8812au/os_dep/linux/os_intfs.c:437:2: error: implicit declaration of function ‘create_proc_read_write_entry’ [-Werror=implicit-function-declaration]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:437:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:444:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:629:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:636:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:643:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:654:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/rtl8812au/os_dep/linux/os_intfs.c:670:8: warning: assignment makes pointer from integer without a cast [enabled by default]
cc1: some warnings being treated as errors
make[2]: *** [/home/john/rtl8812au/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/john/rtl8812au] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic-pae'
make: *** [modules] Error 2
john@john-OptiPlex-755:~/rtl8812au$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/3.2.0-68-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `8812au.ko': No such file or directory
make: *** [install] Error 1
john@john-OptiPlex-755:~/rtl8812au$ sudo modprobe 8812au^C
john@john-OptiPlex-755:~/rtl8812au$ 
```

---

### Post by praseodym on 2014-09-18
Try it like this:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/29/51/6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz
tar xvf 6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz 
cd rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100
make
sudo make install 
```

---

### Post by harmkuiper on 2014-09-19
> **JohnMac said:**
> Hi,

I cannot get my EW-7811UTC driver to install on my PC running 12.04. I do have internet connected. This is the code I get culminating with "No such file or directory.

Any hints


j[CODE]ohn@john-OptiPlex-755:~$ cd ~/rtl8812au
john@john-OptiPlex-755:~/rtl8812au$ make clean
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
john@john-OptiPlex-755:~/rtl8812au$ sudo make install
[sudo] password for john: 
[B]install -p -m 644 8812au.ko  /lib/modules/3.2.0-68-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `8812au.ko': No such file or directory
make: *** [install] Error 1[/B]

You first need to enter the "make" command before the "sudo make install command". Please see Chilli555's instructions on the first page which contains the code for how to recompile if you have a new kernel!

---

### Post by JohnMac on 2014-09-20
Good thanks that works, thanks praseodym. Don't know what the code actually does but  I did change kernals so I found I had to recompile using chili555's code.

):P

---

### Post by anin0 on 2014-11-14
Man, Thank you so much for the "five minutes" method! I managed to install the driver for my [h=1]D-Link DWA-182 rev C1 [SIZE=2]following exactly the procedure you provided.[/SIZE][/h]

---

### Post by Pein1911 on 2014-12-09
I have Ubuntu 14.10 with kernel 3.16, any lucky to install driver !? thanks

a question is why they lock down drivers with kernel version, it made difficult to install driver with newer version of Ubuntu :(

---

### Post by chili555 on 2014-12-09
> **Pein1911 said:**
> I have Ubuntu 14.10 with kernel 3.16, any lucky to install driver !? thanks

a question is why they lock down drivers with kernel version, it made difficult to install driver with newer version of Ubuntu :(It builds for me, albeit with a couple of warnings, on 3.16.0-25 using the method I posted in post #2.

Did you try? What were your errors?

---

### Post by Pein1911 on 2014-12-10
> **chili555 said:**
> It builds for me, albeit with a couple of warnings, on 3.16.0-25 using the method I posted in post #2.

Did you try? What were your errors?

Wow, its work perfectly, thank you !

Edit: I have tested performance and this version of driver was really bad !  While my Onboard wifi chipset from Intel performance was very good both Windows and Ubuntu at Down: 25 Mbps , Up: 6Mbps

Here is on Windows test:

[IMG]http://www.speedtest.net/result/3974030954.png[/IMG]

Here is on linux with driver post #2:

[IMG]https://dl.dropboxusercontent.com/u/91518197/3974022075.png[/IMG]

---

### Post by Pein1911 on 2014-12-10
I have read this topic, but all newer versions driver in this topic are not installable with kernel 3.16
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/1](https://github.com/abperiasamy/rtl8812AU_8821AU_linux/issues/1)

---

### Post by joshua_bankhead on 2015-02-22
> **chili555 said:**
> Here is how you install it in about five minutes.

Leo: "Hey, friend, can I borrow your ethernet connection for just a few minutes? I brought along six of your favorite beverage."

Friend: "Sure, Leo, glad to help you! Let me put a couple of those beverages on ice."

You then open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

Your wireless should now be working. Detach the ethernet, thank the friend and enjoy!

Your wireless should now be working.

Questions? Concerns??

it's not working for me

Delll Inspirion 1545
running Ubuntu 14.04

the laptop has a broadcom wireless card built in.  I could not get it to work after following the advice on a thread here in the forum.

I purchased this EdimaxEW7811UTC to use instead, it was the only one on new egg that stated it was compatible with linux.

i have followed your instructions, including those of the OP about swithcing the settings to use main server.

after runnung 

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

i get
```
Ign http://archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.ubuntu.com trusty-updates InRelease
Ign http://archive.ubuntu.com trusty-backports InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://archive.ubuntu.com trusty-security InRelease
Ign http://archive.ubuntu.com trusty-proposed InRelease
Hit http://archive.ubuntu.com trusty Release.gpg
Hit http://extras.ubuntu.com trusty Release
Get:1 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:2 http://archive.ubuntu.com trusty-backports Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty-security Release.gpg
Hit http://archive.ubuntu.com trusty-proposed Release.gpg
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://archive.ubuntu.com trusty Release                 
Get:3 http://archive.ubuntu.com trusty-updates Release [62.0 kB]       
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages   
Get:4 http://archive.ubuntu.com trusty-backports Release [62.0 kB]       
Hit http://archive.ubuntu.com trusty-security Release                    
Hit http://archive.ubuntu.com trusty-proposed Release                  
Hit http://archive.ubuntu.com trusty/main Sources                      
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources              
Hit http://archive.ubuntu.com trusty/multiverse Sources            
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages    
Hit http://archive.ubuntu.com trusty/universe amd64 Packages      
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages    
Hit http://archive.ubuntu.com trusty/main i386 Packages           
Hit http://archive.ubuntu.com trusty/restricted i386 Packages     
Hit http://archive.ubuntu.com trusty/universe i386 Packages       
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages     
Hit http://archive.ubuntu.com trusty/main Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Get:5 http://archive.ubuntu.com trusty-updates/main Sources [179 kB]
Get:6 http://archive.ubuntu.com trusty-updates/restricted Sources [2,061 B]
Get:7 http://archive.ubuntu.com trusty-updates/universe Sources [104 kB]      
Get:8 http://archive.ubuntu.com trusty-updates/multiverse Sources [4,463 B]
Get:9 http://archive.ubuntu.com trusty-updates/main amd64 Packages [441 kB]  
Get:10 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,875 B]
Get:11 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [253 kB]
Get:12 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.2 kB]
Get:13 http://archive.ubuntu.com trusty-updates/main i386 Packages [431 kB]    
Get:14 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [8,846 B]
Get:15 http://archive.ubuntu.com trusty-updates/universe i386 Packages [253 kB]
Get:16 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [11.3 kB]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Get:17 http://archive.ubuntu.com trusty-backports/main Sources [5,298 B]       
Get:18 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]    
Get:19 http://archive.ubuntu.com trusty-backports/universe Sources [20.0 kB]   
Get:20 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B] 
Get:21 http://archive.ubuntu.com trusty-backports/main amd64 Packages [5,536 B]
Get:22 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:23 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [24.1 kB]
Get:24 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:25 http://archive.ubuntu.com trusty-backports/main i386 Packages [5,550 B] 
Get:26 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:27 http://archive.ubuntu.com trusty-backports/universe i386 Packages [24.1 kB]
Get:28 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Hit http://archive.ubuntu.com trusty-security/main Sources                     
Hit http://archive.ubuntu.com trusty-security/restricted Sources               
Hit http://archive.ubuntu.com trusty-security/universe Sources                 
Hit http://archive.ubuntu.com trusty-security/multiverse Sources               
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages              
Hit http://archive.ubuntu.com trusty-security/restricted amd64 Packages        
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages          
Hit http://archive.ubuntu.com trusty-security/multiverse amd64 Packages        
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Hit http://archive.ubuntu.com trusty-security/restricted i386 Packages         
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages           
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages         
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://archive.ubuntu.com trusty-proposed/main amd64 Packages              
Hit http://archive.ubuntu.com trusty-proposed/restricted amd64 Packages        
Hit http://archive.ubuntu.com trusty-proposed/universe amd64 Packages          
Hit http://archive.ubuntu.com trusty-proposed/multiverse amd64 Packages        
Hit http://archive.ubuntu.com trusty-proposed/main i386 Packages               
Hit http://archive.ubuntu.com trusty-proposed/restricted i386 Packages         
Hit http://archive.ubuntu.com trusty-proposed/universe i386 Packages           
Hit http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages         
Hit http://archive.ubuntu.com trusty-proposed/main Translation-en              
Hit http://archive.ubuntu.com trusty-proposed/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-proposed/universe Translation-en          
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,923 kB in 15s (126 kB/s)                                             
Reading package lists... Done

```

i have restarted and pulled the ethernet cable and nothing.  the network settings dont even register the usb device is plugged in

---

### Post by chili555 on 2015-02-23
> the laptop has a broadcom wireless card built in. Frankly, I'd much rather troubleshoot the Broadcom. I am answering your previous post on the subject.

---

### Post by dave173 on 2015-03-14
ok i'm trying to get wifi configured with this adapter as well. i'm on 14.04 64-bit. Currently connected to ethernet. The driver seems to have built fine for me. i actually had it working using GNOME and NetworkManager (just to make sure it COULD actually work) but I uninstalled NetworkManager as once this box is used in production, GNOME will be going away too... and i will be configuring a few more machines with the same config with command line only. SO with all that said, if someone could help me get up and running, i'd be most appreciative.

While connected to ethernet, i have both LAN and WAN. Once unplugged, I have neither however i can ping localhost and my own LAN IP... not the router or any other clients. The rest of the network is running Windows, Android and iOS devices without any problems... on both bands. 

**So far, I have:**
[LIST]
[*]followed chilli's instructions for building and loading driver 
[*]unplug ethernet cable 
[*]```
sudo vi /etc/network/interfaces
``` 
[/LIST]
```
# The loopback network interface
auto lo
iface lo inet loopback

# The wifi network interface
auto wlan0
iface wlan0 inet static
    address 192.168.1.117
    netmask 255.255.255.0
    network 192.168.1.1
    broadcast 192.168.1.255
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
#these 2 lines generated by wpa-supplicant
    wpa-ssid dafast
wpa-psk a1942e80aef489f5edd436dc47319430ccaf3fc09d27603

auto eth0
iface eth0 inet static
address 192.168.1.117
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4
```
[LIST]
[*]```
sudo reboot
``` 
[*]```
iwconfig
``` 
[/LIST]
 > lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.745 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


[LIST]
[*]```
**dpas@KSPA:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:13:72:ca:b6:75  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:feca:b675/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7770819 (7.7 MB)  TX bytes:1212582 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12886 (12.8 KB)  TX bytes:12886 (12.8 KB)

wlan0     Link encap:Ethernet  HWaddr 74:da:38:25:cb:cf  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:806 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

``` 
[*]```
**dpas@KSPA:~$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: NM10/ICH7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:ca:b6:75
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.117 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:efbef000-efbeffff ioport:ccc0(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 74:da:38:25:cb:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.117 multicast=yes wireless=unassociated
``` 
[*]```
[BOLD]dpas@KSPA:~$ sudo lsmod[/BOLD]
Module                  Size  Used by
ip6table_filter        12815  0 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_ipv4      15012  4 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_tcpudp              12884  4 
xt_conntrack           12760  4 
nf_conntrack           96976  2 xt_conntrack,nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  6 ip6table_filter,ip_tables,xt_tcpudp,xt_conntrack,iptable_filter,ip6_tables
cfg80211              484040  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
gpio_ich               13476  0 
snd_hda_codec_idt      54762  1 
snd_hda_intel          56531  3 
snd_hda_codec         192906  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
dcdbas                 14928  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
8812au               1141073  0 
radeon               1522576  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
ttm                    93424  1 radeon
snd                    69322  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         55071  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
lpc_ich                21080  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
parport_pc             32701  0 
ppdev                  17671  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
psmouse               106714  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
e100                   40819  0 
mii                    13934  1 e100
``` 
[/LIST]

Perhaps this is helpful too?
```
**dpas@KSPA:~/rtl8812au$ sudo ps -ef | grep wlan0**
root       740     1  0 18:41 ?        00:00:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
```

/var/run/wpa_supplicant is empty




I feel like i HAVE to be REALLY close...?

---

### Post by chili555 on 2015-03-15
>     I feel like i HAVE to be REALLY close...? I think you are. > wpa-psk a1942e80aef489f5edd436dc47319430ccaf3fc09d27603Is this your key in plain text or disguised by *wpa_password*? The file /etc/network/interfaces expects the key in plain text.

Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v for verbose should produce enough output that you can see what, if anything, is amiss.

---

### Post by dave173 on 2015-03-15
> **chili555 said:**
> I think you are. Is this your key in plain text or disguised by *wpa_password*? The file /etc/network/interfaces expects the key in plain text.

Gotcha. Changed that and it definitely seemed to help. Not there yet...




> **chili555 said:**
> Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```The -v for verbose should produce enough output that you can see what, if anything, is amiss.

I reduced /etc/network/interfaces to just the entries for auto lo and auto wlon0. Here's the output from above:

```
**dpas@KSPA:~$ sudo ifdown wlan0 && sudo ifup -v wlan0**
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 4860).
wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "dafast" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.1.117/255.255.255.0 broadcast 192.168.1.255           dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.

```

---

### Post by chili555 on 2015-03-15
Did you, by chance, create a wpa_supplicant.conf file? Do all the entries match?

You might try temporarily removing it after backing up:```
sudo mv /etc/wpa_supplicant.conf  ~
```That moves it to your /home/user directory. Now try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Are these ugly errors resolved or at least reduced?> ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argumentAnd, if so, does it connect?

---

### Post by dave173 on 2015-03-15
> **chili555 said:**
> Did you, by chance, create a wpa_supplicant.conf file? Do all the entries match?

I was not using one. Should I?

---

### Post by chili555 on 2015-03-15
> **dave173 said:**
> I was not using one. Should I?Nope.

May we proofread your /etc/network/interfaces file, with the password redacted, of course?

Are you certain that the wireless device is operating correctly? Does it scan and see your network?```
sudo iwlist wlan0 scan
rfkill list all
iwconfig
```

---

### Post by dave173 on 2015-03-15
> **chili555 said:**
> 

May we proofread your /etc/network/interfaces file, with the password redacted, of course?
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


#auto wlan0
#iface wlan0 inet dhcp
#        wireless-essid dafast
#        wireless-mode Managed
#       wireless-key MYPSK




# The wifi network interface
auto wlan0
iface wlan0 inet static
    address 192.168.1.117
    netmask 255.255.255.0
    network 192.168.1.1
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
    wpa-ssid dafast
    #wpa-psk a1942e80aef4ade4f4b7089d1d0dc89f5edd436dc47319430ccaf3fc09d27603
    wpa-psk MYPSK






# The primary network interface
#jauto eth0
#iface eth0 inet dhcp

```


> **chili555 said:**
> 
Are you certain that the wireless device is operating correctly? Does it scan and see your network?```
sudo iwlist wlan0 scan
rfkill list all
iwconfig
```
It's seeing it. [COLOR=#ff0000]**In red bold below.**[/COLOR]

```
**dpaS@KSPA:/$ sudo iwlist wlan0 scan**
iwconfig
wlan0     Scan completed :
          Cell 01 - Address: B0:A7:37:B1:B9:E1
                    ESSID:"DIRECT-roku-422"
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD370050F204104A00011010440001021049000600372A0001201054000800060050F20400011011000F4449524543542D726F6B752D343232
                    Quality=0/100  Signal level=62/100
          Cell 02 - Address: CC:35:40:3A:A1:61
                    ESSID:"Elladog"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Quality=0/100  Signal level=64/100
          Cell 03 - Address: CE:35:40:3A:A1:62
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=64/100
          Cell 04 - Address: CE:03:FA:41:DC:51
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=74/100
          Cell 05 - Address: CE:03:FA:41:DC:52
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=0/100  Signal level=76/100
          Cell 06 - Address: B2:CA:B5:57:89:50
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=48/100
          Cell 07 - Address: 54:A0:50:59:99:58
                    ESSID:"daslow"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    Quality=0/100  Signal level=100/100
          Cell 08 - Address: 30:91:8F:5D:68:40
                    ESSID:"Mando"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=0/100  Signal level=56/100
          Cell 09 - Address: 02:1D:D1:20:BB:60
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=88/100
[COLOR=#ff0000]**          Cell 10 - Address: 54:A0:50:59:99:5C**[/COLOR]
[COLOR=#ff0000]**                    ESSID:"dafast"**[/COLOR]
[COLOR=#ff0000]**                    Protocol:IEEE 802.11AC**[/COLOR]
[COLOR=#ff0000]**                    Mode:Master**[/COLOR]
[COLOR=#ff0000]**                    Frequency:5.745 GHz**[/COLOR]
[COLOR=#ff0000]**                    Encryption key:on**[/COLOR]
[COLOR=#ff0000]**                    Bit Rates:867 Mb/s**[/COLOR]
[COLOR=#ff0000]**                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00**[/COLOR]
[COLOR=#ff0000]**                    IE: IEEE 802.11i/WPA2 Version 1**[/COLOR]
[COLOR=#ff0000]**                        Group Cipher : CCMP**[/COLOR]
[COLOR=#ff0000]**                        Pairwise Ciphers (1) : CCMP**[/COLOR]
[COLOR=#ff0000]**                        Authentication Suites (1) : PSK**[/COLOR]
[COLOR=#ff0000]**                    Quality=100/100  Signal level=84/100**[/COLOR]

```



```
**dpas@KSPA:/$ rfkill list all**
**igdpas@KSPA:/$ iwconfig**
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.745 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by chili555 on 2015-03-15
Please amend as noted:```
# The loopback network interface
auto lo
iface lo inet loopback


#auto wlan0
#iface wlan0 inet dhcp
#        wireless-essid dafast
#        wireless-mode Managed
#       wireless-key MYPSK




# The wifi network interface
auto wlan0
iface wlan0 inet static
    address 192.168.1.117
    netmask 255.255.255.0
[COLOR="#FF0000"]# [/COLOR] network 192.168.1.1
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
    wpa-ssid dafast
    wpa-psk MYPSK
```Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Are the errors removed or reduced and can you connect?

---

### Post by dave173 on 2015-03-15
> **chili555 said:**
> Please amend as noted:```
# The loopback network interface

```Then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Are the errors removed or reduced and can you connect?

Dang, no dice.

```
**dpas@KSPA:~$ sudo ifdown wlan0 && sudo ifup -v wlan0**
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.wlan0.pid
Stopped /sbin/wpa_supplicant (pid 3035).
wpa_supplicant: removing /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "daveh0_fast" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.1.117/255.255.255.0 broadcast 192.168.1.255           dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.

```

---

### Post by chili555 on 2015-03-15
> [COLOR="#FF0000"][B]Cell 10 - Address: 54:A0:50:59:99:5C
                    ESSID:"dafast"
                    Protocol:IEEE 802.11AC
                    Mode:Master
                    Frequency:5.745 GHz
                    Encryption key:on
                    Bit Rates:867 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=84/100[/B][/COLOR]However, you tried to connect to:> wpa_supplicant: wpa-ssid "[COLOR="#FF0000"]daveh0_fast[/COLOR]" -- OKWhere does *daveh0_fast *come from???

---

### Post by dave173 on 2015-03-15
oops, my bad. was just altaring the name of my network for this post. 'daveh0_fast' is the actual name... i forgot to change it in the output.

---

### Post by chili555 on 2015-03-15
Something is still wrong. May I see:```
ls /etc | grep wpa
```Also, please see your Private Messages.

---

### Post by dave173 on 2015-03-15
> **chili555 said:**
> Something is still wrong. May I see:```
ls /etc | grep wpa
```Also, please see your Private Messages.

```
**dpasi@KSPA:~$ ls /etc | grep wpa**
wpa_supplicant/


```

---

### Post by chili555 on 2015-03-15
> dpasi@KSPA:~$ ls /etc | grep wpa
wpa_supplicant/Ah, haaa!!! Gotcha!

How about:```
ls /etc/wpa_supplicant
```I suspect we will find some kind of conf file in there and we'll move it out of the way:```
sudo mv /etc/wpa_supplicant/whatever  ~
```And then try again:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```

---

### Post by dave173 on 2015-03-15
Progress. Errors gone. There were 3 .sh files in there functions.sh, ifupdown.sh and action_wpa.sh

```
**dpas@KSPA:~$ sudo ifdown wlan0 && sudo ifup -v wlan0**
ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: failed to stat component /etc/network/if-pre-up.d/wpasupplicant: No such file or directory
ip addr add 192.168.1.117/255.255.255.0 broadcast 192.168.1.255       dev wlan0 label wlan0
RTNETLINK answers: File exists
Failed to bring up wlan0.
```

---

### Post by chili555 on 2015-03-15
> There were 3 .sh files in there functions.sh, ifupdown.sh and action_wpa.shThose really aren't conf files. We may need to move them back and take a look at their permissions; for reference:```
-rwxr-xr-x   1 root root   945 Oct 10 10:53 action_wpa.sh
-rwxr-xr-x   1 root root 25907 Oct 10 10:53 functions.sh
-rwxr-xr-x   1 root root  4696 Oct 10 10:53 ifupdown.sh
```The key may possibly be that they must be readable and executable.

However, it's all moot if you now can connect. Have you good news?

---

### Post by dave173 on 2015-03-15
Permissions are all in check (after moving them back) and no connection/good news...

```
**dpas@KSPA:~$ ll /etc/wpa_supplicant/**
total 56K
drwxr-xr-x   2 root root 4.0K Mar 15 18:17 ./
drwxr-xr-x 143 root root  12K Mar 15 09:54 ../
-rwxr-xr-x   1 root root  945 Mar  5  2014 action_wpa.sh*
-rwxr-xr-x   1 root root  26K Mar  5  2014 functions.sh*
-rwxr-xr-x   1 root root 4.6K Mar  5  2014 ifupdown.sh*
```

---

### Post by tritoch23 on 2015-03-25
Hi,  I was able to install the module just fine using the 5 minutes method. However, I have a slightly different problem. Whenever I update my Linux kernel, the module stops working and I'm forced to reinstall it using the procedure above. Is there a way to install the module so that it exists in future kernel updates?

---

### Post by chili555 on 2015-03-26
> **tritoch23 said:**
> Hi,  I was able to install the module just fine using the 5 minutes method. However, I have a slightly different problem. Whenever I update my Linux kernel, the module stops working and I'm forced to reinstall it using the procedure above. Is there a way to install the module so that it exists in future kernel updates?I'm sure there is using the dkms mechanism. I just don't know how to use it. Sorry.

---

### Post by kirannbishwa01 on 2015-09-21
[B]updates:
I was getting an error message at[/B]
*make*
**error message:** linux-headers-3.19.0-28-generic not found
**So, updated the linux-header**
*sudo apt-get install -y build-essential linux-headers-3.19.0-28-generic*

**after that,**
[I]cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au[/I]

Works perfect now. Thank you chili555 for the code.

---

### Post by chili555 on 2015-09-21
> sudo apt-get install -y build-essential linux-headers-3.19.0-28-genericI would also do:```
sudo apt-get install linux-headers-generic
```You can do that now independently. By so doing, the headers will automagically be updated every time a later linux image is installed by Update Manager.

Glad it's working!

---

### Post by balcorn80 on 2016-01-31
The 5 Minute Plan worked perfectly for me using Lubuntu 15.10 with this modification for Kernel 4: 

[COLOR=#000000]for Ubuntu 15.10 and greater versions (kernel >= 4)[/COLOR]
[COLOR=#000000]Code:
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/csssuf/rtl8812au.git](https://github.com/csssuf/rtl8812au.git)[/COLOR]
from here:[http://ubuntuforums.org/showthread.php?t=2275709](http://ubuntuforums.org/showthread.php?t=2275709)

I also used 

[COLOR=#000000]2. Turn off power saving feature for USB wifi ([/COLOR][https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters](https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters)[COLOR=#000000])[/COLOR]
[COLOR=#000000]Modify ~/rtl8812au/Makefile :[/COLOR][COLOR=#000000]Code:
replace CONFIG_POWER_SAVING = y with CONFIG_POWER_SAVING = n [/COLOR]
because it made sense to my noob brain.

Thanks!

---

### Post by psychedelicwonders2 on 2016-04-14
> **chili555 said:**
> 
You then open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

Your wireless should now be working. Detach the ethernet, 

So I am trying to get a new Asus AC56 wifi USB adapter to work and followed the above code, but when I got to the last part, sudo modprobe 8812au - nothing seemed to happen and the adapter isn't working?

```
psychwonders@MainStation:~$ cd ~/rtl8812au
psychwonders@MainStation:~/rtl8812au$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-18-generic/build M=/home/psychwonders/rtl8812au  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-18-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-18-generic'
psychwonders@MainStation:~/rtl8812au$ sudo make install
[sudo] password for psychwonders: 
install -p -m 644 8812au.ko  /lib/modules/4.4.0-18-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 4.4.0-18-generic
psychwonders@MainStation:~/rtl8812au$ sudo modprobe 8812au
psychwonders@MainStation:~/rtl8812au$ ^C
psychwonders@MainStation:~/rtl8812au$
```

Do I need to add/create my wireless network somewhere within Ubuntu, or should all available networks show up once the adapter is functioning properly?

For the record I am using 16.04 Final Beta



An update - Ubuntu can now see the wireless networks available, but no matter how many times i enter the password, it will not connect to it?  I've like 10x and it still won't.

Also even though the Asus AC56 sees the wifi networks, there is a blue LED light that is supposed to be on with this adapter and it currently is not.

If I unplug the adapter all of the available wifi networks disappear.  

So it's slightly working, but not quite 100%?




New update - now after continue to try the network password it seems  to have finally taken/saved and actually connected via wifi and I have  been able to disconnect the ethernet - no clue what happened and why it  finally worked after the uptenth time, but seems to be good to go now?

Is there any wifi test within ubuntu that I should run to make sure everything is configured properly?

---

### Post by chili555 on 2016-04-14
> **psychedelicwonders2 said:**
> Is there any wifi test within ubuntu that I should run to make sure everything is configured properly?I suggest that you simply run it and post back if there is any further problem. In that case, we'll need to see the wireless-info from here:  [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by psychedelicwonders2 on 2016-04-14
So the adapter seems to work fine except when I shut down the computer & restart it, Ubuntu doesn't recognize it and I have physically unplug it and plug it back in and then it boots up the wifi network right away - what is causing this and how do I fix it?

---

### Post by chili555 on 2016-04-14
Is the driver loading automatically on boot? After a fresh boot when it is not working as expected, run:```
lsmod | grep 8812
```If the driver is not there, do:```
sudo modprobe 8812au
```Does that start it? If so, next do:```
sudo -i
echo 8812au  >>  /etc/modules
exit
```You should be all set.

---

### Post by psychedelicwonders2 on 2016-04-14
I think that's the problem is the 8812au driver because when I tried to run that last part of the code in the terminal during the initial setup/intall that part of the code didn't do anything:

```
psychwonders@MainStation:~/rtl8812au$ sudo modprobe 8812au
psychwonders@MainStation:~/rtl8812au$ ^C
psychwonders@MainStation:~/rtl8812au$
```

When I run ```
sudo modprobe 8812au
```  to start it, will the terminal show anything or will the wifi just become enabled in the top right menu?

---

### Post by chili555 on 2016-04-14
> that part of the code didn't do anything:That's fine. In this context, 'nothing' is shorthand for, "Command executed as given. There are no warnings or errors to report. Next?"> or will the wifi just become enabled in the top right menu? Hopefully.

But you didn't tell us if the driver was loaded on a fresh boot. Did you check? Would you please?

---

### Post by psychedelicwonders2 on 2016-04-14
Ok so after a restart the adapter didn't start up again and I ran all the code you suggested, but it didn't seem to activate it?

```
psychwonders@MainStation:~$ lsmod | grep 8812
8812au                991232  0
psychwonders@MainStation:~$ sudo modprobe 8812au
[sudo] password for psychwonders: 
psychwonders@MainStation:~$ sudo -i
root@MainStation:~# echo 8812au  >>  /etc/modules
root@MainStation:~# ^C


```

Seems something isn't right is it?

---

### Post by kss18 on 2016-05-01
Chili, That worked like a charm. THANK YOU!

---

### Post by Cristian_Perieanu on 2016-07-03
Hello Guys,

I have a similar AC600 dual band adaptor and the below set of commands was working fine until I've switched to ubuntu 16.1.
My assumption is that this is something with the new version of Kernel, but I am no expert and I need somebody's help to figure this one out.
When I run the last command nothing happens.
```

sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au

```
I think something is wrong because of the following:
```
~/rtl8812AU_8821AU_linux-> ndiswrapper -l
autorun : invalid driver!
netrtwlanu : driver installed
    device (0BDA:A811) present (alternate driver: 8812au)
netrtwlanu_xp : invalid driver!
rtlbt : invalid driver!

```

Can you please help me with a solution?

---

### Post by chili555 on 2016-07-03
> **Cristian_Perieanu said:**
> Hello Guys,

I have a similar AC600 dual band adaptor and the below set of commands was working fine until I've switched to ubuntu 16.1.
My assumption is that this is something with the new version of Kernel, but I am no expert and I need somebody's help to figure this one out.
When I run the last command nothing happens.
```

sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au

```
I think something is wrong because of the following:
```
~/rtl8812AU_8821AU_linux-> ndiswrapper -l
autorun : invalid driver!
netrtwlanu : driver installed
    device (0BDA:A811) present (alternate driver: 8812au)
netrtwlanu_xp : invalid driver!
rtlbt : invalid driver!

```

Can you please help me with a solution?Please try this:```
sudo apt-get purge ndiswrapper-common
sudo apt-get purge ndiswrapper-utils-1.9
```Reboot.

You don't want or need ndiswrapper if you are using the preferable native driver 8812au.

---

### Post by scorpvk on 2016-08-18
Good afternoon!
I get an error make
[ATTACH]270732[/ATTACH]
Help me, please

---

### Post by chili555 on 2016-08-18
> **scorpvk said:**
> Good afternoon!
I get an error make
[ATTACH]270732[/ATTACH]
Help me, pleaseYou are trying to compile mt7601u. The subject of this thread is the very different 8812au. Please start your own new thread.

By the way, mt7601u is included by default in kernel versions 4.4 and later. Consider upgrading.

---

### Post by maxbar on 2016-08-21
I've been having trouble with proprietary and gnab's (worked intermittently only) - the only one that worked reliably for me (even after restart) is abperiasamy's:

[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

As per README.md):
Download, extract, cd into dir, make clean, make, make install, reboot.
(following the instructions at the top for the DKMS install did not work for me - no compile errors or anything, just the adapter won't start / blue light won't turn on / ifconfig won't list it)

The thing I'm struggling though now is using this adapter in AP mode with a wired connection to the cable modem - I followed various guides, using command line and GUI methods, so far no joy :(
Any link to a working and up-to-date guide for running this adapter in AP mode for Ubuntu 16.04.1 would be much appreciated!

---

### Post by chili555 on 2016-08-21
> **maxbar said:**
> I've been having trouble with proprietary and gnab's (worked intermittently only) - the only one that worked reliably for me (even after restart) is abperiasamy's:

[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

As per README.md):
Download, extract, cd into dir, make clean, make, make install, reboot.
(following the instructions at the top for the DKMS install did not work for me - no compile errors or anything, just the adapter won't start / blue light won't turn on / ifconfig won't list it)

The thing I'm struggling though now is using this adapter in AP mode with a wired connection to the cable modem - I followed various guides, using command line and GUI methods, so far no joy :(
Any link to a working and up-to-date guide for running this adapter in AP mode for Ubuntu 16.04.1 would be much appreciated!Not all devices support AP mode. What does this report?```
iw list
```My Intel says:> Supported interface modes:
		 * IBSS
		 * managed
		 *[COLOR="#FF0000"] AP[/COLOR]
		 * AP/VLAN
		 * monitor
		 * P2P-client
		 * P2P-GO
		 * P2P-device


---

### Post by maxbar on 2016-08-22
I didn't get an email that you had responded... I'm now subscribed to this thread and I'll get an email (hopefully) :)

Re. AP support, it def. does, that's the first I checked, but here it goes:

```
Wiphy phy0
        max # scan SSIDs: 9
        max scan IEs length: 2304 bytes
        Retry short limit: 7
        Retry long limit: 4
        Coverage class: 0 (up to 0m)
        Supported Ciphers:
                * WEP40 (00-0f-ac:1)
                * WEP104 (00-0f-ac:5)
                * TKIP (00-0f-ac:2)
                * CCMP (00-0f-ac:4)
        Available Antennas: TX 0 RX 0
        Supported interface modes:
                 * IBSS
                 * managed
                 * AP
                 * monitor
                 * P2P-client
                 * P2P-GO
        Band 1:
                Capabilities: 0x1862
                        HT20/HT40
                        Static SM Power Save
                        RX HT20 SGI
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 16 usec (0x07)
                HT TX/RX MCS rate indexes supported: 0-15, 32
                Bitrates (non-HT):
                        * 1.0 Mbps
                        * 2.0 Mbps
                        * 5.5 Mbps
                        * 11.0 Mbps
                        * 6.0 Mbps
                        * 9.0 Mbps
                        * 12.0 Mbps
                        * 18.0 Mbps
                        * 24.0 Mbps
                        * 36.0 Mbps
                        * 48.0 Mbps
                        * 54.0 Mbps
                Frequencies:
                        * 2412 MHz [1] (20.0 dBm)
                        * 2417 MHz [2] (20.0 dBm)
                        * 2422 MHz [3] (20.0 dBm)
                        * 2427 MHz [4] (20.0 dBm)
                        * 2432 MHz [5] (20.0 dBm)
                        * 2437 MHz [6] (20.0 dBm)
                        * 2442 MHz [7] (20.0 dBm)
                        * 2447 MHz [8] (20.0 dBm)
                        * 2452 MHz [9] (20.0 dBm)
                        * 2457 MHz [10] (20.0 dBm)
                        * 2462 MHz [11] (20.0 dBm)
                        * 2467 MHz [12] (20.0 dBm) (no IR)
                        * 2472 MHz [13] (20.0 dBm) (no IR)
                        * 2484 MHz [14] (20.0 dBm) (no IR)
        Band 2:
                Capabilities: 0x1862
                        HT20/HT40
                        Static SM Power Save
                        RX HT20 SGI
                        RX HT40 SGI
                        No RX STBC
                        Max AMSDU length: 7935 bytes
                        DSSS/CCK HT40
                Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
                Minimum RX AMPDU time spacing: 16 usec (0x07)
                HT TX/RX MCS rate indexes supported: 0-15, 32
                Bitrates (non-HT):
                        * 6.0 Mbps
                        * 9.0 Mbps
                        * 12.0 Mbps
                        * 18.0 Mbps
                        * 24.0 Mbps
                        * 36.0 Mbps
                        * 48.0 Mbps
                        * 54.0 Mbps
                Frequencies:
                        * 5170 MHz [34] (disabled)
                        * 5180 MHz [36] (20.0 dBm) (no IR)
                        * 5190 MHz [38] (20.0 dBm) (no IR)
                        * 5200 MHz [40] (20.0 dBm) (no IR)
                        * 5210 MHz [42] (20.0 dBm) (no IR)
                        * 5220 MHz [44] (20.0 dBm) (no IR)
                        * 5230 MHz [46] (20.0 dBm) (no IR)
                        * 5240 MHz [48] (20.0 dBm) (no IR)
                        * 5260 MHz [52] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5500 MHz [100] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5520 MHz [104] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5540 MHz [108] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5560 MHz [112] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5580 MHz [116] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5600 MHz [120] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5620 MHz [124] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5640 MHz [128] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5660 MHz [132] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5680 MHz [136] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5700 MHz [140] (20.0 dBm) (no IR, radar detection)
                          DFS state: usable (for 72399 sec)
                          DFS CAC time: 60000 ms
                        * 5745 MHz [149] (20.0 dBm) (no IR)
                        * 5765 MHz [153] (20.0 dBm)
                        * 5785 MHz [157] (20.0 dBm) (no IR)
                        * 5805 MHz [161] (20.0 dBm) (no IR)
                        * 5825 MHz [165] (20.0 dBm) (no IR)
                        * 5920 MHz [184] (disabled)
                        * 5940 MHz [188] (disabled)
                        * 5960 MHz [192] (disabled)
                        * 5980 MHz [196] (disabled)
                        * 6000 MHz [200] (disabled)
                        * 6020 MHz [204] (disabled)
                        * 6040 MHz [208] (disabled)
                        * 6060 MHz [212] (disabled)
                        * 6080 MHz [216] (disabled)
        Supported commands:
                 * new_interface
                 * set_interface
                 * new_key
                 * start_ap
                 * new_station
                 * set_bss
                 * join_ibss
                 * set_pmksa
                 * del_pmksa
                 * flush_pmksa
                 * remain_on_channel
                 * frame
                 * set_channel
                 * connect
                 * disconnect
        Supported TX frame types:
                 * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
                 * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
        Supported RX frame types:
                 * IBSS: 0xd0
                 * managed: 0x40 0xd0
                 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
                 * P2P-client: 0x40 0xd0
                 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
        software interface modes (can always be added):
                 * monitor
        interface combinations are not supported
        Device supports scan flush.

```

---

### Post by Paul5mith on 2017-05-14
I had a problem installing this module and noticed for some reason the Wifi worked if I used ```
 sudo make install 
```  but if I manually copied the module into [FONT=lucida console]/lib/modules/<kernel>/extra[/FONT] then the module loaded but the Wifi repeatedly failed to authenticate.

---

### Post by chili555 on 2017-05-14
> **Paul5mith said:**
> I had a problem installing this module and noticed for some reason the Wifi worked if I used ```
 sudo make install 
```  but if I manually copied the module into [FONT=lucida console]/lib/modules/<kernel>/extra[/FONT] then the module loaded but the Wifi repeatedly failed to authenticate.In fact, sudo make install is the correct method. May I assume that, since you say the wifi works if you do so, that this is not a question or a request for guidance?

---

### Post by makkajunior on 2017-05-16
Im Lost tried everything here and still my wifi is not working should i remove the driver and start from scratch ??????

full update from ubuntu 

fresh install of 16.10 first time user of any linux distro since 97 when i tried a few of the earlie versions and could not make heads nor tails.
so i had to return to the darkside. 

Help me chili555 your our only hope :D

sorry had to quote Star Wars

my be some time lag between you posting and i responding....... i'm in Australia

---

### Post by chili555 on 2017-05-16
> **makkajunior said:**
> Im Lost tried everything here and still my wifi is not working should i remove the driver and start from scratch ??????

full update from ubuntu 

fresh install of 16.10 first time user of any linux distro since 97 when i tried a few of the earlie versions and could not make heads nor tails.
so i had to return to the darkside. 

Help me chili555 your our only hope :D

sorry had to quote Star Wars

my be some time lag between you posting and i responding....... i'm in AustraliaThe methods described above are now about three years old, that's a long time in Linux-years. Please start your own new thread and post:```
lsusb
modinfo 8812au
```If I don't catch it right away, and I may not as I'm away from hope on vacation right now, send me a private message. I'll be glad to help.

---

### Post by makkajunior on 2017-05-17
Thanks mate 

really appriciate your responce

---

### Post by barnaby2 on 2018-01-19
HI Chili555, are you still there?

I followed you until the last step and then got this error message:

barnaby@barnaby-desktop:~/rtl8812au$ sudo modprobe 8812au
modprobe: ERROR: could not insert '8812au': Required key not available
barnaby@barnaby-desktop:~/rtl8812au$ 

do you see the problem. Thanks for being there..

---

### Post by chili555 on 2018-01-19
> modprobe: ERROR: could not insert '8812au': Required key not availableQuite easy, really: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

