---
title: "Install wi-fi driver for inspiron 1501"
date: 2015-05-11
forum: Networking &amp; Wireless
---

### Post by Vladimir1989 on 2015-05-11
Hi! Tell me, please, how to install driver wifi for this laptop. Thank you.

---

### Post by wildmanne39 on 2015-05-11
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Vladimir1989 on 2015-05-11
I have no wired connection, only wifi. I can't do automatic updates on ubuntu. Some time ago I installed ubuntu via a wired connection and wi-fi worked, but now do not have this feature.

---

### Post by wildmanne39 on 2015-05-11
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here by using a usb flash drive and a computer with internet:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Vladimir1989 on 2015-05-11
# (natasha@Natasha:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"
Linux Natasha 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 18:00:35 UTC 2014 i686 athlon i686 GNU/Linux
natasha@Natasha:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
                Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
                Kernel driver in use: wl
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
                Subsystem: Dell Device [1028:01f5]
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
natasha@Natasha:~$ lsusb
Bus 001 Device 003: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 09da:90a0 A4 Tech Co., Ltd
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
natasha@Natasha:~$ iwconfig
lo        no wireless extensions.
 
natasha@Natasha:~$ rfkill list all
natasha@Natasha:~$ lsmod
Module                  Size  Used by
bnep                   18829  2
rfcomm                 58045  0
bluetooth             390981  10 bnep,rfcomm
6lowpan_iphc           18262  1 bluetooth
ssb                    51849  1
mii                    13654  0
wl                   6148792  1
dell_wmi               12665  0
sparse_keymap          13708  1 dell_wmi
snd_hda_codec_idt      53624  1
dell_laptop            17859  0
dcdbas                 14448  1 dell_laptop
kvm_amd                50783  0
snd_hda_codec_generic    62849  2 snd_hda_codec_idt
snd_hda_intel          29211  3
kvm                   396281  1 kvm_amd
snd_hda_controller     29944  1 snd_hda_intel
snd_hda_codec         120356  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                91280  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13324  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25722  1 snd_seq_midi
snd_seq                56638  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28579  2 snd_pcm,snd_seq
joydev                 17072  0
snd                    66629  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
serio_raw              13210  0
k8temp                 12854  0
soundcore              14604  2 snd,snd_hda_codec
sp5100_tco             13663  0
radeon               1328356  3
i2c_piix4              17727  0
ttm                    76915  1 radeon
drm_kms_helper         55051  1 radeon
cfg80211              430618  1 wl
drm                   255383  6 ttm,drm_kms_helper,radeon
video                  19528  0
i2c_algo_bit           13190  1 radeon
wmi                    18689  1 dell_wmi
parport_pc             32021  0
ppdev                  17391  0
shpchp                 32136  0
mac_hid                13059  0
ati_agp                13196  0
lp                     17395  0
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12503  0
usbhid                 47001  0
hid                    91893  2 hid_generic,usbhid
pata_acpi              12901  0
uas                    22720  0
usb_storage            52598  6 uas
psmouse                95318  0
sdhci_pci              18607  0
sdhci                  38214  1 sdhci_pci
pata_atiixp            13066  0
ahci                   25622  1
libahci                31066  1 ahci)

---

### Post by wildmanne39 on 2015-05-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2015-05-11
We need to install the correct driver for your device after removing the incorrect one:
```
sudo apt-get purge bcmwl-kernel-source
```
Then:
Download the b43.zip file from the link below to a usb flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. 

Open a terminal and do:
Run the commands one line at a time by coping and pasting for accuracy watch for errors but even if there are some run all other commands.
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43_updated.zip/*  /lib/firmware/b43
sudo modprobe -rv b43 
sudo modprobe -v b43
```
if it does not come on reboot.
Wireless should now be working.

[https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892](https://dl.dropboxusercontent.com/s/19e7y7w6ndozdzq/b43_updated.zip?dl=1&token_hash=AAEELVjeW3iSm3d0ScTg17BSplJ01qhPGCkhav5o9EYiJA&expiry=1400713892)

---

### Post by Vladimir1989 on 2015-05-12
Hi! Installed without problems bcmwl-kernel, but for these teams no. sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43_updated.zip/* /lib/firmware/b43
sudo modprobe-rv b43 
sudo modprobe-v b43
no exits files.

---

### Post by Vladimir1989 on 2015-05-12
[FONT=Arial]And yet, the computer [/FONT][FONT=Arial]restarts [/FONT][FONT=Arial]only [/FONT][FONT=Arial]in enforcing mode [/FONT][FONT=Arial]is turned off[/FONT][FONT=Arial].[/FONT]

---

### Post by wildmanne39 on 2015-05-12
There is no exit file when running those commands from the terminal. You shut down the computer with the power button? is that because you were waiting for exit file?  When you reboot did your wireless work? Are you still having issues shutting down your computer?
From where and why? You were not instructed to install bcmwl-kernel> Installed without problems bcmwl-kernel do you mean you ran this command```
sudo apt-get purge bcmwl-kernel-source
``` Please answer all questions.
Thanks

---

### Post by Vladimir1989 on 2015-05-12
> **Wild Man said:**
> There is no exit file when running those commands from the terminal. You shut down the computer with the power button? is that because you were waiting for exit file?  When you reboot did your wireless work? Are you still having issues shutting down your computer?
From where and why? You were not instructed to install bcmwl-kernel do you mean you ran this command```
sudo apt-get purge bcmwl-kernel-source
``` Please answer all questions.
Thanks
Hi! Today there is no time to explain. A tight schedule. We will continue tomorrow. Thank you.

---

### Post by Vladimir1989 on 2015-05-13
> **Wild Man said:**
> There is no exit file when running those commands from the terminal. You shut down the computer with the power button? is that because you were waiting for exit file?  When you reboot did your wireless work? Are you still having issues shutting down your computer?
From where and why? You were not instructed to install bcmwl-kernel do you mean you ran this command```
sudo apt-get purge bcmwl-kernel-source
``` Please answer all questions.
Thanks


Hello! The situation is this: when I turn off the computer a black screen appears and the string to the label, and nothing else happens, no matter how long I waited. And I just push the off button. So it was before the installation of your teams and after. Wireless connection is not working. Reboot does not help (not working), I just turn off the computer. Code:
sudo apt-get purge bcmwl-kernel-source. It has been established.

---

### Post by Vladimir1989 on 2015-05-13
[COLOR=#C61919]**Wild Man **[/COLOR][FONT=Arial]I[/FONT][FONT=Arial] [/FONT][FONT=Arial]did not go to[/FONT][FONT=Arial] [/FONT][FONT=Arial]ubuntu[/FONT][FONT=Arial] [/FONT][FONT=Arial]a couple of days.[/FONT][FONT=Arial] [/FONT][FONT=Arial]And[/FONT][FONT=Arial] [/FONT][FONT=Arial]went[/FONT][FONT=Arial] [/FONT][FONT=Arial]now[/FONT][FONT=Arial], [/FONT][FONT=Arial]wi[/FONT][FONT=Arial]-fi[/FONT][FONT=Arial] [/FONT][FONT=Arial]earned[/FONT][FONT=Arial]. [/FONT][FONT=Arial]I am writing to you[/FONT][FONT=Arial] [/FONT][FONT=Arial]now[/FONT][FONT=Arial] [/FONT][FONT=Arial]with[/FONT][FONT=Arial] [/FONT][FONT=Arial]this operating system[/FONT][FONT=Arial]. [/FONT][FONT=Arial]But the files[/FONT][FONT=Arial] [/FONT][FONT=Arial]b43[/FONT][FONT=Arial] [/FONT][FONT=Arial]has not been established[/FONT][FONT=Arial]. [/FONT][FONT=Arial]I put[/FONT][FONT=Arial] [/FONT][FONT=Arial]the picture[/FONT][FONT=Arial] [/FONT][FONT=Arial]as it was[/FONT][FONT=Arial]. [/FONT][FONT=Arial]All[/FONT][FONT=Arial] [/FONT][FONT=Arial]left but[/FONT][FONT=Arial] [/FONT][FONT=Arial]the connection[/FONT][FONT=Arial] [/FONT][FONT=Arial]worked.[/FONT]

---

### Post by Vladimir1989 on 2015-05-13
> **Vladimir1989 said:**
> [COLOR=#C61919]**Wild Man **[/COLOR][FONT=Arial]I[/FONT][FONT=Arial]did not go to[/FONT][FONT=Arial]ubuntu[/FONT][FONT=Arial]a couple of days.[/FONT][FONT=Arial]And[/FONT][FONT=Arial]went[/FONT][FONT=Arial]now[/FONT][FONT=Arial], [/FONT][FONT=Arial]wi[/FONT][FONT=Arial]-fi[/FONT][FONT=Arial]earned[/FONT][FONT=Arial]. [/FONT][FONT=Arial]I am writing to you[/FONT][FONT=Arial]now[/FONT][FONT=Arial]with[/FONT][FONT=Arial]this operating system[/FONT][FONT=Arial]. [/FONT][FONT=Arial]But the files[/FONT][FONT=Arial]b43[/FONT][FONT=Arial]has not been established[/FONT][FONT=Arial]. [/FONT][FONT=Arial]I put[/FONT][FONT=Arial]the picture[/FONT][FONT=Arial]as it was[/FONT][FONT=Arial]. [/FONT][FONT=Arial]All[/FONT][FONT=Arial]left but[/FONT][FONT=Arial]the connection[/FONT][FONT=Arial]worked.[/FONT]
Image.

---

### Post by wildmanne39 on 2015-05-13
So your wifi is now working is that correct?
Some of those commands will fail if the file already has been create before but the wifi should still work.
Thanks

---

### Post by Vladimir1989 on 2015-05-13
Yes. Wi-fi works. And hassle-free computer may restart. I don't know how long enough of this work. But you are definitely the first person who helped set up is so easy wi-fi for me. Before long we were doing a lot of extra and unnecessary steps [http://ubuntuforums.org/showthread.php?t=2264282&highlight=Dell+inspiron+1501](http://ubuntuforums.org/showthread.php?t=2264282&highlight=Dell+inspiron+1501) all to no avail, but did you find a solution. THANK YOU very much, if your solution will continue to work!

---

### Post by wildmanne39 on 2015-05-13
If you still have problems shutting down your computer I would start a new thread on that in general help, because turning off the computer with the power button will crash it sooner or later.

You can use this link to help shut it down if you need to until you get it fixed.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)
I am glad it is working.
Enjoy!

---

### Post by Vladimir1989 on 2015-05-13
> **Wild Man said:**
> If you still have problems shutting down your computer I would start a new thread on that in general help, because turning off the computer with the power button will crash it sooner or later.

You can use this link to help shut it down if you need to until you get it fixed.
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)
I am glad it is working.
Enjoy!



[COLOR=#C61919]**Wild Man, i**[/COLOR] just checked again. Wi-fi works, the computer restarts without any problems. We expect that all will be well even. And now I know who to turn first. Thank you!

---

