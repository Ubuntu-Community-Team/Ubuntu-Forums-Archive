---
title: "Broadcam wireless BCM43142  stipped working after a recent update"
date: 2018-03-05
forum: Networking &amp; Wireless
---

### Post by saravanakumar2 on 2018-03-05
After a recent update to my Ubuntu 16.04, my wireless network controller stopped working. It is not detecting wifi networks anymore. 

```
sudo lshw -class network
``` gives me

```
  *-network UNCLAIMED
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d1100000-d1107fff



```

I tried uninstalling the driver and installing it again following [chili555's post]("https://ubuntuforums.org/showthread.php?t=2214110"). But the problem with that is that I don't remember the if have blacklisted or uncommented any driver files earlier. So, naturally, the solution given there did not work for me. I am a linux noob and any help would be greatly appreciated.

---

### Post by jeremy31 on 2018-03-05
Some of the newest kernels have caused issues with dkms packages because of retpoline patches, try
```
sudo apt-get install --reinstall build-essential bcmwl-kernel-source
```
Reboot

---

### Post by saravanakumar2 on 2018-03-07
It didn't work for me.

In between, it threw an error like this:

```
DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Exec format error

```

---

### Post by chili555 on 2018-03-08
I am interested in your kernel version:```
uname -r
```And also which version of the driver is installed:```
sudo dpkg -s bcmwl-kernel-source | grep Version
```And, finally, if there are any clues in the log:```
cat /var/lib/dkms/bcmwl/<version_you_found>/<kernel_version>/x86_64/log/make.log
```Of course, substitute your exact details here. For instance on my system. I get:```
Version: 6.30.223.271+bdcom-0ubuntu3
```And:```
4.13.0-36-generic
```So, I found the make.log at:```
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/4.13.0-36-generic/x86_64/log/make.log
```Thanks.

---

### Post by saravanakumar2 on 2018-03-08
First of all, thank you very much for responding to my message.

Kernel version:
```
4.4.0-116-generic
```

Driver version:
```
Version: 6.30.223.271+bdcom-0ubuntu1~1.2
```
 
Contents of log file:

```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.4.0-116-generic (x86_64)
Wed Mar  7 10:27:50 IST 2018
make: Entering directory '/usr/src/linux-headers-4.4.0-116-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c: In function ‘wl_ch_to_chanspec’:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:2266:18: warning: comparison between ‘enum ieee80211_band’ and ‘enum nl80211_band’ [-Wenum-compare]
   if (chan->band == IEEE80211_BAND_2GHZ) {
                  ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.c:2269:23: warning: comparison between ‘enum ieee80211_band’ and ‘enum nl80211_band’ [-Wenum-compare]
   else if (chan->band == IEEE80211_BAND_5GHZ) {
                       ^
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.o
  Building modules, stage 2.
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  MODPOST 1 modules
  CC      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.mod.o
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.ko
make: Leaving directory '/usr/src/linux-headers-4.4.0-116-generic'

```

---

### Post by chili555 on 2018-03-08
I'm working on a theory. If you reboot, interrupt the boot process to get to the GRUB menu and select an earlier kernel version, likely 4.4.0-112, does the wireless work?

In both -112 and -116, may we see:```
gcc --version
```

-------

Possible reference: [https://answers.launchpad.net/ubuntu/+question/664826](https://answers.launchpad.net/ubuntu/+question/664826) and also: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1750937](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1750937)

---

### Post by saravanakumar2 on 2018-03-09
My earlier kernel version is 4.4.0-109. My WiFi did not work even after switching to this kernel version.

Here are the details you asked for

'gcc --version' for Kernel-109
```
gcc (Ubuntu 5.4.1-2ubuntu1~16.04) 5.4.1 20160904
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

``` 

'gcc --version' for Kernel-116
```
gcc (Ubuntu 5.4.1-2ubuntu1~16.04) 5.4.1 20160904
Copyright (C) 2015 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by chili555 on 2018-03-09
Is gcc-5 installed?```
gcc-5 --version
```If not, please install it:```
sudo apt-get install gcc-5
```It will bring along a few dependencies. Then do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Any improvement?

---

### Post by saravanakumar2 on 2018-03-09
gcc-5 is already installed

Version:
```
gcc-5 (Ubuntu 5.4.1-2ubuntu1~16.04) 5.4.1 20160904
```


Reinstalling '[COLOR=#000000][FONT=&amp]bcmwl-kernel-source[/FONT][/COLOR]' resolved the issue in my earlier kernel version([COLOR=#000000]4.4.0-109[/COLOR]). 

However, the problem still persists for my current kernel version([COLOR=#000000]4.4.0-116[/COLOR]). I get the same error as before


```
modprobe: ERROR: could not insert 'wl': Exec format error
```

---

### Post by chili555 on 2018-03-10
I must painfully and regrettably admit that I am struggling to see what to fix here. My most and least favorite problem is 'everything looks perfect but it won't work.'> Reinstalling 'bcmwl-kernel-source' resolved the issue in my earlier kernel version(4.4.0-109). 
 Is -109 still on your computer and available at the GRUB menu? Does the wireless work as expected?

I haven't and won't give up.

---

### Post by saravanakumar2 on 2018-03-10
Yes, -109 is still on my computer and available at the GRUB menu. With this kernel version, the wireless works perfectly.

P.S: Thank you once again for resolving my problem and not giving up :)

---

### Post by chili555 on 2018-03-10
Until my Google-foo or divine intervention comes to me a bit better, please (temporarily, we hope, stick with -109.

Studying...

---

### Post by chili555 on 2018-04-18
We have new information on this problem. This person claims to have fixed it. [https://askubuntu.com/questions/1025572/wifi-is-not-available-after-rebooting-in-ubuntu-16-04-4-lts](https://askubuntu.com/questions/1025572/wifi-is-not-available-after-rebooting-in-ubuntu-16-04-4-lts)

Please try it. Reboot and select -116 at the GRUB menu.

The file in question can be modified like this:```
sudo nano  /usr/src/linux-headers-4.4.0-116-generic/include/linux/vermagic.h 
```Find these lines:```
#ifdef RETPOLINE
#define MODULE_VERMAGIC_RETPOLINE "retpoline "
```Change them to this:```
/* #ifdef RETPOLINE */
#if 1
#define MODULE_VERMAGIC_RETPOLINE "retpoline "
```Proofread carefully twice, save (Ctrl+o followed by Enter) and exit (Ctrl+x).

Now proceed:```
sudo dpkg-reconfigure bcmwl-kernel-source
sudo service network-manager restart
```Any improvement?

---------------------------------------------------------------------------------------

NOTE TO SEARCHERS: This is probably* ONLY* applicable to the infamous 4.4.0-116 problem. If in doubt, post a new question and ask.

---

### Post by saravanakumar2 on 2018-04-24
This fixed the issue! Thank you very much, kind sir.

---

### Post by chili555 on 2018-04-24
Woo hoo! Thanks for your test and subsequent reply. I am certain that you've helped quite a few searchers.

Glad it's working.

---

