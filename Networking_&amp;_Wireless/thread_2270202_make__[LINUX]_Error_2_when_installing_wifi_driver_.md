---
title: "make: *** [LINUX] Error 2 when installing wifi driver for TP-WN727N (RT2870 chip)"
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by Nguyen_Thanh_Hieu on 2015-03-21
Hey guys I've started using Ubuntu for a week and still can't install the wifi driver for the TP-LINK TL-WN727N USB adapter (RT2870 chip from Ralink). It's pretty annoying cuz it happens everytime I install anything from the terminal. Here's the codes and my system specs :

```

hieutotet@Alpine:~/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870$ sudo make[sudo] password for hieutotet: 
make -C tools
make[1]: Entering directory `/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/tools'
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/tools/bin2h
cp -f os/linux/Makefile.6 /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/Makefile
make  -C  /lib/modules/3.16.0-30-generic/build SUBDIRS=/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-30-generic'
  CC [M]  /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.o
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:537:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/os/rt_linux.h:40,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/rtmp_os.h:42,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/rt_config.h:44,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:28:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:539:3: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/os/rt_linux.h:40,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/rtmp_os.h:42,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/include/rt_config.h:44,
                 from /home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:28:
./arch/x86/include/asm/string_64.h:58:7: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:632:23: warning: assignment makes integer from pointer without a cast [enabled by default]
      pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                       ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:654:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:674:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:912:9: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘long unsigned int’ [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSIRQRequest’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1068:21: warning: unused variable ‘net_dev’ [-Wunused-variable]
  struct net_device *net_dev = pNetDev;
                     ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSFSInfoChange’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1161:20: error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1162:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();  
                    ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1282:8: warning: unused variable ‘pid_number’ [-Wunused-variable]
  pid_t pid_number = -1;
        ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1624:10: error: ‘struct net_device’ has no member named ‘open’
   pNetDev->open   = pDevOpHook->open;
          ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1625:10: error: ‘struct net_device’ has no member named ‘stop’
   pNetDev->stop   = pDevOpHook->stop;
          ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1626:10: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
   pNetDev->hard_start_xmit = (HARD_START_XMIT_FUNC)(pDevOpHook->xmit);
          ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1627:10: error: ‘struct net_device’ has no member named ‘do_ioctl’
   pNetDev->do_ioctl  = pDevOpHook->ioctl;
          ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1633:11: error: ‘struct net_device’ has no member named ‘get_stats’
    pNetDev->get_stats = pDevOpHook->get_stats;
           ^
/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.c:1667:9: error: ‘struct net_device’ has no member named ‘validate_addr’
  pNetDev->validate_addr = NULL;
         ^
make[2]: *** [/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/hieutotet/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-30-generic'
make: *** [LINUX] Error 2


hieutotet@Alpine:~/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870$ uname -a
Linux Alpine 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
hieutotet@Alpine:~/Documents/2009_0820_RT2870_STA_WebUI_v2.2.0.0/RT2870$ 



```

everytime I want to install anything it always end up in "make: *** [LINUX] Error 2"

so is there any solution for this ? Thanks a lot guys

UPDATE:

hey guys thanks to @jeremy31 the solution has been found ! much appreciated !

>                                     **Re: make: *** [LINUX] Error 2 when installing wifi drivers**[INDENT]                     [http://askubuntu.com/questions/45706...r-installation]("http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation") says that this works
     Code:
     [FONT=Ubuntu Mono]sudo apt-get install linux-headers-generic build-essential git[/FONT] 
     Code:
     sudo apt-get install git 
     Code:
     git clone [https://github.com/porjo/mt7601.git](https://github.com/porjo/mt7601.git) 
     Code:
     cd mt7601/src 
     Code:
     make 
     Code:
     sudo make install 
     Code:
     sudo mkdir -p /etc/Wireless/RT2870STA/ 
     Code:
     sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/ 
     Code:
     sudo modprobe mt7601Usta 
                 [/INDENT]
            
                         
                                                                              
     


---

### Post by matt_symes on 2015-03-21
Hi[B]

2009[/B]_0820_RT2870_STA_WebUI_v2.2.0.0

Is 2009 the date the driver was written ? If so and you are using a new kernel then it's may not be a surprise the kernel module is not building.

I would start off by posting some background information.

Open a terminal, plug the wifi device in, wait 20 seconds and the type.

```
lsusb && lsb_release -a && uname -r
```

Post the resulting output from the terminal into your next post.

I am out for most of the day but there are others here who can help you.

Kind regards

---

### Post by Nguyen_Thanh_Hieu on 2015-03-21
Thanks for the quick reply! Here's the output :
```

hieutotet@Alpine:~$ uname -r
3.16.0-30-generic




hieutotet@Alpine:~$ lsusb
Bus 001 Device 003: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4f Trust International B.V. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




hieutotet@Alpine:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39837  1 
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
radeon               1408739  3 
ndiswrapper           283985  0 
gpio_ich               13586  0 
ttm                    85314  1 radeon
snd_hda_codec_hdmi     47548  1 
drm_kms_helper         61574  1 radeon
snd_hda_codec_realtek    72791  1 
drm                   311018  6 ttm,drm_kms_helper,radeon
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
i2c_algo_bit           13413  1 radeon
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
coretemp               13441  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
lpc_ich                21093  0 
serio_raw              13483  0 
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15047  2 snd,snd_hda_codec
shpchp                 37047  0 
mac_hid                13227  0 
parport_pc             32741  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
pata_acpi              13053  0 
atl1c                  46101  0 




hieutotet@Alpine:~$ lsb_release
No LSB modules are available.



```

---

### Post by jeremy31 on 2015-03-21
[http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation](http://askubuntu.com/questions/457061/ralink-148f7601-wifi-adaptor-installation) says that this works
```
[FONT=Ubuntu Mono]sudo apt-get install linux-headers-generic build-essential git
```[/FONT]```
sudo apt-get install git
```
```
git clone https://github.com/porjo/mt7601.git
```
```
cd mt7601/src
```
```
make
```
```
sudo make install
```
```
sudo mkdir -p /etc/Wireless/RT2870STA/
```
```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
```
```
sudo modprobe mt7601Usta
```

---

### Post by Nguyen_Thanh_Hieu on 2015-03-21
okay I'm out for today but I'll let you know if the method works asap , thanks :)

---

### Post by Nguyen_Thanh_Hieu on 2015-03-21
Whoa you're a genius ! It works perfectly !! Thanks a lot guys I owe you big time =d>=d>=d>

---

### Post by aaron36 on 2015-11-15
THIS IS NOT SOLVED 
I have installed the Wifi Dongle in a Windows operating system; ( I know it does work) I deleted all instances of the mt7601 from my system... and followed the instructions above...

the instructions for the MTK7612U  from szedup.com;     [http://www.szedup.com/showinfo554.aspx](http://www.szedup.com/showinfo554.aspx) this is the Driver "DOWNLOAD" for this device Ubuntu / Linux. Inside the Driver are instructions that send you on a "NIGHTMARE SOFTWARE ENGINEERS LABYRINTH" This was originally Ralink then Mediatek now ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^   I am in contact with EDUP and am trying to get them to get the correct PPA Linux or Terminal Commands Ubuntu. UNLESS someone Who HAS THE SOFTWARE SAVY   to take this on.....

 $ lsusb
Bus 002 Device 002: ID 0e8d:7612 MediaTek Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
notice that the Computer sees the device on Bus 002 ID 0e8d:7612 MediaTek lnc. Chip Set

---

### Post by chili555 on 2015-11-15
> notice that the Computer sees the device on Bus 002 ID 0e8d:7612 MediaTek lnc. Chip SetYes, and the device referred to above is entirely different:> 148f:7601 Ralink Technology, Corp. That's why it doesn't work for you. They are different chipsets.

---

### Post by matt_symes on 2015-11-15
> **aaron36 said:**
> THIS IS NOT SOLVED

This is solved !

---

### Post by aaron36 on 2015-11-15
szedup.com is stating the driver you use on this page for the (RT2870 Chip) is the same driver for my (0e8d:7612 chip) or MKT7612u ;  I am in contact with this company and and manufacturer... to get the updated software for mine..... I have the Mini DVD that came with the WiFi Dongle same driver... It needs configuration steps (file modifications) to function... either software provides very minimal instructions for setting up and configuring the Driver Software (they expect me to be the top dollar software engineer)  same driver on github....

---

### Post by chili555 on 2015-11-15
> **aaron36 said:**
> szedup.com is stating the driver you use on this page for the (RT2870 Chip) is the same driver for my (0e8d:7612 chip) or MKT7612u ;  I am in contact with this company and and manufacturer... to get the updated software for mine..... I have the Mini DVD that came with the WiFi Dongle same driver... It needs configuration steps (file modifications) to function... either software provides very minimal instructions for setting up and configuring the Driver Software (they expect me to be the top dollar software engineer)  same driver on github....I just downloaded it. It's certainly not the same as on github that's referenced above. In fact, it is a circa-2011 (!!) package that, I very strongly suspect, predates the creation of the 7612 chip. For any recent Ubuntu version, it won't compile and is useless.

There are and have previously been many driver packages built from the rt2870 bones.

Here is a little clue in the c code:> #if LINUX_VERSION_CODE < KERNEL_VERSION(2,5,0)

/**************************************************************************/
/**************************************************************************/
/*tested for kernel 2.4 series */
/**************************************************************************/
/**************************************************************************/We haven't used kernel version 2.4 in many years. My beard hadn't a single white hair back then!

---

