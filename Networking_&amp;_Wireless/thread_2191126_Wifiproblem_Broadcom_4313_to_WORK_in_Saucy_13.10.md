---
title: "Wifiproblem: Broadcom 4313 to WORK in Saucy 13.10 ?"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by spacedebree on 2013-12-01
I suddenly got a flashback from when I had wifi-issues in Windows 8.1 with this computer (HP g6 laptop). The solution *then* was to download and insall a somewhat older driver for the Broadcom 4313 Wifi chip. Not sure if that is the solution now, or how to do the same thing in Ubuntu if Im needed to.

Recently I choosed to try out Linux and Ubuntu. Everything works fine exept for a not so small problem: The Wifi is not working. Well, it is working in that way that it could see the networks around me, and I can even try to connect to my network. Then it starts working (little wifi indicator on top). After a while it gives up. It cannot connect. The weird thing is that it can connect to my wifi hotspot on my phone. 

So...what do I need to do? I have googled around as well as looking at youtube. But there is a nightmare to find the solution for me; there are several helppages, and helpvideos - but for a totally beginner to Linux, I still look like a huge questionmark.

I guess that this must be quite a common problem? The Wifi-adapter is a very commond kind.

When checking the updater, it tells me "...using sourcecode for Broadcom 802.11 Linux STA driver...." Seems right to me, but it's not working.

I really need to get this to work as it should, otherwize I'll get back to the elephant (windows) again.

Thank you in advance!

Fredrik

---

### Post by praseodym on 2013-12-01
Please open a terminal with CTRL+ALT+T and show the outputs of
```

lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```
Does LAN work?

---

### Post by spacedebree on 2013-12-01
Hello. Yes, LAN is working perfectly.

Heres the result from the Terminal: (smileys are colons in the code...not sure why it shows up like this)

fredrik@fredrik-HP:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183f]
    Kernel driver in use: r8169
fredrik@fredrik-HP:~$ iwconfig
eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


fredrik@fredrik-HP:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
fredrik@fredrik-HP:~$ lsmod

---

### Post by spacedebree on 2013-12-01
Sorry... I missed the info given from the lsmod:

fredrik@fredrik-HP:~$ lsmod
Module                  Size  Used by
michael_mic            12612  0 
arc4                   12608  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69070  12 
bnep                   19564  2 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_idt      50341  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   431315  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20329  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
uvcvideo               80885  0 
btusb                  28267  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
bluetooth             371880  22 bnep,btusb,rfcomm
videobuf2_core         40469  1 uvcvideo
videodev              133390  2 uvcvideo,videobuf2_core
snd_hda_intel          48171  5 
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102033  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
lib80211_crypt_tkip    17619  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
microcode              23518  0 
psmouse                97626  0 
serio_raw              13413  0 
wl                   4207474  0 
rtsx_pci_ms            18151  0 
lpc_ich                21080  0 
memstick               16760  1 rtsx_pci_ms
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              479757  1 wl
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
wmi                    19070  1 hp_wmi
snd                    69141  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  655752  3 
hp_accel               26012  0 
lis3lv02d              20156  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19318  1 i915
drm_kms_helper         52651  1 i915
mei_me                 18421  0 
drm                   296739  4 i915,drm_kms_helper
mei                    77692  1 mei_me
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
soundcore              12680  1 snd
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
r8169                  67341  0 
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25819  2 
libahci                31898  1 ahci
mii                    13934  1 r8169

---

### Post by praseodym on 2013-12-01
This device should run with the native driver:
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
You better copy/paste these commands. Reboot after that

---

### Post by spacedebree on 2013-12-01
When trying these I get a message of that the file or catalogue is not existing.
Should I go on with the commands after these lines, cause now I stopped when I met the message (did type in the lines before, which seemed to work ok)

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf

...and the commands below give me a non-indata file, error

sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)

---

### Post by praseodym on 2013-12-01
Thats ok, just reboot.

---

### Post by spacedebree on 2013-12-02
Excellent! It now works as it should. Could you please tell me what the commands in the Terminal did do? (I'm trying to learn). 
May I also ask you another question. The last times when I'm trying to login, I have to type the password for my keyring. I get a message saying that the keyring was not opened during startup

---

### Post by praseodym on 2013-12-02
You (tried to) remove blacklist files preventing the native drivers to be loaded automatically and to change other blacklist entires.

For the keyring issue: Do not login automatically

---

### Post by Rob Sayer on 2013-12-23
Sorry to hijack, but I have the same adapter in my netbook runnng 13.10 and it's somewhat intermittent on some hotspots.

I don't have bcmwl-kernel-source installed ... it appeared to be deprecated in 13.10 last time I checked, though it worked fine in 13.04.  But terribly in 12.04.  It's using **bcrmsmac**.

Would installing linux-firmware-nonfree be advisable if you're using the bcrmsmac open source driver?

---

### Post by chili555 on 2013-12-23
> **Rob Sayer said:**
> Sorry to hijack, but I have the same adapter in my netbook runnng 13.10 and it's somewhat intermittent on some hotspots.

I don't have bcmwl-kernel-source installed ... it appeared to be deprecated in 13.10 last time I checked, though it worked fine in 13.04.  But terribly in 12.04.  It's using **bcrmsmac**.

Would installing linux-firmware-nonfree be advisable if you're using the bcrmsmac open source driver?Just for the benefit of all the driver dawgs out there, please check:```
modinfo brcmsmac
```In 13.10, it says:> filename:       /lib/modules/3.12.0-031200-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
[COLOR="#FF0000"]firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw[/COLOR]
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
<snip>So, yes, it requires firmware to be installed.

---

### Post by Rob Sayer on 2013-12-23
> **chili555 said:**
> Just for the benefit of all the driver dawgs out there, please check:```
modinfo brcmsmac
```In 13.10, it says:So, yes, it requires firmware to be installed.

Bloody excellent ... I'm kind of weak in wireless matters, and so I'm reluctant to mess around with a more or less working adapter and possibly break it.

I just installed linux-firmware-nonfree and nothing broke.  Whether it works better, I'll have to test it more in the hotspot it's been cutting out in.  And that won't happen for  a few days.  But it seems to be working at least as well as before.

---

### Post by Rob Sayer on 2014-01-02
> **Rob Sayer said:**
> Bloody excellent ... I'm kind of weak in wireless matters, and so I'm reluctant to mess around with a more or less working adapter and possibly break it.

I just installed linux-firmware-nonfree and nothing broke.  Whether it works better, I'll have to test it more in the hotspot it's been cutting out in.  And that won't happen for  a few days.  But it seems to be working at least as well as before.

After further use in the same hotspot I was having trouble in before, installing the firmware makes ZERO difference.

It worked fine in 12.04 with the 3.6 backports installed.  

It was fine in 13.04 with bcmwl-kernel-source.

I was under the distinct inpression that brcmsmac was supposed to be fixed in 13.10.  

I think 13.10 itself is broken, and I'm not alone.

---

### Post by chili555 on 2014-01-02
brcmsmac in 13.10 may be broken but I doubt that the entirety of 13.10 is broken. It works perfectly for Mrs. Chili and me on three different machines and there are few complaints about the release generally. 

I suggest we update brcmsmac and see if it helps. Please get a temporary wired ethernet connection and do:

```
sudo apt-get install linux-headers-generic build-essential
```

I suggest you download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.2/backports-3.12.2-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd ~/Desktop/backports-3.12.2-1/
make defconfig-brcmsmac
make
sudo make install
sudo modprobe -r brcmsmac && sudo modprobe brcmsmac

```
Your wireless should now be working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd ~/Desktop/backports-3.12.2-1/
make clean
make defconfig-brcmsmac
make
sudo make install
sudo modprobe -r brcmsmac && sudo modprobe brcmsmac

```

---

### Post by Rob Sayer on 2014-02-02
Sorry for the late response ... I built the backports-3.12.2-1 module as you suggested.  It works.  Thanks.

However, I stand by my previous comments on 13.10.  I live in a university town and know some pretty good linux geeks.  They agree that 13.10 is as shaky as 13.04 was solid.

Eagerly awaiting 14.04 lts ...

---

### Post by Rob Sayer on 2014-02-11
Well, I just installed lubuntu 13.10 and those commands listed a couple of posts back don't work,  And the terminal doesn't seem to have a copy and paste mode ... sigh ... more research ... at least the wireless does pretty much work without it ...

---

### Post by praseodym on 2014-02-11
Mark the text and "click" it into the terminal with the mouse wheel

---

### Post by zonanz on 2014-05-17
> **praseodym said:**
> This device should run with the native driver:
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
You better copy/paste these commands. Reboot after that

Thanks a lot. This solved my issue.

---

