---
title: "Cannot connect to mobile broadband through Huawei E303 modem"
date: 2015-12-25
forum: Networking &amp; Wireless
---

### Post by Fibonacci on 2015-12-25
I bought what is apparently a Huawei E303 with the brand of a local mobile company, and am trying to connect to the network through it in Ubuntu. It was recognised as a 12d1:15d4 instead of a modem, and so I found I had to use usb_modeswitch.
Switching modes was painful without an internet connection to find the exact string, but I finally managed to do it succesfully and now I've created the file /etc/usb_modeswitch.d/12d1:15d4 with the following content:
```
TargetVendor=  0x12d1
TargetProduct= 0x15d5
InquireDevice= 0

MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```

Even though the modem is now properly recognised and I've created an appropriate connection (for my operator) in plasma-nm, I still can't connect to he net. First I'm prompted by KDE for a password, and none of my account password, “movistar” (the default for that connection) or the SIM PIN seem to work. Then I get one notification stating that “IP configuration was unavailable” and many more with “Connection 'Movistar' deactivated.” Of course I never manage to actually get an internet connection.

The same modem is working fine under Windows, and in fact, I'm using it to post this.

What am I doing wrong?

---

### Post by praseodym on 2015-12-26
Please show the outputs of

```
usb-devices
lsmod
mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
```

---

### Post by Fibonacci on 2015-12-26
> **praseodym said:**
> Please show the outputs of

```
usb-devices
lsmod
mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
```

```
$ usb-devices

...

T:  Bus=04 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=15d5 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=02 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=02 Prot=16 Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=03 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=02 Prot=02 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

...

$ lsmod
Module                  Size  Used by
ppp_deflate            16384  0
bsd_comp               16384  0
twofish_generic        20480  0
twofish_avx_x86_64     49152  2
twofish_x86_64_3way    28672  1 twofish_avx_x86_64
twofish_x86_64         16384  2 twofish_avx_x86_64,twofish_x86_64_3way
twofish_common         24576  4 twofish_generic,twofish_avx_x86_64,twofish_x86_64_3way,twofish_x86_64
xts                    16384  1 twofish_x86_64_3way
ppp_async              20480  0
crc_ccitt              16384  1 ppp_async
huawei_cdc_ncm         16384  0
cdc_wdm                20480  1 huawei_cdc_ncm
cdc_ncm                32768  1 huawei_cdc_ncm
usbnet                 40960  2 huawei_cdc_ncm,cdc_ncm
mii                    16384  1 usbnet
option                 49152  2
usb_wwan               20480  1 option
usbserial              53248  6 option,usb_wwan
snd_hrtimer            16384  1
binfmt_misc            20480  1
nls_iso8859_1          16384  1
drbg                   32768  1
ansi_cprng             16384  0
dm_crypt               28672  2
joydev                 20480  1
xpad                   24576  0
ff_memless             16384  1 xpad
nvidia              10567680  115
input_leds             16384  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
snd_usb_audio         176128  1
media                  24576  2 uvcvideo,videodev
snd_usbmidi_lib        32768  1 snd_usb_audio
gpio_ich               16384  0
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          36864  5
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_core
aesni_intel           167936  9925
aes_x86_64             20480  1 aesni_intel
lrw                    16384  3 aesni_intel,twofish_avx_x86_64,twofish_x86_64_3way
gf128mul               16384  2 lrw,xts
snd_seq_midi           16384  0
glue_helper            16384  3 aesni_intel,twofish_avx_x86_64,twofish_x86_64_3way
snd_seq_midi_event     16384  1 snd_seq_midi
ablk_helper            16384  2 aesni_intel,twofish_avx_x86_64
cryptd                 20480  4965 aesni_intel,ablk_helper
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                69632  3 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  3 snd_hrtimer,snd_pcm,snd_seq
snd                    81920  24 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
lpc_ich                24576  0
drm                   356352  3 nvidia
soundcore              16384  1 snd
mei_me                 32768  0
mei                    98304  1 mei_me
shpchp                 36864  0
nuvoton_cir            20480  0
rc_core                28672  1 nuvoton_cir
8250_fintek            16384  0
mac_hid                16384  0
w83627ehf              45056  0
hwmon_vid              16384  1 w83627ehf
coretemp               16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
ses                    20480  0
enclosure              16384  1 ses
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  2 uas
psmouse               126976  0
e1000e                237568  0
ahci                   36864  5
libahci                32768  1 ahci
ptp                    20480  1 e1000e
pps_core               20480  1 ptp

$ mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/0'
```

---

### Post by praseodym on 2015-12-27
Repeat the last command with "1" or "2" instead of "0"

---

### Post by Fibonacci on 2015-12-30
> **praseodym said:**
> Repeat the last command with "1" or "2" instead of "0"

```
$ mmcli -m 1 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/1'
$ mmcli -m 2 | grep -Ev "imei|equipment|Numbers"
error: couldn't find modem at '/org/freedesktop/ModemManager1/Modem/2'

```

---

### Post by praseodym on 2015-12-30
Have a look at the UMTS checklist here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by Fibonacci on 2015-12-30
> **praseodym]Disable PIN code request (in the mobile phone / with WIN-software or umtsmon), this is often helpful[/QUOTE]
Done.
[QUOTE=praseodym]Stick Sim-/Netlock free (after a change of provider)[/QUOTE]
How?
[QUOTE=praseodym]enter PUK (This is the 8-digit code to unlock the SIM card if the PIN is entered incorrectly multiple times)[/QUOTE]
Where?
[QUOTE=praseodym]SIM card is inserted correctly (or dirty)? (For those who groan at this point. It can easily happen, happens, and no one needs to be embarrassed!)
sufficient Funds are available (may be consumed quickly by using the wrong APN)[/QUOTE]
Not applicable as it works fine under Windows.
[QUOTE=praseodym]Check whether the correct APN is used
Always enter at number * 99 # and never the mobile phone number (I dont know if 99 is country specific )[/QUOTE]
Done.
[QUOTE=praseodym]Check: &#8594 said:**
> 
Couldn't find any "modem" entries.
[QUOTE=praseodym]disable Parallel WLAN / LAN connection
Done.
[QUOTE=praseodym]Use alternative dialer programs (from version 10.10 not really necessary anymore.) Umtsmon / Vodafone Mobile Connect (BMC as successor) / ixconn / sakis3g / wvdial / Ubuntu Kubuntu-NWM[/QUOTE]
Not applicable as I'm using 15.10.
[QUOTE=praseodym]If modem is not detected or is in disk mode: install "USB-modeswitch"
Check whether the package modemmanager is installed (e.g. Lubuntu lacks this package in its default installation)[/QUOTE]
Done.
[QUOTE=praseodym]In some models which are set in the disk mode it is automatically switched to modem mode when drive / virtual CD is removed (right click, remove the drive safely).[/QUOTE]
Not my case as I already explained.
[QUOTE=praseodym]All (kernel) updates installed?
Does Stick / modem work in Windows?[/QUOTE]
Yes.
[QUOTE=praseodym]Browser in offline mode?[/QUOTE]
No.
[QUOTE=praseodym]Check whether "Enable Mobile Broadband" is set (click on the icon in the panel)[/QUOTE]
Done.
[QUOTE=praseodym]Network Manager: Manually set the nameserver settings in the network manager[/QUOTE]
How?
[QUOTE=praseodym]In certain cases it may happen that in network (under the APN) or the "Mobile Network Code" must be specified. Overview here: [http://en.wikipedia.org/wiki/Mobile_Network_Code](http://en.wikipedia.org/wiki/Mobile_Network_Code)[/QUOTE]
Where?
[QUOTE=praseodym]Connections may be required. try different USB ports (if posible: for Notebooks try CardBus USB) to avoid any long USB extensions, possibly using Y-cable. By using Y-cable or CardBus the sticks get a better power supply. Same effect is achieved by connecting to a powered hub (with power adapter).
In poor connections, it may be useful to chose the transmission rate (3G/2G). In Gnome network manager (Ubuntu until 10.10. Possible) klick "Type" button (default "Any") and choose accordingly. Likewise, in alternative dial-in programs and in the K-Network Manager (Kubuntu)
Disable firewall if installed[/QUOTE]
Done.

---

### Post by Fibonacci on 2016-01-07
Bump.

---

### Post by mato3848 on 2016-02-10
i have the same problem, i cant use this modem with my raspberry, in my windows 10 machine it works fine. 
How do you manage to switch the modem ?
Thanks

---

