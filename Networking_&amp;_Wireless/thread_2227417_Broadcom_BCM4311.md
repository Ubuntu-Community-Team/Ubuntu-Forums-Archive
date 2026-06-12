---
title: "Broadcom BCM4311"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by b14ker on 2014-06-01
I have tried linux mint and lubuntu and can not get a wifi search to come up it says my drivers are enabled. Tried everything, any suggestions??

---

### Post by varunendra on 2014-06-01
Welcome to the forums b14ker!

Please open a terminal (Ctrl-Alt-T), and show us the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by b14ker on 2014-06-01
```
 b14ker@PCO ~/Desktop $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Device [1028:0201]
    Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl
b14ker@PCO ~/Desktop $ lspod
No command 'lspod' found, did you mean:
 Command 'lsmod' from package 'kmod' (main)
lspod: command not found
b14ker@PCO ~/Desktop $ lsmod
Module                  Size  Used by
wl                   3999690  1 
gpio_ich               13229  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
bnep                   18895  2 
rfcomm                 53664  0 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
dm_multipath           22402  0 
scsi_dh                14458  1 dm_multipath
snd_hda_codec_idt      48877  1 
coretemp               13195  0 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
kvm                   388083  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
pcmcia                 51828  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
btusb                  27580  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
joydev                 17101  0 
lib80211               14040  1 wl
serio_raw              13230  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                16864  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
yenta_socket           40201  0 
pcmcia_rsrc            18319  1 yenta_socket
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
bluetooth             342263  11 bnep,btusb,rfcomm
cfg80211              409394  1 wl
snd                    60871  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
dm_mirror              21756  0 
dm_region_hash         20121  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
psmouse                91033  0 
firewire_ohci          35529  0 
i915                  705396  2 
sdhci_pci              18535  0 
tg3                   152132  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
usb_storage            48417  0 
crc_itu_t              12627  1 firewire_core
ptp                    18445  1 tg3
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
pps_core               18799  1 ptp
drm_kms_helper         46907  1 i915
wmi                    18673  1 dell_wmi
drm                   243792  3 i915,drm_kms_helper
b14ker@PCO ~/Desktop $ 
```

---

### Post by b14ker on 2014-06-01
But now I did something where There are no drivers showing up

---

### Post by WinEunuchs2Unix on 2014-06-01
The good ole "Broadcom" wireless problem.  I spent many hours this weekend getting it to work and using many suggestions (some fried my machine) until I found this solution: [https://askubuntu.com/questions/235265/netgear-a6200-usb-modem-does-not-work-on-ubuntu-12-10/263971#263971?s=5cfb1ca5-947f-4905-a638-cf17cf9cc87e](https://askubuntu.com/questions/235265/netgear-a6200-usb-modem-does-not-work-on-ubuntu-12-10/263971#263971?s=5cfb1ca5-947f-4905-a638-cf17cf9cc87e)

That solution only gives you the drivers bcmwlhigh5.inf & .sys and includes bcm43xx.cat.  
Next use ndiswrapper (instructions abound in ubuntu forums) to turn the Windows driver into a Linux driver.  
Next use modprobe to insert the Linux driver into the Kernel (instructions abound...). 
When done it will work but you need to unplug the broadcom adapter and plug it back in when waking up from suspend.

FWIW I now have three wireless: wlan0: built-in Intel (Golan) 802.11 a/b/g, wlan1: usb Ralink 802.11 b/g/n and wlan2: usb Netgear A6200 802.11 ac/b/g/n.  The challenge now: automatically switch to the currently fastest Mbps connection.

---

### Post by varunendra on 2014-06-02
> **b14ker said:**
> ```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g **[14e4:4312]** (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: wl
```

If you can connect to internet via ethernet cable or other means, please open a terminal (Ctrl-Alt-T), and install the required firmware for the correct driver with the following commands -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
[s]sudo apt-get install linux-firmware-nonfree[/s] *[COLOR="#FF0000"]# this will no longer install b43 firmware, try the next command below[/COLOR]*
sudo apt-get install firmware-b43-installer
```

If you can't connect to internet, follow this post to install it without internet on the target machine : [http://ubuntuforums.org/showpost.php?p=13062169](http://ubuntuforums.org/showpost.php?p=13062169)

Reboot the computer after installing the firmware, and let us know the result.

**[COLOR="#FF0000"]EDIT:[/COLOR]** 11-Sep-2014 : **Added the new command to install the firmware, since "linux-firmware-nonfree" will no longer install it**. See this [bug report]("https://bugs.launchpad.net/bugs/1367882").

---

### Post by Mohd_Iznan on 2014-06-02
I also have a same problem. After i follow the sudo apt-get, the wifi problem is solve. Thanks bro, now i really like to use ubuntu. Keep in growing up guys....

---

### Post by varunendra on 2014-06-02
Welcome to the forums Iznan! Hope to see you around. :)

---

### Post by b14ker on 2014-06-04
```
 b14ker@PCO ~/Desktop $ sudo apt-get purge bwml-kernel-source E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  b14ker@PCO ~/Desktop $ 
```   Which i did but i get lost after i enter it

---

### Post by Hadaka on 2014-06-04
Hi, see if this untangels your mess, with the ethernet cable
attached ,please do, one line at a time..even if they fail...do the next line

Copy and paste.
```
sudo dpkg --configure -a
sudo rm -rf /var/lib/apt/lists/lock
sudo dpkg -r bcmwl-kernel-source
```
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
now install the driver you need
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by b14ker on 2014-06-04
My only question is after i do the first line, im still a noob.. how do i  get my b14ker@pco up ```
b14ker@PCO ~/Desktop $ sudo dpkg --configure  -a
[sudo] password for b14ker: 
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.141+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.141+bdcom
Kernel:  3.13.0-24-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-24-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.141+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
Building only for 3.13.0-24-generic
Building for architecture i686
Building initial module for 3.13.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-24-generic/updates/

depmod....

DKMS: install completed.


```

---

### Post by Hadaka on 2014-06-04
You currently have the wrong driver loaded
keep your ethernet cable attached and continue
one lne at a time, the last 3 lines load the correct driver
once that is complete and you boot everythin should be fine

---

### Post by b14ker on 2014-06-04
```
b14ker@PCO ~/Desktop $ sudo dpkg --configure -a
[sudo] password for b14ker: 
dpkg: error: dpkg status database is locked by another process
b14ker@PCO ~/Desktop $ sudo rm -rf /var/lib/apt/lists/lock
b14ker@PCO ~/Desktop $ sudo dpkg -r bcml-kernel-source
dpkg: error: dpkg status database is locked by another process i 
b14ker@PCO ~/Desktop $ 


``` i keep getting this bc the first line doesnt seem to finish correctly but im not surel

---

### Post by Hadaka on 2014-06-04
give the first command some time to finish..cose any programs you may have running especialy from the software center
also..go to your home page....not Desktop. check to see if there are any updates running....and finally boot

---

### Post by b14ker on 2014-06-05
```
 b14ker@PCO ~/Desktop $ sudo dpkg --configure -a
[sudo] password for b14ker: 
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.141+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.141+bdcom
Kernel:  3.13.0-24-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-24-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.141+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
Building only for 3.13.0-24-generic
Building for architecture i686
Building initial module for 3.13.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-24-generic/updates/

depmod....

DKMS: install completed.


``` just stuck on this ... leaving over night.

---

### Post by b14ker on 2014-06-05
so its stuck on the same spot, do i restart my pc from where its at or am i doing something wrong

---

### Post by varunendra on 2014-06-06
Something is definitely wrong. It shouldn't take more than 2 minutes.

What happens if you run the following commands -
```
sudo rm /var/lib/dpkg/lock
sudo dpkg -P bcmwl-kernel-source
sudo dpkg --configure -a
```
Does it finish successfully? If yes, you may proceed with the remaining steps suggested by hadaka.

---

### Post by b14ker on 2014-09-10
switched to kali linux (backtrak)

---

