---
title: "EDIMAX EW7811un installation Lenovo ideapad s10-3 and ubuntu 13"
date: 2014-02-27
forum: Networking &amp; Wireless
---

### Post by alessandro10 on 2014-02-27
Hi 
I just installed Ubuntu a couple minutes ago (Absolutely new beginner) and since my wireless card onboard the Lenovo stopped working on the previous OS I am trying to get the usb wireless EDIMAX EW7811un to work.

Now there seem to be also a problem with the computer manual switch for wireless and I am not sure how to read and write commands on the terminal.

Anyone can help pls?

Thank you

---

### Post by wildmanne39 on 2014-02-27
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2014-02-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by alessandro10 on 2014-02-27
here is the wireless file[ATTACH]250755[/ATTACH]

---

### Post by wildmanne39 on 2014-02-28
Your internal wifi card shows up so it is most likely a bad driver causing the issue with it, do you want to try to fix it first or just work with the usb adaptor?
Thanks

---

### Post by alessandro10 on 2014-02-28
I would love to try to fix it,
thanks for your help

---

### Post by wildmanne39 on 2014-02-28
Shutdown your computer and unplug the usb adaptor, then boot up and copy and paste the following commands in the terminal:
```
sudo modprobe -rv wl
sudo modprobe -v brcmsmac
```
does wireless come on? this is a test if it works we will have to make it permanent.
Thanks

---

### Post by alessandro10 on 2014-02-28
wireless does not come on. Can not get it to turn on on the settings

---

### Post by alessandro10 on 2014-02-28
wireless does not come on. Can not get it to turn on on the settings

---

### Post by alessandro10 on 2014-02-28
When I unplug the ethernet cable the system says "Wireless is turned off by hardware switch" and no matter which position I turn the wireless manual switch on it stays OFF. It looks like the switch is not working, that is the hardware is broken

---

### Post by praseodym on 2014-02-28
Hi,

first, check these steps:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

Then uninstall the Broadcom driver completely:

```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot. Maybe you want to upgrade the USB driver according to this:
[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10)

---

### Post by wildmanne39 on 2014-02-28
Sorry, I had to leave for awhile but you are in good hands so I will just back out.

---

### Post by alessandro10 on 2014-03-01
> **praseodym said:**
> Hi,

first, check these steps:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

Then uninstall the Broadcom driver completely:

```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot. Maybe you want to upgrade the USB driver according to this:
[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#Realtek-rtl8192cu-s-Treiber-fuer-13-10)



Ok so this is what I am doing:

1. Check the Link above [http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285) and tried but no luck, this is my lsmod

alessandro@MiniAle:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
______________________________

2. At the 2nd block of instructions this is a copy of the Terminal window:

alessandro@MiniAle:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

alessandro@MiniAle:~$ sudo rm /etc/modprobe.d/broadcom-sta-common.conf
rm: cannot remove ‘/etc/modprobe.d/broadcom-sta-common.conf’: No such file or directory

alessandro@MiniAle:~$ sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
rm: cannot remove ‘/etc/modprobe.d/broadcom-sta-dkms.conf’: No such file or directory

alessandro@MiniAle:~$ sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sed: no input files

alessandro@MiniAle:~$ sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sed: no input files

alessandro@MiniAle:~$ sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sed: no input files.

Now I am going to REBOOT as per instructions and I will try to update USB drives.

At this point I might give up on using the onboard wireless and try the usb device.

Thanks

---

### Post by alessandro10 on 2014-03-01
I tried the commands suggested in the last link too, i.e.

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 

[h=3]Download und Installation:[/h] 
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   




and nothing changed. This is the my situation right now:alessandro@MiniAle:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
alessandro@MiniAle:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
cfg80211              401762  3 b43,brcmsmac,mac80211
coretemp               13195  0 
ssb                    51596  1 b43
joydev                 17097  0 
parport_pc             31981  0 
ppdev                  17391  0 
snd_hda_codec_realtek    50261  1 
rfcomm                 53664  0 
bnep                   18959  2 
bluetooth             323656  10 bnep,rfcomm
snd_hda_intel          42658  3 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
i915                  594442  4 
uvcvideo               71309  0 
microcode              18894  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
videodev              107508  2 uvcvideo,videobuf2_core
snd_timer              24447  2 snd_pcm,snd_seq
psmouse                90642  0 
drm_kms_helper         46867  1 i915
serio_raw              13189  0 
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                16864  0 
drm                   242400  5 i915,drm_kms_helper
soundcore              12600  1 snd
ideapad_laptop         17974  0 
bcma                   40966  3 b43,brcmsmac
sparse_keymap          13708  1 ideapad_laptop
lp                     13299  0 
i2c_algo_bit           13197  1 i915
wmi                    18590  0 
parport                40795  3 lp,ppdev,parport_pc
video                  18777  1 i915
ext2                   67224  1 
mac_hid                13037  0 
hid_generic            12492  0 
usbhid                 47361  0 
hid                    87370  2 hid_generic,usbhid
ahci                   25579  2 
ums_realtek            17733  0 
libahci                26619  1 ahci
usb_storage            48294  1 ums_realtek
r8169                  61562  0 
mii                    13654  1 r8169
alessandro@MiniAle:~$

---

### Post by praseodym on 2014-03-02
There are two drivers loaded:

```
echo "blacklist b43\nblacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Reboot.

---

### Post by alessandro10 on 2014-03-09
When I prompt this 
sudo tee -a /etc/modprobe.d/blacklist.conf

the computer does not seem to respond.

I waited a couple hours and still the command was not executed.

Thanks for your help

A

THis is the situation as of now:

rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
alessandro@MiniAle:~$ lsmod
Module                  Size  Used by
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
arc4                   12536  2 
bnep                   18959  2 
brcmsmac              529716  0 
bluetooth             323656  10 bnep,rfcomm
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
snd_hda_codec_realtek    50261  1 
cfg80211              401762  3 b43,brcmsmac,mac80211
snd_hda_intel          42658  3 
ssb                    51596  1 b43
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
coretemp               13195  0 
joydev                 17097  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              18894  0 
i915                  594442  3 
videodev              107508  2 uvcvideo,videobuf2_core
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse                90642  0 
drm_kms_helper         46867  1 i915
soundcore              12600  1 snd
ext2                   67224  1 
drm                   242400  4 i915,drm_kms_helper
serio_raw              13189  0 
wmi                    18590  0 
ideapad_laptop         17974  0 
sparse_keymap          13708  1 ideapad_laptop
i2c_algo_bit           13197  1 i915
lp                     13299  0 
bcma                   40966  3 b43,brcmsmac
lpc_ich                16864  0 
mac_hid                13037  0 
parport                40795  3 lp,ppdev,parport_pc
video                  18777  1 i915
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
ahci                   25579  2 
libahci                26619  1 ahci
r8169                  61562  0 
mii                    13654  1 r8169

---

### Post by praseodym on 2014-03-09
Then open the file like this

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines
```

blacklist b43
blacklist brcm80211
```
Save, close the editor and reboot

---

### Post by alessandro10 on 2014-03-09
Done. nothing.

rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
alessandro@MiniAle:~$ lsmod
Module                  Size  Used by
arc4                   12536  2 
brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              517444  1 brcmsmac
coretemp               13195  0 
parport_pc             31981  0 
cfg80211              401762  2 brcmsmac,mac80211
ppdev                  17391  0 
joydev                 17097  0 
bnep                   18959  2 
rfcomm                 53664  0 
snd_hda_codec_realtek    50261  1 
bluetooth             323656  10 bnep,rfcomm
snd_hda_intel          42658  3 
uvcvideo               71309  0 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
videodev              107508  2 uvcvideo,videobuf2_core
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
microcode              18894  0 
i915                  594442  3 
snd_timer              24447  2 snd_pcm,snd_seq
psmouse                90642  0 
snd                    60790  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13189  0 
drm_kms_helper         46867  1 i915
ideapad_laptop         17974  0 
drm                   242400  4 i915,drm_kms_helper
soundcore              12600  1 snd
sparse_keymap          13708  1 ideapad_laptop
lpc_ich                16864  0 
wmi                    18590  0 
i2c_algo_bit           13197  1 i915
video                  18777  1 i915
bcma                   40966  2 brcmsmac
ext2                   67224  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
ahci                   25579  2 
libahci                26619  1 ahci
ums_realtek            17733  0 
r8169                  61562  0 
usb_storage            48294  1 ums_realtek
mii                    13654  1 r8169

---

### Post by praseodym on 2014-03-09
[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

Check these steps

---

### Post by alessandro10 on 2014-03-10
I did that already, no luck.

I think I am going to keep the laptop wired and use it to learn linux. Maybe later I will be able to fix it by myself.

THanks

A

---

### Post by praseodym on 2014-03-10
Try to press the button/key combination permanently or repeatedly during boot-up

---

