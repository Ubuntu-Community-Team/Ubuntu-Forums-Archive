---
title: "Dongle Nintendo/Datel Wifimax - Feisty 2.6.20"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by Ryosaeba on 2007-06-21
Good evening everybody,

Not only I am a "newb" in linux but I am french too, so please excuse my poor english.

As mentioned in the title of this post, I have some trouble with the installation of my dongle nintendo on festy 2.6.20 to use it as an access point for my wii.

I have found the following posts explaining how to install the driver zd1211b :
[http://ubuntuforums.org/archive/index.php/t-422499.html](http://ubuntuforums.org/archive/index.php/t-422499.html)
[http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211](http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211)
Patch : [http://www.nabble.com/-PATCH--Make-zd1211-work-with-2.6.20-t3283562.html](http://www.nabble.com/-PATCH--Make-zd1211-work-with-2.6.20-t3283562.html)

My main issue is that I can't compile the driver (step 10). When I don't use the patch, I obtain the following message error :

```

ryosaeba@RYOSAEBA:/usr/src/ZD1211LnxDrv_2_16_0_0$ sudo make
/lib/modules/2.6.20-16-generic/build
/usr/src/ZD1211LnxDrv_2_16_0_0
-I/usr/src/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211B -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/src/ZD1211LnxDrv_2_16_0_0 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.20-16-generic »
  CC [M]  /usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: erreur: linux/config.h : Aucun fichier ou répertoire de ce type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: attention : initialization from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: erreur: expected declaration specifiers or «..." before «write"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: erreur: expected declaration specifiers or «..." before «fd"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: erreur: expected declaration specifiers or «..." before «buf"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: erreur: expected declaration specifiers or «..." before «count"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: attention : type defaults to «int" in declaration of «_syscall3"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: erreur: expected «," or «;" before «_syscall3"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: erreur: «dot11A_Channel" undeclared here (not in a function)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function «zd1205_xmit_frame":
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5025: attention : ISO C90 forbids mixed declarations and code
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5026: attention : assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5029: attention : assignment from incompatible pointer type
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function «zd1205_load_card_setting":
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8708: attention : implicit declaration of function «open"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8725: attention : implicit declaration of function «read"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8729: attention : implicit declaration of function «close"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function «zd1205_save_card_setting":
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8881: attention : implicit declaration of function «write"
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function «zd1205_set_zd_cbs":
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10344: attention : assignment from incompatible pointer type
make[2]: *** [/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Erreur 1
make[1]: *** [_module_/usr/src/ZD1211LnxDrv_2_16_0_0] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.20-16-generic »
make: *** [all] Erreur 2

```

As far as I am not sure to use correctly the patch, I don't paste the message error I obtained by using it.

Please help me, I miss playing mario striker charged football on line.

Thanks in advance for your help !

---

### Post by Ryosaeba on 2007-06-22
up I really need your help.

---

### Post by Ryosaeba on 2007-06-23
up nobody to help me in compilation ?

---

### Post by Ryosaeba on 2007-06-23
Well, I found the right way to compile the driver. Just use the good one ! There is a new one released in sourgeforge. If you want to get it, just download driver using subversion. In terminal, just type :  svn export [https://zd1211.svn.sourceforge.net/svnroot/zd1211/trunk](https://zd1211.svn.sourceforge.net/svnroot/zd1211/trunk) zd1211.

After that modify the Makefile by editing it and set ZD1211REV_B=1 for ZD1211B and follow the instructions of the tutorial.

Now, my dongle is installed, my Wii detect my SSID but even if I don't set up any kind of protection (no wep no wpa), I can't connect my wii to internet because of IP issues. Then, I assume that it is only some configuration to do so please help me to finalize this installation.

Here is what I type in the terminal to use my dongle as an access point considering that eth0 is my wired connection, eth1 is my wireless connection :
```

sudo -s
modprobe -r zd1211b
depmod
modprobe -v zd1211b
modprobe zd1211b
ip link set dev eth1 up
iwconfig eth1 mode master key s:I TYPE MY CODE HERE
iwconfig eth1 essid "I TYPE MY SSID HERE"
ifconfig eth0 0.0.0.0 up
ifconfig eth1 0.0.0.0 up
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig br0 up
dhcpcd br0

```

Maybe I should set some IP adresses after the ifconfig section instead of 0.0.0.0 but which ones ?

---

### Post by jrevillini on 2007-08-14
thank you VERY much for this information.  tres bien!

---

