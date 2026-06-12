---
title: "Configurin Network Interfaces (fail) - newb needs help :/"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by grandfso on 2005-07-01
Hello, I really like Ubuntu(or rather kubuntu), but i have problems with my network. Heres whats happening. After installation, evertything works fine, but then, when I am rebootin OS, i see such errors:
Deconfiguring Network Interfaces  [FAIL].
When kubuntu starts again, i see 
Configuring Network Interfaces  [FAIL].

I would not care about these errors, but when system is up and running, my network doesnt work at all.
I am running control center by typing command 'sudo kcontrol', in Network Settings, i see list of my all, three ethernet adapters(i am using only one of them, but after rebooting, each of these is disabled, when i am enabling eth0, it gots instantly disabled again, and again... I deleted /etc/network/interfaces and configured everything again in Network Settings in Control Center, but I still cant enable my ethernet adapter. It gets disabled all the time, sometimes i dont know why, after fourth or fifth deletion and reconfiguration it starts to work, but only until next reboot. Can any one help me? It is really annoying if i dont have connection to internet after each restart. Please,

Kind Regards,
grandfso


P.S. I am posting my /etc/network/interfaces file content, because now internet works, so maybe... I dont know, i am newbie
> iface lo inet loopback

iface eth0 inet dhcp

iface eth2 inet

iface eth1 inet


I read somewhere that posting following info, may be helpful for gurus, so... take a look:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:4F:1C:B6:56
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe1c:b656/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:604647 (590.4 KiB)  TX bytes:144334 (140.9 KiB)
          Interrupt:19 Base address:0xd800

eth2      Link encap:Ethernet  HWaddr 00:0E:A6:5E:70:6B
          inet6 addr: fe80::20e:a6ff:fe5e:706b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2430 (2.3 KiB)
          Interrupt:23 Base address:0xa800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
$ lsmod
Module                  Size  Used by
ipv6                  229504  6
binfmt_misc            11272  1
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
snd_usb_audio          60224  1
snd_usb_lib            11776  1 snd_usb_audio
via_rhine              19972  0
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  5 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  2 snd_usb_lib,snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  15 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
usbhid                 29376  0
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
8139cp                 19200  0
8139too                24320  0
mii                     4736  3 via_rhine,8139cp,8139too
pci_hotplug            30512  0
via_agp                 9216  1
agpgart                31784  1 via_agp
analog                 10784  0
gameport                4608  2 snd_via82xx,analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_cp437               5888  3
ntfs                   97136  3
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  7
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  296
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
```

---

### Post by spd106 on 2005-07-01
Hi, you are missing the following line in your interfaces file.
```
auto lo eth0 eth1 eth2
```

This should make them be started on boot.

Hope this helps

---

### Post by grandfso on 2005-07-01
[QUOTE=spd106]Hi, you are missing the following line in your interfaces file.
```
auto lo eth0 eth1 eth2
```

This should make them be started on boot.

Hope this helps[/QUOTE]
 OK, I have edited this file, and I am going to reboot kubuntu. I hope it will work fine, and I will be able to say thank you.

---

### Post by grandfso on 2005-07-01
OK. It works, my interfaces file looks like this:

iface lo inet loopback
auto lo eth0
iface eth2 inet dhcp

iface eth1 inet dhcp

iface eth0 inet dhcp

Thanks for feedback, i am greatful for your help

---

