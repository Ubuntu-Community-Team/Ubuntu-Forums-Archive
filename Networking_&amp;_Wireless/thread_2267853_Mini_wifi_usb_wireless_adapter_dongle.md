---
title: "Mini wifi usb wireless adapter dongle"
date: 2015-03-04
forum: Networking &amp; Wireless
---

### Post by Mel_Blakey on 2015-03-04
I have had problems with my onboard Realtek Network Card (Windows 7 works fine, but Ubuntu slugish) and some of the solutions on here are way above my head. So I bought this:
**[SIZE=2]MINI WIFI USB WIRELESS ADAPTER DONGLE 150MBPS 802.11 N B G NETWORK LAN[/SIZE]**

[http://www.ebay.co.uk/itm/231184930689?_trksid=p2059210.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.co.uk/itm/231184930689?_trksid=p2059210.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)

Can anyone talk me through installing the driver for it? It came with a CD containing a linux driver: 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO

It does work. But it is still slow.

I have searched on here. But, I just don't understand some of the solutions. One did ask for this though, so here is some info.

> sudo lspci -v

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 3672
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at c1500000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00
    Kernel driver in use: rtsx_pci

To simplify trouble shooting I have disconected to onboard network card. However, I would still like to use this on the rare occasion that I surf using Windows 7.

Regards

---

### Post by chili555 on 2015-03-04
The driver that came with the USB is too old; sorry.

I'd really rather troubleshoot the internal. Do you mind?

May we see:```
lsusb
lspci -nn | grep 0280
```Thanks.

---

### Post by Mel_Blakey on 2015-03-04
Hello

Either way...suites me
> lsusb
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6321 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mel@LaptopDancer2:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)


Thanks.

---

### Post by chili555 on 2015-03-04
Let's try a simple fix before we get out the bigger hammer! In a terminal:```
sudo -i
echo "options rtl8192ce ips=0 fwlps=0"  >  /etc/modprobe.d/rtl8192ce.conf
exit
```With the USB detached, reboot and test.

---

### Post by Mel_Blakey on 2015-03-05
This worked like a dream....I even marked the thread solved. But, When I turned the machine off and back on again for a 2nd time it has become erratic again!


*I appologise for the delay in getting back to you. This is due to the time difference.*

---

### Post by chili555 on 2015-03-05
> **Mel_Blakey said:**
> This worked like a dream....I even marked the thread solved. But, When I turned the machine off and back on again for a 2nd time it has become erratic again!


*I appologise for the delay in getting back to you. This is due to the time difference.*A bigger hammer, then! Before we start, we need a few details. Please run and post:```
lsb_release -d
uname -r 
arch
```Thanks.

---

### Post by Mel_Blakey on 2015-03-05
> lsb_release -d
Description:    Ubuntu 14.04.2 LTS

uname -r 
3.13.0-46-generic

~$ arch
x86_64

It is acting very strange now. In so much as: 

If the signal indicator shows 3 out of 4 bars it either works perfectly (faster than before) or it drops the connection between the laptop & wifi.

With full strength it does not connect at all or takes a very long time.

---

### Post by chili555 on 2015-03-05
Please open a terminal and, with a working internet connection, do:```
sudo apt-get install linux-headers-generic build-essential 
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.gz
tar -zxvf backports-3.19-rc1-1.tar.gz 
cd backports-3.19-rc1-1
make defconfig-rtlwifi
make
sudo make install
```Reboot and tell us if there is any improvement.

---

### Post by Mel_Blakey on 2015-03-05
There seems to be a definite improvement. Its holding full strength & not dropped out once yet. I'll give it a few hours before I mark it solved though ;)

Thanks ever so much for your help and the loan of of your big hammer!

---

### Post by Mel_Blakey on 2015-03-05
Looks like you've cured it doc....

Thanks!!!

---

### Post by chili555 on 2015-03-05
When you compile a driver from source, you've built it for your currently running kernel only. When Update Manager installs a later linux-image, after the requested reboot, recompile:```
cd backports-3.19-rc1-1
make clean
make defconfig-rtlwifi
make
sudo make install
```And reboot once more.

I'm glad it's working.

In order to help others with the same hardware, please use thread tools at the top to mark Solved.

---

### Post by Mel_Blakey on 2015-03-06
> **chili555 said:**
> When you compile a driver from source, you've built it for your currently running kernel only. When Update Manager installs a later linux-image, after the requested reboot, recompile:```
cd backports-3.19-rc1-1
make clean
make defconfig-rtlwifi
make
sudo make install
```And reboot once more.

Hello

I am reletively new to Linux, so I have never compiled a driver from source. *(maybe it should be the next thing that I learn to do)*.

This is a fresh install (6 weeks ago) onto a machine / drive that only had windows 7 on it before. However, I cloned the Home folder of my previous machines' Ubuntu 14.04.
[LIST]
[*]Is it possible that I carried an incompatible driver over? 
[*]Should I have run the code above after copying over the Home folder? 
[/LIST]

Once again thanks!

---

### Post by chili555 on 2015-03-06
> **Mel_Blakey said:**
> Hello

I am reletively new to Linux, so I have never compiled a driver from source. *(maybe it should be the next thing that I learn to do)*.Isn't that exactly what you did based on my proposed solution at post #8? No?

The source code to compile a driver may be found in your home directory. The installed and working, or not, driver is found in /lib/modules/. ```
modinfo rtl8192ce
filename:       [COLOR="#FF0000"]/lib/modules[/COLOR]/3.13.11-03131111-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
```Moving or copying your home directory will not affect the installed driver.

---

### Post by Mel_Blakey on 2015-03-07
> Isn't that exactly what you did based on my proposed solution at post #8? No? Did I? Blimey!
Anyway my lappy is much better...

**THANK YOU!**

---

### Post by chili555 on 2015-03-07
Awesome! Glad it's working.

---

### Post by Mel_Blakey on 2015-04-11
The issues have returned.

Does the above procedure have to be repeated after certain updates?

---

### Post by coffeecat on 2015-04-11
> **Mel_Blakey said:**
> The issues have returned.

Does the above procedure have to be repeated after certain updates?

As chili555 is offline at the moment, I'll just direct you to his post #11 in this thread. It sounds as though you had a kernel upgrade in the updates, in which case you will need to recompile the wireless driver for the new kernel. If you experience difficulty with that, post back with details and I'm sure chili555 will help you when he is next online.

---

### Post by chili555 on 2015-04-11
> **coffeecat said:**
> As chili555 is offline at the moment, I'll just direct you to his post #11 in this thread. It sounds as though you had a kernel upgrade in the updates, in which case you will need to recompile the wireless driver for the new kernel. If you experience difficulty with that, post back with details and I'm sure chili555 will help you when he is next online.Exactly correct!

Thanks!

---

### Post by Mel_Blakey on 2015-04-11
> **chili555 said:**
> Exactly correct!

Thanks!

[COLOR=#000080]**Thanks for the replys..... I followed post 11 and it has fixed it**[/COLOR] :p

---

