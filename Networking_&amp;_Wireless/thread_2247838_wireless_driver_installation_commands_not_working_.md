---
title: "wireless driver installation commands not working anymore after kernel update."
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by chkneater on 2014-10-10
I'm having another issue with a Belkin Wireless USB adapter, after kernel upgrades the usual commands to fix the wireless have failed to work..  

the commands I usually use are:

sudo apt-get remove --purge wicd
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install build-essential linux-headers-generic git
git clone [https://github.com/lwfinger/rtl8192du.git](https://github.com/lwfinger/rtl8192du.git)
cd rtl8192du
sudo make clean
sudo make
sudo make install
sudo modprobe 8192du

But now whenever I get to the 'make' part of the commands I get this:
```
hellkiller@hellkiller-desktop:~/rtl8192du$ sudo make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.0-70-lowlatency/build M=/home/hellkiller/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-70-lowlatency'
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_cmd.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_security.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_debug.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_io.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_ioctl_set.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_ieee80211.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_mlme.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_mlme_ext.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_wlan_util.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_pwrctrl.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_rf.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_recv.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_sta_mgt.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_ap.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_xmit.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_p2p.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_sreset.o
  CC [M]  /home/hellkiller/rtl8192du/core/rtw_efuse.o
  CC [M]  /home/hellkiller/rtl8192du/hal/hal_intf.o
  CC [M]  /home/hellkiller/rtl8192du/hal/hal_com.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_hal_init.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_phycfg.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_rf6052.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_dm.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_rxdesc.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_cmd.o
  CC [M]  /home/hellkiller/rtl8192du/hal/usb_halinit.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192du_led.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192du_xmit.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192du_recv.o
  CC [M]  /home/hellkiller/rtl8192du/hal/Hal8192DUHWImg.o
  CC [M]  /home/hellkiller/rtl8192du/hal/usb_ops_linux.o
  CC [M]  /home/hellkiller/rtl8192du/hal/rtl8192d_xmit.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/osdep_service.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/os_intfs.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/usb_intf.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/usb_ops_linux.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/ioctl_linux.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/xmit_linux.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/mlme_linux.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/recv_linux.o
  CC [M]  /home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.o
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_assoc&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:2444:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:2444:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_disassoc&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:2501:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:2501:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action_p2p&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3165:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3165:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_p2p_action_public&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3197:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3197:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3232:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3232:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: &#8216;struct cfg80211_mgmt_tx_params&#8217; declared inside parameter list [enabled by default]
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: In function &#8216;cfg80211_rtw_mgmt_tx&#8217;:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3584:5: warning: passing argument 1 of &#8216;cfg80211_mgmt_tx_status&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3151:6: note: expected &#8216;struct net_device *&#8217; but argument is of type &#8216;struct wireless_dev *&#8217;
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for &#8216;rtw_cfg80211_ops.mgmt_tx&#8217;) [enabled by default]
make[2]: *** [/home/hellkiller/rtl8192du/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/hellkiller/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-70-lowlatency'
make: *** [modules] Error 2
hellkiller@hellkiller-desktop:~/rtl8192du$ 
[QUOTE]

This is lsusb:
[QUOTE]
hellkiller@hellkiller-desktop:~$ sudo lsusb
[sudo] password for hellkiller: 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 006 Device 002: ID 05b8:3155 Agiler, Inc. 
hellkiller@hellkiller-desktop:~[QUOTE]

this is lspci:
[QUOTE}0:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
03:06.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10)

```

Anyway, I think that sums it up... old wireless driver installation commands not working anymore after kernel update.

---

### Post by praseodym on 2014-10-10
Here it worked with kernel 3.8 (which is not recommended anymore):

[http://ubuntuforums.org/showthread.php?t=2176114&p=12799964#post12799964](http://ubuntuforums.org/showthread.php?t=2176114&p=12799964#post12799964)

Try installing the Trusty-hardware enablement stack. Check first:
```

sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
``` 
If no errors occur, repeat it without "-s" and try it again after rebooting. It will install kernel 3.11

---

### Post by chili555 on 2014-10-10
At the git site, there are two branches. I believe the 'git clone' step downloads the default branch. I suggest you instead try the other branch, kernel-version:```
sudo rm -rf  rtl8192du
wget https://github.com/lwfinger/rtl8192du/archive/kernel-version.zip
unzip kernel-version.zip
cd rtl8192du-kernel-version
make
sudo make install
sudo modprobe 8192du
```

---

### Post by Vladlenin5000 on 2014-10-10
Just an additional comment:

You don't really know what you're doing and the sooner you're aware of that the better (it avoids future problems stemmed from blindly issuing commands).

1. If you already removed/purged packages A. B or C you don't need to do it again, unless you reinstalled packages A, B or C meanwhile (of course you didn't or that is what I hope);
2. If you already installed needed packages A, B or C you don't need to install them again, unless you uninstalled them meanwhile (again, why would you do that?);
3. Likewise you don't need to clone a git repository twice. In this situation you were just advised to clone a _different branch_ and that is a correct troubleshoot.

Please report back after following Dr. Chili's advice. Thank you.

---

### Post by chkneater on 2014-10-11
> **Vladlenin5000 said:**
> Just an additional comment:

You don't really know what you're doing and the sooner you're aware of that the better (it avoids future problems stemmed from blindly issuing commands).

1. If you already removed/purged packages A. B or C you don't need to do it again, unless you reinstalled packages A, B or C meanwhile (of course you didn't or that is what I hope);
2. If you already installed needed packages A, B or C you don't need to install them again, unless you uninstalled them meanwhile (again, why would you do that?);
3. Likewise you don't need to clone a git repository twice. In this situation you were just advised to clone a _different branch_ and that is a correct troubleshoot.

Please report back after following Dr. Chili's advice. Thank you.

D00D, you don't even know what the prob was so why are you talking like you knew the answer all along?  I fully understand what I am doing and if you had read the OP you'd see that after kernel upgrades I have to run those commands, in this case they aren't working, just like Chili555 said, cuz of the repository...

I have not tried the solution yet and I willl get back to you when I feel

---

### Post by Vladlenin5000 on 2014-10-11
As a matter of fact, I know exactly what your problem was/is: You have a WiFi device which isn't natively supported and you used to compile a driver from that git; now that driver no longer works in your new Ubuntu release - lots of errors - and you were suggested to try a new one that also needs to be compiled but compiled from a different git branch. At this point we aren't sure if it'll work but testing it is a necessary troubleshooting step.

Now, allow me to reformulate with specific examples what I said before in a generic/abstract way.

My **comment #1** refers to this:
```
sudo apt-get remove --purge wicd
sudo apt-get remove --purge ndiswrapper*
```
At one time I suppose you had *wicd* and *ndiswrapper *and, not surprisingly, you had to uninstall/purge both in order to try the compiled driver hence those two commands were needed. So far so good.
Why are you removing it again now? Have you installed both of them again? If so, why? In the name of all 3000+ deities created since the beginning of civilization, WHY? If not, issuing those commands again is a pure waste of time, a waste of **_your_ time.
You probably missed (or ignored) the message *Package ...' is not installed, so not removed*.

My **comment #2** refers to this:
```
sudo apt-get install build-essential linux-headers-generic git
```
It's the same thing as #1 but in reverse. Why are you installing them again? Another pure waste of time... Note: There are cases where one or more programs become corrupted and need to be reinstalled but that is done by adding the parameter *--reinstall*. Issuing a simple *apt-get install *command for any package already installed results in a message saying exactly that, the package is already installed... I guess you missed that too...

My **comment #3** refers to this:
```
git clone [https://github.com/lwfinger/rtl8192du.git](https://github.com/lwfinger/rtl8192du.git)
```
Once cloned everything that's in the the git repository is copied to a local folder at your /home/your_user_name and, in this case, the folder is [I]rtl8192du.

[/I]Bottom line: In order to compile the same driver again you could have started by going to that folder (*cd rtl8192du*) and *make*, *make install* and *modprobe* as usual. Again, you don't want to do it know because you already know it no longer works.

Now, allow me to deconstruct Dr. Chilli's suggestion...
```
sudo rm -rf  rtl8192du   <- Removes the previously git cloned folder, recursively (-r) and forcing removal if needed (-f)
wget https://github.com/lwfinger/rtl8192du/archive/kernel-version.zip   <- downloads the kernel-version.zip file
unzip kernel-version.zip   <- extracts the downloaded file to /home/your_user_name
(...) (you're already familiar with the remaining commands)
```


PS - Next time you need to post results please use the Go Advanced button below, click "#" and paste it inside. Otherwise it results in an horrible wall of text most people WON'T read. I did but I admit now I probably shouldn't have. Now I'm here wasting my time replying to a rude person who doesn't know the basics and apparently doesn't care.
PSS - Please don't address me as "dude", "dood" or anything similar, ever again.

---

