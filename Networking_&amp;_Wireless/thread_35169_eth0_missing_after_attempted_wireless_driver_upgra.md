---
title: "eth0 missing after attempted wireless driver upgrade"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by MechR on 2005-05-17
Hmm, I tried the instructions [here](http://ubuntuforums.org/showthread.php?t=26623) for enabling WPA usage, but now Ubuntu can't seem to detect eth0 (my built-in wireless Intel hardware) at all* :(  Notably, the "dmesg | grep ipw" step didn't return any output.  Does anyone know how I might fix this?  Thanks in advance :)

*: Before, eth0 would show up in the list in Network Settings (System -> Administration -> Networking), but now it is missing.  Manually typing eth0 in Connection Properties (the window that pops up when you click the system tray icon) shows an error.  Also, the Device Manager used to have a longer list of info on the wireless hardware (PRO/Wireless 2200BG) in the Advanced tab.  And doing "sudo ifup eth0" spits out a number of errors, with several mentions of "no such device."

---

### Post by chilly_willy2 on 2005-05-17
Is there any mention of it in lspci?  Also, are all the necessary modules loaded (lsmod)?

---

### Post by MechR on 2005-05-17
[QUOTE=chilly_willy2]Is there any mention of it in lspci?  Also, are all the necessary modules loaded (lsmod)?[/QUOTE]In lspci there are these listed:
0000:06:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1068 (rev 04)

I can't tell whether lsmod has what I need, though...

Module                  Size  Used by
isofs                  33720  0
udf                    77060  0
speedstep_centrino      7892  1
proc_intf               4100  0
freq_table              4100  1 speedstep_centrino
cpufreq_userspace       4572  1
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
i915                   18304  1
drm                    59412  2 i915
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
af_packet              20744  4
e100                   32384  0
mii                     4736  1 e100
firmware_class          9728  0
ieee80211              21252  0
ieee80211_crypt         5832  1 ieee80211
ohci1394               31876  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
hw_random               5524  0
ehci_hcd               29444  0
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  4 ehci_hcd,usbhid,uhci_hcd
snd_hda_intel          15584  2
snd_hda_codec          63232  1 snd_hda_intel
snd_pcm_oss            47648  1
snd_mixer_oss          16896  2 snd_pcm_oss
snd_pcm                82440  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              23684  1 snd_pcm
snd                    50532  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_hda_intel,snd_pcm
intel_agp              20636  1
agpgart                31784  3 drm,intel_agp
rtc                    12216  0
nls_iso8859_1           4224  1
vfat                   12928  1
fat                    37792  1 vfat
nls_cp437               5888  2
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
evdev                   9088  0
capability              5000  0
tsdev                   7488  0
commoncap               7808  1 capability
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  0
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  800
thermal                13576  0
processor              22708  2 speedstep_centrino,thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by MechR on 2005-05-18
Aha, found my problem :D  There was a tiny flaw in the instructions that got mentioned later in the thread.  I've posted there to hopefully get it changed :)

---

