---
title: "Realtek r8180 running with WEP (Hardy)"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by dsdreamer on 2008-05-04
I wanted to report success with the Realtek 8180 with the Philips 2400 radio on Hardy Heron. 

Based on the tar file found at:
[http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html](http://rapidshare.com/files/92812937/rtl818x-mod2.6.24.tar.bz2.html)

It builds nicely under 2.6.24-17-generic
```
tar xjf rtl818x-mod2.6.24.tar.bz2 
ls
cd rtl-wifi/
make
```

Results in...
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_softmac.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_rx.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_tx.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_wx.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_module.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211-rtl.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_ccmp-rtl.o
  CC [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8187_core.o
  CC [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8180_93cx6.o
  CC [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8180_wx.o
  CC [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8180_rtl8225.o
  CC [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8180_rtl8225z2.o
  LD [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8187.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_core.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_sa2400.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_93cx6.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_wx.o
/home/me/code/rtl-wifi/rtl818x-newstack/r8180_wx.c:469: warning: ‘r8180_wx_set_monitor_type’ defined but not used
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_max2820.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_gct.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_rtl8225.o
  CC [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180_rtl8255.o
/home/me/code/rtl-wifi/rtl818x-newstack/r8180_rtl8255.c: In function ‘rtl8255_rf_init’:
/home/me/code/rtl-wifi/rtl818x-newstack/r8180_rtl8255.c:1710: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180.o
  Building modules, stage 2.
  MODPOST 7 modules
  CC      /home/me/code/rtl-wifi/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211-rtl.ko
  CC      /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/me/code/rtl-wifi/ieee80211/ieee80211_crypt_wep-rtl.ko
  CC      /home/me/code/rtl-wifi/rtl8187-newstack/r8187.mod.o
  LD [M]  /home/me/code/rtl-wifi/rtl8187-newstack/r8187.ko
  CC      /home/me/code/rtl-wifi/rtl818x-newstack/r8180.mod.o
  LD [M]  /home/me/code/rtl-wifi/rtl818x-newstack/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
```

Next, following the instructions at the following Wiki: [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing) everything worked as I would have hoped except that I could not get the ieee80211_crypt_wep-rtl module to load automatically.  I simply added it to /etc/modules as a crude but effective way to make it stick.

After 24 hours of use, it seem perfectly stable and robust in station mode using WEP.  

I hope this helps someone.  I believe we should thank Pedro Roginovicci for this patched version which seems to compile and run nicely under Ubuntu 8.10.

--dsdreamer.

---

### Post by Kajaste on 2008-06-19
This is indeed good news for all of us with the rtl8180 and hardy. Using .22 kernel on hardy really sucked. 

A small note: One should first install build-essential and linux-headers-`uname -r` before one can do make.

For convenience here's a list of the commands I used for the install (based on the rtl-wifi installation guide mentioned in the original post):
```

 * * * Getting the source code and build dependencies * * * 
sudo -s
cd /usr/src
apt-get install build-essential module-assistant
module-assistant prepare
wget http://kjo.herbesfolles.org/docs/rtl818x-mod2.6.24.tar.bz2
tar jxf rtl818x-mod2.6.24.tar.bz2
cd rtl-wifi

 * * * Removing the mainline ieee80211 stack (will be replaced) * * *
rm -r /lib/modules/`uname -r`/kernel/net/ieee80211
rm -r /lib/modules/`uname -r`/kernel/net/mac80211
modprobe -r ieee80211 mac80211 cfg80211

 * * * Building and copying over the modules * * *
make
mkdir  /lib/modules/`uname -r`/kernel/net/ieee80211
cp ieee80211/*.ko  /lib/modules/`uname -r`/kernel/net/ieee80211
cp rtl8187-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
cp rtl818x-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
depmod -ae

 * * * Adding modules to autoload * * *
echo ieee80211_crypt_wep-rtl >> /etc/modules
echo ieee80211_crypt_ccmp-rtl >> /etc/modules
echo ieee80211_crypt_tkip-rtl >> /etc/modules

 * * * Loading the modules * * *
modprobe ieee80211_crypt_wep-rtl
modprobe ieee80211_crypt_ccmp-rtl
modprobe ieee80211_crypt_tkip-rtl
modprobe r8180

```

Just as all self-compiled modules, this one has to be recompiled after every kernel update too:
```

sudo -s
cd /usr/src/rtl-wifi

 * * * Remove the mainline ieee80211 stack again * * *
rm -r /lib/modules/`uname -r`/kernel/net/ieee80211
rm -r /lib/modules/`uname -r`/kernel/net/mac80211
modprobe -r ieee80211 mac80211 cfg80211

 * * * Build and copy over the modules * * *
make clean
make
mkdir  /lib/modules/`uname -r`/kernel/net/ieee80211
cp ieee80211/*.ko  /lib/modules/`uname -r`/kernel/net/ieee80211
cp rtl8187-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
cp rtl818x-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
depmod -ae

 * * * Load the modules * * *
modprobe ieee80211_crypt_wep-rtl
modprobe ieee80211_crypt_ccmp-rtl
modprobe ieee80211_crypt_tkip-rtl
modprobe r8180

```

Built it on the 2.6.24-19-generic (i386) and works fine.

---

