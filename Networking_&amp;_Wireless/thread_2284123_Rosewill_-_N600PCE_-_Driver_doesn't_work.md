---
title: "Rosewill - N600PCE - Driver doesn't work"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by Drakarian on 2015-06-27
Hi All,

I have an issue with my wireless card, it seems the linux driver provided by rosewill is too old, I have read several forums about this but haven't been able to resolve the issue. 

this is the error message:

```
make -C tools
make[1]: Entering directory `/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools'
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/tools/bin2h
cp -f os/linux/Makefile.6 /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/Makefile
make -C /lib/modules/3.16.0-41-generic/build SUBDIRS=/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-41-generic'
  CC [M]  /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.o
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:505:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
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
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:31,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:32:
./arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:507:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
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
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:31,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:32:
./arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
 void *memmove(void *dest, const void *src, size_t count);
       ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:659:20: warning: assignment makes integer from pointer without a cast [enabled by default]
   pClonedPkt->tail = pClonedPkt->data + pClonedPkt->len;
                    ^
In file included from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_os.h:44:0,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/rtmp_comm.h:69,
                 from /home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:32:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/include/os/rt_linux.h:1001:34: warning: assignment makes integer from pointer without a cast [enabled by default]
   ((RTPKT_TO_OSPKT(_pkt))->tail) = (PUCHAR)((_start) + (_len))
                                  ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:678:2: note: in expansion of macro &#8216;SET_OS_PKT_DATATAIL&#8217;
  SET_OS_PKT_DATATAIL(pRxPkt, pData, DataSize);
  ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:705:15: warning: assignment makes integer from pointer without a cast [enabled by default]
  pOSPkt->tail = pOSPkt->data + pOSPkt->len;
               ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c: In function &#8216;__RtmpOSFSInfoChange&#8217;:
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:1133:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t&#8217;
   pOSFSInfo->fsuid = current_fsuid();
                    ^
/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.c:1134:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t&#8217;
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/darkarian/Desktop/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-41-generic'
make: *** [LINUX] Error 2
```

---

### Post by QIII on 2015-06-27
When pasting the results of commands in the terminal, please use code tags.  It preserves formatting and makes your posts much easier to read.

If you are using the "Reply to Thread" button or starting a new thread - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

