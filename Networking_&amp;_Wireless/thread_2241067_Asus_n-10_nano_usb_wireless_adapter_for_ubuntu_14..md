---
title: "Asus n-10 nano usb wireless adapter for ubuntu 14.04 lts"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by cgameing on 2014-08-24
Looked on so many fourms and tried ndiswrapper (with every avaliable .inf driver from the asus cd)
To no sucesss

Please help.

Errorlog...

##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    
tar: Old option 'f' requires an argument.
Try 'tar --help' or 'tar --usage' for more information.
rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308
rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308.tar
USB-N10 Linux Driver Quick Start.txt
Authentication requested [root] for make clean:
install.sh: 38: [: unexpected operator
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
Authentication requested [root] for make driver:
install.sh: 48: [: unexpected operator
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-34-generic/build M=/home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-34-generic'
  CC [M]  /home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308/core/rtw_cmd.o
In file included from /home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308/core/rtw_cmd.c:23:0:
/home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308/include/osdep_service.h:1384:2: error: implicit declaration of function &#8216;daemonize&#8217; [-Werror=implicit-function-declaration]
  daemonize("%s", name);
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/USERNAME/Desktop/Drivers/driver/rtl8188C_8192C_usb_linux_v4.0.1-1_6911.20130308] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-34-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


Thanks

---

### Post by chili555 on 2014-08-24
Please obtain a working internet connection, open a terminal and do:```
sudo apt-get install git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
cd rtl8192cu-fixes
make
sudo make install
sudo modprobe 8192cu
```Your wireless should now be working.

Please post back your result; we will have a couple of items to clean up once we're certain it's working.

---

### Post by cgameing on 2014-09-07
testing it now
sorry for the wait

woha dident know the usb had lights on it
seems to be working so far

---

### Post by cgameing on 2014-09-07
Wow thanks it works your awesome
That took me forever to do (i bought this like 5 months ago)
Thank you so much

heres the log:
USERNAME@USERNAME-PC:~$ sudo apt-get install git
[sudo] password for USERNAME: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version.
git set to manually installed.
The following packages were automatically installed and are no longer required:
  libcpufreq0 libsdl-image1.2 libsdl1.2debian
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 4 not to upgrade.
USERNAME@USERNAME-PC:~$ git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 390, done.
remote: Total 390 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (390/390), 1.75 MiB | 192.00 KiB/s, done.
Resolving deltas: 100% (201/201), done.
Checking connectivity... done.
USERNAME@USERNAME-PC:~$ cd rtl8192cu-fixes/
USERNAME@USERNAME-PC:~/rtl8192cu-fixes$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-35-generic/build M=/home/USERNAME/rtl8192cu-fixes  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-35-generic'
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_cmd.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_security.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_debug.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_io.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_ioctl_query.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_ioctl_set.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_ieee80211.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_mlme.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_mlme_ext.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_wlan_util.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_pwrctrl.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_rf.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_recv.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_sta_mgt.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_ap.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_xmit.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_p2p.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_tdls.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_br_ext.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_iol.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/rtw_sreset.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/core/efuse/rtw_efuse.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/hal_intf.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/hal_com.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/dm.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/rtl8192c_xmit.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/osdep_service.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/os_intfs.o
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/os_intfs.c:1003:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/os_intfs.c:1003:2: warning: (near initialization for &#8216;rtw_netdev_ops.ndo_select_queue&#8217;) [enabled by default]
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/usb_intf.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/ioctl_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/xmit_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/mlme_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/recv_linux.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.o
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c: In function &#8216;rtw_android_priv_cmd&#8217;:
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:382:30: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  if (copy_from_user(command, (void *)priv_cmd.buf, priv_cmd.total_len)) {
                              ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:568:4: warning: passing argument 1 of &#8216;get_int_from_command&#8217; makes pointer from integer without a cast [enabled by default]
    pwfd_info->rtsp_ctrlport = ( u16 ) get_int_from_command( priv_cmd.buf );
    ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:334:5: note: expected &#8216;char *&#8217; but argument is of type &#8216;compat_uptr_t&#8217;
 int get_int_from_command( char* pcmd )
     ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:588:4: warning: passing argument 1 of &#8216;get_int_from_command&#8217; makes pointer from integer without a cast [enabled by default]
    pwfd_info->wfd_device_type = ( u8 ) get_int_from_command( priv_cmd.buf );
    ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:334:5: note: expected &#8216;char *&#8217; but argument is of type &#8216;compat_uptr_t&#8217;
 int get_int_from_command( char* pcmd )
     ^
/home/USERNAME/rtl8192cu-fixes/os_dep/linux/rtw_android.c:612:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
   if (copy_to_user((void *)priv_cmd.buf, command, bytes_written)) {
                    ^
  LD [M]  /home/USERNAME/rtl8192cu-fixes/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/USERNAME/rtl8192cu-fixes/8192cu.mod.o
  LD [M]  /home/USERNAME/rtl8192cu-fixes/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-35-generic'
USERNAME@USERNAME-PC:~/rtl8192cu-fixes$ sudo make install
install -p -m 644 8192cu.ko  /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.13.0-35-generic
USERNAME@USERNAME-PC:~/rtl8192cu-fixes$ sudo modprobe 8192cu

---

### Post by cgameing on 2014-09-07
No seriously THANK YOU SO MUCH!

---

### Post by praseodym on 2014-09-07
Hi,

in this case the driver needs to be compiled again after a kernel upgrade:
```

cd rtl8192cu-fixes
make clean
make
sudo make uninstall
sudo make install
```
Alternatively, there is a driver available using dkms (dynamic kernel module support) which builds it automatically:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9

```

Edit: Its the same one, so just run the 1st and the last 2 commands.

---

### Post by PenterX on 2015-02-19
> **chili555 said:**
> Please obtain a working internet connection, open a terminal and do:```
sudo apt-get install git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
cd rtl8192cu-fixes
make
sudo make install
sudo modprobe 8192cu
```Your wireless should now be working.

Please post back your result; we will have a couple of items to clean up once we're certain it's working.

Hi again. I made that and it compiled and works but has error like in default driver -- it cannot connect and asking me password infinitely

---

### Post by chili555 on 2015-02-19
> **PenterX said:**
> Hi again. I made that and it compiled and works but has error like in default driver -- it cannot connect and asking me password infinitelyWhich driver is actually loaded? Old, new or (shudder!) both?```
lsmod | grep 8192
```

---

### Post by cgameing on 2015-04-05
Thanks

---

### Post by cgameing on 2015-04-11
Just letting you know
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
no longer works

it requires a username+password?

---

### Post by chili555 on 2015-04-12
> **cgameing said:**
> Just letting you know
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
no longer works

it requires a username+password?It works perfectly for me just now:```
chili@T410:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 402, done.
remote: Total 402 (delta 0), reused 0 (delta 0), pack-reused 402
Receiving objects: 100% (402/402), 1.77 MiB | 676.00 KiB/s, done.
Resolving deltas: 100% (205/205), done.
Checking connectivity... done.

```'Just now' being April 12, 2015 at 8:56 am EDT. I was also able to download and extract the zip.

---

### Post by roger_moore on 2015-09-07
```
sudo apt-get install git
git clone https://github.com/pvaret/rtl8192cu-fixes.git
cd rtl8192cu-fixes
make
sudo make install
sudo modprobe 8192cu
```

This fix worked on my Linux Mint mate 17.2 install with the same usb wifi adaptor. Thanks guys.

---

### Post by Tom_Slab on 2015-12-24
My solution (yesterday on lenovob50-30 linux mint 17.3 based on ubuntu 14.04) worked:


Firstly I needed to install correct driver from github (if you have git already, first line could be omitted):

sudo apt-get install git
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
cd rtl8192cu-fixes
make
sudo make install
sudo modprobe 8192cu

after that 8192cu.ko driver file is in /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless folder present, you can check it if you want,
but be careful, if you have other kernel, the right path is /lib/modules/<your kernel> i.e. /lib/modules/3.16.0-38-generic/kernel/drivers/net/wireless



then I needed to blacklist rtl8192 drivers, so system does not load it at start

sudo nano /etc/modprobe.d/blacklist.conf

and added this lines:

blacklist rtl8192cu
blacklist rtlwifi
blacklist rtl8192c_common

actually the native drivers are in /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rtlwifi



after that I needed to tell kernel which driver should be picked for my usb wifi (asus usb n-10 nano):

sudo nano /etc/rc.local

and added this line:

modprobe 8192cu




alternative there is a good manual on site [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) (there will be dkms approach used)

or open readme file at ./rtl8192cu-fixes after git clone command executed (driver downloaded to ./rtl8192cu-fixes)

---

