---
title: "HP Pavilion Wireless"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by expatCM on 2011-07-17
I had a problem getting wireless to work with an HP Pavilion and solved it with the help on this thread.
[http://ubuntuforums.org/showthread.php?t=1801185](http://ubuntuforums.org/showthread.php?t=1801185)

In summary the solution was to install 

firmware-b43-installer
b43-fwcutter

and it worked.

However ...  it did not stay that way....  wireless no longer works.

Yesterday I was using the wireless connection and suddenly it stopped.   The blue light showing active wireless has turned orange.

If I right click the network connection icon at the top menu then either the Enable Wireless is grayed out or it is available but selecting it does nothing and a reboot clears the selection.

The output of sudo lshw -C network is
```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:b3000000-b3003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:73:0c:26:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


```

which shows the network as disabled.

Any idea what went wrong and how to fix it?

---

### Post by wildmanne39 on 2011-07-17
Hi, run this is a terminal
```
lspci -nn
```
```
lsmod
```
```
iwconfig
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by expatCM on 2011-07-17
Output of the three commands as follows. Thank you.


```

lspci -nn

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)


lsmod

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
binfmt_misc            13213  1 
nvidia               9766978  40 
snd_hda_codec_conexant    43782  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
b43                   296610  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
mac80211              257001  1 b43
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              156212  2 b43,mac80211
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
uvcvideo               66851  0 
sparse_keymap          13666  1 hp_wmi
r852                   17878  0 
snd_timer              28659  2 snd_pcm,snd_seq
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_ecc               13070  1 nand
videodev               75143  1 uvcvideo
mtd                    26720  2 sm_common,nand
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
serio_raw              12990  0 
k8temp                 12872  0 
ssb                    45942  1 b43
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
nv_tco                 13331  0 
i2c_nforce2            12906  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sata_nv                23176  2 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_amd               13762  0 
forcedeth              58190  0 


iwconfig

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

---

### Post by wildmanne39 on 2011-07-17
Hi, try these command in a terminal and see if it will connect if it does not post the results of these command back here.
```
rfkill unblock wifi
```
```
sudo ifconfig wlan0 down
```
```
sudo ifconfig wlan0 up
```
if it connects please mark thread solved.

---

### Post by expatCM on 2011-07-17
no output from the first two commands.  The third returned 

SIOCSIFFLAGS: No such device

---

### Post by expatCM on 2011-07-17
and the latest news is .............

I rebooted and the blue wireless light came on and I was able to make a connection.  This worked for about 15 seconds.  The connection dropped and the 'Enable Wireless' check box was unselected and grayed out but the blue light remained on.

Rebooted again and a connection was established.   After five minutes it is still good.

I really do not understand what is happening here ...........

---

### Post by wildmanne39 on 2011-07-17
Hi, I am not sure either, I do know that you do not want a wired connection to your system while you are using wireless, also people are reporting problems if they turn there wireless off by the button or a function key. 

I hope your card is not having issues? Maybe someone else will have an idea if this happens again.

---

### Post by expatCM on 2011-07-17
Thanks for making a contribution to the thread .... yes, let us see if there are any other suggestions ...

---

### Post by Sharpie1 on 2011-07-17
I just updated to 11.04, I previously used the fwcutter drivers to get my Wireless working (Inspiron 6400) however after updating, wireless was reported as "disabled by hardware switch" I had to disable the proprietary hardware drivers (The Broadcom STA driver) completely, (via the Additional Drivers control panel) reboot, and it worked fine... 

Sharpie1

---

### Post by expatCM on 2011-07-17
Is there any way I can disable the internal wireless card (that will survive a reboot)?   I have a USB D-Link card but when I connect it the system hangs so I assume that there is a conflict with the internal card.

If I can eliminate the internal card and use the D-Link card I will at least know where is the problem ....

---

### Post by Sharpie1 on 2011-07-17
I can toggle mine on and off in the BIOS (on mine, hit F2 at the very first splash screen)

Sharpie1

---

### Post by expatCM on 2011-07-18
I think I  need to take the laptop in to the shop.  The present status is that it will not even POST ...  no idea why ...  first impressions are that this is a fundamental failure. In any event this is not exactly a happy ending ..

---

