---
title: "Wireless is disabled by hardware switch problem"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by todor-a on 2014-01-07
Hello
I am currently using Ubuntu 13.10 on my Lenovo Ideapad z570 and i can't enable my wifi connection.

When i turn my hardware switch ON, my bluetooth powers up but the wifi stays gray with the 'disabled by hardware switch' message.

The laptop is not soft blocked.

Things I've done so far from reading the forums:


I tried to remove the battery and press the power button.

I did bios reset.



I don't have windows so i cannot dual boot and enable the wifi from there.

I HAD wifi connection from the live usb when i was installing ubuntu. 

Can someone please help me with this problem
Thanks.

---

### Post by chili555 on 2014-01-07
Let's gather some diagnostic information first. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
iwconfig
rfkill list all
```Thanks.

---

### Post by todor-a on 2014-01-07
> 03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]

> eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

> 0: ideapad_bluetooth: Bluetooth	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


Thanks

---

### Post by chili555 on 2014-01-07
When you press the switch or key combination, does this change at all?```
rfkill list all
```Does this change anything?```
sudo modprobe ideapad-laptop
sudo rfkill unblock all
rfkill list all
```

---

### Post by todor-a on 2014-01-07
HW switch off
> 0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



HW Switch ON
> 0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no





When Hw switch is off i have one less bluetooth device in 'list all'?
The Soft switch button works OK (enables and disables wifi, but hard blocked is allways 'yes')
Also modprobe changes nothing. :(

---

### Post by todor-a on 2014-01-07
I also want to point out that if now i insert the live usb and boot Ubuntu in try mode i will have Wifi.
My 2 cents are that the installed version has messed up something but i really have no idea whats the problem. :(

---

### Post by chili555 on 2014-01-07
May I see:```
lsmod 
dmesg | grep -i -e wmi -e dmi
```What is the position of this switch?[ATTACH=CONFIG]249300[/ATTACH]

Thanks.

---

### Post by todor-a on 2014-01-07
The position of the switch is on the right side and the Wifi indicator powers up just like it should. But it still shows up as hard blocked.

Module                   Size   Used by
parport_pc              32701  0 
ppdev  17671  0 
rfcomm                  69130  12 
bnep                    19704  2 
binfmt_misc             17468  1 
nls_iso8859_1           12713  1 
x86_pkg_temp_thermal     14162  0 
intel_powerclamp        14705  0 
coretemp                13435  0 
crct10dif_pclmul        14289  0 
crc32_pclmul            13113  0 
ghash_clmulni_intel     13259  0 
cryptd                  20359  1 
ghash_clmulni_intel
joydev                  17377  0 
acer_wmi                32522  0 
snd_hda_codec_hdmi     41117  5 
snd_hda_codec_realtek    55704  1 
uvcvideo                80885  0 
videobuf2_vmalloc       13216  1 uvcvideo
rts5139                331166  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40499  1 uvcvideo
videodev              133509  2 uvcvideo,videobuf2_core
microcode               23576  0 
snd_hda_intel           48171  5 
arc4                   12608  2 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
psmouse                97655  0 
snd_hwdep              13602  1 snd_hda_codec
serio_raw              13413  0 
iwldvm                237469  0 
mac80211              597268  1 iwldvm
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
btusb                  28267  0 
snd_seq_midi           13324  0 
bluetooth             372041  22 bnep,btusb,rfcomm
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
nouveau               943717  1 
mxm_wmi                13021  1 nouveau
lpc_ich                21080  0 
wmi                    19070  3 acer_wmi,mxm_wmi,nouveau
ttm                    84169  1 nouveau
ideapad_laptop         18342  0 
sparse_keymap          13948  2 acer_wmi,ideapad_laptop
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  661261  3 
iwlwifi               165675  1 iwldvm
video                  19318  3 i915,acer_wmi,nouveau
drm_kms_helper         52710  2 i915,nouveau
mei_me                 18421  0 
drm                   297056  7 ttm,i915,drm_kms_helper,nouveau
soundcore              12680  1 snd
cfg80211              480503  3 iwlwifi,mac80211,iwldvm
i2c_algo_bit           13413  2 i915,nouveau
mei                    77782  1 mei_me
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
r8169                  67581  0 
mii                    13934  1 r8169





> [    0.000000] DMI: LENOVO HuronRiver Platform/Emerald Lake, BIOS 45CN37WW 09/22/2011
[   13.708656] wmi: Mapper loaded
[   14.811948] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.912815] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.305313] acer_wmi: Brightness must be controlled by acpi video driver
[   17.389635] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   17.389708] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   17.389761] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   17.389809] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16

---

### Post by chili555 on 2014-01-07
Please try:```
sudo modprobe -rf acer-wmi
sudo rfkill unblock all
rfkill list all
```If this helps, we can make it persistent.

---

### Post by todor-a on 2014-01-07
Still no luck :(
I even rebooted my laptop just to make sure.
> [COLOR=#000000]*0: ideapad_bluetooth: Bluetooth*[/COLOR]
[COLOR=#000000]*Soft blocked: no*[/COLOR]
[COLOR=#000000]*Hard blocked: no*[/COLOR]
[COLOR=#000000]*2: phy0: Wireless LAN*[/COLOR]
[COLOR=#000000]*Soft blocked: no*[/COLOR]
[COLOR=#000000]*Hard blocked: yes*[/COLOR]
[COLOR=#000000]*7: hci0: Bluetooth*[/COLOR]
[COLOR=#000000]*Soft blocked: no*[/COLOR]
[COLOR=#000000]*Hard blocked: no*[/COLOR]


**Edit**: i've  used 
> [COLOR=#000000][FONT=Ubuntu Mono]lsmod
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -i -e wmi -e dmi[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

and it still shows the same info with acer_wmi. But i disabled it few minutes ago...\

**Edit2**: I've blacklisted acer-wmi in Blacklist.conf but my wifi is still hard locked
the new modules for 'wmi' are  mxm_wmi,nouveau



[/FONT][/COLOR]dmesg | grep -i -e wmi -e dmi[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]> 

[    0.000000] DMI: LENOVO HuronRiver Platform/Emerald Lake, BIOS 45CN37WW 09/22/2011[   13.603982] wmi: Mapper loaded
[   14.761164] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.458161] HDMI: invalid ELD data byte 0
[   18.458315] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   18.458386] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   18.458438] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   18.458485] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15


[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by praseodym on 2014-01-07
[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

Check these solutions.

---

### Post by chili555 on 2014-01-07
Aside from trying the live DVD for an earlier Ubuntu version, 12.04 LTS, for example, I'm afraid I have no other suggestions. My understanding is that the module acer-wmi is supposed to translate key presses to action. It appears to not be working correctly here. I suggest you file a bug against acer-wmi: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by todor-a on 2014-01-07
> [http://ubuntuforums.org/showthread.p...5#post12490285]("http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285")

[COLOR=#000000]Check these solutions.[/COLOR]
Thank you! It worked!
I also wanna thank chili555 for wasting so much time with my problem
You guys are great :)

---

### Post by mörgæs on 2014-01-07
Good, please mark the thread 'solved'.

---

### Post by niko123456 on 2014-01-07
I recently had this problem.

My backlight wasn't turning on during installation.. so I booted with acpi=off.

This made my backlight work but not my wireless (open source or proprietary driver). 

So I figured out that it was important my /boot/grub/grub.cfg file didn't make any reference to acpi=off

---

### Post by Os_Tyler on 2014-02-26
I have been struggling with similar issues on a Lenovo Yoga 2 Pro.

I cleared the pre-installed OS and loaded ubuntu 12.04. Everything looked good, but I had no wireless connectivity.

Clicking the wireless icon in the menu bar at the top of the string showed: "wireless is disabled by hardware switch"

I found this post on the lenovo forums that suggested removing the ideapad_laptop module via:
modprobe -r ideapad_laptop

[http://forums.lenovo.com/t5/Idea-Windows-based-Tablets-and/Wifi-is-hardware-disabled/td-p/1307405](http://forums.lenovo.com/t5/Idea-Windows-based-Tablets-and/Wifi-is-hardware-disabled/td-p/1307405)

After removing the ideapad_laptop module, wireless began working as expected.

This was my long-sought solution ... hope it helps someone else.

As per the lenovo forums link above, to implement the fix across reboots on an ubuntu distro, edit /etc/modprobe.d/myownblacklist.conf and add the line: "blacklist ideapad_laptop"

---

