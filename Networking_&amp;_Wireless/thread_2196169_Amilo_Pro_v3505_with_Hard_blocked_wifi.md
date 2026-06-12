---
title: "Amilo Pro v3505 with Hard blocked wifi"
date: 2013-12-28
forum: Networking &amp; Wireless
---

### Post by jbarcewicz on 2013-12-28
Hi, 
I'm trying to solve it for several hours now. I have quite old Fujitsu Siemens Amilo Pro v3505 laptop. Installed Windows 7 and Ubuntu 13.10. When running Win7 wifi works fine (same as hardware switch to turn wifi on/off), when restarted to Ubuntu wifi still works, but when computer was turned off and then Ubuntu started, wifi is Hard blocked and switch doesn't work. Please see my system details and maybe somebody had the same problem. I've checked many posts with similar issues but no solution helped for me (like modprobe wistron_btns):

```
# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

```
# iwconfig 
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.

```

```
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:bc:5c:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6448 (6.4 KB)  TX bytes:6448 (6.4 KB)


wlan0     Link encap:Ethernet  HWaddr 00:18:de:24:9c:52  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
# lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:0a:e4:bc:5c:ea
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:d2000000-d2003fff ioport:2000(size=256) memory:d0000000-d001ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:24:9c:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.11.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d4000000-d4000fff

```

```
# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:06.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0a:06.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0a:06.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
0a:06.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

```
# lsmod
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18893  2 
rfcomm                 53664  0 
bluetooth             323534  10 bnep,rfcomm
coretemp               13195  0 
kvm                   364766  0 
joydev                 17097  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    45473  1 
pcmcia                 51368  0 
snd_hda_intel          42658  3 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
microcode              18830  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
yenta_socket           40193  0 
psmouse                90642  0 
serio_raw              13189  0 
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
arc4                   12536  2 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
iwl3945                63619  0 
iwlegacy               87971  1 iwl3945
mac80211              513247  2 iwl3945,iwlegacy
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
i915                  589697  3 
cfg80211              401436  3 iwl3945,iwlegacy,mac80211
snd_timer              24447  2 snd_pcm,snd_seq
video                  18777  1 i915
drm_kms_helper         46867  1 i915
drm                   242354  4 i915,drm_kms_helper
snd                    60790  17 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
sdhci_pci              18481  0 
sdhci                  37468  1 sdhci_pci
ahci                   25579  2 
libahci                26554  1 ahci
sky2                   52910  0

```

```
# dmesg | tail -n15
[  104.569360] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  104.803526] atkbd serio0: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[  104.803537] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.609281] atkbd serio0: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[  599.609292] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.706959] atkbd serio0: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[  599.706969] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.784726] atkbd serio0: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[  599.784737] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.843356] atkbd serio0: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[  599.843365] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.901696] atkbd serio0: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[  599.901706] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.
[  599.960392] atkbd serio0: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[  599.960401] atkbd serio0: Use 'setkeycodes e056 <keycode>' to make it known.

```

Any ideas?

Cheers,
jbk

---

### Post by praseodym on 2013-12-28
Tried a BIOS reset to default settings?

---

### Post by jbarcewicz on 2013-12-28
> **praseodym said:**
> Tried a BIOS reset to default settings?

BIOS reset to default didn't help. Still Hard blocked: yes.
Btw I have also tried with Fedora, OpenSUSE, PuppyLinux and Mint (live cds) all of them were seeing wifi card but with HW off and switch didn't work as well

Cheers,
jbk

---

### Post by praseodym on 2013-12-28
Try the acer_wmi:
```

sudo modprobe -v acer_wmi wireless=1
sudo rfkill unblock all
```

---

### Post by jbarcewicz on 2013-12-28
> **praseodym said:**
> Try the acer_wmi:
```

sudo modprobe -v acer_wmi wireless=1
sudo rfkill unblock all
```

The result is:
```
# modprobe -v acer_wmi wireless=1
insmod /lib/modules/3.11.0-14-generic/kernel/drivers/platform/x86/wmi.ko 
insmod /lib/modules/3.11.0-14-generic/kernel/drivers/input/sparse-keymap.ko 
insmod /lib/modules/3.11.0-14-generic/kernel/drivers/platform/x86/acer-wmi.ko wireless=1
ERROR: could not insert 'acer_wmi': No such device
```

jbk

---

### Post by jbarcewicz on 2013-12-29
Hi,
Any other ideas? I would be really appreciate if somebody could help me :) I'm trying to convince my family to use linux as a primary system but cannot install one with working wifi on laptop.

jbk

---

### Post by praseodym on 2013-12-29
Try ACER-Hotkeys:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms module-assistant debhelper
wget https://launchpad.net/~cogito-16/+archive/ppa/+files/acerhk-source_0.5.35-16_all.deb
sudo dpkg -i acer*.deb
cd /usr/src
sudo tar -xjf acerhk.tar.bz2 
sudo mv modules acerhk-0.5.35 
```
Create a new file:
```

gksudo gedit /usr/src/acerhk-0.5.35/dkms.conf
```
Add into the file:```

PACKAGE_NAME=acerhk
PACKAGE_VERSION=0.5.35

DEST_MODULE_LOCATION=/extra
BUILT_MODULE_NAME=acerhk
BUILT_MODULE_LOCATION=acerhk/

MAKE="'make' -C acerhk/ all"
CLEAN="'make' -C acerhk/ clean"
AUTOINSTALL="yes"
```
Save, close the editor and install```

sudo dkms add -m acerhk -v 0.5.35 
sudo dkms build -m acerhk -v 0.5.35 
sudo dkms install -m acerhk -v 0.5.35 
```
Try the module```

sudo modprobe acerhk 
```
and the keys, and/or```

sudo rfkill unblock all
```

---

### Post by jbarcewicz on 2013-12-29
Thanks for replay.
There is a problem with: 
```
sudo dkms build -m acerhk -v 0.5.35
```

It produces:
```
# /usr/src$ sudo dkms build -m acerhk -v 0.5.35 

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C acerhk/ all......(bad exit status: 2)
ERROR (dkms apport): binary package for acerhk: 0.5.35 not found
Error! Bad return status for module build on kernel: 3.11.0-14-generic (i686)
Consult /var/lib/dkms/acerhk/0.5.35/build/make.log for more information.
```

And make.log:```

DKMS make.log for acerhk-0.5.35 for kernel 3.11.0-14-generic (i686)
nie, 29 gru 2013, 14:21:37 CET
make: Entering directory `/var/lib/dkms/acerhk/0.5.35/build/acerhk'
make -C /lib/modules/`uname -r`/build SUBDIRS=/var/lib/dkms/acerhk/0.5.35/build/acerhk CONFIG_FUNCTION_TRACER= modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-14-generic'
  CC [M]  /var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.o
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c: In function ‘acerhk_proc_init’:
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2709:5: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
     entry = create_proc_read_entry("info",
     ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2709:11: warning: assignment makes pointer from integer without a cast [enabled by default]
     entry = create_proc_read_entry("info",
           ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2720:13: warning: assignment makes pointer from integer without a cast [enabled by default]
       entry = create_proc_read_entry("key",
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2732:9: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
         entry = create_proc_entry("led", 0222, proc_acer_dir);
         ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2732:15: warning: assignment makes pointer from integer without a cast [enabled by default]
         entry = create_proc_entry("led", 0222, proc_acer_dir);
               ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2741:16: error: dereferencing pointer to incomplete type
           entry->write_proc = acerhk_proc_led;
                ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2746:17: warning: assignment makes pointer from integer without a cast [enabled by default]
           entry = create_proc_entry("wirelessled", 0222, proc_acer_dir);
                 ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2756:18: error: dereferencing pointer to incomplete type
             entry->write_proc = acerhk_proc_wirelessled;
                  ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2761:19: warning: assignment makes pointer from integer without a cast [enabled by default]
             entry = create_proc_entry("blueled", 0222, proc_acer_dir);
                   ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2771:20: error: dereferencing pointer to incomplete type
               entry->write_proc = acerhk_proc_blueled;
                    ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c: At top level:
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2957:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘model_init’
 static void __devinit model_init(void)
                       ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2982:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acerhk_remove’
 static int __devexit acerhk_remove(struct platform_device *dev);
                      ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2984:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acerhk_probe’
 static int __devinit acerhk_probe(struct platform_device *dev)
                      ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:3066:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acerhk_remove’
 static int __devexit acerhk_remove(struct platform_device *dev)
                      ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:3092:12: error: ‘acerhk_probe’ undeclared here (not in a function)
  .probe  = acerhk_probe,
            ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:3093:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
  .remove  = __devexit_p(acerhk_remove),
  ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:3093:25: error: ‘acerhk_remove’ undeclared here (not in a function)
  .remove  = __devexit_p(acerhk_remove),
                         ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:136:14: warning: ‘reg2’ defined but not used [-Wunused-variable]
 static void *reg2;
              ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:386:13: warning: ‘enable_dritek_keyboard’ defined but not used [-Wunused-function]
 static void enable_dritek_keyboard(void)
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:392:13: warning: ‘disable_dritek_keyboard’ defined but not used [-Wunused-function]
 static void disable_dritek_keyboard(void)
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:764:12: warning: ‘get_cmos_index’ defined but not used [-Wunused-function]
 static int get_cmos_index(void)
            ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:876:29: warning: ‘find_hk_area’ defined but not used [-Wunused-function]
 static unsigned long __init find_hk_area(void)
                             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:1328:20: warning: ‘setup_model_features’ defined but not used [-Wunused-function]
 static void __init setup_model_features(unsigned int series)
                    ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2003:20: warning: ‘probe_model’ defined but not used [-Wunused-function]
 static void __init probe_model(void) {
                    ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2228:13: warning: ‘init_input’ defined but not used [-Wunused-function]
 static void init_input(void)
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2326:13: warning: ‘release_input’ defined but not used [-Wunused-function]
 static void release_input(void)
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2694:12: warning: ‘acerhk_proc_init’ defined but not used [-Wunused-function]
 static int acerhk_proc_init(void)
            ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2806:13: warning: ‘acerhk_proc_cleanup’ defined but not used [-Wunused-function]
 static void acerhk_proc_cleanup(void)
             ^
/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.c:2949:26: warning: ‘acerhk_misc_dev’ defined but not used [-Wunused-variable]
 static struct miscdevice acerhk_misc_dev = {
                          ^
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/acerhk/0.5.35/build/acerhk/acerhk.o] Error 1
make[1]: *** [_module_/var/lib/dkms/acerhk/0.5.35/build/acerhk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-14-generic'
make: *** [acerhk.ko] Error 2
make: Leaving directory `/var/lib/dkms/acerhk/0.5.35/build/acerhk'
```

---

### Post by praseodym on 2013-12-29
Obviously it does not work anymore with kernel 3.11. Try Ubuntu 12.04 LTS with Live-CD or stick

---

### Post by pro-power on 2014-07-22
Sorry to bump this old thread, but the solution to Amilo Pro V3505 Wifi problem is to upgrade your bios to the latest version. **B0G 27.04.2007**

[http://support.ts.fujitsu.com/Download/Index.asp](http://support.ts.fujitsu.com/Download/Index.asp)

Bios update fixed Wlan in Linux Mint 17 (Ubuntu 14.04) and Suse 13.1

---

### Post by praseodym on 2014-07-22
There is a new version available now for new kernels:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/07/20/6674857-acerhk-0.5.6_dkms.tar.gz
sudo tar xvf 6674857-acerhk-0.5.6_dkms.tar.gz -C /usr/src
sudo dkms add -m acerhk -v 0.5.6
sudo dkms build -m acerhk -v 0.5.6
sudo dkms install -m acerhk -v 0.5.6 
```

---

