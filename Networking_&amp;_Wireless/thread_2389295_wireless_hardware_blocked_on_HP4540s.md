---
title: "wireless hardware blocked on HP4540s"
date: 2018-04-14
forum: Networking &amp; Wireless
---

### Post by bowowon on 2018-04-14
Hi all, 

 I try to connect to my wireless on my HP4540s but my terminal indicate : 

 ```
 ~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes 
  :~$ rfkill unblock all
~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
~$ sudo rfkill unblock all
[sudo] password for ulimwengu: 
~$ rfkill list all
    Soft blocked: no
    Hard blocked: yes
```
 ```
 lsmod | grep -e hp -e wmi
snd_rawmidi            32768  1 snd_seq_midi
wmi_bmof               16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_pcm
shpchp                 36864  0
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    24576  2 wmi_bmof,hp_wmi
```


```
$ sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
$ sudo modprobe -r hp-wireless
$  sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```


```
$ sudo modprobe hp-wmi
$ sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
$ sudo unblock all 


$ sudo rfkill unblock all 
$ sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
$ :(
```



Here what I have done,

But nothing work, what can I do ? 

Kind regard,
Armand

---

### Post by chili555 on 2018-04-14
Please check here: [https://askubuntu.com/questions/811575/ubuntu-server-16-04-01-no-internet-connection](https://askubuntu.com/questions/811575/ubuntu-server-16-04-01-no-internet-connection)

You have already tried unloading hp-wmi with no result. I am afraid the only option left is to tape off the pin.

---

### Post by bowowon on 2018-04-14
Thank for your answer chili555, 

I get an eye currently,

Edit : I have follow the recommandation, my wifi receive packages and all but still unable to connect my computer at the network,  what can I do ?

Kind regard,
Armand

---

### Post by chili555 on 2018-04-14
The short version is that you have tried the wireless or Airplane Mode button and there was no change. You tried removing hp-wmi and there was no change. The only thing that I know of that is left is to apply tape to the pin that reports the position of the wireless switch. Sometimes, it's pin 13 or pin 20: [http://www.jarzebski.pl/files/images/mask-pin-20-2.jpg](http://www.jarzebski.pl/files/images/mask-pin-20-2.jpg)

If you are not comfortable removing and reinstalling the wireless card, do not proceed. I haven't any other suggestions.

---

### Post by bowowon on 2018-04-14
I will try, learning by doing is the only thing, 

Thank you for your time, maybe I will update our discussion if any,

Thank you again, regard,
Armand

---

### Post by bowowon on 2018-04-17
Hi,

I have try to install driver and all, I am on the *_[RT3290 Linux Driver (Ubuntu 16.04 or latest)]("http://www.linkbucks.com/AXqEa")_* ubuntu driver of [http://onthim.blogspot.fr/2015/06/install-ralink-rt3290-wi-fi-driver-on.html](http://onthim.blogspot.fr/2015/06/install-ralink-rt3290-wi-fi-driver-on.html) .

Currently I get this error : 
 
make -C tools
make[1]: Entering directory '/home/ulimwengu/Downloads/RT3290_u16/src/tools'
gcc -g bin2h.c -o bin2h
chmod +x bin2h
make[1]: Leaving directory '/home/ulimwengu/Downloads/RT3290_u16/src/tools'
/home/ulimwengu/Downloads/RT3290_u16/src/tools/bin2h
cp -f os/linux/Makefile.6 /home/ulimwengu/Downloads/RT3290_u16/src/os/linux/Makefile
make -C /lib/modules/4.13.0-38-generic/build SUBDIRS=/home/ulimwengu/Downloads/RT3290_u16/src/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.13.0-38-generic'
  CC [M]  /home/ulimwengu/Downloads/RT3290_u16/src/os/linux/../../os/linux/sta_ioctl.o
In file included from ./include/linux/bitmap.h:8:0,
                 from ./include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/cpufeature.h:4,
                 from ./arch/x86/include/asm/thread_info.h:63,
                 from ./include/linux/thread_info.h:37,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from ./include/linux/preempt.h:80,
                 from ./include/linux/spinlock.h:50,
                 from ./include/linux/seqlock.h:35,
                 from ./include/linux/time.h:5,
                 from ./include/linux/stat.h:18,
                 from ./include/linux/module.h:10,
                 from /home/ulimwengu/Downloads/RT3290_u16/src/include/os/rt_linux.h:18,
                 from /home/ulimwengu/Downloads/RT3290_u16/src/include/rtmp_os.h:42,
                 from /home/ulimwengu/Downloads/RT3290_u16/src/include/rtmp_comm.h:56,
                 from /home/ulimwengu/Downloads/RT3290_u16/src/os/linux/../../os/linux/sta_ioctl.c:33:
In function &#8216;memcpy&#8217;,
    inlined from &#8216;rt_ioctl_iwaplist&#8217; at /home/ulimwengu/Downloads/RT3290_u16/src/os/linux/../../os/linux/sta_ioctl.c:700:2:
./include/linux/string.h:305:4: error: call to &#8216;__read_overflow2&#8217; declared with attribute error: detected read beyond size of object passed as 2nd parameter
    __read_overflow2();
    ^
scripts/Makefile.build:308: recipe for target '/home/ulimwengu/Downloads/RT3290_u16/src/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/home/ulimwengu/Downloads/RT3290_u16/src/os/linux/../../os/linux/sta_ioctl.o] Error 1
Makefile:1550: recipe for target '_module_/home/ulimwengu/Downloads/RT3290_u16/src/os/linux' failed
make[1]: *** [_module_/home/ulimwengu/Downloads/RT3290_u16/src/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-38-generic'
Makefile:380: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2

Maybe someone have an advice ? 
Thank you

---

### Post by chili555 on 2018-04-17
I am unfamiliar with the package. As well, the link to the driver doesn't open for me. 

[SIZE=3]**This site can’t be reached**[/SIZE]
[www.linkbucks.com](www.linkbucks.com) refused to connect.


The blogspot page claims it's for weak signal strength; you don't have that.

Do you have that device?```
lspci -nnk | grep 0280 -A3
```I'd ask the author of the driver for advice about the error.

---

### Post by jeremy31 on 2018-04-17
It is unlikely that 2 year old source code will compile on the 4.13 kernel.  You can try going into BIOS and reset to defaults and see if that unblocks the wifi or you can mask the pin

---

