---
title: "Belkin wireless networking"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by chkneater on 2015-08-22
I'm wondering if there is going to ever be or has been an Ubuntu that supports wireless Belkin USB sticks.  I know the driver needs to be installed on this distro which is 12.04, I also tried 14 but same thing, no response.  On the 12.04 distro I HAVE the rtl8192du driver folder and the contents but haven't had luck installing it.  I'm wondering when I upgrade if I'll be able to use this driver or if the native driver will work out of the box.  whatever the case why is it so hard to get Belkins to work when I've had success with them years ago, and what should I do to enable the Belkin USB wireless in the future versions?

---

### Post by chili555 on 2015-08-22
As of Ubuntu 15.04 and even with a 4.0-xx kernel installed, rtl8192du is still not supported by default. You'd still need to compile it.

Please tell us what you've done so far that failed. Maybe some smart person around here can help.

----

Reference: [https://github.com/lwfinger/rtl8192du](https://github.com/lwfinger/rtl8192du)

---

### Post by chkneater on 2015-08-22
Well if it's anyone I know you can... this is odd, you gave me the right driver diirectory, easy instructions to compile it, and at every kernel update I would just run Make clean, Make, Make install and modprobe, then I would plug it in and it worked with everfy kernel up to 12.04.  I scanned the error codes after running the commands and noticed that it was always erroring out when it got to the modprobe directory  and say things like 'files in modprobe need to be conf. files)  so I looked and there are two unused empty unnamed folders that only the root can move or delete.  I even tried copying the right files from modprobe.d  and making a new folder to replace it but I can't overrite it, even synaptic and apt failed to get rid of them, but I'm quite sure that is a big part of the issue but not the whole issue, but I can't fix anything else till I get these two folders removed from that folder.  I can barely keep my eyes open RN my insomnia has caught up to me and the screen is melting to me so I'm gonna be off for a bit but I'll stay logged on and chedk periodically but sleep is overwhelming me.  I'll talk to ya later Chili and thanks for the past help and any future help you might provide :-)

---

### Post by chili555 on 2015-08-22
Please see your other post and my reply.

---

### Post by chkneater on 2015-08-22
[So would it be better to just dis Ndiswrapper and just deal with getting the rtl8192du working?   I can do that, I have the driver backed up several ways just in case but it wont MAKE on 12.04  when  compile it.. I take that back, it MAKES just fine, no errors but MAKE INSTALL is where  I have probs this is the MAKE output:[\hellkiller@hellkiller-desktop:~/Desktop$ cd rtl8192
```

hellkiller@hellkiller-desktop:~/Desktop$ cd rtl8192du
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.0-82-lowlatency/build M=/home/hellkiller/Desktop/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-82-lowlatency'
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_cmd.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_security.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_debug.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_io.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_ioctl_set.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_ieee80211.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_mlme.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_mlme_ext.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_wlan_util.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_pwrctrl.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_rf.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_recv.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_sta_mgt.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_ap.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_xmit.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_p2p.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_sreset.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/core/rtw_efuse.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/hal_intf.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/hal_com.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_hal_init.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_phycfg.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_rf6052.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_dm.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_rxdesc.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_cmd.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/usb_halinit.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192du_led.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192du_xmit.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192du_recv.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/hal8192duhwimg.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/usb_ops_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/hal/rtl8192d_xmit.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/osdep_service.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/os_intfs.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/usb_intf.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/usb_ops_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/ioctl_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/xmit_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/mlme_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/recv_linux.o
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/ioctl_cfg80211.o
/home/hellkiller/Desktop/rtl8192du/os_dep/ioctl_cfg80211.c:3627:2: warning: initialization from incompatible pointer type [enabled by default]
/home/hellkiller/Desktop/rtl8192du/os_dep/ioctl_cfg80211.c:3627:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
  CC [M]  /home/hellkiller/Desktop/rtl8192du/os_dep/rtw_android.o
  LD [M]  /home/hellkiller/Desktop/rtl8192du/8192du.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hellkiller/Desktop/rtl8192du/8192du.mod.o
  LD [M]  /home/hellkiller/Desktop/rtl8192du/8192du.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-82-lowlatency'
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ 
[CODE]

This was just the MAKE command obiously and it went fine but\ look at this whe I MAKE INSTALL:

[CODE]hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         fglrx.conf
blacklist-ath_pci.conf      blacklist-oss.conf           New Folder
blacklist.conf              blacklist-rare-network.conf  New Folder2
blacklist-firewire.conf     blacklist-watchdog.conf      vmwgfx-fbdev.conf
blacklist-framebuffer.conf  dkms.conf
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ 
   
```

Notice that lsusb couldn't fine modprobe.d but the ls command worked fine.  You see the two stupid blank useless folders?  I can't move them, delete them i tried making a standard modprobe file but it wouldn't let me replace, tried renaming them but the option was grayed out... I wanted to just delete modprobe and replace it with the original.

---

### Post by chkneater on 2015-08-22
And this is the result of modprob notice all the warnings about the folders and not binding files?...:


> hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ sudo modprobe rtl8192du
WARNING: All config files need .conf: /etc/modprobe.d/New Folder, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/New Folder2, it will be ignored in a future release.
FATAL: Module rtl8192du not found.
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ ls /etc/modprobe.d
bash: hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$: No such file or directory
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ alsa-base.conf              blacklist-modem.conf         fglrx.conf
alsa-base.conf: command not found
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ blacklist-ath_pci.conf      blacklist-oss.conf           New Folder
blacklist-ath_pci.conf: command not found
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ blacklist.conf              blacklist-rare-network.conf  New Folder2
blacklist.conf: command not found
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ blacklist-firewire.conf     blacklist-watchdog.conf      vmwgfx-fbdev.conf
blacklist-firewire.conf: command not found
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ blacklist-framebuffer.conf  dkms.conf
blacklist-framebuffer.conf: command not found
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ 
bash: hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$: No such file or directory
hellkiller@hellkiller-desktop:~/Desktop/rtl8192du$ 
   

---

### Post by chili555 on 2015-08-22
Let's take one step at a time. This is a warning, not an error:> WARNING: All config files need .conf: /etc/modprobe.d/New Folder, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/New Folder2, it will be ignored in a future release.If you are sure they are empty and useless, we can remove them:```
sudo rm -rf /etc/modprobe.d/New\ Folder
sudo rm -rf /etc/modprobe.d/New\ Folder2
```Be careful; rm -rf is absolute and irrevocable. If you are unsure, stop and ask me.

Second:> $ sudo modprobe rtl8192du
<snip>
FATAL: Module rtl8192du not found.The module is not found because the module you compiled is actually 8192du:```
LD [M] /home/hellkiller/Desktop/rtl8192du/[COLOR="#FF0000"]8192du.ko[/COLOR]
```rtl8192du is not the same as 8192du. Please try:```
sudo modprobe 8192du
```Finally, I suggest you get rid of ndiswrapper altogether and I'll be happy to assist.

What is the result of:```
lsusb
```

---

