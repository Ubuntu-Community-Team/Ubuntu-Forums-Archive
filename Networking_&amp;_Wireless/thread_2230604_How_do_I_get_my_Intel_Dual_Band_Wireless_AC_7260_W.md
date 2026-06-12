---
title: "How do I get my Intel Dual Band Wireless AC 7260 WIFI Card to Work with Linux?"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by ev-bacon on 2014-06-20
[COLOR=#000000][FONT=Arial]’m quite new to Linux, and am not sure how to go about getting this to work.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I’m not sure how to get my Toshiba Satellite E55-A5114’s WIFI Card to Work [COLOR=#4D4D4D][FONT=Open Sans](Computer info: [http://goo.gl/VknKja](http://goo.gl/VknKja)). [/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]While in Windows 8.1, I was able to figure out that I have an Intel Dual Band Wireless AC 7260 WIFI Card by clicking on This Computer—> Device Manager—> Network Adapters.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I did some searching with Google, and found these page from Intel’s Linux Drivers/Downloadss:[/FONT][/COLOR]

[LIST]
[*][http://goo.gl/AYHWRL](http://goo.gl/AYHWRL)
[*][http://goo.gl/7k4NNg](http://goo.gl/7k4NNg)
[*][http://goo.gl/vTXCKM](http://goo.gl/vTXCKM)
[/LIST]
[COLOR=#000000][FONT=Arial]So, using those pages as guidelines, can someone tell me exactly what I should type into the Terminal in order to get my WIFI work work?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm not certain which distro I'm going to use, I'm downloading a number of different ones to see which I like best. Some of them are Apt-based, others RMP-based and still others are Pacman-based; I don't think any of them are Yum-based, however I do believe that Yum is available in a number of different ones I'm going to try. If there are different Terminal commands to be used for each of those, please tell me how I could get it to work depending on which packaging-system they use.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If you're wondering, here are the distros I'm going to try:[/FONT][/COLOR]

[LIST]
[*]snowlinux-4-glacier-amd64.iso deepin_2013.1_en_amd64.iso
[*]kubuntu-14.04-desktop-amd64.iso linuxmint-16-kde-dvd-64bit.iso
[*]Mageia-4-x86_64-DVD.iso openSUSE-13.1-DVD-x86_64.iso
[*]archlinux-2014.06.01-dual.iso OpenMandrivaLx-2014.0.x86_64.iso
[*]antergos-2014.06.14-x86_64.iso
[*]debian-live-7.5.0-amd64-gnome-desktop.iso
[*]elementaryos-stable-amd64.20130810.iso
[/LIST]
[COLOR=#000000][FONT=Arial]
Like I said, I’m relatively new to Linux, especially when it comes to getting hardware to work. So whatever help you can provide me will be extremely appreciated![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks so much everyone![/FONT][/COLOR]

---

### Post by jeremy31 on 2014-06-20
What modules are loaded ```
lsmod
``` and is there anything in dmesg about it ```
dmesg | grep iwl
```

---

### Post by Thomas_Le on 2014-07-16
I am having a hell of a time getting a dual boot to work on a new sager 9377. I have the intel 7260 like in this thread. I found a script from another post and this is the output from it 



    > 


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


tvle83-VirtualBox 3.13.0-30-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i7-4810MQ CPU @ 2.80GHz
Memory : 7985 MB
Uptime : 23:33:59 up 20 min,  2 users,  load average: 0.24, 0.11, 0.11




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Kernel driver in use: e1000




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


iwlwifi               169932  0 
cfg80211              484040  1 iwlwifi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=======o========o==============o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=======o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | e1000  | connected    | yes     | 1000 Mb/s |              | <MAC ID removed>


    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------+--------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC ID removed>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


n3Rd4L1fe            : ssid=n3Rd4L1fe | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search [www.huaweimobilewifi.com]("http://www.huaweimobilewifi.com")




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1003ms
rtt min/avg/max/mdev = 3.498/48.420/93.342/44.922 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.019/0.024/0.029/0.005 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : en_US.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[iwlwifi]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~




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




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=65b5da51-08b7-4478-981a-a7502c285aab ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.540419] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.540699] audit: initializing netlink socket (disabled)
[    2.741427] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


    ======== Done ========



This is inside a VM so I can be connected to the internet and refer to posts and such while trying to troubleshoot the issue. 

I found the site with the firmware and i copied them to /lib/firmware. I don't know how to tell it to use a certain firmware file though.

Any help would be greatly appreciated.

I am using the latest Linux Ubuntu 14.04

---

### Post by jeremy31 on 2014-07-17
If you have a normal install of Ubuntu, try the lspci command there and see if it detects the 7620 then

---

### Post by Tosho on 2014-09-10
On my Thinkpad T440, running Ubuntu 14.04 x64, kernel 3.16.2

```

tosho@t440:~$ iwconfig wlan0 
wlan0     IEEE 802.11abgn  ESSID:"toti"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 10:FE:ED:E9:46:12   
          Bit Rate=11 Mb/s   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:443   Missed beacon:0

tosho@t440:~$ lsmod
Module                  Size  Used by
xt_addrtype            12713  2 
xt_conntrack           12760  1 
ipt_MASQUERADE         12880  1 
iptable_nat            13110  1 
nf_conntrack_ipv4      14857  2 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
nf_nat_ipv4            13316  1 iptable_nat
nf_nat                 26308  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack          105687  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
bridge                121755  0 
stp                    12976  1 bridge
llc                    14441  2 stp,bridge
dm_thin_pool           57518  1 
dm_persistent_data     62569  1 dm_thin_pool
dm_bio_prison          15526  1 dm_thin_pool
dm_bufio               28235  1 dm_persistent_data
libcrc32c              12644  1 dm_persistent_data
iptable_filter         12810  1 
ip_tables              27718  2 iptable_filter,iptable_nat
x_tables               34194  5 ip_tables,ipt_MASQUERADE,xt_conntrack,iptable_filter,xt_addrtype
ctr                    13193  2 
ccm                    17856  2 
snd_hda_codec_hdmi     48243  1 
snd_hda_codec_realtek    73695  1 
snd_hda_codec_generic    70087  1 snd_hda_codec_realtek
arc4                   12573  2 
intel_rapl             19196  0 
x86_pkg_temp_thermal    14312  0 
intel_powerclamp       19099  0 
coretemp               13638  0 
kvm                   464279  0 
crct10dif_pclmul       14268  0 
crc32_pclmul           13180  0 
ghash_clmulni_intel    13230  0 
rfcomm                 75114  8 
aesni_intel           152648  4 
bnep                   19884  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
snd_hda_intel          30683  5 
glue_helper            14095  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_hda_controller     35518  1 snd_hda_intel
cryptd                 20531  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec         144889  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
iwlmvm                225277  0 
snd_hwdep              17709  1 snd_hda_codec
snd_pcm               105052  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
mac80211              687021  1 iwlmvm
joydev                 17587  0 
i915                  945853  7 
serio_raw              13483  0 
iwlwifi               190534  1 iwlmvm
uvcvideo               86628  0 
rtsx_pci_ms            18337  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
binfmt_misc            17508  1 
thinkpad_acpi          82198  1 
btusb                  32605  0 
memstick               16968  1 rtsx_pci_ms
nvram                  14462  1 thinkpad_acpi
bluetooth             467228  22 bnep,btusb,rfcomm
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              521225  3 iwlwifi,mac80211,iwlmvm
videobuf2_core         59635  1 uvcvideo
snd_rawmidi            31197  1 snd_seq_midi
v4l2_common            15715  1 videobuf2_core
snd_seq                63540  2 snd_seq_midi_event,snd_seq_midi
videodev              154834  3 uvcvideo,v4l2_common,videobuf2_core
lpc_ich                21176  0 
6lowpan_iphc           18968  1 bluetooth
media                  22008  2 uvcvideo,videodev
drm_kms_helper         62042  1 i915
wmi                    19379  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30118  2 snd_pcm,snd_seq
drm                   316819  6 i915,drm_kms_helper
snd                    84025  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
intel_smartconnect     12637  0 
video                  20521  1 i915
mac_hid                13275  0 
i2c_algo_bit           13564  1 i915
soundcore              15091  2 snd,snd_hda_codec
mei_me                 19565  0 
mei                    88632  1 mei_me
parport_pc             32906  0 
ppdev                  17711  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23482  0 
ahci                   30167  3 
psmouse               113097  0 
e1000e                229859  0 
libahci                32533  1 ahci
rtsx_pci               46393  2 rtsx_pci_ms,rtsx_pci_sdmmc
ptp                    19534  1 e1000e
pps_core               19381  1 ptp

tosho@t440:~$ dmesg | grep iwl
[    8.547827] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X
[    8.554079] iwlwifi 0000:03:00.0: loaded firmware version 23.214.9.0 op_mode iwlmvm
[    8.591599] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.592017] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    8.592460] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    8.805029] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.290520] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    9.290961] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S

tosho@t440:~$ lspci | grep 7260
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 83)


```

I had issues with my wi-fi: 
1. It had very low speed over Wi-Fi - around 1mbp/s  - download around 80kb/s, and I fix this when I turn off the power managment (found the solution here).

2. it's still slow  - now speedtest show me transfer rate for download around 20-30mbp/s and upload around 50-60mbp/s, where my ISP is providing 80mbp/s for download, and I'm with a 300Mbp/s router.  When I was with the Win7 (that comes with the laptop) the speed was normal - around 70-80mbp/s. 
So is there anything else to tweak, config. Actually I don't know if the dualband is in use, how to check that.

---

### Post by slickymaster on 2014-09-10
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by jeremy31 on 2014-09-10
You could try ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
``` and reboot and see if the speed is better

---

