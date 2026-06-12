---
title: "I can connect to wifi on other compers but not on this laptop"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by ourexpectation on 2013-12-22
I just installed Ubuntu 13.10 and I cant connect to wifi even though I can see the list please help ;(

I also CAN connect to wifi on other devices

---

### Post by varunendra on 2013-12-23
Welcome to the forums ! :)

Ubuntu 10.10 is outdated and has reached its **[End Of Life]("https://wiki.ubuntu.com/Releases")**, means you won't get any security or software updates and will have to compromise with outdated software and drivers.

I would personally recommend to do a fresh install of 12.04.3 instead, which is the current LTS (Long Term Supported) and will be supported until April 2017.

If you that makes sense to you, I'd also recommend to download the ISO via torrents to ensure integrity of the ISO as well as a faster download. Official links for torrents can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

However, if you have any specific reason to stick with 10.10, let me know and we may try to troubleshoot the problem on it.

---

### Post by ourexpectation on 2013-12-23
ohh sorry I mean 13.10 I was so frustrated I meant to type 13.10
I currently have 13.10 and wont let me connect sorry about that

---

### Post by ourexpectation on 2013-12-23
I recently installed Ubuntu 13.10 and I have looked everywhere for a solution and been stuck for 2 days now..
all my other devices can connect but Ubuntu cannot



lspci
&#12288;
```
root@saint-HP-Pavilion-11-x2-Notebook-PC[/EMAIL]:~# lspci
00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0a)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0a)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0a)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0a)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0a)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0a)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0a)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0a)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0a)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0a)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5227 (rev 01)
02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
```
&#12288;
&#12288;
lsusb

```
root@saint-HP-Pavilion-11-x2-Notebook-PC:~# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 04f3:0193 Elan Microelectronics Corp. 
Bus 001 Device 008: ID 06cb:2239 Synaptics, Inc. 
Bus 001 Device 007: ID 1bcf:2c5a Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 005: ID 1bcf:2c59 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 010: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

&#12288;
ifconfig

```
root@saint-HP-Pavilion-11-x2-Notebook-PC[/EMAIL]:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85868 (85.8 KB)  TX bytes:85868 (85.8 KB)
wlan0     Link encap:Ethernet  HWaddr 34:23:87:04:ec:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:692 (692.0 B)  TX bytes:8562 (8.5 KB)
```
&#12288;
PLEASE HELP

---

### Post by Hodevah on 2013-12-23
HI. I am not an expert but I can tell you right about now that the best way for people to help you is to post the output (placed in code tages i.e. "#" ) the info that is at this link here:


[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

This way, all the information about your system, network, etc.. is readily available to the one's that you are hoping to provide you with some help in getting your wireless situation resolved. ;)

---

### Post by ourexpectation on 2013-12-23
I posted the output

---

### Post by Bucky Ball on 2013-12-23
> **ourexpectation said:**
> I posted the output

What Hodevah means is:

```
Post it in code tags. One way of doing this is to create a [quote] and replace 'quote' at either end with 'code'.

Another way is to use the # icon in the 'Go Advanced' window.
```

I have edited and added tags to your post so you get the idea. ;)

First question: Can you get online with a cable? If so, do that, do an update, check additional drivers.

Second: Post the result of this:

```
sudo lshw -C network
```

Thanks.

---

### Post by ourexpectation on 2013-12-23
No I am on a laptop that doesn't have a cable port thing idk


```
root@saint-HP-Pavilion-11-x2-Notebook-PC:~# sudo lshw -C network

PCI (sysfs)  


&#12288;

  *-network               [D^[[C^[[D^[[A

       description: Wireless interface

       product: RT3290 Wireless 802.11n 1T/1R PCIe

       vendor: Ralink corp.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wlan0

       version: 00

       serial: 34:23:87:04:ec:13

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=rt2800pci driverversion=3.11.0-12-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn

       resources: irq:107 memory:90410000-9041ffff

root@saint-HP-Pavilion-11-x2-Notebook-PC:~# 

root@saint-HP-Pavilion-11-x2-Notebook-PC:~# 

root@saint-HP-Pavilion-11-x2-Notebook-PC:~# 

root@saint-HP-Pavilion-11-x2-Notebook-PC:~# ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:65536  Metric:1

          RX packets:160 errors:0 dropped:0 overruns:0 frame:0

          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:12896 (12.8 KB)  TX bytes:12896 (12.8 KB)


wlan0     Link encap:Ethernet  HWaddr 34:23:87:04:ec:13  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:7 errors:0 dropped:0 overruns:0 frame:0

          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:824 (824.0 B)  TX bytes:9288 (9.2 KB)


&#12288;

```

---

### Post by Bucky Ball on 2013-12-24
iwconfig probably better than ifconfig for wireless. ;)

You have a driver installed and for all intents and purposes this should be working (and does with that kernel, apparently 'out of the box'). It may, of course, be the wrong driver.

 It is very difficult if you have no cable connection (very unusual ... what laptop?), but not impossible. You will probably need a machine that is online, though, and something to save files to to transfer to this machine (USB dongle, perhaps).

When you say wifi is not working, without meaning to sound dumb, how do you know? You are trying to connect to your network and it is not (constantly spinning icon?) When you left click on the network icon, do you see any networks? Even if they aren't yours? Do you need to enter a static IP address to get things going or anything else exotic? Have you manually set up a connection in Network Manager? (Right click network icon, edit connections, Wireless tab, setup connection).

Please provide the output of 'iwconfig'. Not sure if that will help as we have all details, but these pages will help, but you need a connection or a machine that is connected and a dongle. A step by step:

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

If the above one doesn't work there's a heap of successful possibilities here:

[https://duckduckgo.com/?q=+RT3290++ubuntu](https://duckduckgo.com/?q=+RT3290++ubuntu)

*Note: You are running this driver: rt2800pci. The first link I provide advises you need to run rt3562. You could try downloading that to the machine you are posting from (from the Realtek site), stick it on a dongle and follow the instructions on that link. Good luck.

---

### Post by ourexpectation on 2013-12-24
Does windstream have anything to do with it because I think windstream is windows only drivers?

---

### Post by Bucky Ball on 2013-12-24
Windstream? Never heard of it. Are you trying to use a Windows program in Ubuntu? Anyhow, can we get back on topic?

Please reread and respond to my last post. There is a solution in the first link.

---

### Post by ourexpectation on 2013-12-24
It will not connect I can see them just wont connect it shows bars moving but will not fully connect

it gives me errors while make and install drivers


```
saint@saint-HP-Pavilion-11-x2-Notebook-PC:~$ iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

^^^^^iwconfig



```
sudo make:
      DBGPRINT(RT_DEBUG_ERROR, ("AES_Key_Unwrap: allocate %d bytes memory failure.\n", sizeof(UINT8)*PlainLength));
      ^
  CC [M]  /home/saint/down/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/saint/down/os/linux/../../common/mlme.o
In file included from /home/saint/down/include/rtmp_os.h:42:0,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/include/rt_config.h:36,
                 from /home/saint/down/os/linux/../../common/mlme.c:30:
/home/saint/down/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/saint/down/os/linux/../../common/mlme.c:529:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecEnd -
       ^
/home/saint/down/include/os/rt_linux.h:463:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
/home/saint/down/os/linux/../../common/mlme.c:530:7: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
       (UINT32)&pAd->RalinkCounters.OneSecStart);
       ^
/home/saint/down/include/os/rt_linux.h:463:76: note: in definition of macro &#8216;NdisZeroMemory&#8217;
 #define NdisZeroMemory(Destination, Length)         memset(Destination, 0, Length)
                                                                            ^
  CC [M]  /home/saint/down/os/linux/../../common/cmm_wep.o
  CC [M]  /home/saint/down/os/linux/../../common/action.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_data.o
  CC [M]  /home/saint/down/os/linux/../../common/rtmp_init.o
  CC [M]  /home/saint/down/os/linux/../../common/rtmp_init_inf.o
/home/saint/down/os/linux/../../common/rtmp_init_inf.c: In function &#8216;rt28xx_init&#8217;:
/home/saint/down/os/linux/../../common/rtmp_init_inf.c:162:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
   DBGPRINT(RT_DEBUG_OFF,("PllCtrl:0x%x\n",PllCtrl.word));
   ^
/home/saint/down/os/linux/../../common/rtmp_init_inf.c:178:10: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
          AUTO_WAKEUP_STRUC AutoWakeupCfg;
          ^
  CC [M]  /home/saint/down/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_aes.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_sync.o
  CC [M]  /home/saint/down/os/linux/../../common/eeprom.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_info.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_wpa.o
/home/saint/down/os/linux/../../common/cmm_wpa.c: In function &#8216;PeerPairMsg3Action&#8217;:
/home/saint/down/os/linux/../../common/cmm_wpa.c:1032:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/saint/down/os/linux/../../common/cmm_radar.o
  CC [M]  /home/saint/down/os/linux/../../common/spectrum.o
/home/saint/down/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/saint/down/os/linux/../../common/spectrum.c:1972:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
   DBGPRINT(RT_DEBUG_ERROR, ("%s unable to alloc memory for measure report buffer (size=%d).\n", __FUNCTION__, sizeof(MEASURE_RPI_REPORT)));
   ^
  CC [M]  /home/saint/down/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/saint/down/os/linux/../../common/rt_channel.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_profile.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_asic.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/saint/down/os/linux/../../common/ps.o
  CC [M]  /home/saint/down/os/linux/../../common/uapsd.o
  CC [M]  /home/saint/down/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/saint/down/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/saint/down/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_profile.o
/home/saint/down/os/linux/../../os/linux/rt_profile.c: In function &#8216;STA_MonPktSend&#8217;:
/home/saint/down/os/linux/../../os/linux/rt_profile.c:409:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat=]
         DBGPRINT(RT_DEBUG_ERROR, ("%s : Size is too large! (%d)\n", __FUNCTION__, pRxBlk->DataSize + sizeof(wlan_ng_prism2_header)));
         ^
  CC [M]  /home/saint/down/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/saint/down/os/linux/../../sta/assoc.o
  CC [M]  /home/saint/down/os/linux/../../sta/auth.o
  CC [M]  /home/saint/down/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/saint/down/os/linux/../../sta/sync.o
  CC [M]  /home/saint/down/os/linux/../../sta/sanity.o
  CC [M]  /home/saint/down/os/linux/../../sta/rtmp_data.o
/home/saint/down/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxDataFrame&#8217;:
/home/saint/down/os/linux/../../sta/rtmp_data.c:283:17: warning: unused variable &#8216;pFmeCtrl&#8217; [-Wunused-variable]
  FRAME_CONTROL *pFmeCtrl = &pHeader->FC;
                 ^
/home/saint/down/os/linux/../../sta/rtmp_data.c:282:8: warning: unused variable &#8216;OldPwrMgmt&#8217; [-Wunused-variable]
  UCHAR OldPwrMgmt = PWR_ACTIVE;
        ^
/home/saint/down/os/linux/../../sta/rtmp_data.c: In function &#8216;STAHandleRxMgmtFrame&#8217;:
/home/saint/down/os/linux/../../sta/rtmp_data.c:766:5: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
     UCHAR uRSSI2;
     ^
  CC [M]  /home/saint/down/os/linux/../../sta/connect.o
  CC [M]  /home/saint/down/os/linux/../../sta/wpa.o
  CC [M]  /home/saint/down/os/linux/../../sta/sta_cfg.o
/home/saint/down/os/linux/../../sta/sta_cfg.c: In function &#8216;RTMPQueryInformation&#8217;:
/home/saint/down/os/linux/../../sta/sta_cfg.c:3956:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("sizeof UCHAR=%d, channel=%d \n", sizeof(UCHAR), pAd->CommonCfg.Channel));
    ^
/home/saint/down/os/linux/../../sta/sta_cfg.c: In function &#8216;RtmpIoctl_rt_private_get_statistics&#8217;:
/home/saint/down/os/linux/../../sta/sta_cfg.c:7220:1: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 3 has type &#8216;EEPROM_NIC_CONFIG3_STRUC&#8217; [-Wformat=]
 sprintf(extra+strlen(extra), "pAd->NicConfig3.field.CoexAnt == 0x%x\n\n",pAd->NicConfig3);
 ^
  CC [M]  /home/saint/down/os/linux/../../common/rt_os_util.o
  CC [M]  /home/saint/down/os/linux/../../os/linux/sta_ioctl.o
In file included from /home/saint/down/include/os/rt_linux.h:40:0,
                 from /home/saint/down/include/rtmp_os.h:42,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/os/linux/../../os/linux/sta_ioctl.c:33:
/home/saint/down/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_giwscan&#8217;:
include/net/iw_handler.h:554:9: warning: array subscript is below array bounds [-Warray-bounds]
   memcpy(stream + point_len, extra, iwe->u.data.length);
         ^
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_linux.o
/home/saint/down/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/saint/down/os/linux/../../os/linux/rt_linux.c:508:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/saint/down/include/os/rt_linux.h:18,
                 from /home/saint/down/include/rtmp_os.h:42,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/os/linux/../../os/linux/rt_linux.c:35:
/usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/saint/down/os/linux/../../os/linux/rt_linux.c:510:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/saint/down/include/os/rt_linux.h:18,
                 from /home/saint/down/include/rtmp_os.h:42,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/os/linux/../../os/linux/rt_linux.c:35:
/usr/src/linux-headers-3.11.0-12-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/saint/down/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/saint/down/os/linux/../../os/linux/rt_linux.c:662:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/saint/down/include/rtmp_os.h:42:0,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/os/linux/../../os/linux/rt_linux.c:35:
/home/saint/down/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/saint/down/include/os/rt_linux.h:992:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/saint/down/os/linux/../../os/linux/rt_linux.c:681:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/saint/down/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/saint/down/os/linux/../../os/linux/rt_linux.c:708:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/saint/down/os/linux/../../common/ba_action.o
In file included from /home/saint/down/include/rtmp_os.h:42:0,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/include/rt_config.h:36,
                 from /home/saint/down/os/linux/../../common/ba_action.c:3:
/home/saint/down/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/saint/down/include/os/rt_linux.h:992:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/saint/down/include/os/rt_linux.h:1035:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;
  SET_OS_PKT_DATATAIL(__pRxPkt, __pData, __DataSize);      \
  ^
/home/saint/down/os/linux/../../common/ba_action.c:1550:2: note: in expansion of macro &#8216;RTMP_OS_PKT_INIT&#8217;
  RTMP_OS_PKT_INIT(pRxBlk->pRxPacket,
  ^
  CC [M]  /home/saint/down/os/linux/../../common/rt_led.o
  CC [M]  /home/saint/down/os/linux/../../common/cmm_mac_pci.o
/home/saint/down/os/linux/../../common/cmm_mac_pci.c: In function &#8216;RT28xxPciMlmeRadioOn&#8217;:
/home/saint/down/os/linux/../../common/cmm_mac_pci.c:2245:13: warning: unused variable &#8216;Cancelled&#8217; [-Wunused-variable]
  BOOLEAN    Cancelled;
             ^
  CC [M]  /home/saint/down/os/linux/../../common/cmm_data_pci.o
/home/saint/down/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPFreeTXDUponTxDmaDone&#8217;:
/home/saint/down/os/linux/../../common/cmm_data_pci.c:543:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
/home/saint/down/os/linux/../../common/cmm_data_pci.c: In function &#8216;RTMPHandleMgmtRingDmaDoneInterrupt&#8217;:
/home/saint/down/os/linux/../../common/cmm_data_pci.c:738:8: warning: unused variable &#8216;TXWISize&#8217; [-Wunused-variable]
  UINT8 TXWISize = pAd->chipCap.TXWISize;
        ^
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_rbus_pci_drv.o
/home/saint/down/os/linux/../../os/linux/rt_rbus_pci_drv.c: In function &#8216;RTMPInitPCIeDevice&#8217;:
/home/saint/down/os/linux/../../os/linux/rt_rbus_pci_drv.c:1349:22: warning: unused variable &#8216;Index&#8217; [-Wunused-variable]
  UINT32 MacCsr0 = 0, Index= 0;
                      ^
  CC [M]  /home/saint/down/os/linux/../../common/rtmp_mcu.o
/home/saint/down/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/saint/down/os/linux/../../common/rtmp_mcu.c:464:8: warning: unused variable &#8216;offset&#8217; [-Wunused-variable]
  ULONG offset;
        ^
/home/saint/down/os/linux/../../common/rtmp_mcu.c:463:8: warning: unused variable &#8216;Configuration&#8217; [-Wunused-variable]
  ULONG Configuration;
        ^
  CC [M]  /home/saint/down/os/linux/../../common/ee_prom.o
  CC [M]  /home/saint/down/os/linux/../../common/ee_efuse.o
  CC [M]  /home/saint/down/os/linux/../../common/rt_rf.o
  CC [M]  /home/saint/down/os/linux/../../chips/rt30xx.o
  CC [M]  /home/saint/down/os/linux/../../chips/rt3290.o
/home/saint/down/os/linux/../../chips/rt3290.c: In function &#8216;RT3290_AsicTxAlcGetAutoAgcOffset&#8217;:
/home/saint/down/os/linux/../../chips/rt3290.c:1564:25: warning: assignment discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
     pTxPowerTuningEntry = &(TxPowerTuningTable[TuningTableIndex + TX_POWER_TUNING_ENTRY_OFFSET]);
                         ^
/home/saint/down/os/linux/../../chips/rt3290.c: In function &#8216;MlmeAntSelection&#8217;:
/home/saint/down/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE,("AntS: AvgTxErrorRatio = %d , TxErrorRatio = %d, AccuTxTotalCnt = %d, Rssi = %d\n",AvgTxErrorRatio, TxErrorRatio, AccuTxTotalCnt, Rssi));
    ^
/home/saint/down/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2507:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE, ("AntS: Train State: AntennaDiversityCount = %d\n", pAd->AntennaDiversityInfo.AntennaDiversityCount));
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2522:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE,("AntS, Ant 0, Tx: %d, Rx: %d\n",pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[0],pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[0]));
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2522:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2523:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE,("AntS, Ant 1, Tx: %d, Rx: %d\n",pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[1],pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[1]));
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2523:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2526:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE,("AntS: Train State: PER[Main] = %d, PER[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityPER[0],pAd->AntennaDiversityInfo.AntennaDiversityPER[1])); 
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2526:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2527:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE,("AntS: TotalTxCount[Main] = %d, TotalTxCount[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[0],pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[1])); 
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2527:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2528:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
     DBGPRINT(RT_DEBUG_TRACE,("AntS: TotalRxCount[Main] = %d, TotalRxCount[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[0],pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[1])); 
     ^
/home/saint/down/os/linux/../../chips/rt3290.c:2528:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2545:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_TRACE,("AntS: AntSAuxDelta = %d, AntSRssiFactor = %d, AntSPERFactor = %d\n",
      ^
/home/saint/down/os/linux/../../chips/rt3290.c:2545:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2545:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2559:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
         DBGPRINT(RT_DEBUG_TRACE,("AntS: Good Rssi is at Main !! ++%d\n",(diffRssi*Ant0TotalPacket/pAd->StaCfg.AntSRssiFactor))); 
         ^
/home/saint/down/os/linux/../../chips/rt3290.c:2565:9: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
         DBGPRINT(RT_DEBUG_TRACE,("AntS: Good Rssi is at Aux !!++%d\n",(diffRssi*Ant1TotalPacket/pAd->StaCfg.AntSRssiFactor))); 
         ^
/home/saint/down/os/linux/../../chips/rt3290.c:2574:8: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
        DBGPRINT(RT_DEBUG_TRACE,("AntS: Good PER is at Main !! ++%d\n", (diffPER*Ant0TotalPacket/pAd->StaCfg.AntSPERFactor))); 
        ^
/home/saint/down/os/linux/../../chips/rt3290.c:2581:8: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
        DBGPRINT(RT_DEBUG_TRACE,("AntS: Good PER is at Aux !! ++%d\n", (diffPER*Ant1TotalPacket/pAd->StaCfg.AntSPERFactor))); 
        ^
/home/saint/down/os/linux/../../chips/rt3290.c:2583:7: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
       DBGPRINT(RT_DEBUG_TRACE,("AntS: Delta Packet = %d,%d, diffRssi = %d, diffPER = %d\n",(diffRssi*Ant0TotalPacket/pAd->StaCfg.AntSRssiFactor),(diffPER*Ant1TotalPacket/pAd->StaCfg.AntSPERFactor),diffRssi, diffPER)); 
       ^
/home/saint/down/os/linux/../../chips/rt3290.c:2583:7: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2595:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_TRACE,("AntS: Stop Train State: PER[Main] = %d, PER[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityPER[0],pAd->AntennaDiversityInfo.AntennaDiversityPER[1])); 
      ^
/home/saint/down/os/linux/../../chips/rt3290.c:2595:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2596:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_TRACE,("AntS: TotalTxCount[Main] = %d, TotalTxCount[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[0],pAd->AntennaDiversityInfo.AntennaDiversityTxPacketCount[1])); 
      ^
/home/saint/down/os/linux/../../chips/rt3290.c:2596:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c:2597:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat=]
      DBGPRINT(RT_DEBUG_TRACE,("AntS: TotalRxCount[Main] = %d, TotalRxCount[Aux] = %d\n",pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[0],pAd->AntennaDiversityInfo.AntennaDiversityRxPacketCount[1])); 
      ^
/home/saint/down/os/linux/../../chips/rt3290.c:2597:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
/home/saint/down/os/linux/../../chips/rt3290.c: In function &#8216;BtCoexSetting&#8217;:
/home/saint/down/os/linux/../../chips/rt3290.c:3244:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat=]
    DBGPRINT(RT_DEBUG_TRACE, ("%s:COEX_MODE is active(Two Antenna Mode)!!! CoexMode = %d, BBPCurrentBW = %d, Rssi = %d, RfR49Value = 0x%x\n", 
    ^
/home/saint/down/os/linux/../../chips/rt3290.c: In function &#8216;Profile_TwoAnt&#8217;:
/home/saint/down/os/linux/../../chips/rt3290.c:4097:2: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;CMB_CTRL_STRUC&#8217; [-Wformat=]
  printk("cmbCtrl = %x\n",cmbCtrl);
  ^
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_pci_rbus.o
  CC [M]  /home/saint/down/os/linux/../../os/linux/rt_rbus_pci_util.o
  CC [M]  /home/saint/down/os/linux/../../os/linux/pci_main_dev.o
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:43:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
 static VOID __devexit rt2860_remove_one(struct pci_dev *pci_dev);
                       ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:44:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
 static INT __devinit rt2860_probe(struct pci_dev *pci_dev, const struct pci_device_id  *ent);
                      ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:63:46: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__devinitdata&#8217;
 static struct pci_device_id rt2860_pci_tbl[] __devinitdata =
                                              ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:85:17: error: &#8216;rt2860_pci_tbl&#8217; undeclared here (not in a function)
     id_table:   rt2860_pci_tbl,
                 ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:86:17: error: &#8216;rt2860_probe&#8217; undeclared here (not in a function)
     probe:      rt2860_probe,
                 ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:88:5: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
     remove:     __devexit_p(rt2860_remove_one),
     ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:88:29: error: &#8216;rt2860_remove_one&#8217; undeclared here (not in a function)
     remove:     __devexit_p(rt2860_remove_one),
                             ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:292:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_probe&#8217;
 static INT __devinit   rt2860_probe(
                        ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:463:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rt2860_remove_one&#8217;
 static VOID __devexit rt2860_remove_one(
                       ^
In file included from /home/saint/down/include/os/rt_linux.h:18:0,
                 from /home/saint/down/include/rtmp_os.h:42,
                 from /home/saint/down/include/rtmp_comm.h:56,
                 from /home/saint/down/os/linux/../../os/linux/pci_main_dev.c:32:
include/linux/module.h:87:32: error: &#8216;__mod_pci_device_table&#8217; aliased to undefined symbol &#8216;rt2860_pci_tbl&#8217;
 extern const struct gtype##_id __mod_##gtype##_table  \
                                ^
include/linux/module.h:145:3: note: in expansion of macro &#8216;MODULE_GENERIC_TABLE&#8217;
   MODULE_GENERIC_TABLE(type##_device,name)
   ^
/home/saint/down/os/linux/../../os/linux/pci_main_dev.c:71:1: note: in expansion of macro &#8216;MODULE_DEVICE_TABLE&#8217;
 MODULE_DEVICE_TABLE(pci, rt2860_pci_tbl);
 ^
cc1: some warnings being treated as errors
make[2]: *** [/home/saint/down/os/linux/../../os/linux/pci_main_dev.o] Error 1
make[1]: *** [_module_/home/saint/down/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [LINUX] Error 2

```

^^^^^^^^^ sudo make


```

sudo make install:
saint@saint-HP-Pavilion-11-x2-Notebook-PC:~/down$ sudo make install
make -C /home/saint/down/os/linux -f Makefile.6 install
mkdir: cannot create directory &#8216;/etc/Wireless&#8217;: File exists
make[1]: Entering directory `/home/saint/down/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/saint/down/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3290sta.ko /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;rt3290sta.ko&#8217;: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/saint/down/os/linux'
make: *** [install] Error 2

```

---

### Post by varunendra on 2013-12-24
I was wondering about that. :)

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by ourexpectation on 2013-12-24
Like this idk if I did it right I followed the best I can.




```

*************** info trace ***************


***** uname -a *****


Linux saint-HP-Pavilion-11-x2-Notebook-PC 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu

Description:	Ubuntu 13.10

Release:	13.10

Codename:	saucy


***** lspci *****


02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]

	Subsystem: Hewlett-Packard Company Device [103c:18ec]

	Kernel driver in use: rt2800pci


***** lsusb *****


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

Bus 001 Device 009: ID 04f3:0193 Elan Microelectronics Corp. 

Bus 001 Device 008: ID 06cb:2239 Synaptics, Inc. 

Bus 001 Device 007: ID 1bcf:2c5a Sunplus Innovation Technology Inc. 

Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

Bus 001 Device 006: ID 0483:91d1 STMicroelectronics 

Bus 001 Device 005: ID 1bcf:2c59 Sunplus Innovation Technology Inc. 

Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

Bus 001 Device 013: ID 054c:0439 Sony Corp. 

Bus 001 Device 010: ID 1c4f:0003 SiGma Micro HID controller

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****


&#12288;

***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Encryption key:off

          Power Management:off

          


***** rfkill *****


0: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no


***** lsmod *****


hp_wmi                 14062  0 

sparse_keymap          13948  1 hp_wmi

rt2800pci              18690  0 

rt2800lib              79963  1 rt2800pci

rt2x00pci              13287  1 rt2800pci

rt2x00mmio             13603  1 rt2800pci

rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio

mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib

cfg80211              479757  2 mac80211,rt2x00lib

eeprom_93cx6           13344  1 rt2800pci

crc_ccitt              12707  1 rt2800lib

wmi                    19070  1 hp_wmi


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------

  Type:              802.11 WiFi

  Driver:            rt2800pci

  State:             disconnected

  Default:           no

  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties

    WEP Encryption:  yes

    WPA Encryption:  yes

    WPA2 Encryption: yes


  Wireless Access Points 


&#12288;

&#12288;

***** NetworkManager.state *****

[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true

WimaxEnabled=true


***** NetworkManager.conf *****


[main]

plugins=ifupdown,keyfile,ofono

dns=dnsmasq


[ifupdown]

managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo

iface lo inet loopback


***** iwlist *****


&#12288;

***** resolv.conf *****


&#12288;

***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]

blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]

blacklist evbug

blacklist usbmouse

blacklist usbkbd

blacklist eepro100

blacklist de4x5

blacklist eth1394

blacklist snd_intel8x0m

blacklist snd_aw2

blacklist i2c_i801

blacklist prism54

blacklist bcm43xx

blacklist garmin_gps

blacklist asus_acpi

blacklist snd_pcsp

blacklist pcspkr

blacklist amd76x_edac


***** modinfo *****


rt2800pci

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko

firmware:       rt2860.bin

version:        2.3.0

srcversion:     259E8826760AAB9E718FD85

depends:        rt2x00lib,rt2800lib,rt2x00mmio,rt2x00pci,eeprom_93cx6

parm:           nohwcrypt:Disable hardware encryption. (bool)


rt2800lib

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko

version:        2.3.0

srcversion:     26219235502295A1CDE028F

depends:        rt2x00lib,mac80211,crc-ccitt


rt2x00pci

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko

version:        2.3.0

srcversion:     BD4DED63CAE52A1875B21D1

depends:        rt2x00lib,mac80211


rt2x00mmio

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko

version:        2.3.0

srcversion:     2C5ADAF564EF1DAD569D9C3

depends:        rt2x00lib


rt2x00lib

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko

version:        2.3.0

srcversion:     8AE9D454A710B1C25F9F518

depends:        mac80211,cfg80211


mac80211

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/net/mac80211/mac80211.ko

srcversion:     367212A7EC9CD2205F8C5C9

depends:        cfg80211

parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)

parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)

parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)

parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


cfg80211

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/net/wireless/cfg80211.ko

srcversion:     1FEC83877CF068095FA2F9F

depends:        

parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)

parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


eeprom_93cx6

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko

version:        1.0

srcversion:     215D8C1284A3C33B4A5A1C5

depends:        


crc_ccitt

--------------------

filename:       /lib/modules/3.11.0-12-generic/kernel/lib/crc-ccitt.ko

srcversion:     2294FCAD06D727386004EEB

depends:        


&#12288;

***** udev rules *****


# PCI device 0x1814:0x3290 (rt2800pci)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[    0.724417] audit: initializing netlink socket (disabled)

[    2.244132] wmi: Mapper loaded

[    2.308438] cfg80211: Calling CRDA to update world regulatory domain

[    2.394074] rt2800pci 0000:02:00.0: irq 107 for MSI/MSI-X

[    2.394165] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected

[    2.404370] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected

[    2.415488] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'

[    2.876809] cfg80211: World regulatory domain updated:

[    2.876811] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

[    2.876814] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    2.876816] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    2.876817] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[    2.876819] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    2.876820] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    2.915099] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

[    4.887824] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[    5.370404] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'

[    5.370682] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37

[    5.415968] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[    5.416456] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[    6.536950] wlan0: authenticate with <MAC address removed>

[    6.551889] wlan0: send auth to <MAC address removed> (try 1/3)

[    6.553427] wlan0: authenticated

[    6.555886] wlan0: associate with <MAC address removed> (try 1/3)

[    6.559150] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)

[    6.559237] wlan0: associated

[    6.559282] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[    8.975753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[    9.135733] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[    9.499737] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[    9.659732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[    9.663841] cfg80211: Calling CRDA to update world regulatory domain

[    9.668041] cfg80211: World regulatory domain updated:

[    9.668047] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

[    9.668051] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    9.668054] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    9.668057] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)

[    9.668060] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    9.668063] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[    9.788379] wlan0: authenticate with <MAC address removed>

[    9.947738] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   10.107740] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   10.115835] wlan0: send auth to <MAC address removed> (try 1/3)

[   10.807782] wlan0: send auth to <MAC address removed> (try 2/3)

[   11.819776] wlan0: send auth to <MAC address removed> (try 3/3)

[   12.819878] wlan0: authentication with <MAC address removed> timed out

[   13.023756] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   13.183756] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   13.483755] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   13.643954] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   18.475734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   18.635728] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   18.795735] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   18.955726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   20.175733] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   20.335727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   25.171732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   25.331725] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   25.491730] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   25.651727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   25.651887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   26.871732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   27.031724] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   27.191735] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   27.351736] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   27.511730] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   27.671727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   28.891736] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   29.051732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   33.887734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   34.047727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   34.207754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   34.367727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   35.587752] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   35.747726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   40.583726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   40.743735] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   40.903726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   41.063727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   42.283724] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   42.443731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   47.275724] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   47.435720] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   47.595723] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   47.755729] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   48.975731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   49.135722] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   51.167721] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   51.327721] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   51.487711] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   51.647715] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   52.867717] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   53.027712] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   54.207720] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   54.367731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   54.527723] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   54.687727] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   55.907730] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   56.067741] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   60.903717] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   61.063714] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   61.223709] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   61.383715] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   62.603717] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   62.763713] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   67.595774] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   67.755720] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   67.915729] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   68.075721] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   68.111796] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   69.295715] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   69.455825] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   74.291866] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   74.451766] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   74.611749] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   74.771766] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   74.811725] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   75.995820] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   76.159769] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   79.167746] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   79.327760] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   79.487753] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   79.647752] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   79.683810] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   80.867731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   81.027833] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   82.239777] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   82.399794] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   82.559752] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   82.719800] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   82.755729] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   83.939750] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   84.099760] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   88.935754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   89.095764] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   89.259722] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   89.419746] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   89.455859] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   90.639732] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   90.799745] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   95.631751] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   95.791780] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   95.951723] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   96.111813] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[   96.147746] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[   97.335762] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[   97.495748] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  102.331824] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  102.491726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  102.651712] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  102.811758] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  102.847815] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  104.031838] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  104.191761] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  107.171806] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  107.331747] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  107.491745] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  107.651743] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  107.687778] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  108.871780] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  109.035775] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  110.163746] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  110.323740] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  110.483756] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  110.643694] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  110.679830] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  111.863740] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  112.023734] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  133.163737] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  133.323689] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  133.483738] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  133.643704] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  133.679781] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  134.863708] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  135.023774] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  166.167720] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  166.327711] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  166.487720] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  166.647679] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  166.683728] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  167.867672] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  168.027711] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  209.167696] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  209.327699] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  209.487726] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  209.647696] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  209.683733] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  210.867707] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  211.027731] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  262.167676] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  262.327678] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  262.487670] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  262.647758] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  262.683719] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  263.867672] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  264.027685] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  325.163653] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  325.323653] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  325.483606] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  325.643650] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  325.679678] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  326.863750] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  327.023603] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  388.167588] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  388.327572] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  388.487590] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  388.647565] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  388.683663] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  389.867586] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  390.027589] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  407.271595] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  407.431661] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  407.591590] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  407.751565] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  407.787574] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  408.975618] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  409.135602] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  413.967647] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  414.127597] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  414.287608] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  414.447604] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  414.483701] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  415.667606] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  415.827560] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  420.663564] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  420.823660] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  420.983607] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  421.143550] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  421.179569] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  422.363564] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  422.523594] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  427.355598] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  427.515625] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  427.675559] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  427.835591] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  427.871635] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  429.059575] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  429.219604] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  432.171607] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  432.331623] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  432.491602] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  432.651603] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  432.687637] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  433.871545] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  434.031606] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  435.283616] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  435.443601] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  435.603591] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  435.763599] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  435.799630] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  436.983601] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  437.143574] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  441.975614] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  442.135599] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  442.295589] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  442.455594] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  442.491683] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  443.675616] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  443.835586] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  448.667604] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  448.827576] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  448.987587] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  449.147597] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  449.183615] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  450.367531] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  450.535601] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  455.363703] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  455.523582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  455.683589] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  455.843582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  455.879621] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  457.071524] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  457.231611] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  460.172138] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  460.331587] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  460.491579] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  460.651589] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  460.687645] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  461.871601] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  462.031584] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  463.275582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  463.435614] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  463.595582] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  463.755531] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  463.791597] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  464.975586] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  465.135530] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  469.967522] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  470.127526] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  470.287541] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  470.447637] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  470.483626] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  471.667611] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  471.827593] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  476.663575] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  476.823528] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  476.983667] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  477.143580] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  477.179616] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  478.363528] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  478.523522] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  483.359524] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  483.519573] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  483.679581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  483.839785] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  483.875607] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  485.063530] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  485.223556] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  488.179592] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  488.339514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  488.499516] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  488.659639] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  488.695608] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  489.879575] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  490.039567] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  491.255515] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  491.415661] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  491.575610] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  491.735524] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  491.771542] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  492.955529] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  493.115550] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  497.947572] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  498.107520] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  498.267595] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  498.427562] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  498.463616] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  499.655606] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  499.815585] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  504.651562] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  504.811600] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  504.971520] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  505.131520] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  505.167597] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  506.351508] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  506.511563] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  511.347564] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  511.507541] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  511.667514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  511.827559] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  511.863584] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  513.047561] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  513.211530] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  516.179570] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  516.339545] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  516.499547] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  516.659546] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  516.695581] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  517.879509] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  518.039555] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  519.163555] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  519.323556] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  519.483553] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  519.643552] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  519.679586] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  520.867638] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  521.027524] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  542.167553] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  542.327549] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  542.487544] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  542.647540] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  542.683574] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  543.867545] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  544.027535] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  575.167506] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  575.327481] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  575.487561] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  575.647527] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  575.683566] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  576.867523] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  577.027522] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  618.167505] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  618.327499] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  618.487497] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  618.647499] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  618.683537] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  619.867500] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  620.027496] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  671.167477] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  671.327491] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  671.487492] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  671.647492] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  671.683521] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  672.867475] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  673.027471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  734.167465] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  734.327461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  734.487470] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  734.647484] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  734.683431] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  735.867460] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  736.027461] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  797.167390] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  797.327432] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  797.487420] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  797.647418] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  797.683451] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  798.867428] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  799.027429] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  816.339421] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  816.499408] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  816.659414] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  816.823754] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  816.859464] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  818.043449] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  818.203416] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  823.039411] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  823.199391] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  823.359449] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  823.519421] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  823.555466] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  824.743404] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  824.903440] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  829.731363] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  829.891456] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  830.055408] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  830.215763] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  830.251439] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  831.443364] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  831.603401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  836.435416] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  836.595383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  836.755511] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  836.915403] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  836.951450] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  838.139361] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  838.299385] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  841.175399] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  841.335394] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  841.495369] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  841.655409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  841.691448] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  842.875396] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  843.039408] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  844.279438] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  844.439409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  844.599383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  844.759363] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  844.795430] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  845.979413] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  846.139395] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  850.975397] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  851.135358] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  851.295474] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  851.455360] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  851.491445] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  852.675386] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  852.835405] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  857.675436] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  857.835439] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  857.995447] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  858.155344] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  858.191372] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  859.375409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  859.535403] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  864.371454] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  864.531914] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  864.691460] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  864.851390] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  864.887467] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  866.071383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  866.231520] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  869.183341] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  869.343370] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  869.503340] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  869.663340] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  869.699446] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  870.883382] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  871.043383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  872.295389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  872.455387] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  872.615388] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  872.775402] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  872.811407] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  873.995336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  874.155391] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  878.987403] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  879.147376] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  879.307409] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  879.467380] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  879.507443] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  880.695383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  880.855338] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  885.687334] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  885.848569] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  886.007375] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  886.167402] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  886.203415] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  887.387375] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  887.547378] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  892.388267] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  892.547430] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  892.707338] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  892.867379] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  892.903470] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  894.095383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  894.255325] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  897.171352] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  897.331325] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  897.491359] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  897.651322] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  897.687340] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  898.871364] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  899.033667] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  900.211369] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  900.371362] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  900.531359] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  900.691368] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  900.727391] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  901.911366] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  902.071365] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  906.907369] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  907.067334] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  907.227364] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  907.387369] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  907.423399] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  908.607366] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  908.767435] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  913.603334] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  913.763323] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  913.923333] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  914.083335] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  914.119570] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  915.303576] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  915.463383] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  920.295375] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  920.455361] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  920.615309] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  920.775551] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  920.811395] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  921.999360] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  922.159357] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  925.167361] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  925.327347] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  925.487356] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  925.647350] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  925.683391] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  926.871354] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  927.031347] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  928.163355] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  928.323348] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  928.483352] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  928.643352] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  928.679387] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  929.863353] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  930.023477] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  951.167345] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  951.327337] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  951.487339] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  951.647336] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  951.683374] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  952.867342] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  953.027335] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  984.171332] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  984.331327] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  984.491325] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  984.651322] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[  984.687359] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[  985.871329] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[  986.031320] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1027.163306] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1027.323300] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1027.483306] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1027.643310] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1027.679335] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1028.863306] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1029.023302] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1080.171281] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1080.331297] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1080.491282] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1080.651275] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1080.687312] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1081.871277] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1082.031285] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1143.163222] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1143.323219] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1143.483217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1143.643214] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1143.679236] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1144.863249] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1145.023255] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1206.167210] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1206.327223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1206.487231] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1206.647180] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1206.683261] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1207.867223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1208.027221] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1225.303235] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1225.463230] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1225.623235] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1225.783217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1225.819252] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1227.003273] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1227.163216] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1231.995219] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1232.155171] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1232.315219] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1232.475217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1232.511249] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1233.699215] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1233.859248] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1238.695213] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1238.855211] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1239.015223] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1239.175217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1239.211254] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1240.395233] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1240.555213] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1245.391212] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1245.551158] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1245.711207] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1245.871211] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1245.907237] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1247.091207] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1247.251246] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1250.175204] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1250.335194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1250.495193] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1250.655194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1250.691232] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1251.875206] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1252.035201] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1253.295208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1253.455185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1253.615208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1253.775207] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1253.811242] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1254.995204] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1255.155214] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1259.987208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1260.147203] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1260.307208] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1260.467536] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1260.503179] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1261.687258] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1261.847205] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1266.683196] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1266.843186] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1267.003221] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1267.163201] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1267.199230] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1268.383199] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1268.543144] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1273.379140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1273.539196] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1273.699152] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1273.859185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1273.895250] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1275.079148] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1275.239147] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1278.183151] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1278.343175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1278.503185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1278.663189] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1278.699224] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1279.883195] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1280.043193] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1281.259203] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1281.419192] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1281.579200] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1281.743147] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1281.779167] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1282.963151] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1283.123187] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1287.959240] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1288.119194] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1288.279147] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1288.439191] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1288.475269] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1289.659180] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1289.819193] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1294.655184] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1294.815217] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1294.975181] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1295.135219] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1295.171187] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1296.359185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1296.519132] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1301.351310] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1301.511180] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1301.671137] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1301.831197] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1301.867225] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1303.051191] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1303.211133] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1306.183176] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1306.343171] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1306.503172] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1306.663170] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1306.699207] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1307.883175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1308.043174] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1309.243185] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1309.403183] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1309.563186] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1309.723193] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1309.759217] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1310.943190] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1311.103176] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1315.939391] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1316.099165] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1316.259198] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1316.419176] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1316.455261] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1317.643172] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1317.803225] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1322.635179] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1322.795204] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1322.955175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1323.115276] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1323.151138] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1324.335119] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1324.495165] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1329.331166] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1329.491178] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1329.651202] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1329.811170] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1329.847225] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1331.031169] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1331.191170] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1334.207161] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1334.367153] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1334.527157] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1334.687152] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1334.723193] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1335.907166] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1336.067157] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1337.163162] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1337.323175] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1337.483159] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1337.643170] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1337.679210] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1338.863162] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1339.023158] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1360.167167] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1360.327149] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1360.487166] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1360.647112] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1360.683192] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1361.867179] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1362.027148] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1393.163143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1393.323140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1393.483143] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1393.643134] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1393.679165] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0

[ 1394.863150] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1395.023084] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1436.163114] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1436.323105] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1436.483163] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush

[ 1436.643117] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

[ 1436.679084] ieee80211 phy0: rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 0


****************** done ******************


&#12288;

```

---

### Post by varunendra on 2013-12-26
I'm sorry I've completely lost track and grasp of this thread and what we all have been trying here (mostly because you posted multiple threads which have now been merged).

Could you please elaborate what all have you tried so far (links to the guides, posts you followed would be very nice), where did you get that driver that you tried to install only to fail, etc.?

If you are sure you haven't made any critical changes that you don't remember or can't revert now, we can try installing a newer driver, hopefully one that works with this kernel.

Oh, and does this system only has a wireless card and no Ethernet?? That would be a big surprise for me, but if so, do you have any alternate way to connect Ubuntu to internet? That would be a great help should we need to install some support packages.

---

