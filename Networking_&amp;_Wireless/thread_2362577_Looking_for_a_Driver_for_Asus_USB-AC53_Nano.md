---
title: "Looking for a Driver for Asus USB-AC53 Nano"
date: 2017-05-30
forum: Networking &amp; Wireless
---

### Post by tastyjalapeno on 2017-05-30
According to their description this network adapter is compatible with linux although I cant find anything but windows drivers.

Anyone have any idea how to get this running on ubuntu 17.04?

---

### Post by wildmanne39 on 2017-05-30
Please click on the wireless script in my signature and follow the directions to run it with the adapter plugged in and paste the output to pastebin, then the link back here.

---

### Post by Hadaka on 2017-05-30
Hi, no probable driver for linux found per..
[https://wikidevi.com/wiki/ASUS_USB-AC53_Nano](https://wikidevi.com/wiki/ASUS_USB-AC53_Nano)
Looks, like a different usb wifi will be needed.
Good Luck.

---

### Post by wildmanne39 on 2017-05-30
Depending on the device version I believe there may be a driver for it, I am still waiting for him to run the wireless script so we can see for sure.

---

### Post by chili555 on 2017-05-30
Is it one of these?```
alias:          usb:v7392pB822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392pC822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p184Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p1841d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB812d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB82Cd*dc*dsc*dp*icFFiscFFipFFin*

```88x2bu.ko, perhaps...

---

### Post by tastyjalapeno on 2017-05-31
Here's the update. Not able to connect to the internet so I went with option 2, allowed the .txt to be run as executable. After running it a new file was not created. After it fails to create new file if i double click and on the prompt select display all it says is as follows.

########## wireless info START ##########

---

### Post by Hadaka on 2017-05-31
Hi, It seems I was incorrect in stating no driver available for your usb.
Dr chili555 and the Wildmanne39 are correct, I apologize for posting incorrect
information. Please post your wireless info.text file as requested.
Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

---

### Post by tastyjalapeno on 2017-06-01
[https://pastebin.com/RiNfrbPn](https://pastebin.com/RiNfrbPn)

---

### Post by chili555 on 2017-06-01
It is, indeed, an 88x2bu device. I have tried to compile the driver myself and applied several supposed fixes but with no success.

I suggest that you ask Edimax here: [https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1200_dual-band/ew-7822ulc](https://www.edimax.com/edimax/download/download/data/edimax/global/download/for_home/wireless_adapters/wireless_adapters_ac1200_dual-band/ew-7822ulc)

I am unable to get beyond this error:```
/home/chili/Desktop/Forum/EW-7822ULC_Linux_Driver_1.0.0.9/RTL88x2BU_WiFi_linux_v5.1.7_19806_BTCOEX20161024-3333.20161025/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.c:13333:6: error: implicit declaration of function ‘is_compat_task’ [-Werror=implicit-function-declaration]
  if (is_compat_task())
      ^~~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/home/chili/Desktop/Forum/EW-7822ULC_Linux_Driver_1.0.0.9/RTL88x2BU_WiFi_linux_v5.1.7_19806_BTCOEX20161024-3333.20161025/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/os_dep/linux/ioctl_linux.o' failed

```Of course, you could also follow the advice above:> Looks, like a different usb wifi will be needed.
Good Luck.

---

### Post by jeremy31 on 2017-06-01
Hello chili555,
Have you checked the original file for a module already built?  I may have different source code but I found a module already built in EW-7822ULC_Linux_Driver_1.0.0.9/RTL88x2BU_WiFi_linux_v5.1.7_19806_BTCOEX20161024-3333.20161025/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
The vermagic from modinfo shows it was built using 3.13.0-24

I downloaded from the link in [https://ubuntuforums.org/showthread.php?t=2362669](https://ubuntuforums.org/showthread.php?t=2362669) and after I did the make clean in that directory with the built module, I had no issue with it

EDIT: I was able to build using 4.4 kernels but had the same failure when trying with 4.8

I might have a fix for 4.8 as I forked a github project and added this device
```
cd Desktop
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu
make clean
make
sudo make install
```
Reboot

---

### Post by chili555 on 2017-06-02
> **jeremy31 said:**
> Hello chili555,
Have you checked the original file for a module already built?  I may have different source code but I found a module already built in EW-7822ULC_Linux_Driver_1.0.0.9/RTL88x2BU_WiFi_linux_v5.1.7_19806_BTCOEX20161024-3333.20161025/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/
The vermagic from modinfo shows it was built using 3.13.0-24

I downloaded from the link in [https://ubuntuforums.org/showthread.php?t=2362669](https://ubuntuforums.org/showthread.php?t=2362669) and after I did the make clean in that directory with the built module, I had no issue with it

EDIT: I was able to build using 4.4 kernels but had the same failure when trying with 4.8

I might have a fix for 4.8 as I forked a github project and added this device
```
cd Desktop
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu
make clean
make
sudo make install
```
RebootIt builds for me with no error! Woo hoo!

I suggest that tastyjalapeno proceed and report back his result.

---

### Post by praseodym on 2017-06-02
Hi,

is it the same as this one?

[https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-beim-medion-akoya-e421/#post-7687973](https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-beim-medion-akoya-e421/#post-7687973)

BT driver in the other link

---

### Post by chili555 on 2017-06-02
> **praseodym said:**
> Hi,

is it the same as this one?

[https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-beim-medion-akoya-e421/#post-7687973](https://forum.ubuntuusers.de/topic/wlan-funktioniert-nicht-beim-medion-akoya-e421/#post-7687973)

BT driver in the other linkNo. The original post concerns this: Bus 002 Device 002: ID [COLOR="#FF0000"]0b05:184c[/COLOR] ASUSTek Computer, Inc.

The alias is not included in 8723bu:```
chili@T440p:~/Desktop/Forum/rtl8723bu$ modinfo 8723bu.ko
filename:       /home/chili/Desktop/Forum/rtl8723bu/8723bu.ko
version:        v4.3.6.11_12942.20141204_BTCOEX20140507-4E40
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5BF3FED249D372A5671D770
alias:          usb:v7392pA611d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB720d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
<snip>
```

---

### Post by flarkington on 2017-06-12
```
cd Desktop
git clone https://github.com/jeremyb31/rtl8822bu.git
cd rtl8822bu
make clean
make
sudo make install
```

This worked for me.  I'm running 14.04.

I also did the the instructions here [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")  for the wireless-info script

and also installed the steps here for a different Asus wifi adapter [https://ubuntuforums.org/showthread.php?t=2241067]("https://ubuntuforums.org/showthread.php?t=2241067")

I was working on it last night and had the idea this morning that i had not unplugged the hard ethernet cable, so i did that and all of a sudden i get a notification saying "new open wifi networks are available"

UPDATE:
Broke something unrelated in 14.04 so I updated to 16.04 - still works

---

### Post by clhsu1104 on 2017-09-23
no need driver

---

### Post by jamesray1 on 2017-11-08
So I got a WiFi stick and asked the seller about Linux support. He referred me to the RTL8812AU driver, e.g. [here]("https://github.com/sloretz/rtl8811au"). However I wasn't able to get that to work nor a fork of the same directory. So I bought another WiFi USB dongle, but after trying to install it today I haven't been successful yet. The CD installation was read only so I copied that to another directory, logged in as root user, navigated to the directory, ran ./install.sh and copied the output to a file which is available [here]("https://gist.github.com/jamesray1/6c09ffd883322ffe4fa9bcf5f29fda16"), which I have also added the wireless-info.txt file to.

---

### Post by jamesray1 on 2017-11-08
@jeremy31, your instructions didn't work. My output is [here]("https://gist.github.com/jamesray1/6c09ffd883322ffe4fa9bcf5f29fda16#file-with-git-clone-jeremyb31-slash-rtl8822bu-dot-git-txt").

---

### Post by jeremy31 on 2017-11-09
jamesray try Ubuntu 16.04 and not 16.04.2 as it won't compile with newer kernels

---

### Post by Yellow Pasque on 2017-11-29
jeremy, maybe you should adapt some of the changes for newer kernels from:
[https://github.com/maurossi/rtl8812au](https://github.com/maurossi/rtl8812au)

I whipped together a patch to get your repo to build here on Debian 4.14 kernel. I don't have the device in question, so I can't tell you if it really works.

Off-Topic: Sorry for full copy/paste. I tried to use the attachment mechanism, but it failed. I selected my file and it added it to the upload list. Then I clicked 'upload' and it acted like it was doing something, but I don't see my uploaded file.

```
diff -Naur -x '.*' rtl8822bu/include/osdep_service_linux.h rtl8822bu.patched/include/osdep_service_linux.h
--- rtl8822bu/include/osdep_service_linux.h	2017-11-28 23:35:27.286289782 -0500
+++ rtl8822bu.patched/include/osdep_service_linux.h	2017-11-28 22:49:45.608091492 -0500
@@ -45,7 +45,12 @@
 #include <linux/semaphore.h>
 #endif
 #include <linux/sem.h>
+
 #include <linux/sched.h>
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4, 11, 0))
+	#include <linux/sched/signal.h>
+#endif
+
 #include <linux/etherdevice.h>
 #include <linux/wireless.h>
 #include <net/iw_handler.h>
diff -Naur -x '.*' rtl8822bu/os_dep/linux/ioctl_cfg80211.c rtl8822bu.patched/os_dep/linux/ioctl_cfg80211.c
--- rtl8822bu/os_dep/linux/ioctl_cfg80211.c	2017-11-28 23:35:27.303290286 -0500
+++ rtl8822bu.patched/os_dep/linux/ioctl_cfg80211.c	2017-11-28 23:21:06.073653646 -0500
@@ -742,12 +742,30 @@
 		struct ieee80211_channel *notify_channel;
 		u32 freq;
 		u16 channel = cur_network->network.Configuration.DSConfig;
+		
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,12,0))
+		struct cfg80211_roam_info roam_info = {};
+#endif
 
 		freq = rtw_ch2freq(channel);
 		notify_channel = ieee80211_get_channel(wiphy, freq);
 #endif
 
 		RTW_INFO(FUNC_ADPT_FMT" call cfg80211_roamed\n", FUNC_ADPT_ARG(padapter));
+		
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,12,0))
+		roam_info.channel = notify_channel;
+		roam_info.bssid = cur_network->network.MacAddress;
+		roam_info.req_ie =
+			pmlmepriv->assoc_req+sizeof(struct rtw_ieee80211_hdr_3addr)+2;
+		roam_info.req_ie_len =
+			pmlmepriv->assoc_req_len-sizeof(struct rtw_ieee80211_hdr_3addr)-2;
+		roam_info.resp_ie =
+			pmlmepriv->assoc_rsp+sizeof(struct rtw_ieee80211_hdr_3addr)+6;
+		roam_info.resp_ie_len =
+			pmlmepriv->assoc_rsp_len-sizeof(struct rtw_ieee80211_hdr_3addr)-6;
+		cfg80211_roamed(padapter->pnetdev, &roam_info, GFP_ATOMIC);
+#else		
 		cfg80211_roamed(padapter->pnetdev
 #if LINUX_VERSION_CODE > KERNEL_VERSION(2, 6, 39) || defined(COMPAT_KERNEL_RELEASE)
 		                , notify_channel
@@ -758,6 +776,7 @@
 		                , pmlmepriv->assoc_rsp + sizeof(struct rtw_ieee80211_hdr_3addr) + 6
 		                , pmlmepriv->assoc_rsp_len - sizeof(struct rtw_ieee80211_hdr_3addr) - 6
 		                , GFP_ATOMIC);
+#endif
 	} else {
 #if LINUX_VERSION_CODE < KERNEL_VERSION(3, 11, 0) || defined(COMPAT_KERNEL_RELEASE)
 		RTW_INFO("pwdev->sme_state(b)=%d\n", pwdev->sme_state);
@@ -1721,7 +1740,7 @@
 #endif
 static int cfg80211_rtw_change_iface(struct wiphy *wiphy,
                                      struct net_device *ndev,
-                                     enum nl80211_iftype type, u32 *flags,
+                                     enum nl80211_iftype type,
                                      struct vif_params *params) {
 	enum nl80211_iftype old_type;
 	NDIS_802_11_NETWORK_INFRASTRUCTURE networkType;
@@ -3595,7 +3614,13 @@
 	mon_ndev->type = ARPHRD_IEEE80211_RADIOTAP;
 	strncpy(mon_ndev->name, name, IFNAMSIZ);
 	mon_ndev->name[IFNAMSIZ - 1] = 0;
+	
+#if (LINUX_VERSION_CODE >= KERNEL_VERSION(4,11,9))
+	mon_ndev->needs_free_netdev = false;
+	mon_ndev->priv_destructor = rtw_ndev_destructor;
+#else
 	mon_ndev->destructor = rtw_ndev_destructor;
+#endif
 
 #if (LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 29))
 	mon_ndev->netdev_ops = &rtw_cfg80211_monitor_if_ops;
@@ -3661,7 +3686,7 @@
 #if (LINUX_VERSION_CODE >= KERNEL_VERSION(4, 1, 0))
     unsigned char name_assign_type,
 #endif
-    enum nl80211_iftype type, u32 *flags, struct vif_params *params) {
+    enum nl80211_iftype type, struct vif_params *params) {
 	int ret = 0;
 	struct net_device *ndev = NULL;
 	_adapter *padapter = wiphy_to_adapter(wiphy);
@@ -6094,7 +6119,13 @@
 #endif
 
 #if defined(CONFIG_PM) && (LINUX_VERSION_CODE >= KERNEL_VERSION(3, 0, 0))
-	wiphy->flags |= WIPHY_FLAG_SUPPORTS_SCHED_SCAN;
+
+#if (LINUX_VERSION_CODE < KERNEL_VERSION(4,12,0))
+ 	wiphy->flags |= WIPHY_FLAG_SUPPORTS_SCHED_SCAN;
+#else // kernel >= 4.12
+	wiphy->max_sched_scan_reqs = 1;
+#endif
+
 #ifdef CONFIG_PNO_SUPPORT
 	wiphy->max_sched_scan_ssids = MAX_PNO_LIST_COUNT;
 #endif

```

---

### Post by avcat on 2018-02-16
I was able to successfully compile and install the driver using make on Ubuntu 16.04.3, but after rebooting I still don't have a wireless connection.

Here is my [ATTACH]278564[/ATTACH]

---

### Post by jeremy31 on 2018-02-17
avcat, Is Secure Boot disabled in BIOS?

---

### Post by avcat on 2018-02-17
Hi Jeremy, I double checked and Secure Boot is disabled by default in my BIOS (MSI Click Bios 5)

---

### Post by jeremy31 on 2018-02-17
What happens with ```
sudo modprobe -v 8822bu
```

---

### Post by avcat on 2018-02-17
Here's the output:

```

insmod /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/8822bu.ko

```

---

### Post by jeremy31 on 2018-02-17
Run the script again now

---

### Post by avcat on 2018-02-17
[ATTACH]278571[/ATTACH]

---

### Post by jeremy31 on 2018-02-17
Any results from  ```
dmesg | grep 8822
```
For some reason the script didn't show anything helpful

---

### Post by avcat on 2018-02-17
There was no output after running dmesg | grep 8822

---

### Post by jeremy31 on 2018-02-17
I am not sure what is happening but I would ```
cd rtl8822bu
sudo make uninstall
```
Then try
```
git clone https://github.com/bijju/Asus_USB-AC53_rtl8822bu.git
cd Asus_USB-AC53_rtl8822bu
make clean
make
sudo make install
```
Reboot and see if that works better

---

### Post by avcat on 2018-02-17
Thanks jeremy. I wasn't able to compile that version of the driver - here's the error:
```
  CC [M]  /home/amelia/Desktop/Asus_USB-AC53_rtl8822bu/os_dep/linux/ioctl_cfg80211.o
/home/amelia/Desktop/Asus_USB-AC53_rtl8822bu/os_dep/linux/ioctl_cfg80211.c:6884:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^
/home/amelia/Desktop/Asus_USB-AC53_rtl8822bu/os_dep/linux/ioctl_cfg80211.c:6884:25: note: (near initialization for ‘rtw_cfg80211_ops.change_virtual_intf’)
/home/amelia/Desktop/Asus_USB-AC53_rtl8822bu/os_dep/linux/ioctl_cfg80211.c:6907:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^
/home/amelia/Desktop/Asus_USB-AC53_rtl8822bu/os_dep/linux/ioctl_cfg80211.c:6907:22: note: (near initialization for ‘rtw_cfg80211_ops.add_virtual_intf’)
cc1: some warnings being treated as errors

```

---

### Post by praseodym on 2018-03-05
[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Try this one instead

---

