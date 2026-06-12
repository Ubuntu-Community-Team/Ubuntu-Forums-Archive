---
title: "Unable to install Netgear A6100 wifi adaptater - Ubuntu 15.10"
date: 2016-03-28
forum: Networking &amp; Wireless
---

### Post by wolfboy2 on 2016-03-28
Hello,

I'm using Ubuntu 15.10, and I can't install my Netgear A6100 wifi adaptater.

I read those thread :

[http://ubuntuforums.org/showthread.php?t=2235778](http://ubuntuforums.org/showthread.php?t=2235778)
[http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac](http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac)
[http://ubuntuforums.org/showthread.php?t=2240631&page=3](http://ubuntuforums.org/showthread.php?t=2240631&page=3)

And I finally followed the instructions in this one (third post) :

[http://ubuntuforums.org/showthread.php?t=2275054&highlight=8812au](http://ubuntuforums.org/showthread.php?t=2275054&highlight=8812au)

I had this problem :

> 
git clone [https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch](https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch)
Cloning into 'linux-3.18.patch'...
fatal: repository 'https://github.com/pld-linux/rtl8812au/blob/master/linux-3.18.patch/' not found


So I downloaded the zip file here :
[https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

Then I had this message :

> 

~/rtl8812AU_8821AU_linux/include$ cd /home/minor117/rtl8812AU_8821AU_linux

~/rtl8812AU_8821AU_linux$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-34-generic/build M=/home/minor117/rtl8812AU_8821AU_linux  modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-34-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-34-generic'

~/rtl8812AU_8821AU_linux$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/
install: cannot stat ‘8812au.ko’: No such file or directory
Makefile:1055: recipe for target 'install' failed
make: *** [install] Error 1



So I used the command shown in the second step :

> cd /home/minor117/rtl8812AU_8821AU_linux/include

To modify the file :
> ioctl_cfg80211.h

But that hasn't changed a thing, I still have this message :
> ~/rtl8812AU_8821AU_linux$ sudo make install
install -p -m 644 8812au.ko  /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/
install: cannot stat ‘8812au.ko’: No such file or directory
Makefile:1055: recipe for target 'install' failed
make: *** [install] Error 1

I'm totally lost, so if someone could help me I'd be very grateful !

Thanks

---

