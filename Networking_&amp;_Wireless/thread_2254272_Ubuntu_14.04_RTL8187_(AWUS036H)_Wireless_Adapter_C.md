---
title: "Ubuntu 14.04 RTL8187 (AWUS036H) Wireless Adapter Connection Issues"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by rbuanno on 2014-11-26
The adapter of course works sort of out of the box.
But I have noticed it drops connection randomly and refuses to reconnect.
Also It powers down my adapter and won't turn back on until manually unplugged and again plugged in on.
The power downs happen rather frequently and its a issue for me.
The speed of the adapter seems much slower compared to its performance in Windows so I know its capable of more.
Also I notice this same adapter does not have these issues in Windows, no power downs and no connection drops that i have noticed.

How can I install the newest rtl8187 driver? I guess thats what I should try next correct?

I have used these settings and they semi-sort of help with performance,

modprobe rtl8187
iwconfig wlan0 rate 5M auto
iwconfig wlan0 rts 512
iwconfig wlan0 frag 512
iwconfig wlan0 retry long 21
iwconfig wlan0 retry short 21

This semi-fix however is not up to my liking and I'm looking for more performance,
like I see with this adapter in windows.

Look forward to hearing some recommendations.

---

### Post by Jack Harper on 2014-11-26
Can you post results of:

lsusb

lsmod

I also found this concerning drivers [http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter](http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter)

---

### Post by rbuanno on 2014-12-14
Sorry for such a late response I have just been extremely busy.
Jack if you can help me that would be super awesome!

```


root@sanctuary:/etc# lsusb
Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 005: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

root@sanctuary:/etc# lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  8 
arc4                   12608  2 
bnep                   19624  2 
rtl8187                64909  0 
mac80211              630653  1 rtl8187
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
cfg80211              484040  2 mac80211,rtl8187
snd_usb_audio         153993  1 
eeprom_93cx6           13344  1 rtl8187
snd_usbmidi_lib        29215  1 snd_usb_audio
joydev                 17381  0 
nouveau              1097199  4 
i915                  784207  1 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
ttm                    85150  1 nouveau
drm_kms_helper         55071  2 i915,nouveau
intel_rapl             18773  0 
mxm_wmi                13021  1 nouveau
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec_hdmi     46368  2 
drm                   303102  8 ttm,i915,drm_kms_helper,nouveau
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
i2c_algo_bit           13413  2 i915,nouveau
btusb                  32412  0 
kvm_intel             143187  0 
kvm                   455835  1 kvm_intel
bluetooth             391136  22 bnep,btusb,rfcomm
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm               102099  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
shpchp                 37032  0 
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mei_me                 18627  0 
mac_hid                13205  0 
snd_timer              29482  2 snd_pcm,snd_seq
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
mei                    82276  1 mei_me
aesni_intel            55624  2 
snd                    69322  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
soundcore              12680  1 snd
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
video                  19476  3 i915,nouveau,asus_wmi
glue_helper            13990  1 aesni_intel
serio_raw              13462  0 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
binfmt_misc            17468  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106714  0 
firewire_ohci          40409  0 
r8169                  67581  0 
e1000e                254433  0 
ahci                   25819  4 
firewire_core          68769  1 firewire_ohci
mii                    13934  1 r8169
libahci                32716  1 ahci
crc_itu_t              12707  1 firewire_core
ptp                    18933  1 e1000e
pps_core               19382  1 ptp

root@sanctuary:/home/ronald# lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: c8:60:00:00:2f:99
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.13-6 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:70 memory:fbe00000-fbe1ffff memory:fbe28000-fbe28fff ioport:f080(size=32)
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:00:29:15
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:71 ioport:a000(size=256) memory:da104000-da104fff memory:da100000-da103fff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@3:2
       logical name: wlan0
       serial: 00:c0:ca:7b:cd:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-43-generic firmware=N/A ip=192.168.1.139 link=yes multicast=yes wireless=IEEE 802.11bg

root@sanctuary:/home/ronald# nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        C8:60:00:00:29:15


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [Pretty Fly for a Wifi 2.4GHz] --------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           yes
  HW Address:        00:C0:CA:7B:CD:C9


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    6C7J5:           Infra, F8:E4:FB:25:A7:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    38:              Infra, 5C:57:1A:C1:24:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA2
    J9JH8:           Infra, 18:1B:EB:45:C6:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2
    JKN94:           Infra, 18:1B:EB:18:6D:6B, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA2
    JV3B4:           Infra, 18:1B:EB:18:95:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    SJW29:           Infra, 18:1B:EB:4B:DF:87, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    linksys:         Infra, 00:22:6B:56:C0:DC, Freq 2412 MHz, Rate 54 Mb/s, Strength 69
    *Pretty Fly for a Wifi 2.4GHz: Infra, B4:75:0E:AF:A0:C4, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    KXMF3:           Infra, 00:7F:28:0F:1D:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA2
    KQIF0:           Infra, 00:26:62:0B:0C:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WEP
    Vanessa:         Infra, AC:B3:13:72:57:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2


  IPv4 Settings:
    Address:         192.168.1.139
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        C8:60:00:00:2F:99


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


```


Let me know what other information you may need. I noticed that in connection information there is no driver listed? Maybe this is part of the issue?

Thanks Jack.

---

### Post by rbuanno on 2014-12-15
Also if anyone can recommend a really good adapter for ubuntu 14.04 please do, If I cannot get this resolved I will purchase a new adapter. This Alfa adapter issue is KILLING me.

--------------EDIT--------------------

Upon reading about rtl8187 : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

I am now aggravated and contemplating buying a new adapter. That information is dated however so I'm hoping for someone to respond that they have a fix or I should purchase new adapters.

For anyone thinking about buying an ALFA adapter for there Linux compatibility DON'T.
I mean sure it kinda works, but so far none of the fixes on the internet for performance have worked. It's a good adapter for windows and that's it. I'll be posting reviews on newegg about its poor performance to deter linux users from this.
Just because this adapter has good range doesn't make up for its lack of functionality and performance. 

I don't consider myself a linux all-star, but I can follow directions and so far there are no fixes to make this work at speeds advertised.

---

### Post by Jack Harper on 2014-12-15
[http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter](http://askubuntu.com/questions/178009/how-do-i-install-drivers-for-the-alfa-awus036h-usb-wireless-adapter)

Have you tried this solution?

Concerning USB adapters that have good Linux support check these links:

[http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

[http://arstechnica.com/civis/viewtopic.php?t=1237279](http://arstechnica.com/civis/viewtopic.php?t=1237279)

---

### Post by rbuanno on 2014-12-15
Thanks for replying again Jack, Your the man.

However, When I go to make && make install these I get these errors, hopefully you can help me decipher whats going on :

```

root@sanctuary:/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012# make
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-43-generic'
  CC [M]  /home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:153:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_probe&#8217;
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:155:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_disconnect&#8217;
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf);
                       ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:168:12: error: &#8216;rtl8187_usb_probe&#8217; undeclared here (not in a function)
  .probe  = rtl8187_usb_probe,           
            ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:169:16: error: &#8216;rtl8187_usb_disconnect&#8217; undeclared here (not in a function)
  .disconnect = rtl8187_usb_disconnect,   
                ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:2: error: implicit declaration of function &#8216;create_proc_entry&#8217; [-Werror=implicit-function-declaration]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
  ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:14: warning: assignment makes pointer from integer without a cast [enabled by default]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
              ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_init_one&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:461:16: warning: assignment makes pointer from integer without a cast [enabled by default]
  priv->dir_dev = create_proc_entry(dev->name, 
                ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:2: error: implicit declaration of function &#8216;create_proc_read_entry&#8217; [-Werror=implicit-function-declaration]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
  ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:489:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-tx", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:518:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("registers", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1382:12: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  u8 seg = ((u32)txbuf % 4);
            ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_initendpoints&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1588:14: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
   seg_size = (u32)ptrcontext->transfer_buffer % 4;
              ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: At top level:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3762:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_probe&#8217;
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3862:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_disconnect&#8217;
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf)
                       ^
cc1: some warnings being treated as errors
make[2]: *** [/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-43-generic'
make: *** [all] Error 2


root@sanctuary:/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012# make install
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko: kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/misc/eeprom/eeprom_93cx6.ko
make[1]: Entering directory `/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187'
make -C /lib/modules/3.13.0-43-generic/build M=/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-43-generic'
  CC [M]  /home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:153:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_probe&#8217;
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:155:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_disconnect&#8217;
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf);
                       ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:168:12: error: &#8216;rtl8187_usb_probe&#8217; undeclared here (not in a function)
  .probe  = rtl8187_usb_probe,           
            ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:169:16: error: &#8216;rtl8187_usb_disconnect&#8217; undeclared here (not in a function)
  .disconnect = rtl8187_usb_disconnect,   
                ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:2: error: implicit declaration of function &#8216;create_proc_entry&#8217; [-Werror=implicit-function-declaration]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
  ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:427:14: warning: assignment makes pointer from integer without a cast [enabled by default]
  rtl8180_proc=create_proc_entry(RTL8187_MODULE_NAME, S_IFDIR, init_net.proc_net);
              ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_init_one&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:461:16: warning: assignment makes pointer from integer without a cast [enabled by default]
  priv->dir_dev = create_proc_entry(dev->name, 
                ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:2: error: implicit declaration of function &#8216;create_proc_read_entry&#8217; [-Werror=implicit-function-declaration]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
  ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:479:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-rx", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:489:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("stats-tx", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:518:4: warning: assignment makes pointer from integer without a cast [enabled by default]
  e = create_proc_read_entry("registers", S_IFREG | S_IRUGO,
    ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1382:12: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
  u8 seg = ((u32)txbuf % 4);
            ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_initendpoints&#8217;:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:1588:14: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
   seg_size = (u32)ptrcontext->transfer_buffer % 4;
              ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c: At top level:
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3762:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_probe&#8217;
 static int __devinit rtl8187_usb_probe(struct usb_interface *intf,
                      ^
/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.c:3862:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8187_usb_disconnect&#8217;
 static void __devexit rtl8187_usb_disconnect(struct usb_interface *intf)
                       ^
cc1: some warnings being treated as errors
make[3]: *** [/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187/r8187_core.o] Error 1
make[2]: *** [_module_/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-43-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ronald/Downloads/rtl8187L_linux_1041.0209.2012/rtl8187'
make: *** [install] Error 2




```

Can you shine some light on what might be going on? 
I'm going to browse through the other links you sent me now about the adapters.

Again, thanks and your the man!

Ronald

---

### Post by Jack Harper on 2014-12-15
Did you install build-essential and kernel headers as instructed in that link?

---

### Post by rbuanno on 2014-12-15
Yes, I follow instructions pretty good ;P

Proof lol :

```

root@sanctuary:/home/ronald# apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.13.0-43-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```

---

### Post by rbuanno on 2014-12-16
My new alternative for the lack of support on this friggin adapter is to use my old WRT54GL WiFi Router with DD-WRT in client bridge mode as my WiFi adapter.... BOO YA.

It's truely a shame that this adapter won't work with the newest LTS. I hope this is fixed in a timely manner. 

I'll be watching this thread hoping for more help, as I now own 2 of these ALFA adapters D:

Le Sigh. Thank god for DD-WRT.

---

### Post by dougiestyletone on 2015-01-08
I yearn to plug in a modern USB 3.0 Wireless Adapter that allows me to take full advantage of the extreme speed and throughput of my Netgear Nighthawk Router.  Alas, nothing new works very well, so my standby is my trusty single-band TP-Link TL-WN822N.  Works great on Ubuntu 14.04 LTS.  Hopefully with time, I will be able to enjoy modern technology.

---

### Post by rbuanno on 2015-01-09
I hear you on that one. As I stated I'm using an old WRT54GL WiFi Router with DD-WRT on it :D
Its a pretty solid setup. I use it in client-bridge mode so it is basically a super-adapter with 4 more slots to connect stuff!
I think I'm just gonna stay away from WiFi Dongles in generally unless I have to pen. test or use my laptop for emails / shh :P

---

### Post by hutchic on 2015-10-16
> **rbuanno said:**
> Thanks for replying again Jack, Your the man.

However, When I go to make && make install these I get these errors, hopefully you can help me decipher whats going on :



I'm having similar problems to you and although I don't have a solution I think the error you got trying to compile the driver is a kernel that's newer than what the driver source is made for

---

### Post by seraphim1976 on 2016-07-11
sudo apt-get install 8187* 

it worked for me after connecting and disconnecting every 5 minutes and now it's been ok for 2 hours

---

### Post by wildmanne39 on 2016-07-11
Can you please tell us what ubuntu version you are using and everything you did if you installed that driver your self then it would take a lot more then just that command to get it installed.

However I believe the newer ubuntu's have that driver installed bu default. Please more information.
Thanks

---

