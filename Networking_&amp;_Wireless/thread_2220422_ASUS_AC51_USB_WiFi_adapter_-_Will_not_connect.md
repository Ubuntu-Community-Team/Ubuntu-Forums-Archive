---
title: "ASUS AC51 USB WiFi adapter - Will not connect"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by nick107 on 2014-04-27
Hello everyone! New user to linux, currently running Ubuntu 14 and i am loving it so far! Just need to learn the ropes :P


This is my first post, however I have searched far and wide for an answer and have tried many solutions
but I still seem to have an error.

I bought an [Asus AC51]("http://www.amazon.com/Dual-Band-Wireless-AC600-Wi-Fi-Adapter-USB-AC51/dp/B00HM0K61Y") and followed [this]("http://ubuntuforums.org/showthread.php?t=2152658") tutorial to get it working. I used the files from the CD it came with rather than the ones in the turorial. However I get an error when I sudo make inside the /mt7610u_wifi_sta_v3001_dpo_20130725 folder. Here is the error

```
nick@nkuzyk1:~/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725$ sudo make[sudo] password for nick: 
make -C tools
make[1]: Entering directory `/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/tools'
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/tools/bin2h
chipset = mt7650u
chipset = mt7630u
chipset = mt7610u
cp -f os/linux/Makefile.6 /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/Makefile
make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.o
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsUsDelay&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:176:8: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
  ULONG i;
        ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:500:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pHeader802_3, HdrLen);
   ^
In file included from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/os/rt_linux.h:31,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_os.h:44,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_comm.h:75,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:31:
/usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:502:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
   NdisMoveMemory(skb->tail, pData, DataSize);
   ^
In file included from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/cpumask.h:4,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/msr.h:10,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/processor.h:20,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/thread_info.h:22,
                 from include/linux/thread_info.h:54,
                 from /usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/os/rt_linux.h:31,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_os.h:44,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_comm.h:75,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:31:
/usr/src/linux-headers-3.13.0-24-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:653:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_os.h:44:0,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/rtmp_comm.h:75,
                 from /home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:31:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/include/os/rt_linux.h:886:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:672:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:698:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:1109:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:1110:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();
                    ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpDrvAllRFPrint&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:2032:4: warning: passing argument 2 of &#8216;file_w->f_op->write&#8217; from incompatible pointer type [enabled by default]
    file_w->f_op->write(file_w, pBuf, BufLen, &file_w->f_pos);
    ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:2032:4: note: expected &#8216;const char *&#8217; but argument is of type &#8216;UINT32 *&#8217;
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:2017:22: warning: unused variable &#8216;macValue&#8217; [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
                      ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:2017:9: warning: unused variable &#8216;macAddr&#8217; [-Wunused-variable]
  UINT32 macAddr = 0, macValue = 0;
         ^
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSIRQRelease&#8217;:
/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.c:2153:21: warning: unused variable &#8216;net_dev&#8217; [-Wunused-variable]
  struct net_device *net_dev = (struct net_device *)pNetDev;
                     ^
make[2]: *** [/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/nick/Desktop/asus/mt7610u_wifi_sta_v3001_dpo_20130725/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [LINUX] Error 2


 
```
Hopefully thats enough info. Thanks for the support!

---

### Post by nick107 on 2014-04-28
Anyone at all? Would love to start using Ubuntu as my main OS

---

### Post by ryder-tim on 2014-07-29
I am having the same exact issue.   Not sure what the error is.

---

### Post by chili555 on 2014-07-29
There is a newer version of the driver available, but don't bother. I tried it and it won't compile in 14.04 either. I currently know of no way to get this device going aside from trying the tricky and twitchy ndiswrapper. We could try that or you could get an inexpensive USB wireless device and wait six months or so to see if a driver is included in future kernel versions.

If you want to try ndiswrapper, you will need Windows **XP** inf and probably sys files appropriate to your architecture; either 32- or 64-bit.

---

### Post by praseodym on 2014-07-29
[http://www.mediatek.com/en/downloads/mt7610u-usb/](http://www.mediatek.com/en/downloads/mt7610u-usb/)

According to here it is supported until kernel 3.11, which is Ubuntu 12.04.5 (or using the LTE stack). So you should install that instead of 14.04.

---

### Post by likwidoxigen on 2015-01-18
Resurrecting this thread. Fixed up the driver for 14.10 with Kernel 3.16.0-29-generic. It's not pretty but it works.
I'll likely keep the driver updated for a bit if things stop working 

Updated driver source and instructions on:
[https://github.com/likwidoxigen/mt7610u_wifi](https://github.com/likwidoxigen/mt7610u_wifi)

Cheers!

---

### Post by Alexander_Andreyev on 2015-10-11
Apparently, your fix does not work.  I tried your code base with Linux 3.11, 3.13 on Ubuntu 14.04.3 LTS , 3.19 on Ubuntu 15.04.   In all cases result is the same: the kernel module builds with lots of warnings, loads successfully and the adapter connects to the base station.  However, in 3-5 seconds of moderate network load (opening a page in FireFox) the kernel freezes, forcing me to use hardware hard reset button. Any help appreciated!

---

### Post by likwidoxigen on 2015-10-11
All correct. Check the github. Connects and works perfect on GN mixed networks a and ac seem to break it. No idea why because *buntu won't drop a kernel dump to go through or give any sort of debugging info. If you've got debugging info or a anything else that can help post it up on gitub or here.

Thanks!!

> **Alexander_Andreyev said:**
> Apparently, your fix does not work.  I tried your code base with Linux 3.11, 3.13 on Ubuntu 14.04.3 LTS , 3.19 on Ubuntu 15.04.   In all cases result is the same: the kernel module builds with lots of warnings, loads successfully and the adapter connects to the base station.  However, in 3-5 seconds of moderate network load (opening a page in FireFox) the kernel freezes, forcing me to use hardware hard reset button. Any help appreciated!

---

