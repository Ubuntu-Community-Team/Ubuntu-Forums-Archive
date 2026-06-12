---
title: "Wi-fi disconnects after waking up from 'suspend'"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by yash_pal2 on 2014-05-22
OS: Ubuntu 14.04 AMD 64; dual boot with Windows 7
Laptop: Dell Inspiron-M5010 

When I wake up the computer from 'suspend', after more than 1[SIZE=1][SUP]1[/SUP]/[SUB]2[/SUB][/SIZE] -2 hours, the wi-fi connection does not come up, and 'enable networking' becomes unticked of its own accord but 'enable wi-fi' does not appear when I right click on the wi-fi applet on the top panel/menubar. I have to restart the computer and the wi-fi connection comes up. I feel this problem has come up after updating on or about 12 May when some updates were installed.

After installing Ubuntu 14.04 the wireless did not work and after a lot of searching on the web, I purged the broadcom proprietary driver and installed some other driver; wi-fi came to life; now it goes into coma.

Any solutions will be gratefully acknowledged; however I have no expertise in locating or amending the system files.

---

### Post by varunendra on 2014-05-22
Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
cat /var/log/pm-suspend.log
```
..after resuming from suspend.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by yash_pal2 on 2014-05-23
I give the output of the three commands, as suggested by you
```

   yashpal@yashpal-Inspiron-M5010:~$ uname -mr  
 3.13.0-24-generic x86_64  
 yashpal@yashpal-Inspiron-M5010:~$ lspci -nnk | grep -iA2 net  
 04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)  
     Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]  
     Kernel driver in use: bcma-pci-bridge  
 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
     Subsystem: Dell Device [1028:0448]  
     Kernel driver in use: r8169  
 yashpal@yashpal-Inspiron-M5010:~$  
 


 


 parport                42348  3 lp,ppdev,parport_pc  

 hid_generic            12548  0  
 usbhid                 52616  0  
 hid                   106148  2 hid_generic,usbhid  
 psmouse               102222  0  
 ahci                   25819  4  
 r8169                  67581  0  
 libahci                32168  1 ahci  
 mii                    13934  1 r8169  
              total       used       free     shared    buffers     cached  
 Mem:       4044780    1527144    2517636       6576      80028     780600  
 -/+ buffers/cache:     666516    3378264  
 Swap:      2928636          0    2928636  
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:  
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:  
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:  
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:  
 stop: Unknown instance:  
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:  
 Kernel modesetting video driver detected, not using quirks.  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:  
 kernel.acpi_video_flags = 0  
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.  
 


 Thu May 22 19:26:31 IST 2014: performing suspend  
 Thu May 22 20:31:28 IST 2014: Awake.  
 Thu May 22 20:31:28 IST 2014: Running hooks for resume  
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:  
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:  
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:  
 


 /dev/sda:  
  setting Advanced Power Management level to 0xfe (254)  
  APM_level    = 254  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:  
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:  
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:  
 Reloaded unloaded modules.  
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.  
  
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:  
 /etc/pm/sleep.d/10_grub-common resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:  
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:  
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:  
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.  
 


 Thu May 22 20:31:29 IST 2014: Finished.  
 Initial commandline parameters:  
 Thu May 22 21:05:22 IST 2014: Running hooks for suspend.  
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:  
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:  
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:  
 Linux yashpal-Inspiron-M5010 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  
 Module                  Size  Used by  
 ctr                    13049  0  
 ccm                    17773  0  
 bnep                   19624  2  
 rfcomm                 69160  8  
 snd_hda_codec_hdmi     46207  1  
 btusb                  32412  0  
 bluetooth             395423  22 bnep,btusb,rfcomm  
 arc4                   12608  2  
 brcmsmac              563041  0  
 cordic                 12574  1 brcmsmac  
 brcmutil               15618  1 brcmsmac  
 b43                   387371  0  
 mac80211              626489  2 b43,brcmsmac  
 uvcvideo               80885  0  
 videobuf2_vmalloc      13216  1 uvcvideo  
 videobuf2_memops       13362  1 videobuf2_vmalloc  
 videobuf2_core         40664  1 uvcvideo  
 videodev              134688  2 uvcvideo,videobuf2_core  
 cfg80211              484040  3 b43,brcmsmac,mac80211  
 ssb                    62379  1 b43  
 dell_wmi               12761  0  
 sparse_keymap          13948  1 dell_wmi  
 dell_laptop            18168  0  
 dcdbas                 14928  1 dell_laptop  
 snd_hda_codec_idt      54645  1  
 snd_hda_intel          52355  5  
 snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13602  1 snd_hda_codec  
 kvm_amd                59987  0  
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel  
 kvm                   451511  1 kvm_amd  
 snd_seq_midi           13324  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 snd_rawmidi            30144  1 snd_seq_midi  
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel  
 joydev                 17381  0  
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi  
 serio_raw              13462  0  
 edac_core              62291  0  
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi  
 edac_mce_amd           22617  0  
 k10temp                13126  0  
 snd_timer              29482  2 snd_pcm,snd_seq  
 sp5100_tco             13979  0  
 i2c_piix4              22155  0  
 snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi  
 radeon               1514165  3  
 bcma                   52096  3 b43,brcmsmac  
 ttm                    85115  1 radeon  
 drm_kms_helper         52758  1 radeon  
 soundcore              12680  1 snd  
 drm                   302817  5 ttm,drm_kms_helper,radeon  
 i2c_algo_bit           13413  1 radeon  
 wmi                    19177  1 dell_wmi  
 video                  19476  0  
 mac_hid                13205  0  
 parport_pc             32701  0  
 ppdev                  17671  0  
 lp                     17759  0  
 parport                42348  3 lp,ppdev,parport_pc  
 hid_generic            12548  0  
 usbhid                 52616  0  
 hid                   106148  2 hid_generic,usbhid  
 psmouse               102222  0  
 ahci                   25819  4  
 r8169                  67581  0  
 libahci                32168  1 ahci  
 mii                    13934  1 r8169  
              total       used       free     shared    buffers     cached  
 Mem:       4044780    2028468    2016312      27848      85184     857728  
 -/+ buffers/cache:    1085556    2959224  
 Swap:      2928636          0    2928636  
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:  
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:  
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:  
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:  
 stop: Unknown instance:  
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:  
 Kernel modesetting video driver detected, not using quirks.  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:  
 kernel.acpi_video_flags = 0  
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.  
 


 Thu May 22 21:05:23 IST 2014: performing suspend  
 Thu May 22 22:06:43 IST 2014: Awake.  
 Thu May 22 22:06:43 IST 2014: Running hooks for resume  
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:  
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:  
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:  
 


 /dev/sda:  
  setting Advanced Power Management level to 0xfe (254)  
  APM_level    = 254  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:  
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:  
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:  
 Reloaded unloaded modules.  
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:  
 /etc/pm/sleep.d/10_grub-common resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:  
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:  
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:  
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.  
 


 Thu May 22 22:06:44 IST 2014: Finished.  
 Initial commandline parameters:  
 Fri May 23 07:04:00 IST 2014: Running hooks for suspend.  
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:  
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:  
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:  
 Linux yashpal-Inspiron-M5010 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux  
 Module                  Size  Used by  
 ctr                    13049  0  
 ccm                    17773  0  
 rfcomm                 69160  8  
 bnep                   19624  2  
 snd_hda_codec_hdmi     46207  1  
 btusb                  32412  0  
 bluetooth             395423  22 bnep,btusb,rfcomm  
 arc4                   12608  2  
 brcmsmac              563041  0  
 cordic                 12574  1 brcmsmac  
 brcmutil               15618  1 brcmsmac  
 b43                   387371  0  
 mac80211              626489  2 b43,brcmsmac  
 cfg80211              484040  3 b43,brcmsmac,mac80211  
 dell_wmi               12761  0  
 ssb                    62379  1 b43  
 sparse_keymap          13948  1 dell_wmi  
 uvcvideo               80885  0  
 snd_seq_midi           13324  0  
 videobuf2_vmalloc      13216  1 uvcvideo  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 videobuf2_memops       13362  1 videobuf2_vmalloc  
 videobuf2_core         40664  1 uvcvideo  
 videodev              134688  2 uvcvideo,videobuf2_core  
 snd_rawmidi            30144  1 snd_seq_midi  
 dell_laptop            18168  0  
 snd_hda_codec_idt      54645  1  
 dcdbas                 14928  1 dell_laptop  
 snd_hda_intel          52355  5  
 snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel  
 snd_hwdep              13602  1 snd_hda_codec  
 kvm_amd                59987  0  
 kvm                   451511  1 kvm_amd  
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi  
 radeon               1514165  3  
 joydev                 17381  0  
 snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel  
 serio_raw              13462  0  
 ttm                    85115  1 radeon  
 edac_core              62291  0  
 k10temp                13126  0  
 edac_mce_amd           22617  0  
 sp5100_tco             13979  0  
 i2c_piix4              22155  0  
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel  
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi  
 drm_kms_helper         52758  1 radeon  
 snd_timer              29482  2 snd_pcm,snd_seq  
 snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi  
 drm                   302817  5 ttm,drm_kms_helper,radeon  
 soundcore              12680  1 snd  
 bcma                   52096  3 b43,brcmsmac  
 i2c_algo_bit           13413  1 radeon  
 wmi                    19177  1 dell_wmi  
 parport_pc             32701  0  
 ppdev                  17671  0  
 video                  19476  0  
 lp                     17759  0  
 parport                42348  3 lp,ppdev,parport_pc  
 mac_hid                13205  0  
 hid_generic            12548  0  
 usbhid                 52616  0  
 hid                   106148  2 hid_generic,usbhid  
 ahci                   25819  4  
 libahci                32168  1 ahci  
 psmouse               102222  0  
 r8169                  67581  0  
 mii                    13934  1 r8169  
              total       used       free     shared    buffers     cached  
 Mem:       4044780    1812228    2232552       7492     121388     947148  
 -/+ buffers/cache:     743692    3301088  
 Swap:      2928636          0    2928636  
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:  
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:  
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:  
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:  
 stop: Unknown instance:  
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:  
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:  
 Kernel modesetting video driver detected, not using quirks.  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:  
 kernel.acpi_video_flags = 0  
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.  
 


 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.  
 


 Fri May 23 07:04:00 IST 2014: performing suspend  
 Fri May 23 13:21:26 IST 2014: Awake.  
 Fri May 23 13:21:26 IST 2014: Running hooks for resume  
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:  
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:  
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:  
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:  
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:  
 


 /dev/sda:  
  setting Advanced Power Management level to 0x80 (128)  
  APM_level    = 128  
 


 /dev/sda:  
  setting standby to 36 (3 minutes)  
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:  
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:  
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:  
 /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.  
 


 Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:  
 Reloaded unloaded modules.  
 /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:  
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:  
 /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:  
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.  
 


 Running hook /etc/pm/sleep.d/10_grub-common resume suspend:  
 /etc/pm/sleep.d/10_grub-common resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:  
 /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:  
 /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.  
  
 Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:  
 /usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.  
 


 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:  
 /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.  
 


 Fri May 23 13:21:26 IST 2014: Finished.  
 yashpal@yashpal-Inspiron-M5010:~$  

```

Thanks for telling me how to use code, I always wondered how others did it.
The output of:                       cat /var/log/pm-suspend.log
starts from parport                42348  3 lp,ppdev,parport_pc

---

### Post by varunendra on 2014-05-23
> **yash_pal2 said:**
> ```

 brcmsmac              563041  0  
 cordic                 12574  1 brcmsmac  
 brcmutil               15618  1 brcmsmac  
 **[COLOR="#FF0000"]b43[/COLOR]**                   387371  0  
 mac80211              626489  2 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac  
 cfg80211              484040  3 **[COLOR="#FF0000"]b43[/COLOR]**,brcmsmac,mac80211  

```

As highlighted above, the "b43" driver is loading unnecessarily it seems. Have you done anything to make it load at startup? If yes, undo that, we don't want b43 for your card. It is only conflicting with the correct driver "brcmsmac" for resources.

If you are sure you have done no manual tweaking anywhere to make it load, try blacklisting it -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and check -
```
lsmod | egrep 'b43|brcm|ssb'
```
You shouldn't see "b43" or "ssb" in the output, only "brcmsmac" (and its supporting drivers). If so, is the problem solved?

---

### Post by yash_pal2 on 2014-05-23
Thanks. I did all that was suggested by you and after restarting the computer, the output of
```

   [COLOR=#9900ff][COLOR=#990099]lsmod[/COLOR] | egrep 'b43|brcm|ssb'[/COLOR]

```

did not contain    
[COLOR=#990099]"b43" or "ssb" in the output, only "brcmsmac" and (hopefully) its supporting drivers[/COLOR]. Total 6 lines of output.

I hope the problem is solved and will be known after about 3 hours when I again awake it from 'suspend'.

I donot manually configure anything nor install *anything *from PPAs as I have no expertise in repairing the OS if it is broken. I would also like to add that 98% of new users will be like me if use of Linux/ Debian/Red Hat/BSD and derivatives grows.

---

### Post by yash_pal2 on 2014-05-24
Woke up the computer after about 3 hours under 'suspend'. Wi-Fi came up. Problem appears to be resolved.
Solved. Many Thanks to the Sea God.

---

### Post by varunendra on 2014-05-24
Congratulations from the 'Sea God' ! :D

Hope the fix is permanent, but feel free to bump the thread if the problem returns. :)

---

### Post by marcelpaulo on 2014-11-24
Hey there, Varun !

I hope I'm not doing the wrong thing hijacking this already solved thread. If the correct etiquette is opening a new thread, please let me know and I'll gladly do it. This is my very first post in this forum, so I fear disrespecting the forum etiquette.

I'm bumping into exactly the same problem as the OP, even though my environment is different: a fresh Xubuntu 14.10 installed 3 days ago, and my wireless card is different. Your comments were immensely helpful, pointed me to the right direction to dig into the problem.

Here are my networking devices:

```

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:04b0]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi

```

and here my kernel version:

```

3.16.0-24-generic x86_64

```

I ran lsmod after rebooting the machine, and diff'ed the output with the modules list from /var/log/pm-suspend.log:

```

paulo@monk:~/tmp$ diff resume now
2,3c2,4
< ctr                    13049  0 
< ccm                    17731  0 
---
> ums_realtek            18045  0 
> ctr                    13049  2 
> ccm                    17731  2 
83c84
< i915                  917618  3 
---
> i915                  917618  4 
87c88
< drm                   310919  5 i915,drm_kms_helper
---
> drm                   310919  6 i915,drm_kms_helper
101c102
< usb_storage            66398  1 uas
---
> usb_storage            66398  2 uas,ums_realtek
110d110
< 

```


The only significant difference I can see is module **ums_realtek**: it was loaded after the reboot but not after the suspend.

I should point out that, just like the OP, if I suspend the machine and resume it straight away, the error doesn't happen. I suspended it last night before going to bed, and resumed it when I woke up today, and the error happened. It seems to happen only when the interval between suspend and resume is large enough, not sure how large (the OP mentions more than 1-1½ hours).

Now I'm kind of clueless on how to move forward debugging this. I'll be immensely thankful if you could point me to the right direction.

Paulo

---

### Post by marcelpaulo on 2014-11-24
PS: I forgot to mention that I have TLP installed, following [these instructions]("http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html"). I'm using the defaults, not tweaked in any way, here's the output from /etc/default/tlp:

```

# ------------------------------------------------------------------------------
# tlp - Parameters for power save


# Hint: some features are disabled by default, remove the leading # to enable them


# Set to 0 to disable/1 to enable TLP
TLP_ENABLE=1


# Seconds laptop mode has to to wait after the disk goes idle before doing a sync.
# Non-zero value enables, zero disables laptop mode.
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2


# Dirty page values (timeouts in secs).
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60


# Select a cpu frequency scaling governor: ondemand/powersave/performance/conservative
# Intel Core i processor with intel_pstate driver: powersave/performance 
# Important:
# - You *must* disable your distribution's governor settings or conflicts will occur
# - ondemand is sufficient for *almost all* workloads, you should know what you're doing!
#CPU_SCALING_GOVERNOR_ON_AC=ondemand
#CPU_SCALING_GOVERNOR_ON_BAT=ondemand


# Set the min/max frequency available for the scaling governor.
# Possible values strongly depend on your cpu. For available frequencies see
# tlp-stat output, Section "+++ Processor".
# Hint: Parameters are disabled by default, remove the leading # to enable them,
#       otherwise kernel default values are used.
#CPU_SCALING_MIN_FREQ_ON_AC=0
#CPU_SCALING_MAX_FREQ_ON_AC=0
#CPU_SCALING_MIN_FREQ_ON_BAT=0
#CPU_SCALING_MAX_FREQ_ON_BAT=0


# Set the cpu "turbo boost" feature: 0=disable / 1=allow
# Requires an Intel Core i processor and kernel 3.7 or later.
# Important:
# - This may conflict with your distribution's governor settings
# - A value of 1 does *not* activate boosting, it just allows it
#CPU_BOOST_ON_AC=1
#CPU_BOOST_ON_BAT=0


# Minimize number of used cpu cores/hyper-threads under light load conditions
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1


# Kernel NMI Watchdog
# 0=disable (default, saves power) / 1=enable (for kernel debugging only)
NMI_WATCHDOG=0


# Change CPU voltages aka "undervolting" - Kernel with PHC patch required
# Freq:voltage pairs are written to /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
# CAUTION: only use this, if you thoroughly understand what you are doing!
#PHC_CONTROLS="F:V F:V F:V F:V"


# Hard disk devices, separate multiple devices with spaces (default: sda).
# Devices can be specified by disk id too (lookup with: tlp diskid).
DISK_DEVICES="sda sdb"


# Hard disk advanced power management level: 1(max saving)..254(off)
# Levels 1..127 may spin down the disk.
# Separate values for multiple devices with spaces.
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"


# Hard disk spin down timeout:
# 0:        spin down disabled
# 1..240:   timeouts from 5s to 20min (in units of 5s)
# 241..251: timeouts from 30min to 5.5 hours (in units of 30min)
# (see 'man hdparm' for details)
#DISK_SPINDOWN_TIMEOUT_ON_AC="0 0"
#DISK_SPINDOWN_TIMEOUT_ON_BAT="0 0"


# Select io scheduler for the disk devices: noop/deadline/cfq (Default: cfq)
# Separate values for multiple devices with spaces.
#DISK_IOSCHED="cfq cfq"


# SATA aggressive link power management (ALPM):
# min_power/medium_power/max_performance
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power


# PCI Express Active State Power Management (PCIe ASPM):
# default/performance/powersave
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave


# Radeon graphics clock speed (profile method): low/mid/high/auto/default
# auto = mid on BAT, high on AC; default = use hardware defaults
# (Kernel >= 2.6.35 only, not with fglrx driver!)
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low


# New radeon dynamic power management method (dpm): battery/performance
# (Kernel >= 3.11 only, requires boot option radeon.dpm=1)
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery


# New radeon dpm performance level: auto/low/high (auto is recommended)
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto


# WiFi power saving mode: 1=disable/5=enable
# (Linux 2.6.32 and later, some adapters only!)
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5


# Disable wake on lan: Y/N
WOL_DISABLE=Y


# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).
# A value of 0 disables / >=1 enables power save.
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=1


# Disable controller too (HDA only): Y/N
SOUND_POWER_SAVE_CONTROLLER=Y


# Set to 1 to power off optical drive in UltraBay/MediaBay when running
# on battery. A value of 0 disables this Feature (Default).
# Drive can be powered on again by releasing (and reinserting) the
# eject lever or by pressing the disc eject button on newer models.
# Note: an UltraBay/MediaBay hard disk is never powered off.
BAY_POWEROFF_ON_BAT=0
# Optical drive device to power off (default sr0)
BAY_DEVICE="sr0"


# Runtime Power Management for pci(e) bus devices
# (Kernel >= 2.6.35 only): on=disable/auto=enable
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto


# Runtime PM for *all* pci(e) bus devices, except blacklisted ones:
# 0=disable / 1=enable
RUNTIME_PM_ALL=1


# Exclude pci(e) device adresses the following list from Runtime PM
# (separate with spaces). Use lspci to get the adresses (1st column).
#RUNTIME_PM_BLACKLIST="bb:dd.f 11:22.3 44:55.6"


# Set to 0 to disable/1 to enable usb autosuspend feature
USB_AUTOSUSPEND=1


# Devices from the following list are excluded from usb autosuspend
# (separate with spaces). Use lsusb to get the ids.
# Note: input devices (usbhid) are excluded automatically
#USB_BLACKLIST="1111:2222 3333:4444"


# WWAN devices are excluded from usb autosuspend:
# 0=do not exclude / 1=exclude
# Note: works for ids 05c6:* 0bdb:* 1199:* only
USB_BLACKLIST_WWAN=1


# Set to 1 to disable autosuspend before shutdown/0 to do nothing
# (workaround for usb devices that cause shutdown problems)
#USB_AUTOSUSPEND_DISABLE_ON_SHUTDOWN=1


# Restore radio device state (bluetooth, wifi, wwan) from previous shutdown
# on system startup: 0=disable/1=enable
# Hint: the parameters DEVICES_TO_DISABLE/ENABLE_ON_STARTUP/SHUTDOWN below
#       are ignored when this is enabled!
RESTORE_DEVICE_STATE_ON_STARTUP=0


# Radio devices to disable on startup: bluetooth wifi wwan
#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wifi wwan"


# Radio devices to enable on startup: bluetooth wifi wwan
#DEVICES_TO_ENABLE_ON_STARTUP="wifi"


# Radio devices to disable on shutdown: bluetooth wifi wwan
# (workaround for devices that are blocking shutdown)
#DEVICES_TO_DISABLE_ON_SHUTDOWN="bluetooth wifi wwan"


# Radio devices to enable on shutdown: bluetooth wifi wwan
# (to prevent other operating systems from missing radios)
#DEVICES_TO_ENABLE_ON_SHUTDOWN="wwan"


# Battery charge thresholds (ThinkPad only, tp-smapi or acpi-call kernel module required)
# Charging starts when the remaining capacity falls below the START_CHARGE_TRESH
# value and stops when exceeding the STOP_CHARGE_TRESH value.
# Main battery (values in %)
#START_CHARGE_THRESH_BAT0=75
#STOP_CHARGE_THRESH_BAT0=80
# Ultrabay or slice battery (values in %)
#START_CHARGE_THRESH_BAT1=75
#STOP_CHARGE_THRESH_BAT1=80


# ------------------------------------------------------------------------------
# tlp-rdw - Parameters for the radio device wizard
# Possible devices: bluetooth/wifi/wwan


# Hint: parameters are disabled by default, remove the leading # to enable them


# Radio devices to disable on connect
#DEVICES_TO_DISABLE_ON_LAN_CONNECT="wifi wwan"
#DEVICES_TO_DISABLE_ON_WIFI_CONNECT="wwan"
#DEVICES_TO_DISABLE_ON_WWAN_CONNECT="wifi"


# Radio devices to enable on disconnect
#DEVICES_TO_ENABLE_ON_LAN_DISCONNECT="wifi wwan"
#DEVICES_TO_ENABLE_ON_WIFI_DISCONNECT=""
#DEVICES_TO_ENABLE_ON_WWAN_DISCONNECT=""


# Radio devices to enable/disable when docked
#DEVICES_TO_ENABLE_ON_DOCK=""
#DEVICES_TO_DISABLE_ON_DOCK=""


# Radio devices to enable/disable when undocked
#DEVICES_TO_ENABLE_ON_UNDOCK="wifi"
#DEVICES_TO_DISABLE_ON_UNDOCK=""

```

---

