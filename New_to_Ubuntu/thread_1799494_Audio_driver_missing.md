---
title: "Audio driver missing"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by Anakunda on 2011-07-07
Hello all.,
I've suddenly got a problem with sound card. Although I had audio system working, suddenly my audio driver lost, Looking into Audio preferences/Hardware tab shows an empty list.
Searching a bit for soulutions I found several troubleshooting guides, so made following steps:

aplay -l prints
aplay: device_list:240: No sound cards found...

lspci -v shows my audio chip.

find /lib/modules/`uname -r` | grep snd list my audio chip driver:
/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko

sudo modprobe snd-hda-codec-realtek generates a bunch of errors:
```
FATAL: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_codec_realtek (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```Tried also full reinstall of audio drivers:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop
```This didnot resolve the problem also.

I don't know what happened with my audio driver, any solutions?

---

### Post by jtarin on 2011-07-07
Try the "modprobe" command without sudo. If it runs then "lsmod" and post the results.
Also your error says " Unknown symbol in module, or unknown parameter **(see dmesg)**"

---

### Post by Anakunda on 2011-07-07
modprobe command self prints alot of errors also, mostly because operation not permitted

the lsmod printed this

```
petr@ASUS-UBUNTU:~$ lsmod
Module                  Size  Used by
xts                    12719  12 
gf128mul               14951  1 xts
nls_iso8859_1          12713  5 
nls_cp437              16991  5 
vfat                   21708  5 
fat                    61374  1 vfat
hidp                   22572  0 
cryptd                 20510  0 
aes_x86_64             17208  883 
aes_generic            38279  1 aes_x86_64
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  17 hidp,rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  3 
vesafb                 13761  1 
nvidia              10709116  52 
mxl5005s               46200  1 
af9013                 27812  1 
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
joydev                 17606  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
dvb_usb_af9015         35242  0 
arc4                   12529  2 
uvcvideo               72195  0 
btusb                  18600  2 
ath9k                 118238  0 
psmouse                73535  0 
mac80211              294370  1 ath9k
videodev               82052  1 uvcvideo
ir_nec_decoder         12546  0 
dvb_usb                24290  1 dvb_usb_af9015
dvb_core              110487  1 dvb_usb
usblp                  18233  0 
bluetooth              72448  10 hidp,rfcomm,sco,bnep,l2cap,btusb
v4l2_compat_ioctl32    17078  1 videodev
ath9k_common           13851  1 ath9k
rc_core                26918  8 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,dvb_usb_af9015,ir_nec_decoder,dvb_usb
ath9k_hw              323077  2 ath9k,ath9k_common
soundcore              12680  0 
usbhid                 46956  0 
i2c_nforce2            13058  0 
asus_laptop            24173  0 
ath                    23773  2 ath9k,ath9k_hw
serio_raw              13166  0 
lp                     17825  0 
cfg80211              178528  3 ath9k,mac80211,ath
hid                    91020  2 hidp,usbhid
sparse_keymap          13898  1 asus_laptop
shpchp                 37297  0 
parport                46458  3 parport_pc,ppdev,lp
snd_page_alloc         18484  0 
ses                    17321  0 
enclosure              15217  1 ses
usb_storage            53538  4 
uas                    17996  0 
video                  19438  0 
ahci                   25951  4 
r8169                  48022  0 
libahci                26642  1 ahci

```

---

### Post by jtarin on 2011-07-07
Humour me and run "lspci".:p

---

### Post by Anakunda on 2011-07-07
lspci:

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce G102M] (rev b1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

---

### Post by jtarin on 2011-07-07
OK![ here]("http://www.dbarticles.com/ubuntu-10-04-sound-issues-trying-to-find-the-right-sound-model/") is something for 10.04 but it should work for you too as some people are having problems with this card working automatically. I think it should solve your problem. Read fully before doing anything.

To find your configuration Alasa model
```
cat /proc/asound/card*/codec* | grep Codec
```

And [here]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt") is the database for configurations.

---

### Post by Anakunda on 2011-07-08
That's may be the problem:

cat: /proc/asound/: Directory or file doesnot exist

sudo lshw -C sound prints
```
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP79 High Definition Audio
       vendor: nVidia Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: b1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: memory:fae78000-fae7bfff
```


I don't see my audio chip listed in HD-Audio-Models.txt


Is that problem missing /proc/asound/ folder ?

---

### Post by jtarin on 2011-07-08
OK...look in the bios and see if you have more than one sound chip and try to enable the other and disable the present.

---

### Post by Anakunda on 2011-07-08
That's no help BIOS only shows Realtek HD audio which is enabled.
I still think this has something to do with missing /proc/asound folder.
Filesystem damage is likely since my HDD is broken.

Is there a way to let Ubuntu redetect all HW and completely reinstall all drivers from scratch ?

---

### Post by Anakunda on 2011-07-20
Hello, after some delay I'm back to the problem. Meanwhile I've figured out that this problem was caused by installing of Realtek HDA driver from [http://www.realtek.com/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3](http://www.realtek.com/downloads/downloadsview.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3)

sudo alsamixer gives error: couldnot open mixer, directory or file doesnot exist.

I've already read some reports about realtek driver corrupting the sound system, but no solution:(

My alsa-info report is located here:
[http://www.alsa-project.org/db/?f=1680c5f1d226611d22ff7a94c6e9695e7ea4428f](http://www.alsa-project.org/db/?f=1680c5f1d226611d22ff7a94c6e9695e7ea4428f)

$ dmesg | grep "snd_" :
```
[    7.579644] snd_timer: Unknown symbol snd_info_register (err 0)
[    7.579722] snd_timer: Unknown symbol snd_info_create_module_entry (err 0)
[    7.579820] snd_timer: Unknown symbol snd_info_free_entry (err 0)
[    7.580030] snd_timer: Unknown symbol __snd_printk (err 0)
[    7.580107] snd_timer: Unknown symbol snd_iprintf (err 0)
[    7.580217] snd_timer: Unknown symbol snd_ecards_limit (err 0)
[    7.580312] snd_timer: Unknown symbol snd_oss_info_register (err 0)
[    7.580388] snd_timer: Unknown symbol snd_unregister_device (err 0)
[    7.580485] snd_timer: Unknown symbol snd_device_new (err 0)
[    7.580661] snd_timer: Unknown symbol snd_register_device_for_dev (err 0)
```

Any way to get rid of the realtek driver and restore the audio subsystem?

---

### Post by jtarin on 2011-07-20
> **Anakunda said:**
> sudo alsamixer gives error: couldnot open mixer, directory or file doesnot exist.
Try the command without "sudo"



> **Anakunda said:**
> Any way to get rid of the realtek driver and restore the audio subsystem?
In a terminal issue the command "lsmod" and post the results here.

---

