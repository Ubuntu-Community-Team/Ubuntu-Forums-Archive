---
title: "WiFi hard blocked on linux but works on Windows"
date: 2021-02-08
forum: Networking &amp; Wireless
---

### Post by akash-karnatak on 2021-02-08
I have been using Ubuntu and Windows dual boot for over an year now on  my HP laptop with Ralink RT3290 wireless card. My wifi worked out of the  box on both Windows and Ubuntu. A few days back I decided to update my  BIOS from F.18 to F.45 version. After this update my wifi was hard  blocked on Ubuntu, although it still worked on Windows. It was even hard  blocked on other linux live usbs.

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

 I have tried almost every possible solution that have been posted on the internet. Things that I have tried:-

Toggling physical wifi switch.

sudo rfkill unblock all

Disabling fast boot on windows.

Turning on/off wifi on windows and then trying it on linux.

Disabling `turn off wifi to save power` in windows.

Checking `sudo dmesg` for any errors related to the wifi and wifi driver `rt2800pci`

All these things on Ubuntu 16.04, 18.04, 20.4 and Arch linux live usb.

Resetting the BIOS. Also my BIOS does not have any option to enable/disable wifi.

Updating the kernel to 5.9.0

Black listing hp_wireless and toggling physical wifi switch, black  listing hp_wmi and then toggling physical wifi switch. And all possible  combination of black listing the above two modules.

After power off, removing battery, power cord and then holding power  button for 1 min. Then putting back the battery, power cord and trying  wifi on linux.

Pray to the lord to do a miracle.

But nothing worked. What should I do now?

Some useful information,

```

$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 34:64:a9:7c:f9:c3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff
  *-network DISABLED
       description: Wireless interface
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlp10s0f0
       version: 00
       serial: 38:b1:db:0e:c2:49
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci  driverversion=4.18.0-15-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:b5510000-b551ffff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enp0s20u1
       serial: e6:10:d3:c4:ce:c1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device link=yes multicast=yes

$ ifconfig
enp0s20u1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 2402:3a80:915:c061:bd59:fca6:7c0e:f4ba  prefixlen 64  scopeid 0x0<global>
        inet6 2402:3a80:915:c061:847b:1ace:7982:c38b  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::8a40:3adf:c7b3:4023  prefixlen 64  scopeid 0x20<link>
        ether e6:10:d3:c4:ce:c1  txqueuelen 1000  (Ethernet)
        RX packets 69289  bytes 55005112 (55.0 MB)
        RX errors 30  dropped 0  overruns 0  frame 30
        TX packets 58525  bytes 11380820 (11.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp8s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 34:64:a9:7c:f9:c3  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 7850  bytes 934318 (934.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7850  bytes 934318 (934.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

$ iwconfig
lo        no wireless extensions.

wlp10s0f0  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp0s20u1  no wireless extensions.

enp8s0    no wireless extensions.

$ sudo uname -a
Linux ubuntu 4.18.0-15-generic #16~18.04.1-Ubuntu SMP Thu Feb 7 14:06:04 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

$ sudo dmesg

https://paste.ubuntu.com/p/tSwhQ2XW2G/

```

I am speculating that rt2800pci is not compatible with my new BIOS  version and I need a different driver. I tried building rt3290sta driver  but coundn't do it.

Help :'(

---

### Post by praseodym on 2021-02-08
Please show

```
lsmod
```

---

### Post by akash-karnatak on 2021-02-08
Output of `lsmod`

```

$ lsmod
Module                  Size  Used by
bnep                   20480  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm                   626688  0
irqbypass              16384  1 kvm
arc4                   16384  2
crct10dif_pclmul       16384  0
rt2800pci              16384  0
crc32_pclmul           16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
ghash_clmulni_intel    16384  0
snd_hda_codec_hdmi     49152  1
pcbc                   16384  0
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
aesni_intel           200704  0
rt2x00lib              53248  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
mac80211              802816  3 rt2x00pci,rt2x00lib,rt2800lib
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
snd_hda_intel          40960  4
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
uvcvideo               94208  0
intel_cstate           20480  0
intel_rapl_perf        16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
videobuf2_common       40960  2 videobuf2_v4l2,uvcvideo
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
cfg80211              667648  2 rt2x00lib,mac80211
snd_hwdep              20480  1 snd_hda_codec
joydev                 24576  0
input_leds             16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
media                  40960  2 videodev,uvcvideo
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
serio_raw              16384  0
rtsx_pci_ms            20480  0
snd_seq_midi           16384  0
wmi_bmof               16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
hci_uart              110592  0
lpc_ich                24576  0
memstick               16384  1 rtsx_pci_ms
eeprom_93cx6           16384  1 rt2800pci
btqca                  16384  1 hci_uart
btbcm                  16384  1 hci_uart
snd_rawmidi            32768  1 snd_seq_midi
btintel                20480  1 hci_uart
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
bluetooth             552960  11 btqca,btintel,hci_uart,btbcm,bnep
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
mei                    98304  1 mei_me
soundcore              16384  1 snd
soc_button_array       16384  0
ecdh_generic           24576  1 bluetooth
hp_wireless            16384  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
overlay                94208  1
nls_iso8859_1          16384  1
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
uas                    24576  0
hid_generic            16384  0
usb_storage            69632  2 uas
usbhid                 49152  0
nouveau              1851392  1
i915                 1740800  10
mxm_wmi                16384  1 nouveau
ttm                   110592  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
drm_kms_helper        172032  2 i915,nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   40960  0
fb_sys_fops            16384  1 drm_kms_helper
rtsx_pci_sdmmc         24576  0
psmouse               151552  0
libahci                32768  1 ahci
drm                   458752  8 drm_kms_helper,i915,ttm,nouveau
r8169                  86016  0
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
mii                    16384  1 r8169
video                  45056  2 i915,nouveau
i2c_hid                20480  0
hid                   122880  3 i2c_hid,usbhid,hid_generic
wmi                    24576  4 hp_wmi,wmi_bmof,mxm_wmi,nouveau

```

---

### Post by praseodym on 2021-02-08
Ok, try
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp_wmi.conf
```
Reboot and check
```

rfkill list
```
If its "Soft Blocked", then run
```

sudo rfkill unblock all
```
Sometimes "FastBoot" in Windows prevents wifi from correctly being deactivated.

---

### Post by akash-karnatak on 2021-02-09
Didn't work, it is still hard blocked.

```

[FONT=monospace][COLOR=#000000]0: phy0: Wireless LAN[/COLOR]
        Soft blocked: no
        Hard blocked: yes
[/FONT]
```

---

### Post by praseodym on 2021-02-09
So, lets try to unload that module
```

sudo rmmod hp-wmi
sudo rfkill unblock all
```

---

### Post by akash-karnatak on 2021-02-09
No effect. Still hard blocked :(

```

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

---

### Post by praseodym on 2021-02-09
What about the BIOS downgrade? Do you really need the latest version?

---

### Post by SeijiSensei on 2021-02-09
I had this problem and discovered I had accidentally disabled my wifi card by a key combination or switch. Just a thought.

---

### Post by akash-karnatak on 2021-02-09
I tried downgrading BIOS but my laptop does not allow me to install lower versions( like F.18 and F.43). Install option is grayed out when using the installer. I even created a BIOS recovery USB using the older versions but my laptop ignores the USB when I follow the procedure of flashing BIOS. But when I create BIOS recovery USB with the current version BIOS my laptop recognizes it. Seems like I can only go up the ladder.

---

### Post by akash-karnatak on 2021-02-09
F12 is my wifi key, I have already tried toggling it several times. Toggling it in BIOS, in Windows, in Ubuntu. Even with different modifier keys.

---

### Post by akash-karnatak on 2021-02-10
Yo guys, I have found this 

```

$ cat [FONT=monospace][COLOR=#000000]/sys/module/rt2800pci/drivers/pci\:rt2800pci/0000\:[/COLOR]0a\:00.0/ieee80211/phy0/rfkill0/hard
1[/FONT]

```

I guess changing the 1 to 0 will remove my hard block. But I can't edit this file, even with the root privileges. Why?

---

### Post by jeremy31 on 2021-02-10
That file is read only as it is read from BIOS, only the BIOS can change it.  I have an idea that may or may not work and I doubt it can hurt anything, we can edit grub to pass some info to BIOS at boot
```
gedit admin:///etc/default/grub
```
Go to the line with ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add acpi_osi='Windows 2017' inside the quotes so that it is 
 ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='Windows 2017'"
```
Then do ```
sudo update-grub
```
Reboot

This should make the BIOS think that a Windows 10 version is being loaded rather than the default in Ubuntu of not responding to the BIOS acpi_osi inquiry

---

### Post by akash-karnatak on 2021-02-11
It didn;t work :(. But when I looked for other kernel parameters then I found this,

```

        rfkill.default_state=
		0	"airplane mode".  All wifi, bluetooth, wimax, gps, fm,
			etc. communication is blocked by default.
		1	Unblocked.

	rfkill.master_switch_mode=
		0	The "airplane mode" button does nothing.
		1	The "airplane mode" button toggles between everything
			blocked and the previous configuration.
		2	The "airplane mode" button toggles between everything
			blocked and everything unblocked.

```

which looked promising. I tried them with a bunch of different combinations, like

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rfkill.default_state=1"

```

but either it was still hard blocked, or my wifi module(rt2800pci) didn't load during boot. Even when I manually loaded rt2800pci it didn't detect any wireless interface(`rfkill list` was empty).

---

### Post by jeremy31 on 2021-02-11
I have found a few things but we need to see if it works in a now unsupported Ubuntu release, the ISO can be found at [https://old-releases.ubuntu.com/releases/14.04.1/ubuntu-14.04.1-desktop-amd64.iso](https://old-releases.ubuntu.com/releases/14.04.1/ubuntu-14.04.1-desktop-amd64.iso)
Supposedly there was a change in 2015 that caused these problems

---

### Post by akash-karnatak on 2021-02-12
I have downloaded the ISO and flashed it to a USB.

---

### Post by praseodym on 2021-02-14
You could try this one, that worked up to kernel 4.4-143

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/06/23/5641297-RT3290_u16_v3.tar.gz
tar xvf 5641297-RT3290_u16_v3.tar.gz
cd RT3290_u16
tar xvf src.tar.gz
./compile.sh
sudo ./install.sh
sudo cp firmware/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf  
```
Worked without error?

---

### Post by jeremy31 on 2021-02-14
> **akash-karnatak said:**
> I have downloaded the ISO and flashed it to a USB.

Does it work with no hard block?

---

### Post by akash-karnatak on 2021-02-14
Nope, it's hard blocked even in Ubuntu 14. Also my WiFi works out of the box on OpenBSD 6.8. I guess theirs some problem with rt2800pci driver.

---

### Post by akash-karnatak on 2021-02-15
Ok I tried that with linux kernel 4.1 and it did compile. But I cannot access GUI on that kernel and `iwlist eno1 scan` does not yield any scan results.

---

### Post by chili555 on 2021-02-15
> `iwlist eno1 scan` does not yield any scan results.eno1 is ethernet. Your wireless is likely wlp10s0f0 or similar.

---

### Post by akash-karnatak on 2021-02-15
Usually ethernet begins with the letter "e", but this time even wireless interface has it,

```

$ iwconfig
enxbe85d1a50781  no wireless extensions.

lo        no wireless extensions.

enp8s0    no wireless extensions.

eno1      Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by praseodym on 2021-02-15
Maybe "pin 20" is the solution

[https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

---

### Post by jeremy31 on 2021-02-16
> **praseodym said:**
> Maybe "pin 20" is the solution

[https://ubuntuforums.org/showthread.php?t=2150597](https://ubuntuforums.org/showthread.php?t=2150597)

That should work, there is a video on youtube [https://www.youtube.com/watch?v=yzAKcmlaH1M](https://www.youtube.com/watch?v=yzAKcmlaH1M)

---

### Post by akash-karnatak on 2021-02-16
Thanks a lot guys, my WiFi is finally working. After taping pin 20, wifi is no longer hard blocked. @jeremy31 thank you for that video, I was really confused how the pins were numbered. And thanks to everyone for helping me out. I sure learned a lot while fixing my WiFi.

[IMG]https://i.imgur.com/AQBwn94.png[/IMG]

---

