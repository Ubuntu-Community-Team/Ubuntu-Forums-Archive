---
title: "Ethernet driver problem, desperately need help."
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by Hayat on 2015-10-03
hi everybody, i am new to linux. I have a Dell Optiplex 3020 core i5 machine. I have installed redhat enterprise edition 5 having kernel 2.6.18-164.el5PAE. The builtin ethernet card was not working so i took some help from a thread in this forum [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489) . But unfortunately it didnt workout for me.  Here is some output
#lsmod | grep r816*

r8169                       37573    0
mii                             9409   1 r8169

i downloaded the driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E)

when trying to run the autorun.sh got this 

#./autorun.sh
check old driver and unload it.
rmmod r8169
Build the module and install
In file included from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168.h:34,
                 from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:73:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_dash.h:193:33: warning: no newline at end of file
In file included from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168.h:35,
                 from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:73:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_realwow.h:117:36: warning: no newline at end of file
In file included from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:73:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168.h:338:1: warning: "DMA_BIT_MASK" redefined
In file included from include/asm-generic/pci-dma-compat.h:7,
                 from include/asm/pci.h:140,
                 from include/linux/pci.h:804,
                 from /u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:40:
include/linux/dma-mapping.h:16:1: warning: this is the location of the previous definition
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c: In function &#8216;rtl8168_proc_module_init&#8217;:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:1292: error: &#8216;init_net&#8217; undeclared (first use in this function)
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:1292: error: (Each undeclared identifier is reported only once
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:1292: error: for each function it appears in.)
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c: In function &#8216;rtl8168_init_board&#8217;:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:22173: warning: left shift count >= width of type
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c: In function &#8216;rtl8168_init_one&#8217;:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:22505: warning: assignment discards qualifiers from pointer target type
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c: In function &#8216;rtl8168_cancel_schedule_work&#8217;:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:24195: error: implicit declaration of function &#8216;cancel_work_sync&#8217;
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c: In function &#8216;rtl8168_cleanup_module&#8217;:
/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.c:25356: error: &#8216;init_net&#8217; undeclared (first use in this function)
make[3]: *** [/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src/r8168_n.o] Error 1
make[2]: *** [_module_/u02/0002-r8168-8.040.00.tar.bz2_FILES/r8168-8.040.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2


-------------------------
so i got the clue that old driver are being loaded and its preventing it from installation and i removed it with rmmod command. still same problem


so i further googled the issue and found some where that kernel development rpm must be installed so i installed it from the dvd. 

but still getting the same error.


I would highly appreciate any help.

Many thanks in Advance.[URL="http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E"]
[/URL]

---

### Post by praseodym on 2015-10-03
Hi,

this driver is too new for kernel 2.6.18. Take this old one:

[http://media-cdn.ubuntu-de.org/forum/attachments/06/08/3005217-r8168-dkms-8.028.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/06/08/3005217-r8168-dkms-8.028.00.tar.gz)

Installation:
```

sudo tar xvf 3005217-r8168-dkms-8.028.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.028.00
sudo dkms build -m r8168-dkms -v 8.028.00
sudo dkms install -m r8168-dkms -v 8.028.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot.

Edit: If dkms doesn't work take the even older one attached without dkms.

---

