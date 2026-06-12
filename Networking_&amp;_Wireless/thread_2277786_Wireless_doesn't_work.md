---
title: "Wireless doesn't work"
date: 2015-05-11
forum: Networking &amp; Wireless
---

### Post by simon.yanez90 on 2015-05-11
Hi, i just installed ubuntu mate in a new HP ENVY 15 and everything goes well except for the wireless connection. I don't have a wired connection so I tried to download b43 firmware deb package from another computer and install it in the HP but it doesn't work. When I put ***rfkill list*** it just shows me ***0: hci0 Bluetooth ***but no wireless option.

I tried to make ***rfkill unblock all*** but it also doesn't work.

Thanks for the help.

---

### Post by wildmanne39 on 2015-05-11
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by simon.yanez90 on 2015-05-11
Thank you for your help, here are the results:

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"
Linux simon-HP-ENVY-15-Notebook-PC 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:32:52 UTC 2015 i686 i686 i686 GNU/Linux
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ lspci nnk | grep -iA2 net
Usage: lspci [<switches>]


Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree


Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers


Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's


Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ lsusb
Bus 001 Device 005: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ lsmod
Module                  Size  Used by
bnep                   18895  2 
rfcomm                 58045  12 
parport_pc             32021  0 
ppdev                  17391  0 
b43                   369555  0 
uvcvideo               71465  0 
mac80211              559049  1 b43
btusb                  27649  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
bluetooth             391253  22 bnep,btusb,rfcomm
videobuf2_core         48344  1 uvcvideo
v4l2_common            15132  1 videobuf2_core
videodev              131265  3 uvcvideo,v4l2_common,videobuf2_core
6lowpan_iphc           18262  1 bluetooth
media                  20899  2 uvcvideo,videodev
cfg80211              418839  2 b43,mac80211
snd_hda_codec_hdmi     46396  1 
snd_hda_codec_realtek    70475  1 
snd_hda_codec_generic    62873  1 snd_hda_codec_realtek
ssb                    51835  1 b43
snd_hda_intel          29285  5 
snd_hda_controller     29944  1 snd_hda_intel
hp_wmi                 13741  0 
snd_hda_codec         120371  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
sparse_keymap          13708  1 hp_wmi
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                87194  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13324  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  1 snd_seq_midi
snd_seq                56592  2 snd_seq_midi_event,snd_seq_midi
intel_rapl             18311  0 
x86_pkg_temp_thermal    13845  0 
intel_powerclamp       18385  0 
coretemp               13201  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   388518  0 
snd_timer              28648  2 snd_pcm,snd_seq
crc32_pclmul           12987  0 
aesni_intel            18170  1 
nouveau              1067392  0 
i915                  808547  5 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
cryptd                 15578  1 ablk_helper
mxm_wmi                12893  1 nouveau
ttm                    85257  1 nouveau
joydev                 17113  0 
drm_kms_helper         55007  2 i915,nouveau
serio_raw              13251  0 
drm                   255469  6 ttm,i915,drm_kms_helper,nouveau
bcma                   46331  1 b43
lpc_ich                16877  0 
snd                    66670  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
shpchp                 32143  0 
mei_me                 19064  0 
i2c_algo_bit           13197  2 i915,nouveau
soundcore              14599  2 snd,snd_hda_codec
mei                    72048  1 mei_me
hp_accel               25778  0 
wmi                    18689  3 hp_wmi,mxm_wmi,nouveau
lis3lv02d              19500  1 hp_accel
video                  19475  2 i915,nouveau
hp_wireless            12557  0 
intel_smartconnect     12573  0 
input_polldev          14247  1 lis3lv02d
mac_hid                13059  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
r8169                  61579  0 
ahci                   25622  2 
psmouse                91236  0 
libahci                26970  1 ahci
mii                    13654  1 r8169
```

---

### Post by wildmanne39 on 2015-05-11
The lspci -nnk | grep -iA2 net command should have produced results like these, please copy and paste the command from my pevious post into the terminal and post the result here, I have to identify your device.
```
lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0647]
	Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6617]
	Kernel driver in use: ath9k
```
Also please post the output of:
```
sudo cat /var/log/syslog | grep -e b43 -e wl -e wlan -e wpa -e network -e firmware | tail -n45
```

---

### Post by simon.yanez90 on 2015-05-11
Sorry about that, here are the results:

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ lspci -nnk | grep -iA2 net
08:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2230]
    Kernel driver in use: bcma-pci-bridge
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:228d]
    Kernel driver in use: r8169
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~$ sudo cat /var/log/syslog | grep -e b43 -e wl -e wlan -e wpa -e network -e firmware | tail -n45
May 10 17:26:59 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/firmware-ralink_0.43_all.deb
May 10 17:27:00 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: CRITICAL: /home/simon/Escritorio/firmware-ralink_0.43_all.deb: trying to overwrite '/lib/firmware/rt3290.bin', which is also in package linux-firmware 1.127.11
May 10 17:32:20 simon-HP-ENVY-15-Notebook-PC NetworkManager[831]: <info> kernel firmware directory '/lib/firmware' changed
May 10 17:54:11 simon-HP-ENVY-15-Notebook-PC kernel: [    0.000000] DMI: Hewlett-Packard HP ENVY 15 Notebook PC /228D, BIOS F.09 08/04/2014
May 10 17:54:11 simon-HP-ENVY-15-Notebook-PC kernel: [   12.407322] bluetooth hci0: Direct firmware load failed with error -2
May 10 17:54:13 simon-HP-ENVY-15-Notebook-PC NetworkManager[755]:       interface-parser: parsing file /etc/network/interfaces
May 10 17:54:13 simon-HP-ENVY-15-Notebook-PC NetworkManager[755]:       interface-parser: finished parsing file /etc/network/interfaces
May 10 17:54:13 simon-HP-ENVY-15-Notebook-PC NetworkManager[755]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 10 19:00:21 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
May 10 19:00:21 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 10 19:00:34 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: InstallFile() was called: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 10 19:00:34 simon-HP-ENVY-15-Notebook-PC AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/05c03440bbdb433181b58dedf21beea0
May 10 19:00:34 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/05c03440bbdb433181b58dedf21beea0
May 10 19:00:35 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 10 19:00:41 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/05c03440bbdb433181b58dedf21beea0
May 10 19:00:41 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 10 19:00:44 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/05c03440bbdb433181b58dedf21beea0
May 10 19:01:41 simon-HP-ENVY-15-Notebook-PC kernel: [    0.000000] DMI: Hewlett-Packard HP ENVY 15 Notebook PC /228D, BIOS F.09 08/04/2014
May 10 19:01:41 simon-HP-ENVY-15-Notebook-PC kernel: [   11.796627] bluetooth hci0: Direct firmware load failed with error -2
May 10 19:01:43 simon-HP-ENVY-15-Notebook-PC NetworkManager[727]:       interface-parser: parsing file /etc/network/interfaces
May 10 19:01:43 simon-HP-ENVY-15-Notebook-PC NetworkManager[727]:       interface-parser: finished parsing file /etc/network/interfaces
May 10 19:01:43 simon-HP-ENVY-15-Notebook-PC NetworkManager[727]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 10 19:03:42 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
May 10 19:03:42 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 10 19:03:56 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('firmware-ralink')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
May 10 19:03:56 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('firmware-ralink')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 10 19:04:00 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: InstallFile() was called: /home/simon/Escritorio/Linux/firmware-ralink_0.43_all.deb
May 10 19:04:00 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/firmware-ralink_0.43_all.deb
May 10 19:04:06 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/firmware-ralink_0.43_all.deb
May 10 19:04:08 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: CRITICAL: /home/simon/Escritorio/Linux/firmware-ralink_0.43_all.deb: trying to overwrite '/lib/firmware/rt3290.bin', which is also in package linux-firmware 1.127.11
May 10 19:04:31 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s')), dbus.Array([dbus.String('')], signature=dbus.Signature('s'))
May 10 19:04:31 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('b43-fwcutter')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 10 19:04:38 simon-HP-ENVY-15-Notebook-PC AptDaemon: INFO: InstallFile() was called: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 10 19:04:39 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 10 19:04:48 simon-HP-ENVY-15-Notebook-PC AptDaemon.Worker: INFO: Installing local package file: /home/simon/Escritorio/Linux/b43-fwcutter_015-9_i386.deb
May 11 08:02:49 simon-HP-ENVY-15-Notebook-PC kernel: [    0.000000] DMI: Hewlett-Packard HP ENVY 15 Notebook PC /228D, BIOS F.09 08/04/2014
May 11 08:02:49 simon-HP-ENVY-15-Notebook-PC kernel: [   12.118151] bluetooth hci0: Direct firmware load failed with error -2
May 11 08:02:51 simon-HP-ENVY-15-Notebook-PC NetworkManager[851]:       interface-parser: parsing file /etc/network/interfaces
May 11 08:02:51 simon-HP-ENVY-15-Notebook-PC NetworkManager[851]:       interface-parser: finished parsing file /etc/network/interfaces
May 11 08:02:51 simon-HP-ENVY-15-Notebook-PC NetworkManager[851]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 11 10:25:19 simon-HP-ENVY-15-Notebook-PC kernel: [    0.000000] DMI: Hewlett-Packard HP ENVY 15 Notebook PC /228D, BIOS F.09 08/04/2014
May 11 10:25:19 simon-HP-ENVY-15-Notebook-PC kernel: [   12.641088] bluetooth hci0: Direct firmware load failed with error -2
May 11 10:25:20 simon-HP-ENVY-15-Notebook-PC NetworkManager[720]:       interface-parser: parsing file /etc/network/interfaces
May 11 10:25:20 simon-HP-ENVY-15-Notebook-PC NetworkManager[720]:       interface-parser: finished parsing file /etc/network/interfaces
May 11 10:25:20 simon-HP-ENVY-15-Notebook-PC NetworkManager[720]: <info> monitoring kernel firmware directory '/lib/firmware'.
```

---

### Post by wildmanne39 on 2015-05-11
You have the wrong driver installed so let's remove it:
```
sudo apt-get purge firmware-b43-installer
```
Your Broadcom 14e4:4365 uses bcmwl-kernel-source. It and its dependency dkms are on the installation DVD or USB. Insert the install media and go to pool > restricted > b > bcmwl and drag and drop the bcmwl deb package to your desktop. Do the same with pool > main > d > dkms. Now install the deb files. 
Open a terminal and:
```
cd ~/Desktop
sudo dpkg -i *.deb
sudo modprobe wl
```
Thanks

---

### Post by simon.yanez90 on 2015-05-11
I did it, these are the results:

```
simon@simon-HP-ENVY-15-Notebook-PC:~/Escritorio$ sudo dpkg -i bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_i386.deb
Seleccionando el paquete bcmwl-kernel-source previamente no seleccionado.(Leyendo la base de datos ... 161778 ficheros o directorios instalados actualmente.)
Preparing to unpack bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_i386.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
dpkg: problemas de dependencias impiden la configuración de bcmwl-kernel-source:
 bcmwl-kernel-source depende de dkms; sin embargo:
  El paquete `dkms' no está instalado.
 bcmwl-kernel-source depende de linux-libc-dev; sin embargo:
  El paquete `linux-libc-dev' no está instalado.
 bcmwl-kernel-source depende de libc6-dev; sin embargo:
  El paquete `libc6-dev' no está instalado.


dpkg: error al procesar el paquete bcmwl-kernel-source (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 bcmwl-kernel-source
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~/Escritorio$ sudo dpkg -i dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb
Seleccionando el paquete dkms previamente no seleccionado.
(Leyendo la base de datos ... 161845 ficheros o directorios instalados actualmente.)
Preparing to unpack dkms_2.2.0.3-1.1ubuntu5.14.04_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04) ...
dpkg: problemas de dependencias impiden la configuración de dkms:
 dkms depende de gcc; sin embargo:
  El paquete `gcc' no está instalado.
 dkms depende de make | build-essential | dpkg-dev; sin embargo:
  El paquete `make' no está instalado.
  El paquete `build-essential' no está instalado.
  El paquete `dpkg-dev' no está instalado.


dpkg: error al procesar el paquete dkms (--install):
 problemas de dependencias - se deja sin configurar
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Se encontraron errores al procesar:
 dkms
```

```
simon@simon-HP-ENVY-15-Notebook-PC:~/Escritorio$ sudo modprobe wl
modprobe: FATAL: Module wl not found.
```

And in the right superior part of the screen there's a caution message that says **"Error:BrokenCount>0"**

---

### Post by wildmanne39 on 2015-05-11
I do not read spanish but > dkmslooks like it failed and caused everything else to fail.
Did you install dkms?
Did you use the installation dvd, cd, or usb to install these packages?
Did you go into software center and tell it to let you search for the files from the installation media, refer to the screenshot?
It is possible that gksu is not installed and will not to be installed first.
Thanks

---

### Post by jeremy31 on 2015-05-11
Wild Man, simon.yanez90,

The Ubuntu 14.04.2 install media contains the wrong version of bcmwl-kernel-source for the 3.16 kernel, it will have to be downloaded from a mirror site [http://packages.ubuntu.com/utopic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/utopic/i386/bcmwl-kernel-source/download)

Hopefully the broken dependencies vanish with this version but there are links to those packages- [http://packages.ubuntu.com/utopic/bcmwl-kernel-source](http://packages.ubuntu.com/utopic/bcmwl-kernel-source)

---

### Post by wildmanne39 on 2015-05-11
Thanks Jeremy31, is there a way he can get the driver and dependencies on an usb drive? he does not have internet connection.

---

### Post by simon.yanez90 on 2015-05-11
When I try to install ***dkms*** says that I don't have ***gcc***, and when I try to install ***bcmwl*** says that I need to install ***linux-libc-dev***.


When I bought the computer I installed ***Linux Mint*** on it and the internet wireless conection didn't work, and now with ***Ubuntu Mate*** is the same. Maybe if I install another distribution this problem will disapear?


Thanks for the advices.

---

### Post by jeremy31 on 2015-05-11
Dependencies should be on the install media even if the version of bcmwl-kernel-source is wrong

I will have to look now

---

### Post by simon.yanez90 on 2015-05-11
Is there a way to install all this packages again?

I don't know what else to do.

---

### Post by jeremy31 on 2015-05-11
If you have the DVD/USB you installed from, use the file manager to go to /pool/main/d/dkms and double click on the deb file and see if it installs

---

### Post by simon.yanez90 on 2015-05-11
I'd already made that but it doesn't work. I'm using a USB bootable.

---

### Post by wildmanne39 on 2015-05-11
Apparently you do not have the needed packages installed to install the driver and I do not know a good way to install them without an internet connection. Can you take your computer to a friends house or somewhere you can connect to the internet?
If you get an internet connection do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
```
that should give you all the dependencies you need to install the driver in jermy31's post.
Thanks

---

### Post by simon.yanez90 on 2015-05-11
Finally, I re-installed linux mint 17 and copied the files from the usb bootable.


Thanks for all the help!


PS: What should I do with the post? Put solved in the title?

---

### Post by wildmanne39 on 2015-05-11
Yes mark as solved if you have working wifi with the help of the directions we provided.

---

