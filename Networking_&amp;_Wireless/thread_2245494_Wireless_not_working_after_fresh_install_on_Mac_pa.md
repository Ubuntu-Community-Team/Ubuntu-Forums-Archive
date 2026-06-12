---
title: "Wireless not working after fresh install on Mac parition"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by Ethan_Arns on 2014-09-24
I am trying to get wireless on my Macbook Pro, but it is not working.

Background info: I partitioned my new MacBook Pro Retina (OSX 10.9.5) with the latest Version of Ubuntu (14.04/Trusty) from an .iso loaded with reFInd onto a 50GB partition. I've been trying to get access to wireless, however, Apple took away Ethernet cable ports, so I'm trying to do it by sticking drivers on a USB stick, and then installing them when booted on Linux. Unfortunately, connecting to the internet isn't an option for me, so I have to switch back and forth and do it manually.

I have tried installing trusty's bcmwl-kernel-source with all requirements successfully (both with gui and command line), but could not do "sudo modprobe wl" because it gave the error "Unknown symbol in module, or unknown parameter (see dmesg)", although the gui package program acts like it installed just fine.

Any help would be greatly appreciated.

Note: Chip ID is BCM4360, in case that is relevant.

---

### Post by praseodym on 2014-09-24
Please show the terminal outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by Ethan_Arns on 2014-09-24
Here are the four outputs (separated by --):
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. Device [106b:0134]
04:00.0 Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570]
--
Module                  Size  Used by
snd_hda_codec_hdmi     46254  1 
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  2 
joydev                 17381  0 
applesmc               19308  0 
input_polldev          13896  1 applesmc
btusb                  32412  0 
bluetooth             391196  22 bnep,btusb,rfcomm
snd_hda_codec_cirrus    18855  1 
bcm5974                17589  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             143060  0 
snd_hda_intel          52355  5 
kvm                   451511  1 kvm_intel
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_cirrus
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
snd_hwdep              13602  1 snd_hda_codec
aesni_intel            55624  0 
lib80211               14381  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
nouveau              1097199  3 
ablk_helper            13597  1 aesni_intel
snd_seq_midi           13324  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              484040  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
ttm                    85115  1 nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         53081  1 nouveau
drm                   303102  5 ttm,drm_kms_helper,nouveau
lpc_ich                21080  0 
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus,snd_seq_midi
i2c_algo_bit           13413  1 nouveau
mei_me                 18627  0 
mei                    82276  1 mei_me
soundcore              12680  1 snd
apple_gmux             13665  0 
video                  19476  2 nouveau,apple_gmux
mac_hid                13205  0 
parport_pc             32701  0 
apple_bl               13993  1 apple_gmux
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_apple              13386  0 
hid_generic            12548  0 
hid_logitech_dj        18581  0 
ahci                   25819  3 
libahci                32560  1 ahci
usbhid                 52570  0 
usb_storage            62209  1 
hid                   106148  5 hid_generic,usbhid,hid_logitech_dj,hid_apple
--
lo        no wireless extensions.
--
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
How do I test LAN if it can't connect to routers?

---

### Post by praseodym on 2014-09-24
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

And for 32bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_i386.deb)
or for 64bit:
[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb)

Installation:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo dpkg -i ~/Downloads/*.deb
```

---

### Post by Ethan_Arns on 2014-09-24
dkms went fine, but during the cbmwl-... installation using your code, it all went fine except for the line below:
```
modprobe: ERROR: could not insert 'wl': Unknown symbol in module, or unknown parameter (see dmesg)
```
the dmesg said this:
```
[  140.870956] wl: Unknown symbol mcount (err 0)
```

I've encountered this before, not sure what to do...

---

### Post by praseodym on 2014-09-24
Check:
```

dmesg | grep wl
grep wl /etc/modprobe.d/*
```

---

### Post by Ethan_Arns on 2014-09-24
Okay, the first code put out this:
```
[    5.395453] wl: module license 'MIXED/Proprietary' taints kernel.
[    5.397453] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    5.397620] wl: Unknown symbol mcount (err 0)
```
The second, this:
```
/etc/modprobe.d/blacklist-bcm43.conf:# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/iwlwifi.conf:# /etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/iwlwifi.conf:# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
/etc/modprobe.d/iwlwifi.conf:# microcode file installed on the system.  When removing iwlwifi, first
/etc/modprobe.d/iwlwifi.conf:# remove the iwl?vm module and then iwlwifi.
/etc/modprobe.d/iwlwifi.conf:remove iwlwifi \
/etc/modprobe.d/iwlwifi.conf:(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
```

---

### Post by praseodym on 2014-09-24
Tried rebooting? Driver has been "activated"?

---

### Post by Ethan_Arns on 2014-09-24
I'm sorry but I'm very new to Linux. How do I activate a driver? I've rebooted many times and I still don't see any networks.

EDIT: I saw "Additional Drivers" and it shows the Broadcom advice as "unknown", but it lists the driver I installed for that device.

---

### Post by praseodym on 2014-09-24
Maybe this device is too new. I found a PPA referred:

[https://launchpad.net/~albertomilone/+archive/ubuntu/broadcom](https://launchpad.net/~albertomilone/+archive/ubuntu/broadcom)
```
sudo add-apt-repository ppa:albertomilone/broadcom
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl
```

---

### Post by Ethan_Arns on 2014-09-24
Since I don't have internet access, I downloaded the .deb and installed it with dpkg. I got this error:
```
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 163723 files and directories currently installed.)
Preparing to unpack bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu1~ppa1_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.30+bdcom-0ubuntu1~ppa1) ...
Setting up bcmwl-kernel-source (6.30.223.30+bdcom-0ubuntu1~ppa1) ...
Loading new bcmwl-6.30.223.30+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-32-generic
Building for architecture x86_64
Building initial module for 3.13.0-32-generic
ERROR (dkms apport): kernel package linux-headers-3.13.0-32-generic is not supported
Error! Bad return status for module build on kernel: 3.13.0-32-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
```

---

### Post by praseodym on 2014-09-24
Please show the content of this file:

/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/make.log

---

### Post by Ethan_Arns on 2014-09-24
I think I did this right:

```
DKMS make.log for bcmwl-6.30.223.30+bdcom for kernel 3.13.0-32-generic (x86_64)
Wed Sep 24 14:28:26 PDT 2014
make: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
/usr/src/linux-headers-3.13.0-32-generic/arch/x86/Makefile:98: stack protector enabled but no compiler support
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/shared/linux_osl.o
In file included from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/include/linuxver.h:69:0,
                 from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/shared/linux_osl.c:25:
include/linux/netdevice.h: In function ‘netif_addr_lock_nested’:
include/linux/netdevice.h:2782:6: warning: variable ‘subclass’ set but not used [-Wunused-but-set-variable]
  int subclass = SINGLE_DEPTH_NESTING;
      ^
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.o
In file included from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/include/linuxver.h:69:0,
                 from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:27:
include/linux/netdevice.h: In function ‘netif_addr_lock_nested’:
include/linux/netdevice.h:2782:6: warning: variable ‘subclass’ set but not used [-Wunused-but-set-variable]
  int subclass = SINGLE_DEPTH_NESTING;
      ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:616:3: warning: pointer targets in passing argument 10 of ‘wlc_attach’ differ in signedness [-Wpointer-sign]
   osh, wl->regsva, wl->bcm_bustype, btparam, &err))) {
   ^
In file included from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:77:0:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wlc_pub.h:659:14: note: expected ‘uint *’ but argument is of type ‘int *’
 extern void *wlc_attach(void *wl, uint16 vendor, uint16 device, uint unit, bool piomode,
              ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_toe_get’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:1521:2: warning: pointer targets in passing argument 3 of ‘wlc_iovar_getint’ differ in signedness [-Wpointer-sign]
  if (wlc_iovar_getint(wl->wlc, "toe_ol", toe_ol) != 0)
  ^
In file included from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:77:0:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wlc_pub.h:667:12: note: expected ‘int *’ but argument is of type ‘uint32 *’
 extern int wlc_iovar_getint(struct wlc_info *wlc, const char *name, int *arg);
            ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_event’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:2112:3: warning: pointer targets in passing argument 3 of ‘wlc_get’ differ in signedness [-Wpointer-sign]
   if (wlc_get(wl->wlc, WLC_GET_RADIO, &i) < 0)
   ^
In file included from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:77:0:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wlc_pub.h:666:12: note: expected ‘int *’ but argument is of type ‘mbool *’
 extern int wlc_get(struct wlc_info *wlc, int cmd, int *arg);
            ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_monitor’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:2437:3: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness [-Wpointer-sign]
   strcpy(phdr->devname, wl->dev->name);
   ^
In file included from include/linux/bitmap.h:8:0,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-32-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/include/linuxver.h:40,
                 from /var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:27:
include/linux/string.h:20:15: note: expected ‘char *’ but argument is of type ‘uint8 *’
 extern char * strcpy(char *,const char *);
               ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3247:7: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
       wl->tkip_bcast_data[idx]);
       ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3247:7: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3250:4: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
    wl->tkipmodops->print_stats(debug_buf, wl->tkip_ucast_data);
    ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3250:4: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_proc_read’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3416:6: warning: variable ‘bcmerror’ set but not used [-Wunused-but-set-variable]
  int bcmerror, to_user;
      ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_reg_proc_entry’:
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3471:2: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
  ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3471:22: warning: assignment makes pointer from integer without a cast [enabled by default]
  if ((wl->proc_entry = create_proc_entry(tmp, 0644, NULL)) == NULL) {
                      ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3476:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->read_proc = wl_proc_read;
                ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3477:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->write_proc = wl_proc_write;
                ^
/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.c:3478:16: error: dereferencing pointer to incomplete type
  wl->proc_entry->data = wl;
                ^
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.30+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'

```

---

### Post by praseodym on 2014-09-25
Then install the driver from the Broadcom website:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Follow the steps in the Readme.txt

---

### Post by Ethan_Arns on 2014-09-26
Well, I got a temporary wireless adapter, and typed sudo apt-get install bcmwl-kernel-source, and it just started working right away. I have no idea why it didn't work with manual downloads, but it does now. Praseodym, thank you so much for the help. How do I mark this as solved?

---

### Post by varunendra on 2014-09-29
> **Ethan_Arns said:**
> Well, I got a temporary wireless adapter, and typed sudo apt-get install bcmwl-kernel-source, and it just started working right away. I have no idea why it didn't work with manual downloads, but it does now. Praseodym, thank you so much for the help. How do I mark this as solved?
Using "**Thread Tools**" link above the top post. Screenshots can be found on the page linked to the "[COLOR="#0000CD"]see how[/COLOR]" link in my signature. :)

Since the default "wl" driver has only recently started supporting this card, it makes the value of your feedback even higher. Please do mark it [SOLVED] using the link. Thanks!

---

