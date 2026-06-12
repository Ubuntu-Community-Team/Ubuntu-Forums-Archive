---
title: "Problem at fixing the &quot;ndiswrapper module not found&quot; problem"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by diniz-cpm on 2013-09-30
Hi everyone,

My Ubuntu 12.04.3 LTS works perfectly with an ethernet cable, but can't detect any wireless connection. To fix this, I installed in Windows 8 (which runs in dual boot with Ubuntu) a [Realtek RTL8188EE]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=ob-117672-1") driver, which I believe is the correct one for my notebook. I booted Windows and installed the driver (the setup.exe file).

Ndiswrapper can install this driver, but when I try to run 
```
[COLOR=#333333][FONT=Ubuntu]sudo depmod -a
sudo modprobe ndiswrapper
[/FONT][/COLOR]
```
I get the
```
[FONT=Ubuntu Mono]FATAL: Module ndiswrapper not found[/FONT]
```
error. To fix this, I followed the 'Fix suggestion #2" that can be found [here]("http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found"). But then I got this:
```
daniel@daniel-C14CU51:~$ cd /usr/src/modules/ndiswrapper
daniel@daniel-C14CU51:/usr/src/modules/ndiswrapper$ sudo make
[sudo] password for daniel: 




Cannot find kernel build files in /usr/src/linux-headers-3.8.0-31-generic
Please give the path to kernel build directory with
the KBUILD=<path> argument to make




make: *** [config_check] Error 1
daniel@daniel-C14CU51:/usr/src/modules/ndiswrapper$ 

```
I have no idea of what to do now. Can someone help me? I know absolutely nothing about how Ubuntu really works and command line (I just know how to copy and paste a few commands at the terminal).

Info that might be useful:
Intel® Celeron(R) CPU 847 @ 1.10GHz × 2

```
daniel@daniel-C14CU51:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
02:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 80:ee:73:6b:24:0f  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::82ee:73ff:fe6b:240f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6639722 (6.6 MB)  TX bytes:1066168 (1.0 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50511 (50.5 KB)  TX bytes:50511 (50.5 KB)
```
```
lsmod
Module                  Size  Used by
parport_pc             28284  0 
ppdev                  17113  0 
rfcomm                 47864  0 
bnep                   18258  2 
bluetooth             247165  10 rfcomm,bnep
nls_iso8859_1          12713  1 
joydev                 17613  0 
coretemp               13596  0 
uvcvideo               82214  0 
kvm_intel             137899  0 
i915                  620571  3 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
kvm                   455932  1 kvm_intel
snd_hda_codec_realtek    79916  1 
ghash_clmulni_intel    13259  0 
snd_hda_intel          44339  3 
cryptd                 20501  1 ghash_clmulni_intel
snd_hda_codec         141761  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
drm_kms_helper         49597  1 i915
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
drm                   287564  4 i915,drm_kms_helper
psmouse                97873  0 
serio_raw              13215  0 
sparse_keymap          13890  0 
microcode              23017  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13564  1 i915
snd                    69533  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
video                  19652  1 i915
wmi                    19256  0 
mei                    41820  0 
rtsx_pci_ms            13180  0 
memstick               16605  1 rtsx_pci_ms
lpc_ich                17144  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ext2                   73755  1 
hid_generic            12540  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
rtsx_pci_sdmmc         17800  0 
r8169                  68716  0 
ahci                   25879  4 
libahci                31606  1 ahci
rtsx_pci               34530  2 rtsx_pci_ms,rtsx_pci_sdmmc
```
```
daniel@daniel-C14CU51:~$ sudo lshw -C network
[sudo] password for daniel: 
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7200000-f7203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: eth0
       version: 0a
       serial: 80:ee:73:6b:24:0f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
```
```
 iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.
```
```
uname -mr
3.8.0-31-generic x86_64
```
```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
```

---

### Post by s-bodet on 2013-09-30
Hi,

> Cannot find kernel build files in /usr/src/linux-headers-3.8.0-31-generic Please give the path to kernel build directory with the KBUILD=<path> argument to make 

you probably don't have the right kernel header package.

> sudo apt-get install linux-headers-3.8.0-31-generic

should correct this error message.

Steve

---

### Post by chili555 on 2013-09-30
I suggest you install the proper Linux driver. Verify with:```
lspci -nn | grep 0280
```Is your device 10ec:8179? If so, check here: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

If not, please tell us what it is.> sudo lshw -C network
[sudo] password for daniel: 
[COLOR="#FF0000"]PCI (sysfs)[/COLOR]I don't think you waited long enough.

---

### Post by diniz-cpm on 2013-09-30
> **chili555 said:**
> I suggest you install the proper Linux driver. Verify with:```
lspci -nn | grep 0280
```Is your device 10ec:8179? If so, check here: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)

If not, please tell us what it is.I don't think you waited long enough.
You were right, I didn't wait long enough! I updated my first post so that it now includes the full response to that command.

And my device is [COLOR=#000000]*10ec:8179. *[/COLOR]I followed the directions provided at this link, and I got no error message whatsoever, but it didn't help either.
> **s-bodet said:**
> Hi,



you probably don't have the right kernel header package.



should correct this error message.

Steve
Hi! I did this but it didn't help ):

I think it's worthy to point out that I've been trying to set up a wireless connection on Ubuntu for a week now, so I followed lots of "how to's", tutorials and tips. I have installed and uninstalled ndiswrapper a hundred times (with the software center and with command line). So maybe I've messed up with something important, IDK.

---

### Post by chili555 on 2013-09-30
>  I got no error message whatsoever, but it didn't help either.What does this tell us?```
iwconfig
sudo modprobe rtl8188ee
dmesg | grep rtl
```

---

### Post by diniz-cpm on 2013-09-30
> **chili555 said:**
> What does this tell us?```
iwconfig
sudo modprobe rtl8188ee
dmesg | grep rtl
```
Here's what I got:
```
daniel@daniel-C14CU51:~$ iwconfig

eth0      no wireless extensions.


lo        no wireless extensions.


daniel@daniel-C14CU51:~$ sudo modprobe rtl8188ee
[sudo] password for daniel: 
daniel@daniel-C14CU51:~$ dmesg | grep rtl
[ 1423.926867] rtl8188ee 0000:01:00.0: enabling device (0000 -> 0003)
[ 1423.936177] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[ 1423.986360] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available
```

---

### Post by chili555 on 2013-09-30
> rtlwifi: Firmware rtlwifi/rtl8188efw.bin not availableAh, ha! We need but don't have the required firmware. Please do:```
sudo apt-get install linux-firmware
```Then check:```
ls /lib/firmware/rtlwifi
```Is rtl8188efw.bin now present? If so, unload and reload the driver so it sees the new firmware:```
sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee
``` Better?

---

### Post by diniz-cpm on 2013-09-30
> **chili555 said:**
> Ah, ha! We need but don't have the required firmware. Please do:```
sudo apt-get install linux-firmware
```Then check:```
ls /lib/firmware/rtlwifi
```Is rtl8188efw.bin now present? If so, unload and reload the driver so it sees the new firmware:```
sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee
``` Better?
Hm, I tried this:
```
daniel@daniel-C14CU51:~$ sudo apt-get install linux-firmwareReading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-rb-3.0 gir1.2-gstreamer-0.10 python-mako gir1.2-ubuntuoneui-3.0
  libdmapsharing-3.0-2 rhythmbox-data libdiscid0 libgpod-common
  gir1.2-gnomekeyring-1.0 librhythmbox-core5 libgpod4
  gir1.2-gst-plugins-base-0.10 libubuntuoneui-3.0-1 media-player-info
  python-markupsafe libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
daniel@daniel-C14CU51:~$ ls /lib/firmware/rtlwifi
rtl8192cfw.bin   rtl8192defw.bin  rtl8712u.bin     rtl8723fw.bin
rtl8192cufw.bin  rtl8192sefw.bin  rtl8723fw_B.bin
daniel@daniel-C14CU51:~$ sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee
daniel@daniel-C14CU51:~$ 
daniel@daniel-C14CU51:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


daniel@daniel-C14CU51:~$ sudo modprobe rtl8188ee
daniel@daniel-C14CU51:~$ dmesg | grep rtl
[  127.009095] rtl8188ee 0000:01:00.0: enabling device (0000 -> 0003)
[  127.018535] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[  127.042334] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available
[  171.877282] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[  171.882033] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available
daniel@daniel-C14CU51:~$
```

What's different now is that when I go to System Settings > Additional Drivers there's [this]("https://docs.google.com/file/d/0B-L9IXHAic8qbGRxUV9pR0dfMjQ/edit?usp=sharing"). Before there was something like "there are no available additional drivers".

---

### Post by chili555 on 2013-09-30
I hate it when the system is being stubborn and uncooperative like some ladies in my life! It appears that the linux-firmware package for your Ubuntu version doesn't include 8188exx firmware. Let's try a different approach. ```
wget http://mirror.pnl.gov/ubuntu//pool/main/l/linux-firmware/linux-firmware_1.106_all.deb
sudo dpkg -i linux*.deb 
sudo modprobe -r rtl8188ee && sudo modprobe rtl8188ee
```Does that do it?

---

### Post by diniz-cpm on 2013-10-01
OMG! Now I can connect to wireless! Thank you very much! I was almost giving up haha.

---

### Post by chili555 on 2013-10-01
> **diniz-cpm said:**
> OMG! Now I can connect to wireless! Thank you very much! I was almost giving up haha.Give up? Never.

Please retain the files and note the part from the linked post:>  When Update Manager installs a later linux-image, after reboot, re-compile...Glad it's working! Have fun!

---

