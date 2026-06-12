---
title: "Wifi keeps disconnecting"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by warrenjb on 2014-07-17
Vostro 1510 running Ubuntu 14.04.  Connected to home G wifi with WEP security and wifi keeps disconnecting and reconnecting.  Numerous computers in the house on same wifi network and ubuntu laptop is the only one having this problem.  I've seen others in the forum with similar problems but it seems the solutions vary so I'm not sure what to do. Appreciate any advice.  Thanks in advance.

lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by kc1di on 2014-07-18
Hi warrenjb  and welcome to Ubuntu --
Could you list the output of ```
lsmod
``` command for me. 

I use the BCM4312 without problems.  But it needs the ```
bcmwl-kernel-sorce
``` driver. if that's not the one you install install it. 
and reboot. see if that helps.

---

### Post by warrenjb on 2014-07-20
I have bcmwl-kernel-source installed but perhaps I have something conflicting?  Here is lsmod:
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342206  10 bnep,rfcomm
snd_hda_codec_realtek    55125  1 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
snd_hda_intel          42730  3 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
lib80211_crypt_tkip    17456  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
wl                   3999690  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  705659  3 
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lib80211               14040  2 wl,lib80211_crypt_tkip
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         47182  1 i915
snd_timer              28584  2 snd_pcm,snd_seq
drm                   244037  4 i915,drm_kms_helper
cfg80211              409394  1 wl
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13197  1 i915
soundcore              12600  1 snd
coretemp               13195  0 
lpc_ich                16864  0 
parport_pc             31981  0 
joydev                 17101  0 
serio_raw              13230  0 
ppdev                  17391  0 
wmi                    18673  1 dell_wmi
lp                     13299  0 
mac_hid                13037  0 
video                  18903  1 i915
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
sdhci_pci              18535  0 
ahci                   25579  2 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
sdhci                  37779  1 sdhci_pci
r8169                  61562  0 
libahci                27082  1 ahci
mii                    13654  1 r8169
crc_itu_t              12627  1 firewire_core


Thanks for your help!

---

### Post by Hadaka on 2014-07-21
Hi warrenjb, to determine the correct driver we need to see your wireless card;s
PCI-ID....please open a terminal..ctrl/alt/t and do and post,,
```
lspci -n | grep 0280
```
then,,just for grins 
with the cable connected to the internet  please do
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #ignore any error or cant find,,,on this line
```
then please do..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot
remove the cable and test wireless
thanks.

---

### Post by varunendra on 2014-07-21
Most of us wireless troubleshooters believe that the "wl" driver (that the "bcmwl-kernel-source" package installs) is not correct for your card, or at least not a good one.

Please try the native "b43" driver instead by installing the firmware it requires, and purging the "wl" driver thereafter -
```
sudo apt-get install linux-firmware-nonfree
sudo apt-get purge bcmwl-kernel-source
```
Reboot and check your connection. If the problem persists (or gets worse, in case something went wrong), please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by varunendra on 2014-07-21
Wow, Hadaka proved to be faster than me, and yet he keeps telling me he is 'old' :p

However, I suggest installing the "linux-firmware-nonfree" package first to avoid the cable connection trouble, because at least you are currently able to get a connection, even if not stable.

Besides, Hadaka, there is a typo in your "linux-firmware-nonfree" command -
> **Hadaka said:**
> ```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree**[COLOR="#FF0000"]s[/COLOR]**
sudo modprobe b43
```

Hmm.., you ARE old :lolflag:

---

### Post by warrenjb on 2014-09-11
Thanks to everyone on this thread.  Things were running great until I ran sudo apt-get update and sudo apt-get upgrade last night and suddenly no wireless.  I've attached lsmod and lspci.  Appreciate any help on this.  Thanks.

---

### Post by warrenjb on 2014-09-11
Should anyone else encounter this mysterious loss of wifi I re-installed the b43 firmware and things seem to be working again.  I should have marked this resolved last time but will do so now.

---

### Post by varunendra on 2014-09-11
@warrenjb,

We knew that we are going to see a huge flood of "my b43 broke again (mysteriously)" threads, thanks to our blind faith in "linux-firmware-nonfree" package. It's time we shift our faith back to old-school ways.

Please read this thread : [http://ubuntuforums.org/showthread.php?t=2243895&p=13120186#post13120186](http://ubuntuforums.org/showthread.php?t=2243895&p=13120186#post13120186)
and this bug-report : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882)

---

### Post by hesseny20002 on 2014-09-13
i have the same problem and trying all the mentioned steps but nothing happened >>>

[http://ubuntuforums.org/showthread.php?t=2082305&page=4](http://ubuntuforums.org/showthread.php?t=2082305&page=4)

---

### Post by jeremy31 on 2014-09-13
> **hesseny20002 said:**
> i have the same problem and trying all the mentioned steps but nothing happened >>>

[http://ubuntuforums.org/showthread.php?t=2082305&page=4](http://ubuntuforums.org/showthread.php?t=2082305&page=4)

with an ethernet connection try ```
sudo apt-get install [COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]If you read the last lines in your wireless-info file
[quote][   21.986258] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found[   21.986324] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   21.986380] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/code]

This is happening because the firmware was removed from the linux-firmware-nonfree package and worse yet updating the package will remove the b43 firmware if it was installed.
After installing the firmware package you will likely need a restart

Edit, actually this should install the firmware needed ```
sudo apt-get install firmware-b43-installer b43-fwcutter
```

---

### Post by varunendra on 2014-09-13
@ jeremy31,

Isn't "b43-fwcutter" a dependency of "firmware-b43-installer"? Please check -
```
apt-cache show firmware-b43-installer
```
I'm pretty sure it is, which means mentioning it on the "apt-get install" line is unnecessary if you are already installing "firmware-b43-installer".

---

### Post by jeremy31 on 2014-09-13
> **varunendra said:**
> @ jeremy31,

Isn't "b43-fwcutter" a dependency of "firmware-b43-installer"? Please check -
```
apt-cache show firmware-b43-installer
```
I'm pretty sure it is, which means mentioning it on the "apt-get install" line is unnecessary if you are already installing "firmware-b43-installer".

You are correct but the permissions on the /lib/firmware/b43 folder is different
```
drwxr-xr-x  3 root root    4096 Apr 16 20:24 ath10k-rw-r--r--  1 root root  246804 Jun 26 11:53 ath3k-1.fw
drwxr-xr-x  4 root root    4096 Apr 16 20:24 ath6k
-rw-r--r--  1 root root   35180 Jun 26 11:53 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 Jun 26 11:53 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root    9726 Jun 26 11:53 atmsar11.fw
drwxr-xr-x  2 root root    4096 Jul 26 08:21 av7110
drwxr-x---  2 root root    4096 Sep 13 09:22 b43
drwxr-xr-x  2 root root    4096 Jul 26 08:21 bnx2x
drwxr-xr-x  2 root root    4096 Jul 26 08:21 brcm
-rw-r--r--  1 root root   13388 Jun 26 11:53 carl9170-1.fw
drwxr-xr-x  9 root root    4096 Jul 26 08:21 carl9170fw
-rw-r--r--  1 root root  412528 Jun 26 11:53 cbfw-3.2.1.1.bin
-rw-r--r--  1 root root  414016 Jun 26 11:53 cbfw-3.2.3.0.bin
drwxr-xr-x  3 root root    4096 Jul 26 08:21 cis
-rw-r--r--  1 root root     107 Jun 26 11:53 configure
drwxr-xr-x  2 root root    4096 Jul 26 08:21 cpia2

```

---

### Post by varunendra on 2014-09-13
> **jeremy31 said:**
> You are correct but the permissions on the /lib/firmware/b43 folder is different

I'm sorry, I couldn't understand what you mean to imply.

As much as I understand, it shouldn't make any difference whether 'we' install a dependency or it is pulled-in automatically by dependent package, installation procedure and permissions should remain the same.

Of course I am not a packaging or kernel expert. It is just 'My' understanding, but I would be very, very surprised if it turns out to be incorrect.

In the output though, the 'x' permission for 'others' not being there is indeed a bit unexpected. Is that the difference you meant to emphasize? Is it different in both methods? The curiosity is killing me :p

---

### Post by jeremy31 on 2014-09-13
> **varunendra said:**
> I'm sorry, I couldn't understand what you mean to imply.

As much as I understand, it shouldn't make any difference whether 'we' install a dependency or it is pulled-in automatically by dependent package, installation procedure and permissions should remain the same.

Of course I am not a packaging or kernel expert. It is just 'My' understanding, but I would be very, very surprised if it turns out to be incorrect.

In the output though, the 'x' permission for 'others' not being there is indeed a bit unexpected. Is that the difference you meant to emphasize? Is it different in both methods? The curiosity is killing me :p

I probably should have posted on [http://ubuntuforums.org/showthread.php?t=2243945](http://ubuntuforums.org/showthread.php?t=2243945) as I was trying to figure out why running the command to install firmware-b43-installer didn't seem to work

---

### Post by varunendra on 2014-09-13
Erm.. I'm still confused. Is there really any difference between -
```
sudo apt-get install firmware-b43-installer
```
and
```
sudo apg-get install firmware-b43-installer b43-fwcutter
```
..at all?

I may find some time today to test this myself on a 14.04 virtual machine (if I didn't already delete it to gain space), but it would be very nice if you already have 14.04 installed and could confirm.

---

