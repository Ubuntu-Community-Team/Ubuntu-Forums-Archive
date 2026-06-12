---
title: "Help with installing driver for wireless usb adapter"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by Nitro217 on 2006-12-30
Hi there! 

Have recently converted from Win XP to Xubuntu on a rather old system. Everything went smooth during installation, but I am experiencing huge problems when it comes to making my wireless usb adapter work. I have a 3COM 3CRUSB10075 adapter. [More info here!]("http://www.3com.com/products/en_US/detail.jsp?tab=features&pathtype=purchase&sku=3CRUSB10075")

I have tried different installation solutions, but none have seemed to work. I found an [article on Norwegian]("http://www.linuxmagasinet.no/article/articleview/851/1/3/") explaining a process the author claims should work, but it doesn't seem to do so.

Translated to English:

[LIST=1][*]Download the driver from [http://zd1211.ath.cx/download/zd1211-driver-r48.tgz.]("http://zd1211.ath.cx/download/zd1211-driver-r48.tgz.")
[*]Extract the file using "tar -zxvf zd1211-driver-r48.tgz".
[*]Run "cd zd1211-driver-r48"
[*]"make"
[*]"make install"
[*]Activate driver by using "modprobe -v zd1211"
[/LIST]

I have pasted the entire process from the terminal below. I hope you can figure out what's wrong, because I can't! Alternatively I hope you have some other suggestions on making this work!

Thanks! 

```
user@pc:~/Downloads$ tar -zxvf zd1211-driver-r48.tgz
zd1211-driver-r48/
zd1211-driver-r48/src/
zd1211-driver-r48/src/zdglobal.c
zd1211-driver-r48/src/zdhci.c
zd1211-driver-r48/src/zdglobal.h
zd1211-driver-r48/src/zdshared.c
zd1211-driver-r48/src/zdhci.h
zd1211-driver-r48/src/zdmic.c
zd1211-driver-r48/src/WS11Ur.h
zd1211-driver-r48/src/zd1205_proc.c
zd1211-driver-r48/src/zdshared.h
zd1211-driver-r48/src/zdequates.h
zd1211-driver-r48/src/zdbuf.c
zd1211-driver-r48/src/zdmic.h
zd1211-driver-r48/src/zdpci_hotplug.c
zd1211-driver-r48/src/zdhw.c
zd1211-driver-r48/src/zdsorts.h
zd1211-driver-r48/src/zd80211.h
zd1211-driver-r48/src/zdbuf.h
zd1211-driver-r48/src/zdpci_hotplug.h
zd1211-driver-r48/src/zdhw.h
zd1211-driver-r48/src/zdmmrx.c
zd1211-driver-r48/src/zdconfig
zd1211-driver-r48/src/pHash
zd1211-driver-r48/src/zdsynch.c
zd1211-driver-r48/src/zd1205.c
zd1211-driver-r48/src/zdpci_pcmcia.c
zd1211-driver-r48/src/zdcompat.h
zd1211-driver-r48/src/zdmmrx.h
zd1211-driver-r48/src/zdinlinef.h
zd1211-driver-r48/src/zdusb.c
zd1211-driver-r48/src/zdversion.h
zd1211-driver-r48/src/zd1205.h
zd1211-driver-r48/src/zdpci_pcmcia.h
zd1211-driver-r48/src/zdpsmon.c
zd1211-driver-r48/src/zdusb.h
zd1211-driver-r48/src/WS11UPhR.h
zd1211-driver-r48/src/zdasocsvc.c
zd1211-driver-r48/src/zdpsmon.h
zd1211-driver-r48/src/zdutils.h
zd1211-driver-r48/src/zdtkipseed.c
zd1211-driver-r48/src/zdauthreq.c
zd1211-driver-r48/src/zdtypes.h
zd1211-driver-r48/src/zydas_common.h
zd1211-driver-r48/src/zdtkipseed.h
zd1211-driver-r48/src/zdhw.cpp
zd1211-driver-r48/src/zdapi.h
zd1211-driver-r48/src/WS11UPh.h
zd1211-driver-r48/src/zdpmfilter.c
zd1211-driver-r48/src/zdencrypt.c
zd1211-driver-r48/src/zd1211.c
zd1211-driver-r48/src/zdsm.h
zd1211-driver-r48/src/zddebug.c
zd1211-driver-r48/src/zdauthrsp.c
zd1211-driver-r48/src/zdos.h
zd1211-driver-r48/src/zdpmfilter.h
zd1211-driver-r48/src/zdencrypt.h
zd1211-driver-r48/src/WS11Ub.h
zd1211-driver-r48/src/zd1211.h
zd1211-driver-r48/src/zddebug.h
zd1211-driver-r48/src/WS11UPhm.h
zd1211-driver-r48/sta
zd1211-driver-r48/copying
zd1211-driver-r48/Makefile
zd1211-driver-r48/apdbg.c
user@pc:~/Downloads$ cd zd1211-driver-r48
user@pc:~/Downloads/zd1211-driver-r48$ sudo make
/lib/modules/2.6.17-10-generic/build
/home/user/Downloads/zd1211-driver-r48
-I/home/user/Downloads/zd1211-driver-r48/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/user/Downloads/zd1211-driver-r48 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zd1205.o
/home/user/Downloads/zd1211-driver-r48/src/zd1205.c: In function &#8216;zd1205_tx_isr&#8217;:
/home/user/Downloads/zd1211-driver-r48/src/zd1205.c:1800: warning: &#8216;sw_tcb&#8217; may be used uninitialized in this function
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdasocsvc.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdauthreq.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdauthrsp.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdmmrx.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdshared.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdhci.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdglobal.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdencrypt.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdpmfilter.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdpsmon.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdsynch.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdbuf.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zd1205_proc.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdhw.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zddebug.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdtkipseed.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdmic.o
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdusb.o
/home/user/Downloads/zd1211-driver-r48/src/zdusb.c:396: error: unknown field &#8216;owner&#8217; specified in initializer
/home/user/Downloads/zd1211-driver-r48/src/zdusb.c:396: warning: initialization from incompatible pointer type
make[2]: *** [/home/user/Downloads/zd1211-driver-r48/src/zdusb.o] Error 1
make[1]: *** [_module_/home/user/Downloads/zd1211-driver-r48] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
user@pc:~/Downloads/zd1211-driver-r48$ sudo make install
/lib/modules/2.6.17-10-generic/build
/home/user/Downloads/zd1211-driver-r48
-I/home/user/Downloads/zd1211-driver-r48/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/user/Downloads/zd1211-driver-r48 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/user/Downloads/zd1211-driver-r48/src/zdusb.o
/home/user/Downloads/zd1211-driver-r48/src/zdusb.c:396: error: unknown field &#8216;owner&#8217; specified in initializer
/home/user/Downloads/zd1211-driver-r48/src/zdusb.c:396: warning: initialization from incompatible pointer type
make[2]: *** [/home/user/Downloads/zd1211-driver-r48/src/zdusb.o] Error 1
make[1]: *** [_module_/home/user/Downloads/zd1211-driver-r48] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
user@pc:~/Downloads/zd1211-driver-r48$ 

```

---

### Post by teaker1s on 2006-12-30
make sure you have "build-essential" installed then

make distclean
 make
 sudo make install

---

### Post by Nitro217 on 2006-12-30
And exactly how do I do that? Kind of new to this whole "Linux-deal" so pardon me for being so "blonde". ;)

---

### Post by notoriousdbp on 2006-12-30
in a terminal type sudo apt-get install build-essential
or use synaptic to install it.  The three commands in teaker1s' post are all to be input into a terminal, pressing enter after each one.  Hope that helps.

---

### Post by Nitro217 on 2006-12-30
Mission complete! :p 

After struggling with this for two days now, I have finally configured my wireless network connection!

And I couldn't have done it without you! Thank you a million times! =D> 

The solution was, as you explained, to install "build essentials". I also had to download the newest version of the driver. I just followed the steps I explained in my first posts, and combined them with the last steps of [the guide on zd1211.ath.cx]("http://zd1211.ath.cx/") and puff! Google.com popped up in the Firefox mirror!

Thanks again! ;)

---

