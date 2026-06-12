---
title: "Problems with rtl8723be on Ubuntu -14.04.4-desktop-i386"
date: 2017-06-18
forum: Networking &amp; Wireless
---

### Post by tofazzalshuvo on 2017-06-18
[INDENT]                     Hi,
I am new in ubuntu user.I've got a problem with r8732be (using a PCI card with HP-15ae-140ne) on Ubuntu -14.04.4-desktop-i386..
After booting ubuntu, it's connect automatically but after sometime it will be disconnected!!!
I try many way to solve this, but it doesn't work.
Finally, I find a solution with installing "ndiswrapper".
But I cannot finished installing process because I am new in ubuntu..:(:(:(:(


Can you help me with all the [approprate]("https://www.google.com/search?client=ubuntu&hs=XkM&channel=fs&q=approprate&nfpr=1&sa=X&ved=0ahUKEwjr8u7LgcjUAhXDRo8KHbGmDkUQvgUIJSgB") commands and download link for "ndiswrapper", please ? 
[/INDENT]

---

### Post by praseodym on 2017-06-18
Hi,

lets check which card it is precisely:
```

lspci -nnk
```
Ndiswrapper doesn't work with LAN cards!

---

### Post by tofazzalshuvo on 2017-06-18
when I paste the command it showing,
```
00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: bdw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Broadwell-U Camarillo Device [8086:1603] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: proc_thermal
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 [8086:9c90] (rev e3)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 [8086:9c94] (rev e3)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 [8086:9c98] (rev e3)
    Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 [8086:9c9a] (rev e3)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc3] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
00:1f.6 Signal processing controller [1180]: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:80c2]
    Kernel driver in use: r8169
0d:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330] [1002:6660] (rev ff)
    Kernel driver in use: radeon
13:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be
```

---

### Post by praseodym on 2017-06-18
So it is not a driver problem. Lets chack:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
ifconfig -a
```
Also please install

```
sudo apt-get install ethtool
```

and show
```

sudo ethtool eth0
```

---

### Post by tofazzalshuvo on 2017-06-18
I am not trying for Ethernet...I am trying for wireless connection..

showing for the command "cat /etc/network/interfaces",
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```


showing for the command "ifconfig -a"
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```


showing for the command "cat /etc/resolv.conf"
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0
```


showing for the command "route -n"
```
eth0      Link encap:Ethernet  HWaddr 94:57:a5:ad:53:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1116138 (1.1 MB)  TX bytes:1116138 (1.1 MB)

usb0      Link encap:Ethernet  HWaddr 86:55:7e:f1:79:16  
          inet addr:192.168.42.128  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::8455:7eff:fef1:7916/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62224 errors:23 dropped:0 overruns:0 frame:23
          TX packets:61534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48077643 (48.0 MB)  TX bytes:10735238 (10.7 MB)

wlan0     Link encap:Ethernet  HWaddr 40:b8:9a:3c:47:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


showing for the command "sudo apt-get install ethtool"
```
[sudo] password for shuvo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ethtool is already the newest version.
The following packages were automatically installed and are no longer required:
  libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

showing for the command "sudo ethtool eth0"
```
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no
```

---

### Post by Hadaka on 2017-06-18
Hi, please see post #2
This is the same wireless card as yours.

[https://ubuntuforums.org/showthread.php?t=2364060](https://ubuntuforums.org/showthread.php?t=2364060)
Thanks.

---

### Post by tofazzalshuvo on 2017-06-19
It's solved!!!
Thank you so much...

---

### Post by Hadaka on 2017-06-19
Great ! glad that worked for you.
Thank you for marking your thread Solved.

---

### Post by tofazzalshuvo on 2017-06-19
ohhh...It's worked for temporary..Again it's disconnected and show "You are offline"..

---

### Post by Hadaka on 2017-06-19
Hi, please post the output of..
```
cat /etc/modprobe.d/rtl8723be.conf
```
then do..
```
sudo modprobe -v rtl8723be
```
thanks.

---

### Post by praseodym on 2017-06-19
Please check
```

dmesg | grep rtl
lsmod
rfkill list
```

---

### Post by tofazzalshuvo on 2017-06-20
Please, give me a proper solution ....I am new in Ubuntu...
After sometime of new boot, it's show "disconnected you are off line"...
please! please! please!

---

### Post by praseodym on 2017-06-20
Show the required terminal outputs for diagnosis!

---

### Post by Hadaka on 2017-06-20
Please post the output of..
```
cat/etc/modprobe.d/rtl8723be.conf
```

Does the computer disconnect when you move away from
the router ?
Please respond so we can help you.
thanks

---

### Post by tofazzalshuvo on 2017-06-21
for the command "cat/etc/modprobe.d/rtl8723be.conf" it show,
"bash: cat/etc/modprobe.d/rtl8723be.conf: No such file or directory"

Nothing to show for the command 
"sudo modprobe -v rtl8723be" 



It's disconnect when the computer under the area of router..
Thanks..

My wireless-info.txt Pastebin link is bellow,
[http://paste.ubuntu.com/24909475/](http://paste.ubuntu.com/24909475/)

showing for the command "dmesg | grep rtl"
```
[   12.760993] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   12.760997] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   12.950611] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   13.083144] Using firmware rtlwifi/rtl8723befw.bin
[   13.083650] rtlwifi: channel plan 0x20
[   13.083651] rtlwifi: country code 11
[   13.116364] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.116949] rtlwifi: wireless switch is on
```

showing for the command "lsmod"
```
Module                  Size  Used by
drbg                   28672  1 
ansi_cprng             16384  0 
ctr                    16384  2 
ccm                    20480  2 
bnep                   20480  2 
rfcomm                 65536  8 
intel_rapl             20480  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       16384  0 
coretemp               16384  0 
uvcvideo               73728  0 
kvm                   442368  0 
videobuf2_vmalloc      16384  1 uvcvideo
crc32_pclmul           16384  0 
aesni_intel            20480  4 
aes_i586               20480  1 aesni_intel
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              143360  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_soc_rt286          28672  0 
snd_hda_codec_realtek    77824  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1 
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_hda_intel          32768  5 
arc4                   16384  2 
snd_hda_codec         114688  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           57344  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_soc_core          172032  1 snd_soc_rt286
rtl8723be             131072  0 
xts                    16384  1 aesni_intel
snd_compress           20480  1 snd_soc_core
lrw                    16384  1 aesni_intel
btcoexist             180224  1 rtl8723be
ac97_bus               16384  1 snd_soc_core
gf128mul               16384  2 lrw,xts
rtl_pci                36864  1 rtl8723be
rtlwifi                94208  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0 
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hwdep              16384  1 snd_hda_codec
sparse_keymap          16384  1 hp_wmi
ablk_helper            16384  1 aesni_intel
radeon               1437696  1 
i915                 1036288  4 
mac80211              655360  3 rtl_pci,rtlwifi,rtl8723be
snd_pcm                94208  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
btusb                  40960  0 
snd_seq_midi           16384  0 
btrtl                  16384  1 btusb
snd_seq_midi_event     16384  1 snd_seq_midi
cryptd                 20480  1 ablk_helper
btbcm                  16384  1 btusb
snd_rawmidi            28672  1 snd_seq_midi
btintel                16384  1 btusb
cfg80211              479232  2 mac80211,rtlwifi
bluetooth             454656  25 bnep,btbcm,btrtl,btusb,rfcomm,btintel
ttm                    86016  1 radeon
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper        114688  2 i915,radeon
dw_dmac                16384  0 
i2c_hid                20480  0 
input_leds             16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
joydev                 20480  0 
snd_timer              28672  2 snd_pcm,snd_seq
serio_raw              16384  0 
snd                    69632  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
drm                   303104  8 ttm,i915,drm_kms_helper,radeon
hid                    98304  1 i2c_hid
mei_me                 28672  0 
dw_dmac_core           24576  1 dw_dmac
wmi                    20480  1 hp_wmi
video                  24576  1 i915
mei                    94208  1 mei_me
snd_soc_sst_acpi       16384  0 
soundcore              16384  1 snd
8250_dw                16384  0 
int3403_thermal        16384  0 
i2c_designware_platform    16384  0 
i2c_algo_bit           16384  2 i915,radeon
shpchp                 32768  0 
i2c_designware_core    16384  1 i2c_designware_platform
mac_hid                16384  0 
lpc_ich                20480  0 
parport_pc             32768  0 
hp_wireless            16384  0 
ppdev                  20480  0 
spi_pxa2xx_platform    24576  0 
processor_thermal_device    16384  0 
tpm_crb                16384  0 
intel_soc_dts_iosf     16384  1 processor_thermal_device
lp                     16384  0 
int3402_thermal        16384  0 
int340x_thermal_zone    16384  3 int3402_thermal,processor_thermal_device,int3403_thermal
int3400_thermal        16384  0 
acpi_thermal_rel       16384  1 int3400_thermal
parport                45056  3 lp,ppdev,parport_pc
acpi_pad               16384  0 
psmouse               114688  0 
r8169                  73728  0 
ahci                   36864  2 
libahci                32768  1 ahci
mii                    16384  1 r8169
sdhci_acpi             16384  0 
sdhci                  40960  1 sdhci_acpi

showing for the command "rfkill list"
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by Hadaka on 2017-06-21
Hi, please post the output of..

```
cat /etc/modprobe.d/rtl8723be.conf
```

I forgot to add  space last time..sorry

Your country code is set GB ..but your time zone shows..
##### iw reg get ########################

Region: Asia/Dhaka (based on set time zone)
???? What is correct ????  Asia/Dhaka or Europe/London ??????

---

### Post by tofazzalshuvo on 2017-06-21
showing for the command"cat /etc/modprobe.d/rtl8723be.conf"

options rtl8723be ant_sel=1

Based on set time zone, my zone is Asia/Dhaka..
Please help me..I want to go with ubuntu..I love ubuntu..

---

### Post by Hadaka on 2017-06-21
Hi please copy and paste..
```
sudo iw reg set BD
sudo sed -i 's/=.*/=BD/'
```
boot
Does that help ?

---

### Post by tofazzalshuvo on 2017-06-21
Nothing to showed for the command "sudo iw reg set BD"...

showing for the command "sudo sed -i 's/=.*/=BD/'"
sed: no input files


It's not worked..[IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG][IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

---

### Post by Hadaka on 2017-06-22
Hi, please open a terminal and do..
```
sudo sed -i 's/1/2/' [COLOR=#000000]/etc/modprobe.d/rtl8723be.conf[/COLOR]
```
then post the output of..
```
cat [COLOR=#000000]/etc/modprobe.d/rtl8723be.conf[/COLOR]
```
Thanks

---

### Post by tofazzalshuvo on 2017-06-22
the output for the command "cat [COLOR=#000000]/etc/modprobe.d/rtl8723be.conf"

options rtl8723be ant_sel=2


[/COLOR]

---

### Post by Hadaka on 2017-06-22
Hi, the country code command i gave you was incomplete
I apologize for my error..please copy and paste..
```
sudo iw reg set BD
sudo sed -i 's/=.*/=BD/' /etc/default/crda
```
and reboot
are you now attaching to the internet ok ??

---

### Post by tofazzalshuvo on 2017-06-23
Hi, it has been disconnected sometime after long time but better than before.:(:(:(:(

---

### Post by Hadaka on 2017-06-23
Are you able to access the internet with a wired connection to your router ?
Thanks.

---

### Post by tofazzalshuvo on 2017-06-23
Yes...But it's very slow after sometime..

---

### Post by Hadaka on 2017-06-24
From a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
boot,disconnect the wired connection
and test wireless
thanks.

---

### Post by tofazzalshuvo on 2017-06-26
Hi, It's not solved..It's disconnected again and again.

---

### Post by Hadaka on 2017-06-26
Hi, we have made several changes and you say it has not improved.
Please post a fresh new wireless-info.txt Pastebin, so we can verify those
changes and look for any other errors.
Thanks.

---

### Post by tofazzalshuvo on 2017-06-26
Hi,this is the [COLOR=#000000]fresh new wireless-info.txt Pastebin[/COLOR] link
[http://paste.ubuntu.com/24955254/](http://paste.ubuntu.com/24955254/)
 

I am waiting for your help.. please help me..

---

### Post by Hadaka on 2017-06-26
Hi please COPY and paste one line at a time.
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e "sudo iw reg set BD\nexit 0" | sudo tee -a /etc/rc.local
sudo sed -i '/^REG/ d' /etc/default/crda
echo "REGDOMAIN=BD" | sudo tee -a /etc/default/crda
```
boot and test wireless
Thanks

---

### Post by jeremy31 on 2017-06-27
A kernel update may help, the 4.2 kernel is EOL since last August
```
sudo apt-get install --install-recommends linux-generic-lts-xenial
```
Reboot

---

### Post by tofazzalshuvo on 2017-07-01
Showing for the command "[COLOR=#000000][FONT=&quot]sudo apt-get install --install-recommends linux-generic-lts-xenial[/FONT][/COLOR] "

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

and [COLOR=#000000]this is the [/COLOR][COLOR=#000000][COLOR=#000000] new wireless-info.txt Pastebin[/COLOR][/COLOR][COLOR=#000000] link[/COLOR]
[http://paste.ubuntu.com/24997173/](http://paste.ubuntu.com/24997173/)

---

### Post by jeremy31 on 2017-07-01
```
iwlist scan | egrep -i 'ssid|quality'
```
These results will show the SSID and signal strength with your parameter setting, then we will unload the wifi module and load with one of the antenna settings and check results


```
sudo rm /etc/modprobe.d/rtl8723be.conf
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

Any better or the same?

---

### Post by tofazzalshuvo on 2017-07-02
Hi, no improvement and [COLOR=#000000][COLOR=#000000]this is the [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][COLOR=#000000]new wireless-info.txt Pastebin[/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000] link[/COLOR][/COLOR] 

[http://paste.ubuntu.com/25002492/](http://paste.ubuntu.com/25002492/)

---

### Post by tofazzalshuvo on 2017-07-04
please help me.

---

### Post by jeremy31 on 2017-07-04
Post results for these actions
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

We could also try an older kernel in case you are affected by a kernel bug
```
sudo apt-get install linux-image-4.4.0-77-generic linux-image-extra-4.4.0-77-generic linux-headers-4.4.0-77-generic
```
When it is finished installing reboot and hold the shift key until the grub menu appears, then scroll down to Advanced options or previous linux versions, then scroll to the 4.4.0-77 kernel and boot into it then try the first commands I posted

---

### Post by tofazzalshuvo on 2017-07-05
nothing to showing for the command "sudo modprobe -r rtl8723be"  and it's disconnected.when I reboot it's connected.


nothing to showing for the command "sudo modprobe rtl8723be ant_sel=1"


showing for the command "iwlist scan | egrep -i 'ssid|quality'"


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


                    Quality=40/70  Signal level=-70 dBm  
                    ESSID:"Southern Cng Ltd."
                    Quality=70/70  Signal level=-12 dBm  
                    ESSID:"network"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"Md Alim "


nothing to showing for the command "sudo modprobe -r rtl8723be"


nothing to showing for the command "sudo modprobe rtl8723be ant_sel=2"


showing for the command "iwlist scan | egrep -i 'ssid|quality'"


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


                    Quality=42/70  Signal level=-68 dBm  
                    ESSID:"Southern Cng Ltd."
                    Quality=70/70  Signal level=-14 dBm  
                    ESSID:"network"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"Md Alim "

---

### Post by jeremy31 on 2017-07-05
Since the antenna setting makes no difference do
```
echo "options rtl8723be ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by tofazzalshuvo on 2017-07-05
Hi, It's not worked and this [COLOR=#000000][COLOR=#000000][COLOR=#000000]this is the [/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][COLOR=#000000][COLOR=#000000]new wireless-info.txt Pastebin[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][COLOR=#000000] link[/COLOR][/COLOR][/COLOR][COLOR=#000000] [/COLOR]
[http://paste.ubuntu.com/25026954/](http://paste.ubuntu.com/25026954/)

---

### Post by jeremy31 on 2017-07-05
Have you tried Ubuntu 16.04 to see if the results are different?  The last results show failure to init card.  It might be a hardware issue

---

### Post by tofazzalshuvo on 2017-07-05
Ok...I will boot [COLOR=#000000]Ubuntu 16.04 to see if the results are different and I will post if it's have wireless problem..
If you are know any different way please conform me.

Ubuntu family are very helpful.
[/COLOR][COLOR=#000000]Thanks..[/COLOR]

---

### Post by jeremy31 on 2017-07-06
Just try 16.04 from the ISO, I do not want you to install unless it works

---

### Post by theo1503 on 2017-07-06
Hi, I had the same problem.

Try this : [https://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/](https://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/) 

Another thread about the problem, if you want more information : [https://ubuntuforums.org/showthread.php?t=2304607](https://ubuntuforums.org/showthread.php?t=2304607)

---

