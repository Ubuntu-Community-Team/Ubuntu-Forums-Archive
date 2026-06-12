---
title: "kubuntu wifi disabled by hardware switch"
date: 2015-04-04
forum: Networking &amp; Wireless
---

### Post by joseph_greene on 2015-04-04
I'm running kubuntu 14.10 and cannot connect to the internet via wifi because it is disabled by hardware switch but when I press my network button on the keyboard it does nothing

---

### Post by pissedoffdude on 2015-04-04
Hey there,

Run ```
sudo rfkill list

```

It should return a list.  If your interfaces are soft blocked, unblock them with ```
sudo rfkill unblock #

``` (note you might have to unblock 2 interfaces).

You might want to double check your keyboard button afterwards

---

### Post by joseph_greene on 2015-04-04
```
[sudo] password for joseph: 
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

---

### Post by pissedoffdude on 2015-04-04
What's your laptop model?  We should determine if it's the wireless button, or Kubuntu just not having the right drivers.  Was the device ever working (with kubuntu)?  Also, if you have to enable it with fn+f(xn) do any other fn+f(xi) commands work?

---

### Post by joseph_greene on 2015-04-04
hp pavilion g6 1d98x. and the button works on windows

---

### Post by pissedoffdude on 2015-04-04
Looks like you have a broadcom chipset. Can you temporarily use an ethernet connection?  If so, hook it up, then in a terminal type 'sudo apt-get update'

Afterwards hit alt+f2.  This will bring up a search box.  Type in drivers.  You should see additional drivers.  Go there and install the appropriate drivers for your wireless card

---

### Post by joseph_greene on 2015-04-04
when I went to update my drivers all it had was my graphics card drivers

---

### Post by pissedoffdude on 2015-04-04
Alright.  Hmm.  Did you verify the switch is actually being triggered?  By that I mean, if you trigger it with fn+f command, do you know that fn+f commands work with other keys.  Sometimes, you just need to hit simply the f+x command to get it to work.  Try it out with another command to be sure that this is the case

---

### Post by pissedoffdude on 2015-04-04
Also, if you enable it on Windows and reboot, do you see it working in Kubuntu?  I'm gonna stress again, did it ever work with Kubuntu?  We need to know if it's related to the hardware switch or if it's lacking the right drivers

---

### Post by joseph_greene on 2015-04-04
enabling it in windows and rebooting did not fix the problem, and it has never worked for any linux distro ive tried

---

### Post by wildmanne39 on 2015-04-05
Here is the work that we did when he had a different distro installed, so you will have a frame of reference to the fact that we tried almost everything. I beleive chili555 in networking is needed if you have any chance of getting this device to work.
[http://ubuntuforums.org/showthread.php?t=2271065](http://ubuntuforums.org/showthread.php?t=2271065)

---

### Post by wildmanne39 on 2015-04-05
Moved to Networking and Wireless!

---

### Post by praseodym on 2015-04-05
Check:
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot

---

### Post by joseph_greene on 2015-04-05
didnt work

---

### Post by praseodym on 2015-04-06
Tried to reset the BIOS to default?

---

### Post by chili555 on 2015-04-06
> **praseodym said:**
> Check:
```

echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
RebootA look here:```
modinfo hp_wmi
```...reveals that wireless= is not an available parameter for the driver. Therefore, the conf file created is ineffective. Let's remove it:```
sudo rm /etc/modprobe.d/hp.conf
```Reboot and then run and post:```
lsmod
```Thanks.

---

### Post by joseph_greene on 2015-04-06
```
joseph@joseph-HP-Pavilion-g6-Notebook-PC:~$ lsmod
Module                  Size  Used by
bnep                   19543  2 
rfcomm                 69509  0 
bluetooth             446190  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
binfmt_misc            17468  1 
ipheth                 13462  0 
arc4                   12608  2 
rt2800pci              13630  0 
rt2800mmio             20938  1 rt2800pci
rt2800lib              93180  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55170  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              660592  3 rt2x00lib,rt2x00pci,rt2800lib
uvcvideo               81065  0 
snd_hda_codec_idt      63632  1 
snd_hda_codec_generic    68914  1 snd_hda_codec_idt
snd_hda_codec_hdmi     47547  1 
cfg80211              510218  2 mac80211,rt2x00lib
snd_hda_intel          30420  5 
snd_hda_controller     35152  1 snd_hda_intel
snd_hda_codec         139675  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
snd_hwdep              17698  1 snd_hda_codec
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
videobuf2_core         59104  1 uvcvideo
v4l2_common            15682  1 videobuf2_core
videodev              149725  3 uvcvideo,v4l2_common,videobuf2_core
media                  21963  2 uvcvideo,videodev
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms            18168  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29513  2 snd_pcm,snd_seq
hp_wmi                 14109  0 
snd                    87611  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15052  2 snd,snd_hda_codec
sparse_keymap          13948  1 hp_wmi
memstick               16966  1 rtsx_pci_ms
kvm                   459835  0 
joydev                 17344  0 
serio_raw              13434  0 
shpchp                 37040  0 
i2c_piix4              22159  0 
k10temp                13144  0 
hp_wireless            12637  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
jfs                   185313  1 
hid_generic            12559  0 
usbhid                 52566  0 
hid                   110426  2 hid_generic,usbhid
rtsx_pci_sdmmc         23043  0 
radeon               1416645  2 
psmouse               106593  0 
i2c_algo_bit           13406  1 radeon
ttm                    97680  1 radeon
r8169                  71471  0 
drm_kms_helper         61627  1 radeon
mii                    13934  1 r8169
ahci                   34062  1 
drm                   310919  5 ttm,drm_kms_helper,radeon
rtsx_pci               46301  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32424  1 ahci
wmi                    19193  1 hp_wmi
video                  20128  0 


``` there you go:)

---

### Post by chili555 on 2015-04-06
The module hp_wmi is supposed to properly translate key presses into action; in your case, turn on the wireless. As you have noted, it doesn't do so in Ubuntu. Let's try removing it to see if the wireless comes to life.```
sudo modprobe -r hp_wmi
```Now does the key work? Test:```
rfkill list all
```If it helps, we'll blacklist the module.

---

### Post by joseph_greene on 2015-04-06
still nothing ```
0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes

```

---

### Post by jeremy31 on 2015-04-06
Can you try the Live version(Try Ubuntu) of Ubuntu 12.04 to see if it hard blocks with it?

---

### Post by joseph_greene on 2015-04-07
still nothing

---

### Post by chili555 on 2015-04-07
Frankly, I was pretty confident that most of the rfkill my-switch-doesn't-work problems were finally fixed. We see very few of these recently. The old trick of unloading the wmi module was getting dusty sitting on the shelf.

I have but two suggestions. First, you might try a live session of Ubuntu 15.04 beta: [http://cdimage.ubuntu.com/ubuntu-gnome/releases/vivid/beta-2/](http://cdimage.ubuntu.com/ubuntu-gnome/releases/vivid/beta-2/) If your wireless switch works as expected, install it.

Second, I'd look around in the BIOS to see if there is any relevant setting; perhaps wireless always off, wireless controlled by Windows or wireless always on.

The driver module hp-wmi hasn't any manipulable parameters so it is either loaded or unloaded; we've tried both.```
$ modinfo hp-wmi
filename:       /lib/modules/3.16.0-33-generic/kernel/drivers/platform/x86/hp-wmi.ko
alias:          wmi:5FB7F034-2C63-45e9-BE91-3D44E2C707E4
alias:          wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C
license:        GPL
description:    HP laptop WMI hotkeys driver
author:         Matthew Garrett <mjg59@srcf.ucam.org>
srcversion:     2BEC5DCE5B3A6695D374C6A
depends:        wmi,sparse-keymap
intree:         Y
vermagic:       3.16.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        27:43:73:00:F8:EE:18:3C:88:11:43:4F:EB:7F:D9:5F:C6:87:82:EC
sig_hashalgo:   sha512

```

---

### Post by joseph_greene on 2015-04-07
well thank you ill try those

---

### Post by praseodym on 2015-04-08
Can you try to boot the network before the OS in your BIOS settings?

---

### Post by joseph_greene on 2015-04-09
didnt work, thanks for the sugggestion though @praseodym

---

### Post by praseodym on 2015-04-09
Is there a BIOS upgrade possible?

---

### Post by joseph_greene on 2015-04-15
sorry for the late reply but no there is not a BIOS upgrade possible

---

