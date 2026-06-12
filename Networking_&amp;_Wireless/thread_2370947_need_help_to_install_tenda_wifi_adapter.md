---
title: "need help to install tenda wifi adapter"
date: 2017-09-08
forum: Networking &amp; Wireless
---

### Post by bipin1990 on 2017-09-08
Dear all, i'm trying to install my tenda wifi adapter on ubuntu 14.04 os bu i'm failed i need help to install it. and if anyone can help me in installing on remote server please help me... thanks.

---

### Post by wildmanne39 on 2017-09-08
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2017-09-09
Please click on the "Wireless Script" link in wildmanne39's signature and follow the instructions there

---

### Post by bipin1990 on 2017-09-10
koha@ubuntu:~/Desktop$ cd DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
koha@ubuntu:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo su
[sudo] password for koha: 
root@ubuntu:/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# sudo su
root@ubuntu:/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# make
make -C tools
make[1]: Entering directory `/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: fatal error: stdio.h: No such file or directory
 #include <stdio.h>
                   ^
compilation terminated.
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/tools'
make: *** [build_tools] Error 2
root@ubuntu:/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# make install
make -C /home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Usta.ko /lib/modules/3.16.0-77-generic/kernel/drivers/net/wireless/
install: cannot stat ‘mt7601Usta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
make: *** [install] Error 2
root@ubuntu:/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913# ^C
root@ubuntu:/home/koha/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913#

---

### Post by bipin1990 on 2017-09-10
These error i found..:confused::confused:

---

### Post by bipin1990 on 2017-09-10
can anyone help me on teamviewver?

---

### Post by mörgæs on 2017-09-10
Which Tenda adapter?

---

### Post by QIII on 2017-09-10
Please do not ask for help via TeamViewer, email, private message or any other method. 

First, you don't know anyone here from Adam and that is fantastically unsafe.

Second, that would rob the community of the ability to see the solution.  The Ubuntu Forums are a community resource.  They are not here for your private support only.

Thanks.

---

### Post by coffeecat on 2017-09-10
@bipin1990, in post #3, praseodym wrote:

> **praseodym said:**
> Please click on the "Wireless Script" link in wildmanne39's signature and follow the instructions there

Did you see that post? Did you do what he asks?

The reason I ask is that in your post - #4 of this thread - you appear to have ignored praseodym and instead posted the output of a failed attempt to compile a wireless driver that may or may not be relevant to your device. Compiling your own driver may or may not be the best option for you but, before a judgement can be made about that, forum members need the information provided by the wireless script that praseodym mentions, and which is linked in wildmanne39's signature.

Please help others to help you.

---

### Post by jeremy31 on 2017-09-10
Why not use the 4.4 kernel from 16.04 as it does support the MT7601U?  See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by chenzero on 2017-09-10
It seems that you also encountered problem on installing driver for Ralink MT7601U, 
I also can not get it work on 16.04.

Not sure if the drivers I tried work on 14.04 or not,
but F.Y.I:
[https://ubuntuforums.org/showthread.php?t=2371077](https://ubuntuforums.org/showthread.php?t=2371077)

---

