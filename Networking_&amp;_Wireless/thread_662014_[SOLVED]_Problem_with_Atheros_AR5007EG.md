---
title: "[SOLVED] Problem with Atheros AR5007EG"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by jank on 2008-01-08
Hello 
I am aware that there is several other posts on this specific card,but I either don't understand the guides (yes i'm a noob) or they don't work. If anyone have a detailed how to make this cart work i would be very grateful. I am running 7.10
Plz help

---

### Post by reckless2k2 on 2008-01-08
does this card show up to enable in the restricted drivers list?

---

### Post by jank on 2008-01-08
nope

---

### Post by jank on 2008-01-08
sorry i answered too fast. I thik it shows up. It is called Atheros Hardware acess layer and is enabled.

---

### Post by reckless2k2 on 2008-01-08
i just peeked around and there looks like quite a bit of info on this card on the boards down to the setup. you have to use ndiswrapper it looks like which is odd but it must mean that there's a bug in the driver and this card. have you done anything yet to try to get this going?

this thread looks like good place/directions to follow. 

[http://ubuntuforums.org/showthread.php?t=580672&highlight=Atheros+AR5007EG](http://ubuntuforums.org/showthread.php?t=580672&highlight=Atheros+AR5007EG)

i would say the feisty issue carried over to gusty.

---

### Post by reckless2k2 on 2008-01-08
i think i gave you the worng post:

[http://ubuntuforums.org/showpost.php?p=3101929&postcount=1](http://ubuntuforums.org/showpost.php?p=3101929&postcount=1)

do me a favor and post the results of 

```
lspci -v
```

i just want to make sure it's not just a blacklist issue.

---

### Post by jank on 2008-01-08
thx for the replies I have tried bmartins post (the last) and didn't get it to work. can't try again right now as i don't have access to a wired line. Will post results tomorrow.

---

### Post by jank on 2008-01-09
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, fast devsel, latency 0
        Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: ff200000-ff2fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e880 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at e800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e480 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff300000-ff3fffff
        Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7128
        Flags: fast devsel, IRQ 17
        Memory at ff2f0000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff40
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at d800 [size=256]
        Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
here is the output. Btw how do you get it inside the code box?

---

### Post by reckless2k2 on 2008-01-09
so you have tried to install ndiswrapper and followed that tutorial from before? like if you run 

```
sudo ndiswrapper -l 
```

it shows what? 

i'm just curious because i think the issue is blacklisting the buggy driver built into ubuntu in order to get the ndis driver to work. i did notice that in the other 2 posts. 1 post shows single blacklist while the other post shows a more extensive blacklisting of ath driver.

also post the results of this for me:

sudo iwconfig

sudo ifconfig

---

### Post by jank on 2008-01-09
Jan@jan-laptop:~$ sudo ndiswrapper -l
provide password for jan:
Jan@jan-laptop:~$

it might not be correct to the letter. I thought it was wrong and reopened the terminal and wrote:
Jan@jan-laptop:~$ sudo ndiswrapper -l
Jan@jan-laptop:~$
no password request now.


jan@jan-laptop:~$ sudo iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



jan@jan-laptop:~$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1A:92:FB:D0:CF  

          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::21a:92ff:fefb:d0cf/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:70090 errors:0 dropped:0 overruns:0 frame:0

          TX packets:44392 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:96175785 (91.7 MB)  TX bytes:4325391 (4.1 MB)

          Interrupt:16 Base address:0xc00 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:18 errors:0 dropped:0 overruns:0 frame:0

          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

---

### Post by jank on 2008-01-09
sry for the smiley. here is the line again with a space to prevent it to turn into a smiley again :D

eth0      Link encap:Ethernet  HWaddr 00:1A:92:FB: D0:CF

---

### Post by Digger78 on 2008-01-09
open a terminal 

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```

extract the contents

```
tar -xvf madwifi-ng-r2756+ar5007.tar.gz
```

change to extracted folder

```
cd madwifi-ng-r2756+ar5007
```

compile and install

```
make
```

```
sudo make install
```

**reboot**

open a terminal and type

```
iwlist scan
```

Post the output here, it will confirm if the drivers are installed properly

HTH

---

### Post by reckless2k2 on 2008-01-09
i guess i'm a little confused. if you followed those other posts then you should have had some drivers when you issue that command to check for drivers. did you remove them after they didn't work? 

i'm just a little confused. it looks as though you didn't follow that post and get the drivers. 

if you're on 7.10, you have to follow this link to get ndiswrapper going on the system:

[http://ubuntuforums.org/showthread.php?t=611273](http://ubuntuforums.org/showthread.php?t=611273)

that kinda gets you in the door. you have to have the drivers for that card though. that one post had the drivers. 

after you do all that good stuff from my link right above, you have to blacklist ath as per the previous links i provided. 

in total, that will enable the wifi card using ndis with windows drivers and disable the builtin ath driver in ubuntu that's buggy. 

that check command was 

```
sudo ndiswrapper -l
```

that is a lower case L and not a number one. if you have output of drivers, don't do what i said above because you probably already have the windows drivers installed and you just need to blacklist ath right which is in the other links.

---

### Post by jank on 2008-01-10
My drives don't have any letter besides their name. Is it still possible for me to extract from the terminal? This is what i tried:
jan@jan-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
jan@jan-laptop:~$ cd File Systen:\home\jan\madwifi
bash: cd: File: No such file or directory
jan@jan-laptop:~$ cd File System:/home/jan/madwifi
bash: cd: File: No such file or directory
jan@jan-laptop:~$ C:\home\jan\madwifi
bash: C:homejanmadwifi: command not found
jan@jan-laptop:~$ cd C:\home\jan\madwifi
bash: cd: C:homejanmadwifi: No such file or directory
jan@jan-laptop:~$ cd /file system/home/jan/madwifi
bash: cd: /file: No such file or directory

plz post an example. I have only one linux disk, but i have three windows disks.

still no luck with Ndiswrapper
jan@jan-laptop:~$ ndiswrapper-l
bash: ndiswrapper-l: command not found
jan@jan-laptop:~$ sudo ndiswrapper-l
[sudo] password for jan:
sudo: ndiswrapper-l: command not found
jan@jan-laptop:~$ sudo ndiswrapper-l
sudo: ndiswrapper-l: command not found

---

### Post by Digger78 on 2008-01-10
I have edited my previous post to make it easier.

---

### Post by jank on 2008-01-10
jan@jan-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by jank on 2008-01-10
everything worked well until make here is the code:
jan@jan-laptop:~/madwifi-ng-r2756+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/jan/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/jan/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/jan/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/jan/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
jan@jan-laptop:~/madwifi-ng-r2756+ar5007$ 


sorry for double posting but editing didn't work

---

### Post by Digger78 on 2008-01-10
try

```
sudo apt-get install build-essential
```

then try again from "make"

---

### Post by jank on 2008-01-10
Thanks for all the help. You are both thanked.

---

### Post by Digger78 on 2008-01-10
So it worked?

---

### Post by jank on 2008-01-11
yup thanks again.

---

### Post by Digger78 on 2008-01-11
Np, glad i could help :)

please mark the thread as solved (thread tools)

---

