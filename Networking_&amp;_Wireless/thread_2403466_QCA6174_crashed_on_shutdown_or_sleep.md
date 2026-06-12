---
title: "QCA6174 crashed on shutdown or sleep"
date: 2018-10-11
forum: Networking &amp; Wireless
---

### Post by think.more on 2018-10-11
[COLOR=#333333][FONT=Ubuntu]I am having a problem. I just can't suspend laptop or shutdown, it gets stuck. I narrowed down the cause and it appears it is my wireless card, Killer 1525 and QCA6174 firmware drivers. If I switch off wifi before sleeping or shutting down, laptop doesn't get stuck. Now I am on Ubuntu 18.10, kernel 4.18, everything is updated to newest current version on newest firmware 1.175, but the problem persist. Previously I was on ubuntu 18.04, had same problem on older firmware 1.173, I updated Ubuntu version just to see if it fixes the problem. I also tried files in this repository: [https://github.com/kvokka/msi_gs60/tree/master/wifi](https://github.com/kvokka/msi_gs60/tree/master/wifi). I also tried given files in Killer webpage: [https://www.killernetworking.com/killersupport/driver-downloads/kb/cat/6-linux#faq_80](https://www.killernetworking.com/killersupport/driver-downloads/kb/cat/6-linux#faq_80), but that too didn't help...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]This is excerpt from kernel log, after I close the lid:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Oct 9 19:18:15 linuxtownLaptop kernel: [ 128.693478] Call Trace:
Oct 9 19:18:15 linuxtownLaptop kernel: [ 128.693471] wpa_supplicant D 0 880 1 0x00000004
Oct 9 19:18:15 linuxtownLaptop kernel: [ 128.693336] Freezing of tasks failed after 20.003 seconds (1 tasks refusing to freeze, wq_busy=0):
Oct 9 19:18:15 linuxtownLaptop kernel: [ 127.808445] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
Oct 9 19:18:15 linuxtownLaptop kernel: [ 127.808437] atkbd serio0: Unknown key released (translated set 2, code 0x97 on isa0060/serio0).
Oct 9 19:18:15 linuxtownLaptop kernel: [ 127.805531] atkbd serio0: Use 'setkeycodes e017 <keycode>' to make it known.
Oct 9 19:18:15 linuxtownLaptop kernel: [ 127.805524] atkbd serio0: Unknown key pressed (translated set 2, code 0x97 on isa0060/serio0).
Oct 9 19:18:15 linuxtownLaptop kernel: [ 108.689468] Freezing user space processes ...
Oct 9 19:18:15 linuxtownLaptop kernel: [ 108.646879] rfkill: input handler enabled
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.403227] ath10k_pci 0000:05:00.0: failed to delete WMI vdev 1: -108
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.403192] ieee80211 phy0: Hardware restart was requested
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.285067] PM: Syncing filesystems ... done.
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.285065] PM: suspend entry (deep)
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272631] ath10k_pci 0000:05:00.0: [07]: 0x00036000 1 1 1 1
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272621] ath10k_pci 0000:05:00.0: [06]: 0x00035c00 15 15 15 15
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272612] ath10k_pci 0000:05:00.0: [05]: 0x00035800 0 0 0 0
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272603] ath10k_pci 0000:05:00.0: [04]: 0x00035400 833 833 226 162
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272593] ath10k_pci 0000:05:00.0: [03]: 0x00035000 7 7 8 7
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272584] ath10k_pci 0000:05:00.0: [02]: 0x00034c00 44 44 107 108
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272575] ath10k_pci 0000:05:00.0: [01]: 0x00034800 2 2 37 38
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272565] ath10k_pci 0000:05:00.0: [00]: 0x00034400 1 1 3 3
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272555] ath10k_pci 0000:05:00.0: Copy Engine register dump:
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272553] ath10k_pci 0000:05:00.0: [56]: 0x809A6C34 0x0041A8E0 0x0042932C 0x0042CA44
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272550] ath10k_pci 0000:05:00.0: [52]: 0x800B4405 0x0041A850 0x00422318 0x00005002
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272548] ath10k_pci 0000:05:00.0: [48]: 0x80996BD3 0x0041A830 0x0044FD68 0x00000000
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272545] ath10k_pci 0000:05:00.0: [44]: 0x80992076 0x0041A810 0x0044FD68 0x0046FFE8
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272543] ath10k_pci 0000:05:00.0: [40]: 0x8099638C 0x0041A7F0 0x00404D88 0x00000000
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272540] ath10k_pci 0000:05:00.0: [36]: 0x809BDECC 0x0041A7D0 0x00404D88 0x0040E074
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272538] ath10k_pci 0000:05:00.0: [32]: 0x80947BA7 0x0041A7B0 0x00404D88 0x0040E074
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272535] ath10k_pci 0000:05:00.0: [28]: 0x80942BC4 0x0041A790 0x42D0B71D 0x00400000
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272533] ath10k_pci 0000:05:00.0: [24]: 0x809432A7 0x0041A770 0x0040D400 0xC092E4DC
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272531] ath10k_pci 0000:05:00.0: [20]: 0x4092E4DC 0x0041A710 0x00000000 0x0F000000
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272528] ath10k_pci 0000:05:00.0: [16]: 0x0096BDBC 0x009286B6 0x00000000 0x00000000
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272525] ath10k_pci 0000:05:00.0: [12]: 0x00000009 0x00000000 0x0096C09C 0x0096C0A7
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272523] ath10k_pci 0000:05:00.0: [08]: 0x42D0B71D 0x00400000 0x00000000 0x000A5C88
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272520] ath10k_pci 0000:05:00.0: [04]: 0x0092E4DC 0x00060130 0x00000018 0x0041A760
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272518] ath10k_pci 0000:05:00.0: [00]: 0x05010000 0x00000000 0x0092E4DC 0x42D0B731
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.272512] ath10k_pci 0000:05:00.0: firmware register dump:
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.270500] ath10k_pci 0000:05:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.270497] ath10k_pci 0000:05:00.0: board_file api 2 bmi_id N/A crc32 ae2e275a
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.270310] ath10k_pci 0000:05:00.0: firmware ver SW_RM.1.1.1-00157-QCARMSWPZ-1 api 5 features ignore-otp,no-4addr-pad crc32 10bf8e08
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.269927] ath10k_pci 0000:05:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.269925] ath10k_pci 0000:05:00.0: qca6174 hw2.1 target 0x05010000 chip_id 0x003405ff sub 1a56:1525
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.269916] ath10k_pci 0000:05:00.0: firmware crashed! (guid 2c6b9eda-95ac-4f33-b915-414326bdcc36)
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.269913] wlp5s0: failed to remove key (0, a7:57:58:05:ad:44) from hardware (-110)
Oct 9 19:17:55 linuxtownLaptop kernel: [ 108.269908] ath10k_pci 0000:05:00.0: failed to install key for vdev 0 peer a7:57:58:05:ad:44: -110
What could I try next? I can't use my laptop if I can't put it to sleep and have to manually turn off wifi. I have killer wireless 1525. My card in lshw command[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]product: QCA6174 802.11ac Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]vendor: Qualcomm Atheros[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]And if I try to shutdown (with wifi on), this is what I see on screen and have to force shutdown: [https://i.stack.imgur.com/aTMgu.jpg](https://i.stack.imgur.com/aTMgu.jpg)[/FONT][/COLOR]

---

### Post by appolion on 2018-10-12
This started for me with kernel 4.9.  Right now I'm run 18.04 with kernel 4.4 and hibernation works.

My attempts at scripting disabling the wifi   have not worked


> /lib/systemd/system-sleep
> 
#!/bin/sh
case "$1" in
    pre)        
        #nmcli networking off
        #systemctl stop wpa_supplicant   
        #systemctl stop NetworkManager    
        modprobe -rf ath10k_pci
        sleep 10
        ;;
    post)
        #nmcli networking on
        # systemctl start NetworkManager
        # systemctl start wpa_supplicant
        modprobe ath10k_pci      
        echo 1 > /sys/bus/pci/rescan
        ;;
esac


---

### Post by appolion on 2018-12-21
There are two service files at /etc/systemd/system  wifi-sleep.serivce and wifi-resume.service.   Add the modprobe lines 

wifi-sleep.service
> 
[Unit]
Description=Stop networkmanager before sleep
Before=suspend.target
Before=hibernate.target
Before=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/sbin/modprobe -r ath10k_pci  
ExecStart=/bin/systemctl stop network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
  


wifi-resume.serivce
> 
[Unit]
Description=Enable networkmanager after sleep
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/sbin/modprobe ath10k_pci
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target


---

### Post by christian-va on 2019-10-10
[COLOR=#242729][FONT=Arial]Hi all,

same with me on Ubuntu 18.04.3, ath10k_pci driver qca6174 hw2.1.[/FONT][/COLOR][COLOR=#242729][FONT=Arial]Before upgrading from 16.04, all worked well.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]To give a few hints:

I tried to enable a Systemd 'Unit' for the sleep.target as mentioned in some posts, and also a script like the one above, but both did not work and the system freezed as usual.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However, when I do a manual 'sudo modprobe -r ath10k_pci' in a terminal, and suspend after the module was unloaded manually, the suspend works fine. 
The firmware will crash on unload (see output from dmesg below), but the system will not freeze.

So, it looks like the module is not unloaded like it is when I do that manually, or other suspend processes get started too fast.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**Can someone confirm that the "pre" part if these scripts get executed before anything else when suspending, and the system waits before proceeding to the sleep?**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Also, I noticed that the script in /lib/systemd/system-sleep does reload the driver on resume, so it only does not work before suspend.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas?


Output from dmesg for formware crash:
[/FONT][/COLOR]
[SIZE=2][  860.138040] wlp3s0: deauthenticating from c8:0e:14:dc:44:99 by local choice (Reason: 3=DEAUTH_LEAVING)[/SIZE]
[SIZE=2][  863.145513] ath10k_warn: 149 callbacks suppressed[/SIZE]
[SIZE=2][  863.145521] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer c8:0e:14:dc:44:99: -110[/SIZE]
[SIZE=2][  863.145527] wlp3s0: failed to remove key (0, c8:0e:14:dc:44:99) from hardware (-110)[/SIZE]
[SIZE=2][  863.150866] ath10k_pci 0000:03:00.0: firmware crashed! (guid e332d0dd-30ff-4046-86c9-2564e5f7ea1e)[/SIZE]
[SIZE=2][  863.150885] ath10k_pci 0000:03:00.0: qca6174 hw2.1 target 0x05010000 chip_id 0x003405ff sub 105b:e08e[/SIZE]
[SIZE=2][  863.150891] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0[/SIZE]
[SIZE=2][  863.152052] ath10k_pci 0000:03:00.0: firmware ver SW_RM.1.1.1-00157-QCARMSWPZ-1 api 5 features ignore-otp,no-4addr-pad crc32 10bf8e08[/SIZE]
[SIZE=2][  863.152644] ath10k_pci 0000:03:00.0: board_file api 2 bmi_id N/A crc32 ae2e275a[/SIZE]
[SIZE=2][  863.152649] ath10k_pci 0000:03:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1[/SIZE]

---

### Post by christian-va on 2019-10-10
Hi again,

after tearing my hair for 2 days, I was able to solve the problem with an older firmware qca6174 version.

I was not able to unload the ath10k_pci module before suspend automatically, not via a systemd Unit nor with a script in /lib/systemd/system/system-sleep.
Installing the newest qca6174 formware also did not help.

What helped was an older firmware version from 2016!
Now I have qca6174 hw2.1 version 141 installed, although my notebook runs on 18.04.3 with Kernel 5.

I got that tip from here: [https://askubuntu.com/a/978385/1004167](https://askubuntu.com/a/978385/1004167) so I got the firmware from there: [https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157](https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157) and copied the ath10k_pci/QCA6174/hw2.1 files (which my card is using) into my /lib/firmware/ath10k/QCA6174/hw2.1 folder.

After a reboot, I did not have to unload the driver before suspend (removed my scripts). Going to sleep and resume works for me now, as it did before upgrading from 16.04.

---

