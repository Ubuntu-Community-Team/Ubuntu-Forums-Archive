---
title: "How to install wifi driver on unbuntu?"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by RadScorpius on 2014-01-15
I just recently installed Ubuntu on my Lenovo ThinkPad E540,  now I can not figure out how to install the driver for the wireless  adopter. I've seen people with the exact same computer and have the wifi  working, so there must be a way to install it.


  Please help. Thanks

---

### Post by RadScorpius on 2014-01-15
Not only the wifi, also the indicator lights for Cap-lock and number-lock. Are these problems solvable? My laptop is Lenovo's ThinkPad E540 if that helps.

---

### Post by carl4926 on 2014-01-15
So the wifi worked when you were testing it in live mode before install?

I suspect it could be a part of your wifi needs blacklisting
Please post the result of
```
lspci -nnk
```

---

### Post by carl4926 on 2014-01-15
please don't double post

---

### Post by mastablasta on 2014-01-15
what wireless chip do you have?: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
have you tried using additional drivers applicaiton?

---

### Post by QIII on 2014-01-15
*Threads **merged***

---

### Post by RadScorpius on 2014-01-15
> **mastablasta said:**
> what wireless chip do you have?: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
have you tried using additional drivers applicaiton?

I tried that but it said i have no additional drivers that i can install. The wireless chip is Realtek RTL8723BE wireless LAN (64-bit).

---

### Post by RadScorpius on 2014-01-15
> **carl4926 said:**
> So the wifi worked when you were testing it in live mode before install?

I suspect it could be a part of your wifi needs blacklisting
Please post the result of
```
lspci -nnk
```

It worked when i still had Windows 8 on it.

---

### Post by carl4926 on 2014-01-15
> **zhunter141 said:**
> It worked when i still had Windows 8 on it.
Sorry
Please post the code we need to see to help you

---

### Post by RadScorpius on 2014-01-15
> **carl4926 said:**
> Sorry
Please post the code we need to see to help you

What you mean the code?

---

### Post by carl4926 on 2014-01-15
> **carl4926 said:**
> So the wifi worked when you were testing it in live mode before install?

I suspect it could be a part of your wifi needs blacklisting
Please post the result of
```
lspci -nnk
```

Open a terminal
Paste the above code in to it and hit enter

Copy the result with your mouse and paste it herein code tags #

---

### Post by 3rdalbum on 2014-01-15
You can open a terminal by pressing Control-Alt-T.

---

### Post by astrob0t on 2014-01-15
Carl4926 had asked to post the result of the below code

```
[SIZE=4]lspci -nnk[/SIZE]
```

To do this, please open up terminal by pressing ***ctrl+alt+t ***or any other GUI way possible and copy paste the above command in to the terminal and hit ***return***
Then copy the result and post it below.

---

### Post by wildmanne39 on 2014-01-15
*Thread moved to **Networking & Wireless**.*

---

### Post by RadScorpius on 2014-01-15
> **carl4926 said:**
> Open a terminal
Paste the above code in to it and hit enter

Copy the result with your mouse and paste it herein code tags #

Here is everything i got.

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller [8086:0c04] (rev 06)
    Subsystem: Lenovo Device [17aa:5028]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
    Subsystem: Lenovo Device [17aa:502a]
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 [8086:8c18] (rev d4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM87 Express LPC Controller [8086:8c4b] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c03] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 04)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel modules: i2c-i801
01:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 740M] [10de:1292] (rev a1)
    Subsystem: Lenovo Device [17aa:502a]
    Kernel modules: nouveau, nvidiafb
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5227] (rev 01)
    Subsystem: Lenovo Device [17aa:5028]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:5028]
    Kernel driver in use: r8169
    Kernel modules: r8169
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: Lenovo Device [17aa:b728]

---

### Post by chili555 on 2014-01-15
Please see my answer here: [http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)  You have the same device and require the same driver. Please feel free to post back if you need additional guidance.

---

### Post by carl4926 on 2014-01-15
Yuck
[http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)

---

### Post by RadScorpius on 2014-01-15
> **chili555 said:**
> Please see my answer here: [http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)  You have the same device and require the same driver. Please feel free to post back if you need additional guidance.

Do i type and excute these commands one at a time or all of them together? And what is the "second link"?

sudo apt-get install linux-headers-generic build-essential git
git clone [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)
cd rtl8723be
make
sudo make install
sudo modprobe rtl8723be

---

### Post by chili555 on 2014-01-15
> **carl4926 said:**
> Yuck
[http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10](http://askubuntu.com/questions/389268/no-wifi-connection-on-ubuntu-13-10)It is actually pretty easy to implement the solution. Figuring out how to do the solution in the first place and trying it on my test mule was yuck.

Only the OP can decide if it is worse than having no wireless at all or buying a 50 ft. CAT5 cable.

---

### Post by chili555 on 2014-01-15
> **RadScorpius said:**
> Do i type and excute these commands one at a time or all of them together? And what is the "second link"?

sudo apt-get install linux-headers-generic build-essential git
git clone [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)
cd rtl8723be
make
sudo make install
sudo modprobe rtl8723beSimply copy and paste each command one at a time and press enter after each one. The second link is part of the command. Just copy and paste it, too. 

Off to lunch with Mrs. Chili; the others will help if you get stuck. I hope I return to see a [SOLVED].

---

### Post by RadScorpius on 2014-01-15
> **chili555 said:**
> Simply copy and paste each command one at a time and press enter after each one. The second link is part of the command. Just copy and paste it, too. 

Off to lunch with Mrs. Chili; the others will help if you get stuck. I hope I return to see a [SOLVED].

So after i did all the commands do i always have to do this after restart? 
cd ~/rtl8723be
make clean
make
sudo make install
sudo modprobe rtl8723be

---

### Post by RadScorpius on 2014-01-15
> **chili555 said:**
> Simply copy and paste each command one at a time and press enter after each one. The second link is part of the command. Just copy and paste it, too. 

Off to lunch with Mrs. Chili; the others will help if you get stuck. I hope I return to see a [SOLVED].

This is what i got from the first few commands, I'm going to restart and see it if worked.

****@Computer-name :~$ sudo apt-get install linux-headers-generic build-essential git
[sudo] password for hunter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 git-man libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl liberror-perl
  libstdc++6-4.6-dev libtimedate-perl
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn
  git-email git-gui gitk gitweb libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.6 git git-man
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libdpkg-perl liberror-perl libstdc++6-4.6-dev libtimedate-perl
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.2 MB of archives.
After this operation, 44.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libstdc++6-4.6-dev amd64 4.6.3-1ubuntu5 [1,660 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++-4.6 amd64 4.6.3-1ubuntu5 [6,954 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++ amd64 4:4.6.3-1ubuntu5 [1,442 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdpkg-perl all 1.16.1.2ubuntu7.2 [180 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main dpkg-dev all 1.16.1.2ubuntu7.2 [469 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main build-essential amd64 11.5ubuntu2.1 [5,816 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main fakeroot amd64 1.18.2-1 [87.2 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main liberror-perl all 0.17-1 [23.8 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main git-man all 1:1.7.9.5-1 [630 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main git amd64 1:1.7.9.5-1 [6,087 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-xs-perl amd64 0.04-2build2 [12.4 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 16.2 MB in 30s (529 kB/s)                                              
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 210385 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7.2_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7.2_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2.1_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.2-1_amd64.deb) ...
Selecting previously unselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously unselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.9.5-1_all.deb) ...
Selecting previously unselected package git.
Unpacking git (from .../git_1%3a1.7.9.5-1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7.2) ...
Setting up dpkg-dev (1.16.1.2ubuntu7.2) ...
Setting up fakeroot (1.18.2-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.9.5-1) ...
Setting up git (1:1.7.9.5-1) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2.1) ...
hunter@edge:~$ git clone [http://github.com/lwfinger/rtl8723be](http://github.com/lwfinger/rtl8723be)
Cloning into 'rtl8723be'...
remote: Reusing existing pack: 70, done.
remote: Total 70 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (70/70), done.
hunter@edge:~$ cd rtl8723be
hunter@edge:~/rtl8723be$ make
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  CC [M]  /home/hunter/rtl8723be/base.o
  CC [M]  /home/hunter/rtl8723be/rc.o
  CC [M]  /home/hunter/rtl8723be/debug.o
  CC [M]  /home/hunter/rtl8723be/regd.o
  CC [M]  /home/hunter/rtl8723be/efuse.o
  CC [M]  /home/hunter/rtl8723be/cam.o
  CC [M]  /home/hunter/rtl8723be/ps.o
  CC [M]  /home/hunter/rtl8723be/core.o
  CC [M]  /home/hunter/rtl8723be/stats.o
  CC [M]  /home/hunter/rtl8723be/pci.o
  LD [M]  /home/hunter/rtl8723be/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hunter/rtl8723be/rtlwifi.mod.o
  LD [M]  /home/hunter/rtl8723be/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Entering directory `/home/hunter/rtl8723be/btcoexist'
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be/btcoexist modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  CC [M]  /home/hunter/rtl8723be/btcoexist/halbtc8723b2ant.o
  CC [M]  /home/hunter/rtl8723be/btcoexist/halbtcoutsrc.o
  CC [M]  /home/hunter/rtl8723be/btcoexist/rtl_btc.o
  LD [M]  /home/hunter/rtl8723be/btcoexist/btcoexist.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hunter/rtl8723be/btcoexist/btcoexist.mod.o
  LD [M]  /home/hunter/rtl8723be/btcoexist/btcoexist.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Leaving directory `/home/hunter/rtl8723be/btcoexist'
make[1]: Entering directory `/home/hunter/rtl8723be/rtl8723be'
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be/rtl8723be modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  CC [M]  /home/hunter/rtl8723be/rtl8723be/hw.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/table.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/sw.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/trx.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/led.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/fw.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/phy.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/rf.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/dm.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/pwrseq.o
  CC [M]  /home/hunter/rtl8723be/rtl8723be/pwrseqcmd.o
  LD [M]  /home/hunter/rtl8723be/rtl8723be/rtl8723be.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hunter/rtl8723be/rtl8723be/rtl8723be.mod.o
  LD [M]  /home/hunter/rtl8723be/rtl8723be/rtl8723be.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Leaving directory `/home/hunter/rtl8723be/rtl8723be'
hunter@edge:~/rtl8723be$ sudo make install
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Entering directory `/home/hunter/rtl8723be/btcoexist'
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be/btcoexist modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Leaving directory `/home/hunter/rtl8723be/btcoexist'
make[1]: Entering directory `/home/hunter/rtl8723be/rtl8723be'
make -C /lib/modules/3.2.0-58-generic/build M=/home/hunter/rtl8723be/rtl8723be modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic'
make[1]: Leaving directory `/home/hunter/rtl8723be/rtl8723be'
find /lib/modules/3.2.0-58-generic -name "btcoexist_*.ko" -exec rm {} \;
find /lib/modules/3.2.0-58-generic -name "r8723be_*.ko" -exec rm {} \;
sudo modprobe rtl8723be
hunter@edge:~/rtl8723be$ sudo modprobe rtl8723be

---

### Post by RadScorpius on 2014-01-15
Solved!!! Thanks Chili!!!

---

### Post by yo_iss on 2014-05-02
Under Ubuntu 14.04, if 
```
$ make
```
returns errors, stay in your rtl8723be directory, just do a 
```
$ [COLOR=#000000][FONT=Ubuntu Mono]git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
and then ```
$ make
$ sudo make install
$ sudo modprobe rtl8723be
```
as said in [/FONT][/COLOR]http://ubuntuforums.org/showthread.php?t=2205497

Worked fine for me ; thanks to all

Medion Akoya MD99330 (E1318T Notebook)

---

