---
title: "installing rtl8187L linux driver"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-06-08
Realtek provides a linux driver for its rtl8187L chipset (note: not 8187b). I've downloaded it, but don't know how to install it. Since it's not a windows driver, i'm assuming ndiswrapper is not the way to go. I searched for documentation on how to do this, but came up empty. Surely this is documented somewhere? If anyone could provide me a link, I'd appreciate it. Please do not send a link to an rtl8187b install page...that has separate issues and requires the windows driver.

---

### Post by chili555 on 2008-06-08
If you can see where it is now, Places -> Home, or, perhaps Places -> Home -> Desktop, then you can right click it and select 'Extract here.' Go to the directory that's then been created and see the README. Some prerequisites will be listed which can usually be satisfied with:```
sudo apt-get install build-essential
sudo apt-get install linux-headers-generic
```Post back if you get stuck.

---

### Post by scholzilla on 2008-06-08
Thanks for the reply. I think this is going to be complicated. When I use make to recompile the driver as instructed by README, it's unsuccessful. Reading the output, it looks as though there is some problem with one of the C scripts. If you're really dedicated and know programming like I don't, I could send you a copy of the output and the C file that appears to contain the problem (something about an invalid pointer).

---

### Post by chili555 on 2008-06-09
It would help most to get a link to the package you downloaded. Then I will see if I can trouble-shoot the compilation.

---

### Post by scholzilla on 2008-06-09
You're a beautiful human being. The driver can be [found here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true#362"). Should you be successful, I will put up a how-to sticky and, of course, credit you.

Just a few notes. Here's what I get from running make; the first reference to the softmac.c script that seems to be the beginning of the problem appears just a few lines below where all the directories/files are listed:


```

matt@Ogodei:~/linux_wifi_driver$ sudo ./makedrv
ieee80211/
ieee80211/license
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_rx.c
ieee80211/tags
ieee80211/ieee80211_crypt_tkip.c
ieee80211/Makefile
ieee80211/readme
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211.h
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt.h
rtl8187/
rtl8187/license
rtl8187/r8180_rtl8225z2.c
rtl8187/r8180_rtl8225.h
rtl8187/r8187_led.c
rtl8187/r8180_93cx6.h
rtl8187/r8180_wx.h
rtl8187/r8180_hw.h
rtl8187/copying
rtl8187/r8187_led.h
rtl8187/r8180_pm.h
rtl8187/tags
rtl8187/r8187.h
rtl8187/Makefile
rtl8187/r8180_rtl8225.c
rtl8187/readme
rtl8187/install
rtl8187/.tmp_versions/
rtl8187/.tmp_versions/r8187.mod
rtl8187/changes
rtl8187/r8180_wx.c
rtl8187/r8180_pm.c
rtl8187/r8187_core.c
rtl8187/r8180_93cx6.c
rtl8187/authors
rtl8187/ieee80211.h
rtl8187/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/matt/linux_wifi_driver/ieee80211/tmp
make -C /lib/modules/2.6.24-18-generic/build M=/home/matt/linux_wifi_driver/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.o
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
[B]/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:421: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
[/B]/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;:
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:495: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;:
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:915: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol_rtl&#8217;:
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2120: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2229:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2229: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2229: error: (Each undeclared identifier is reported only once
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2229: error: for each function it appears in.)
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2230:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2231:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2232:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2233:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2234:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;:
/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.c:2255: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
make[2]: *** [/home/matt/linux_wifi_driver/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/matt/linux_wifi_driver/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/matt/linux_wifi_driver/rtl8187/tmp
make -C /lib/modules/2.6.24-18-generic/build M=/home/matt/linux_wifi_driver/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/matt/linux_wifi_driver/rtl8187/r8187_core.o
In file included from /home/matt/linux_wifi_driver/rtl8187/r8187_core.c:64:
/home/matt/linux_wifi_driver/rtl8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:450: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:450: error: (Each undeclared identifier is reported only once
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:450: error: for each function it appears in.)
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_remove&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:456: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8187_rx_urbsubmit&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:730: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:1648: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2053:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8180_init&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2053: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_probe&#8217;:
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2938: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/matt/linux_wifi_driver/rtl8187/r8187_core.c:2956: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
make[2]: *** [/home/matt/linux_wifi_driver/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/matt/linux_wifi_driver/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2

```

Also, I have the latest version of of build-essential installed.

UPDATE: Strangely, I was able to connect with no problems at a cafe last night. This in spite of the fact that lshw -C network lists no wireless driver. Is it possible that there is a hidden, native linux driver that is running my wireless and that I'm just getting a weak signal from other APs? Network Manager shows a strong signal from the APs that I'm dropping, but it also shows that I'm connected when I'm not so I don't know if I can believe it. I hope I'm not sending you on a wild goose chase.

---

### Post by chili555 on 2008-06-10
I hope the native driver is working, because, despite working on this for hours and Googling for hours, I cannot get this to work. I have fixed some issues, others have popped up, run it on an earlier kernel, all to no avail. 

The native driver is *rtl8187.* You can see if it's loaded with:```
lsmod | grep 8187
```If it is not loaded, try:```
sudo modprobe rtl8187
```Then let's take a look at:```
iwconfig
ifconfig
```Thanks.

---

### Post by scholzilla on 2008-06-10
Yikes. Sorry I caused you that much trouble. I appreciate your efforts. 

Do I want to blacklist ehci_hcd, ohci_hcd in /etc/modprobe.d/blacklist or are these what are working for me?:

```
matt@Ogodei:~$ lsmod | grep 8187
rtl8187                36096  0 
mac80211              165652  1 rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               146028  4 rtl8187,ehci_hcd,ohci_hcd


matt@Ogodei:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"TOOLEY'S "  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:DF:E6:C7   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=48/64  Signal level=49/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

matt@Ogodei:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d3:d8:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60042 (58.6 KB)  TX bytes:60042 (58.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:d8:96:a1  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1239901 (1.1 MB)  TX bytes:262714 (256.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-D8-96-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

So is the usbcore output from lsmod what tells me that the rtl8187 driver is loaded? The driver doesn't show up under iwconfig, but I do seem to be connecting from this cafe fine. Is there a way to configure my connection so I'm not dropping connections so often from other APs that seem to be stable for everyone else?

Many thanks, again.

---

### Post by chili555 on 2008-06-11
> Do I want to blacklist ehci_hcd, ohci_hcd in /etc/modprobe.d/blacklist or are these what are working for me?No, they seem to br working perfectly.> that the rtl8187 driver is loaded? Yes, it is loading fine.> The driver doesn't show up under iwconfigIt wouldn't. It would show under:```
sudo lshw -C network
```I can't see anything about your settings that I might change. Try to keep the USB device as high as you can. Some of your buddies no doubt have laptops that have the antenna surrounding the screen. In borderline conditions, having your antenna a bit higher may make all the difference.

Let's both keep looking for a better RTL8187 driver. The very few out there today are problematic.

You might try ndiswrapper, if you are a bit intrepid. It's not hard to install and even easier to remove, if it doesn't meet your expectations.

---

### Post by scholzilla on 2008-06-12
yes, let's both keep looking. I also forgot to mention that the driver doesn't show up under lshw -C network either, as far as I can tell:

```

matt@Ogodei:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.12 multicast=yes wireless=IEEE 802.11g
```

---

### Post by scholzilla on 2008-06-23
The key to making this device work, it turns out, is not to install ANY driver. The native driver in Hardy works just fine. Following the various posts for installing the 8187b driver will only lead you down the same frustrating road I walked down. Likewise, the driver offered for linux by the realtek website does not work.

---

### Post by auditt on 2008-06-29
The native driver in Hardy DOES work but DOES NOT work the way it should. 

If I'm just doing web browsing, it works great. However, once I start reaching higher traffic volumes it shuts down until I reboot.

I've tried a number of "fixes" with no luck.


ARGH!

---

### Post by Tlingit on 2008-07-19
rtl8187L get this to work.

[for rtl8187  (-->   L   <--)] only

ndiswrapper
airckrack-ng custom rtl8187L driver with patch
then you will have to blacklist something.

But it i still didn't get very good performance with it. It worked.

However if you do not want to use ndiswrapper will have to rebuild your kernel with OUT the new mac80211 MODULE, and with the current ieee80211.

If any one would help me set this kernel up. as in remove the mac module and precompile the ieee module into the kernel.

I can find out how to compile the kernel, but i just can't find out how do this step, before i compile it onto my system. 

Sweet hope i helped.

---

### Post by phantasm715 on 2008-09-11
ahhh a year later still no solution :( has linux gave up on wireless, Tlingit i would really be isnterested if you have fixed that issue or not ? i have purchased an alfa 500mw card that got RTL8187L chipset and keep getting my connection dropped, if it connects at all, anyone ?

---

### Post by rashwan on 2008-09-12
i posted similar problem (sorry for double posting) and still no answer and i guess it will took long with Linux to reach 0000000000000000000000.1% of windows compatability thats always make Linux the 2nd or maybe 3rd choice to the users

---

### Post by phantasm715 on 2008-09-13
apparently using Wicd tool with default drivers seems to work, at least with open networks, (havent tested wep,wpa), tested on Kubuntu 8.4.0

---

### Post by rashwan on 2008-09-13
actually Wicd does not work with secured networks , and kubuntu works by default but its silly buggy distro

---

### Post by phantasm715 on 2008-09-13
no, it doesnt work openbox on Kubuntu, it might connect but wont get you an ip address.

---

### Post by darrenpaullittle on 2008-09-13
hi not a problem just goto aircrack-ng home page it shows a list of compatible drivers, select which one you want, and just copy and past the instructions in the terminal,

---

### Post by phantasm715 on 2008-09-14
surprisingly aircrack-ng RTL8187L instructions didnt work either they created the new interface what seemed to be using new drivers, would scan environment but wouldnt connect.

---

### Post by rashwan on 2008-09-15
[CENTER]thats right , aircrack-ng Driver just let you to scan but will never connect even to unsecured networks , finally i knew that the native driver of this device contains bugs such as connection drop ..no signal...etc
so you have to use ndiswrapper other wise do like me: "DELETE linux SUX install fresh compatibe system such as WINDOWS[/CENTER]

---

### Post by phantasm715 on 2008-09-15
well if your in it just for the internet ndiswrapper will do just fine, easy to install, but if u wanna do packet injection your out of luck, go try it on windowz(heh,snickering)

---

### Post by sunkssss on 2008-10-26
Has anybody figured out how to get ndiswrapper working in 64-bit systems? The 64-bit windows drivers are not working (32-bit of course not) and there doesn't seem to be any solution out there yet. Any help would be really appreciated.

---

### Post by alexelprogramador on 2010-07-30
Hi again! :popcorn:

ok, now, im not ussing Ubuntu 10.04 wich the compatibility of RTL8187L module is solved.

Im now with Debian "testing" Squeeze 

```
root@beep:~# uname -a
Linux beep 2.6.32-3-amd64 #1 SMP Wed Feb 24 18:07:42 UTC 2010 x86_64 GNU/Linux
```

[IMG]http://a.imageshack.us/img186/9030/mydebiansystem.jpg[/IMG]


the trouble is that, in spite of it has loaded propperly the modules of the device: rtl8187, it doesnt work what it should be.

what I want to mean, is that the device is loaded, it conects but it works slow and allways disconnect from the AP.

I try to install the module again as suggested on REALTEK home page "at download section, you can get it ussing the search box"

[IMG]http://a.imageshack.us/img30/5484/rtl8187realtekdriverlin.jpg[/IMG]

look that the driver is updated to te kernel **Linux driver for kernel*2.6.X** and the version is made at **2010/1/27**

anybody does compiled it and replaced what Debian testing is ussing?

---

### Post by nerdy_kid on 2010-08-22
i compiled it, didn't work though.  tried ndiswrapper and that didnt work either.

---

### Post by Gizim on 2010-08-31
Same problem with a Roswell USB Adapter using RTL8187

---

### Post by nerdy_kid on 2010-09-02
I actually returned my wireless card (it didn't hardly work in windows either) and got a identical replacment which works with the driver off of realtek's site and with the rtl8187 driver included in the linux kernel (2.6.32.24)

---

