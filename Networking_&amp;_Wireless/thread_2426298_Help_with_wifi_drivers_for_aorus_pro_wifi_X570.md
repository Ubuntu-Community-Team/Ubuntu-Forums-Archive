---
title: "Help with wifi drivers for aorus pro wifi X570"
date: 2019-09-06
forum: Networking &amp; Wireless
---

### Post by mongrel-shark on 2019-09-06
Hi Guys

I just bought a new pc with x570 aorus pro wifi mobo. I have installed Ubuntu 16.04 after failing to get 18.04 to install. I prefer 16 anyway so no problem here I hope.

The wifi is not detecting. I have googled a lot and there is a fix, but I'm not enough of a linux guru to understand what I need to do. Something about kernals and drivers.

[https://unix.stackexchange.com/questions/518571/locating-drivers-for-intel-ax200-wireless-on-5-1-kernel](https://unix.stackexchange.com/questions/518571/locating-drivers-for-intel-ax200-wireless-on-5-1-kernel) seems to have a solution,

I folowed the link to [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release) and copy pasted the CLI stuff. which returned.

```
mongrel@CADboss:~$ git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
Cloning into 'backport-iwlwifi'...
remote: Counting objects: 94412, done.
remote: Compressing objects: 100% (10805/10805), done.
remote: Total 94412 (delta 69845), reused 94096 (delta 69587)
Receiving objects: 100% (94412/94412), 14.64 MiB | 1.27 MiB/s, done.
Resolving deltas: 100% (69845/69845), done.
Checking connectivity... done.
mongrel@CADboss:~$ git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.gitmake defconfig-iwlwifi-public
Cloning into 'defconfig-iwlwifi-public'...
fatal: repository 'https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.gitmake/' not found

```


Help please I've hit the wall, and gone right through it into a new place were nothing makes any sense.


p.s. I dont have permission to add new tags, if someone could get this thread tagged with x570 that would be a big help to new players...

---

### Post by wildmanne39 on 2019-09-06
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by mongrel-shark on 2019-09-06
Some extra info


Bluetooth worked in 18.04 live USB. It doesn't in 16.04.
My network cable works in every ubuntu I tried today., unfortunately I would need a very long one to get from router to pc. (Possible, but not practical)
In the below cli ouputs. I do have a wifi dongle plugged in, Its a d-link DWA-131. Its to slow for regular usage, but great for times like this when network otherwise unavailable..

Note the unclaimed adapter down in lshw -C network output. Pretty sure thats my wifi that I want to get working.

I'm tapped dry for ideas. But happy to ping CLI for more info if anyone can tell me what to copy paste :D

```

mongrel@CADboss:~$  lspci

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1480
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 1481
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1483
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1483
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1483
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:05.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1484
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1482
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1484
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1440
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1441
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1442
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1443
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1444
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1445
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1446
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1447
01:00.0 Non-Volatile memory controller: Device 1987:5016 (rev 01)
02:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57ad
03:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57a3
03:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57a3
03:08.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57a4
03:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57a4
03:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 57a4
04:00.0 Network controller: Intel Corporation Device 2723 (rev 1a)
05:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
06:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1485
06:00.1 USB controller: Advanced Micro Devices, Inc. [AMD] Device 149c
06:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 149c
07:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
08:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
09:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X] (rev e7)
09:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 580]
0a:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 148a
0b:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device 1485
0b:00.1 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1486
0b:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 149c
0b:00.4 Audio device: Advanced Micro Devices, Inc. [AMD] Device 1487

mongrel@CADboss:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fca00000-fca03fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 03
       serial: b4:2e:99:3e:ff:e4
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:fc900000-fc91ffff ioport:f000(size=32) memory:fc920000-fc923fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:4
       logical name: wlx00ad244a2b28
       serial: 00:ad:24:4a:2b:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-60-generic firmware=N/A ip=10.0.0.4 link=yes multicast=yes wireless=IEEE 802.11
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by pcfan1234 on 2019-09-07
Your mobo is too new for 16.04, even for 18.04 without new kernels. Install 19.04.

---

### Post by mongrel-shark on 2019-09-07
Is there a way to use newer kernal on 16.04?

Can i confirm that drivers are known to work on 19? Silly me just spent half a day installing stuff and getting settled in to current install.

Maybe I should just get a better Wifi dongle or PCI card? I'd use a dongle on other stuff and can hopefully wait for a kernal update??

---

### Post by mongrel-shark on 2019-09-07
The links I posted above have instructions to update kernal. I have the file downloaded, but no idea if its actually the right one, or what to do with it if it is....

---

### Post by pcfan1234 on 2019-09-07
With 16.04 you use a system that is partially out end of life (repositories universe/multiverse).
That is the 1st reason why I do not recommend 16.04.
Because the X570 chipset is new, I recommend 19.04 or 18.04.2.

---

### Post by wildmanne39 on 2019-09-07
I think you may be headed down the wrong track before you go any further please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by mongrel-shark on 2019-09-07
Had the same problem in 18.04 live usb. Although Blutooth did work. I guess I can try a 19 usb and if it works I'll consider reinstall lol.

As this is a work from home pc I'd prefer to stick to LTS versions, and don't like 18 much and the work from work pc is 16.04...

How about looking into the kernal update that worked for someone else with a similar wifi module? I found some more firmware here [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)
I found my Kernal info
```
mongrel@CADboss:~$ cat /proc/version
Linux version 4.15.0-60-generic (buildd@lcy01-amd64-024) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.10)) #67~16.04.1-Ubuntu SMP Mon Aug 26 08:57:33 UTC 2019
```


I just don't know how to confirm my modules details? Running duel boot so maybe I could check windows device manager for the module name? 

Once I have the right backport I may need need help installing it. Although looks like a simple copy paste as root job?

---

### Post by mongrel-shark on 2019-09-07
Just doing update and upgrade before running wildmanne's script.

While I wait for my slow-fi dongle. I'm reading up more on the backports, also downloading 19.02 iso
 on another computer (running Ubuntu 14.04)
I confirmed its a Intel® Wi-Fi 6 AX200 160MHz via windoze device manager.   Looks Like I either need kernal 5.1 or later, or backported fimware? Correct me if I am misunderstanding something?

(I have to take a break to brag here. i got some fancy new 5000mbit m.2 ssd to go with the new Ryzen 5 3600x, rebooting from win to linux in under 10s, most of which is memory check on 64gb... From Grub, windoze in 3-4 sec Ubuntu login in the time it takes to release the enter key, blink and you miss the whole bootup.)

Ok updates done, wifi script output attached. If I wasn't so keen to solve this, not sure I'd want to share all that router info..... I suppose I could always unplug my dongle while the script runs.:D

from what I can see, its almost working?

If I disappear for a few min, I'll be trying the 19.02 live usb.... Back soon.

---

### Post by guiverc on 2019-09-07
> **mongrel-shark said:**
> 
Once I have the right backport I may need need help installing it. Although looks like a simple copy paste as root job?

The SE Unix & Linux solution you saw was for kernel 5.1.  Ubuntu 16.04 uses the 4.4 kernel by default, or 4.15 kernel with HWE enabled, so to backport a 5.1 patch requires taking out the code, adding to your kernel source code and re-compiling your new kernel, followed by testing etc.

For a kernel module to be just copy/pasted there need to be no changes to API/ABI otherwise you should expect *kernel panic* and your system just halts. (thus why you copy/paste the code in your backport & recompile - so you've got warnings and most ABI changes are taken care of).  I would **not** call this a simple copy/paste job - but i'm not a kernel hacker.

Yes some modules may allow for what you're doing, IF there no changes in the interfaces used by the module(s) etc.. but checking the changes that occurred between two kernels that far part isn't a quick job; but again that's me as a non-kernel hacker.

If you want to see if a later kernel works, I'd suggest trying Ubuntu 19.10 (daily; [http://iso.qa.ubuntu.com/qatracker/milestones/404/builds](http://iso.qa.ubuntu.com/qatracker/milestones/404/builds))  as these will let you see if your problem still exists with the 5.2 kernel currently in use by 19.10.   To me anyway, it's easier than backporting kernel modules & changes.

---

### Post by mongrel-shark on 2019-09-07
I tried the iso from here: [http://releases.ubuntu.com/disco/](http://releases.ubuntu.com/disco/) It didn't boot. Pressing escape on the purple ubuntu screen showed all failed and error. Shaky photo of screen attached.

I'll try the daily one here next [http://iso.qa.ubuntu.com/qatracker/milestones/404/builds/198855/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/404/builds/198855/downloads)

I'd still be very interested to know more about the kernal hacking. Looks like the bit I need to change is purely for the wifi card.... Be hard to break it worse and while a reinstall after breaking stuff would be annoying, not the end of the world. I might learn stuff.

I can always keep using my $30 slow-fi dongle, or get a pci card to get me through till 20.04lts comes out. As a fallback plan.

[ATTACH=CONFIG]283957[/ATTACH]

---

### Post by praseodym on 2019-09-07
Obviously a typo in the first post for installing. Do the instruction line by line

Same like this?!

[https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604](https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604)

---

### Post by mongrel-shark on 2019-09-07
Ok I got live usb Eaon Disco Dingo running. Wifi worked, mostly, some power  saving bugs/fetures turned it off. So can't have any sleep or screen time out  options enabled. Thats possibly not a deal-breaker, but most of the stuff I need  for work was not well supported. I'll have another look today, because  the dingo is far superior to the beaver IMO.

If I can get  Freecad, 3 versions, Legacy, Stable 0.18.1 and Daily are required.  Inkscape, Gimp and Blender alll running well with latest versions. I could  possibly dingo until 20.04 comes out. Although I don't know about the  lack of menu bars... I had to mod firefox to bring it back as many  functions otherwise unavailable. And freecad 0.18 is the latest I could  get without annoying the dev's on the forum or compiling from source. No 0.18.1. ppa or snap....

I'll have another play soon. See how I feel about it all.




> **praseodym said:**
> Obviously a typo in the first post for installing. Do the instruction line by line

Same like this?!

[https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604](https://ubuntuforums.org/showthread.php?t=2387339&page=2&p=13759604#post13759604)

Typo not obvious to me. Would be great if someone could clarify what those commands actually do and where the typo was. Looks like its working for a few people with minimal drama. wifi on LTS Ubuntu is still the preferred solution here. As mentioned if it breaks stuff I'll either live usb and undo the changes (Which would be hard if I copy paste comands with blind faith) or reinstall. I can't see any hardware damage happening if I am ready to power off if things hang.

---

### Post by mongrel-shark on 2019-09-07
oh p.s. I have the correct backport file iwlwifi-cc-a0-46.ucode downloaded. Can I skip the whole git part?

---

### Post by chili555 on 2019-09-07
> **mongrel-shark said:**
> oh p.s. I have the correct backport file iwlwifi-cc-a0-46.ucode downloaded. Can I skip the whole git part?The git part is the actual driver. The ucode part is the firmware required by the driver. *Both *are required.

jeremy31's post in the link is perfect. I suggest that you proceed.

---

### Post by mongrel-shark on 2019-09-08
I did the backport. Now my dongle dosent work either. How do I undo what I did?

---

### Post by mongrel-shark on 2019-09-08
Oh also no updates after I did backport. The instructions said to do stuff after a kernal update, but never got any updates. Currently only have internet via cat5

---

### Post by jeremy31 on 2019-09-08
Post results for ```
rfkill list; dmesg | grep iwl
```

---

### Post by mongrel-shark on 2019-09-08
```
:~$ rfkill list; dmesg | grep iwl
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    3.792561] Loading modules backported from iwlwifi
[    3.792562] iwlwifi-stack-public:master:8042:654c426c
[    3.806767] iwlwifi 0000:04:00.0: enabling device (0000 -> 0002)
[    3.812152] iwlwifi 0000:04:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    3.812533] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-52.ucode failed with error -2
[    3.812643] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-51.ucode failed with error -2
[    3.812737] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-50.ucode failed with error -2
[    3.812746] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-49.ucode failed with error -2
[    3.812751] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-48.ucode failed with error -2
[    3.812757] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-47.ucode failed with error -2
[    3.812762] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-46.ucode failed with error -2
[    3.812767] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-45.ucode failed with error -2
[    3.812772] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-44.ucode failed with error -2
[    3.812777] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-43.ucode failed with error -2
[    3.812782] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-42.ucode failed with error -2
[    3.812872] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-41.ucode failed with error -2
[    3.812879] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-40.ucode failed with error -2
[    3.812884] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-cc-a0-39.ucode failed with error -2
[    3.812885] iwlwifi 0000:04:00.0: no suitable firmware found!
[    3.812887] iwlwifi 0000:04:00.0: minimum version required: iwlwifi-cc-a0-39
[    3.812888] iwlwifi 0000:04:00.0: maximum version supported: iwlwifi-cc-a0-52
[    3.812890] iwlwifi 0000:04:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
[    7.338683] WARNING: CPU: 0 PID: 433 at /home/mongrel/backport-iwlwifi/net/wireless/core.c:866 wiphy_register+0xae3/0xaf0 [cfg80211]
[    7.338683] Modules linked in: rtl8xxxu(+) mac80211(OE) bnep nls_iso8859_1 edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi kvm snd_seq_midi_event snd_rawmidi irqbypass crct10dif_pclmul crc32_pclmul snd_seq ghash_clmulni_intel snd_seq_device btusb snd_timer pcbc iwlwifi(OE) btrtl btbcm btintel snd bluetooth aesni_intel cfg80211(OE) aes_x86_64 crypto_simd glue_helper cryptd joydev input_leds wmi_bmof i2c_piix4 ecdh_generic compat(OE) soundcore shpchp mac_hid parport_pc ppdev lp parport autofs4 hid_generic uas usb_storage usbhid hid amdkfd amd_iommu_v2 amdgpu mxm_wmi chash ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops igb drm dca ahci i2c_algo_bit libahci ptp nvme pps_core nvme_core
[  137.813398] WARNING: CPU: 8 PID: 153 at /home/mongrel/backport-iwlwifi/net/wireless/core.c:866 wiphy_register+0xae3/0xaf0 [cfg80211]
[  137.813399] Modules linked in: nls_utf8 isofs rtl8xxxu mac80211(OE) bnep nls_iso8859_1 edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi kvm snd_seq_midi_event snd_rawmidi irqbypass crct10dif_pclmul crc32_pclmul snd_seq ghash_clmulni_intel snd_seq_device btusb snd_timer pcbc iwlwifi(OE) btrtl btbcm btintel snd bluetooth aesni_intel cfg80211(OE) aes_x86_64 crypto_simd glue_helper cryptd joydev input_leds wmi_bmof i2c_piix4 ecdh_generic compat(OE) soundcore shpchp mac_hid parport_pc ppdev lp parport autofs4 hid_generic uas usb_storage usbhid hid amdkfd amd_iommu_v2 amdgpu mxm_wmi chash ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops igb drm dca ahci i2c_algo_bit libahci ptp nvme pps_core


```


Should I manually upgrade my kernal? Was just reading how, not sure if I should..... I'm running 4.15

---

### Post by jeremy31 on 2019-09-08
Try ```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-cc-a0-48.ucode
```
Reboot

---

### Post by mongrel-shark on 2019-09-08
WOOOHOOOO

It works!!

If you can see this post I got the mobo wifi working. cat5 and dongle not plugged in :D


Everything seems stable so far.

Thanks a million to all that offered advice and assistance.

Making this thread as solved. 
But...
I have a few remaining questions.

1. I'm not sure if my dongle still  works if I ever need a backup would be nice to know its available. Should something happen to my mobo wifi.
How can I see if its still available? 
I did
 
 ```
:~$ sudo lshw -C network
[sudo] password for mongrel: 
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 1a
       serial: dc:fb:48:00:2e:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-60-generic firmware=48.4fa0041f.0 ip=10.0.0.8 latency=0 link=yes multicast=yes
       resources: irq:73 memory:fca00000-fca03fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 03
       serial: b4:2e:99:3e:ff:e4
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:fc900000-fc91ffff ioport:f000(size=32) memory:fc920000-fc923fff
```

Cant see it there.Possibly because Ubuntu prefers the mobo wifi, or possibly because the driver for the dongle is no longer getting loaded?
The dongle is a d-link DWA-131. I seem to remember having to do some firmware related stuff to get it to work. Thread I used was [https://ubuntuforums.org/showthread.php?t=2351720&page=2](https://ubuntuforums.org/showthread.php?t=2351720&page=2).
Am I correct to think I could repeat that process to re-enable my dongle, possibly also disabling mobo wifi?




2. Is there anything else I should be aware of when doing sysadmin type stuff on this pc after todays efforts?

My current understanding is that I am now using drivers that where made for kernal 5.1 and later, which (may?) have been modified to allow backporting to earlier kernals. Would this be rougly correct?



Finally
I'd love to learn more about linux stuff. I got really good with win-7 years ago, because I had to fix stuff constantly. Since shifting to  Ubuntu some 6 years ago. I hardly ever have to fix stuff, so not getting  the chance to learn like before. If someone could take the time to  explain in more detail what I was doing with these changes I would greatly appreciate  it. Over the last 6 years I have gotten a basic to fair idea of how the  system works, but I'm hopeless with CLI commands. I can copy past like a  pro (and even understand vaguely what I am doing), but when I try stuff  on my own I get 80% typo/syntax problems lol. (link to a basic cheat  sheet with common file navigation and useful system tasks would be  amazing. I've googled this many times, but not found anything great yet,  everything assumes I know more than I do. I'd be very happy to find  something with fairly detailed explanations. even if more of a book that  a sheet....)

---

### Post by jeremy31 on 2019-09-09
You could try ```
cd backport-iwlwifi
sudo make uninstall
cd ~
wget https://cdn.kernel.org/pub/linux/kernel/projects/backports/stable/v5.3-rc4/backports-5.3-rc4-1.tar.gz
tar -zxvf backports-5.3-rc4-1.tar.gz
cd backports-5.3-rc4-1
make defconfig-wifi
make
sudo make install
```
Reboot and see if the Intel and the USB wifi work

---

### Post by mongrel-shark on 2019-09-12
Sigh. Its gone down again. I haven't changed anything, but did get new Linux Kernel update. Guessing that's what broke it.

I'm back on the dongle. It worked so that's a win.
```

 sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fca00000-fca03fff
  *-network
       description: Ethernet interface
       product: I211 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 03
       serial: b4:2e:99:3e:ff:e4
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.4.0-k firmware=0. 6-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:24 memory:fc900000-fc91ffff ioport:f000(size=32) memory:fc920000-fc923fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:4
       logical name: wlx00ad244a2b28
       serial: 00:ad:24:4a:2b:28
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-62-generic firmware=N/A ip=10.0.0.4 link=yes multicast=yes wireless=IEEE 802.11
```

I tried jeremy31's way. That looked good at first, but returned a lot of fails for the last three steps.
```

mongrel@CADboss:~/backports-5.3-rc4-1$ make defconfig-wifi
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
lex -ozconf.lex.c -L zconf.l
make[2]: lex: Command not found
Makefile:23: recipe for target 'zconf.lex.c' failed
make[2]: *** [zconf.lex.c] Error 127
Makefile.real:41: recipe for target 'defconfig-wifi' failed
make[1]: *** [defconfig-wifi] Error 2
Makefile:40: recipe for target 'defconfig-wifi' failed
make: *** [defconfig-wifi] Error 2
mongrel@CADboss:~/backports-5.3-rc4-1$ make
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-ar5523
|     make defconfig-ath10k
|     make defconfig-ath5k
|     make defconfig-ath6kl
|     make defconfig-ath9k
|     make defconfig-ath9k-debug
|     make defconfig-b43
|     make defconfig-b43legacy
|     make defconfig-brcmfmac
|     make defconfig-brcmsmac
|     make defconfig-carl9170
|     make defconfig-cw1200
|     make defconfig-hwsim
|     make defconfig-iwlwifi
|     make defconfig-libertas
|     make defconfig-libertas_tf
|     make defconfig-mwifiex
|     make defconfig-mwl8k
|     make defconfig-rtlwifi
|     make defconfig-wcn36xx
|     make defconfig-wifi
|     make defconfig-wil6210
|     make defconfig-wwan
\--
Makefile.real:45: recipe for target '.config' failed
make[2]: *** [.config] Error 1
Makefile:40: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
Makefile:30: recipe for target 'default' failed
make: *** [default] Error 2
mongrel@CADboss:~/backports-5.3-rc4-1$ sudo make install
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-ar5523
|     make defconfig-ath10k
|     make defconfig-ath5k
|     make defconfig-ath6kl
|     make defconfig-ath9k
|     make defconfig-ath9k-debug
|     make defconfig-b43
|     make defconfig-b43legacy
|     make defconfig-brcmfmac
|     make defconfig-brcmsmac
|     make defconfig-carl9170
|     make defconfig-cw1200
|     make defconfig-hwsim
|     make defconfig-iwlwifi
|     make defconfig-libertas
|     make defconfig-libertas_tf
|     make defconfig-mwifiex
|     make defconfig-mwl8k
|     make defconfig-rtlwifi
|     make defconfig-wcn36xx
|     make defconfig-wifi
|     make defconfig-wil6210
|     make defconfig-wwan
\--
Makefile.real:45: recipe for target '.config' failed
make[1]: *** [.config] Error 1
Makefile:40: recipe for target 'install' failed
make: *** [install] Error 2

```

Any suggestions welcome.

---

### Post by jeremy31 on 2019-09-12
Try a ```
make clean && sudo make install
```

---

### Post by mongrel-shark on 2019-09-14
Looks like I need to configure something before thats going to work.

I can't see my AW200 in the list....

```
mongrel@CADboss:~/backports-5.3-rc4-1$ make clean && sudo make install
[sudo] password for mongrel: 
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-ar5523
|     make defconfig-ath10k
|     make defconfig-ath5k
|     make defconfig-ath6kl
|     make defconfig-ath9k
|     make defconfig-ath9k-debug
|     make defconfig-b43
|     make defconfig-b43legacy
|     make defconfig-brcmfmac
|     make defconfig-brcmsmac
|     make defconfig-carl9170
|     make defconfig-cw1200
|     make defconfig-hwsim
|     make defconfig-iwlwifi
|     make defconfig-libertas
|     make defconfig-libertas_tf
|     make defconfig-mwifiex
|     make defconfig-mwl8k
|     make defconfig-rtlwifi
|     make defconfig-wcn36xx
|     make defconfig-wifi
|     make defconfig-wil6210
|     make defconfig-wwan
\--
Makefile.real:45: recipe for target '.config' failed
make[1]: *** [.config] Error 1
Makefile:40: recipe for target 'install' failed
make: *** [install] Error 2
```
Tried 
```

mongrel@CADboss:~/backports-5.3-rc4-1$ make defconfig-iwlwifi
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
lex -ozconf.lex.c -L zconf.l
make[2]: lex: Command not found
Makefile:23: recipe for target 'zconf.lex.c' failed
make[2]: *** [zconf.lex.c] Error 127
Makefile.real:41: recipe for target 'defconfig-iwlwifi' failed
make[1]: *** [defconfig-iwlwifi] Error 2
Makefile:40: recipe for target 'defconfig-iwlwifi' failed
make: *** [defconfig-iwlwifi] Error 2

```

---

### Post by mongrel-shark on 2019-09-14
Re ran this 
```

cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install

```

Rebooted to do second step and it was working.

I guess I might have to re-do this sometimes after and update? Is that the best way, or should I do a make clean first?

---

### Post by mongrel-shark on 2020-01-31
Ok so things have been working great for a few months.

New kernel updates break my backport install, but running

```
cd backport-iwlwifi
make clean
make defconfig-iwlwifi-public
make -j4
sudo make install
```

followed by reboot gets it working again.

until kernel 4.15.0-74 and 0-76 After doing the reboot the system freezes upon login. I type password, hit enter and everything is frozen. I have to hard reboot and use grub to boot from 4.15.0-72. or earlier.

Tried this also
```
:~/backport-iwlwifi$ update-initramfs -u
ln: failed to create hard link '/boot/initrd.img-4.15.0-76-generic.dpkg-bak' => '/boot/initrd.img-4.15.0-76-generic': Operation not permitted
cp: cannot create regular file '/boot/initrd.img-4.15.0-76-generic.dpkg-bak': Permission denied

```

So far I am still stuck on 4.15.0-72.

I saw (sorry cant find page again to provide link) there is a new ppa for iwlwif for 18.04 as of 2020. I wonder if this works in 16.04 also or if there is a 16.04 version?

Any ideas welcome.

note i can't use ubuntu 18-19 as most of my work programs need menu bars to work and are not compatible with those releases. I am waiting on the roomerd 20.04 to bring back menubar support for programs like freecad, inkscape and firefox. I also strongly prefer stable releases, as I don't have time or skills to be fixing stuff constantly. I just want a stable open source OS thats not windoze or mac..... Perhaps its time to move away from ubuntu?

---

### Post by mongrel-shark on 2020-01-31
quick update.

I found the post mentioning the new wilwifi backport ppa.[https://askubuntu.com/questions/1046589/backport-for-iwlwifi](https://askubuntu.com/questions/1046589/backport-for-iwlwifi)

also found the PPA [https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi](https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi)
which supports 16.04.

While booted into 4.15.0-72 kernal I have uninstalled my git version and installed the ppa version. Will reboot and report.


Also worth mentioning, I can access the later kernels in recovery mode and as a guest, but no wifi card detected. haven't tried the dongle or cat5, but they probably work.

---

### Post by mongrel-shark on 2020-01-31
Switching to PPA backport did the trick. I am now online in 4.15.0-76.

Hopefully I won't have issues with kernal updates making me reset the backport anymore. :p

For anyone else that's a linux dummy and had the same problem, my process went like this:

Use grub advanced menu to boot into last kernel with everything working, in my case this was 2 kernels back.

once ubuntu booted and logged in. Open terminal and:

```

cd backport-iwlwifi
sudo make uninstall

```
Note rebbot required to take effect, before rebooting add and install the ppa. While you still have working internet.
```
sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi
sudo apt-get update
sudo apt install backport-iwlwifi-dkms
```

now reboot into latest kernal (do nothing at grub screen). everything should work.

If you never did the manual backport then you just need to add the ppa and install. Using a dongle or network cable to get internet  :D

---

### Post by n-b-agostini on 2020-08-28
I have ran into similar issues. Wifi would sometimes work, sometimes stop working at after booting to Ubuntu in a dual boot system, which appeared to be random.

For me, the solution is to issue a Full Shutdown of Windows before booting into Ubuntu.
This can be done by holding the shift key and pressing the shutdown button, or by clicking restart.

If you do not do it, windows fast boot will remain enabled and I noticed two problems when booting on Ubuntu:
[LIST=1]
[*]My shared data partition is mounted as read only
[*]Wifi network card is not detected. Looking at the loaded modules, cfg80211 does not appear to load properly.
[/LIST]

Issuing a full shutdown on windows prevents the problem from happening.

My setup:
[LIST]
[*]Dual boot of windows 10 and ubuntu 20.04
[*]CPU:  AMD Ryzen 9 3900X
[*]Motherboard: Aorus x570 wifi pro
[*]Wifi hardware: Wi-Fi 6 AX200
[/LIST]

```
# Partitions on of my system:
/dev/nvme0n1p1     529M Windows recovery environment/dev/nvme0n1p2     100M EFI System
/dev/nvme0n1p3     16M Microsoft reserved
/dev/nvme0n1p4     194.7G Microsoft basic data
/dev/nvme0n1p5     556.7G Microsoft basic data (Shared partition between the 2 OS)
/dev/nvme0n1p6     201.9G Linux LVM  (with separate volumes for root and home)

```
```
When it is working:
$ lsmod | grep iwlwif
iwlwifi               331776  1 iwlmvm
cfg80211              704512  3 iwlmvm,iwlwifi,mac80211
```


```
$ modinfo iwlwifi
filename:       /lib/modules/5.4.0-42-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
...
firmware:       iwlwifi-cc-a0-50.ucode
...
depends:        cfg80211
name:           iwlwifi
vermagic:       5.4.0-42-generic SMP mod_unload 

```

```
$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Wi-Fi 6 AX200

```

Hope this helps other people.

---

### Post by CelticWarrior on 2020-08-28
Just disable Fast Startup in Windows. For a dual-boot it's a must.

---

