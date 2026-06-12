---
title: "Update to latest 10.04 kernel broke my wifi"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by alexcckll on 2011-07-17
I am running 10.04LLTS on a Lenovo Ideapad S12.. accepted updates today (linux kernel 2.6.32.33.generic, Sun Java, Evolution)... after rebooting, it was sat at the splash screen for AGES... I restarted with Alt-SYSRQ-REIESUB as it appeared to have crashed.

I then reboot... to find that it didn't see my Wifi interface.  I have rebooted to the next kernel down (2.6.32.32) to put out this call for help.

CANONICAL - WHY THE **** HAVE YOU BROKEN MY WIFI ON MY NETBOOK???????!!!!!

Please fix ASAP.

I don't know what my Wifi interface is - I bought the machine preinstalled - and this is the first 10.04 update that has broken things.

This is unacceptable.

---

### Post by alexcckll on 2011-07-17
Here's lspci - under previous kernel.

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:0d.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:0e.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Here's lsmod.

alex@ubuntu:~$ lsmod
Module                  Size  Used by
michael_mic             1732  4 
arc4                    1153  2 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_realtek   203376  1 
binfmt_misc             6587  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
rfcomm                 33421  4 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
sco                     7917  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
l2cap                  30624  16 rfcomm,bnep
lib80211_crypt_tkip     7596  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
uvcvideo               57374  0 
nvidia               9961216  50 
wl                   1959598  0 
soundcore               6620  1 snd
video                  17375  0 
psmouse                63245  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
btusb                  10989  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               3978  0 
lib80211                5046  2 lib80211_crypt_tkip,wl
shpchp                 28835  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
nvram                   6203  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67096  1 usbhid
tg3                   109324  0 
ahci                   32360  3

---

### Post by alexcckll on 2011-07-17
Hmm - seemed to recover on 2nd boot - after I ran under 2.6.32.32 and called for help...

Maybe I ought to just look into switching off the splashscreen.

Sudo lshw -C network's output was the same under both now..

---

