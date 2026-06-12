---
title: "AC7260 Card Not Recognized"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by kgeekworking on 2014-08-09
I have a new Asus laptop that came with an Intel model AC7260HMW wireless card.  It appears as though the PCI ids do not match any of those in the current driver. The LSHW command sees the card, however always reports it as UNCLAIMED. Thinking that it may be a matter of kernel + driver versions, I first started with Trusty 3.13 then tried Uptopic Alpha1 3.15, then Uptopic Alpha2 with kernel 3.16. 

What leads me to believe that the device code is just not listed is that LSPCI lists "Subsystem: Intel Corporation Device [8086:4c70]", but modifno iwlwifi does not list the subsystem device number.  It has many similar codes, but not this one.

Am I on the right track?  Is there any way to add a new alias for this ID so that the system will recognize it?

The results of the wireless script are below

```



	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Q502LA 3.16.0-6-generic x86_64,  Ubuntu Utopic Unicorn (development branch), utopic

CPU    : Intel(R) Core(TM) i5-4210U CPU @ 1.70GHz
Memory : 7868 MB
Uptime : 17:18:47 up 0 min,  3 users,  load average: 0.18, 0.06, 0.02


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev cb)
	Subsystem: Intel Corporation Device [8086:4c70]


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0457:108d Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 13d3:5656 IMC Networks 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: hci0: Bluetooth                no            no
1: asus-wlan: Wireless LAN        no            no
2: asus-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

asus_nb_wmi            16990  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          196012  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd  _hda_codec,snd_hda_intel,snd_hda_controller,snd_pc  m_dmaengine
wmi                    19193  1 asus_wmi
video                  20128  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
snd_pcm       (2): maximum_substreams=4 | preallocate_dma=1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o====  =======o=========o===========o==============o=====  ======
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o====  =======o=========o===========o==============o=====  ======
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         192.168.15.120
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.15.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WWanEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.15.1    0.0.0.0         UG    0      0        0 eth0
192.168.15.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.15.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.224/0.243/0.263/0.024 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.017/0.018/0.019/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[asus_nb_wmi]
filename:       /lib/modules/3.16.0-6-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     AE4F09ABD125394483A12C3
depends:        asus-wmi
parm:           wapf:WAPF value (uint)

[asus_wmi]
filename:       /lib/modules/3.16.0-6-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     B5FEEAA49A8BE4D7FB6ABFD
depends:        sparse-keymap,wmi,video

[snd_soc_rt5640]
filename:       /lib/modules/3.16.0-6-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
srcversion:     A1A2C72AFBB456093B0DCBD
depends:        snd-pcm,snd-soc-core,snd-soc-rl6231

[snd_soc_rl6231]
filename:       /lib/modules/3.16.0-6-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
srcversion:     A9A4828818D1BE4F6603399
depends:        

[snd_soc_core]
filename:       /lib/modules/3.16.0-6-generic/kernel/sound/soc/snd-soc-core.ko
srcversion:     5822C7720554611D1A46531
depends:        snd-pcm,snd-pcm-dmaengine,snd,snd-compress
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)

[snd_pcm]
filename:       /lib/modules/3.16.0-6-generic/kernel/sound/core/snd-pcm.ko
srcversion:     9D890D9058E0C29CAD74F14
depends:        snd,snd-timer
parm:           preallocate_dma:Preallocate DMA memory when the PCM devices are initialized. (int)
parm:           maximum_substreams:Maximum substreams with preallocated DMA memory. (int)

[wmi]
filename:       /lib/modules/3.16.0-6-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.16.0-6-generic/kernel/drivers/acpi/video.ko
srcversion:     1F0A8320EA3104D192AA1AE
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-6-generic.efi.signed root=UUID=03cd1f28-1966-4883-8403-d2a11e559853 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.039759] Initializing cgroup subsys net_cls
[    0.039770] Initializing cgroup subsys net_prio
[    0.879514] audit: initializing netlink subsys (disabled)
[    0.994208] wmi: Mapper loaded
[    1.002703] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.735317] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f0e)
[    3.057440] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.107726] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.235642] asus_wmi: ASUS WMI generic driver loaded
[    3.238689] asus_wmi: Initialization: 0x1
[    3.238889] asus_wmi: BIOS WMI version: 7.9
[    3.238953] asus_wmi: SFUN value: 0x4a2877
[    3.243220] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input20
[    3.296125] asus_wmi: Backlight controlled by ACPI video driver

	======== Done ========


```

---

### Post by chili555 on 2014-08-09
May I see:```
sudo modprobe iwlwifi
dmesg | grep iwl
dmesg | grep 03:00
```I love a mystery!

---

### Post by kgeekworking on 2014-08-11
Thank you very much for the reply. 

If I force iwlwifi to load dmesg just shows the copyright message (same as if you force load the module on a system without any intel cards installed). 

This is how I reached my conclusion that the card is likely an OEM version with a custom subsystem revision number that is not on the alias list for the driver.  If this conclusion is correct then I would have to either wait until upstream finds and adds the number or edit the source and manually compile the driver every time that there is a kernel update. 

Unfortunately I needed to use the laptop for work, so I ended up swapping the card with the Atheros card from my wife's laptop. She is running Windows, so the Intel card is OK in her system and the Atheros card just works in Ubuntu.

---

### Post by chili555 on 2014-08-11
I am glad you are all set by any method. I was actually looking forward to editing the source code! I suggest you file a bug and leave the link here so others may read and add to it. [https://bugs.launchpad.net/ubuntu/+source/linux](https://bugs.launchpad.net/ubuntu/+source/linux)

If any searchers wander by and see this, I am fairly certain that we could edit some .c code in the backports suite and get the device working. We just need a tester to confirm.

---

### Post by chili555 on 2014-08-31
Please see: [http://ubuntuforums.org/showthread.php?t=2242147&page=2](http://ubuntuforums.org/showthread.php?t=2242147&page=2) 

A so far working solution is posted there.

---

### Post by richwillal on 2014-12-28
For anyone looking for the solution to this issue, the updated driver is now incorporated into the latest kernel builds.  I've confirmed this on the latest Ubuntu 14.04 and Linux MInt with the kernel updated to 3.16.0-28-generic.

I hope this helps.

---

### Post by jeremy31 on 2014-12-29
> **richwillal said:**
> For anyone looking for the solution to this issue, the updated driver is now incorporated into the latest kernel builds.  I've confirmed this on the latest Ubuntu 14.04 and Linux MInt with the kernel updated to 3.16.0-28-generic.

I hope this helps.

With 14.04, the issue should be solved in kernel 3.13.0-43 for the rev cb 7260 card
```
 modinfo /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko | grep -i 4c70alias:          pci:v00008086d000008B1sv*sd00004C70bc*sc*i*

```
I haven't checked the latest 14.10 kernel

---

