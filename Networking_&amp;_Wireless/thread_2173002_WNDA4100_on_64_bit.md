---
title: "WNDA4100 on 64 bit"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by dunmireg on 2013-09-07
**uname -r**

3.8.0-30-generic

**lsmod | grep rt**

rt3573sta             721035  1 
parport_pc             28284  1 
parport                46562  3 ppdev,lp,parport_pc



**lsusb**

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0846:9012 NetGear, Inc. 
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 004: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0

Is that what you were looking for? Thanks again for all the help!

---

### Post by chili555 on 2013-09-07
Exactly. Let's dig deeper before we abandon the tricky rt3573sta. Please run and post:```
iwconfig
modinfo rt3573sta | grep 9012
dmesg | grep -e wlan -e rt3
```Thanks.

---

### Post by dunmireg on 2013-09-07
**iwconfig**

ra0       Ralink STA  ESSID:"GY4E4"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1F:90:D7:A7:74   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-22 dBm  Noise level:-28 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

**modinfo rt3573sta | grep 9012**

alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*in*

**dmesg | grep -e wlan -e rt3** 
 nothing hapens, just starts a new line

I don't know if this is helpful but after deleting and reinstalling everything and following the outlines earlier I could connect to the wireless using my card but everything froze when I opened firefox and tried to navigate away from the home screen. So I don't know if that indicates a connection problem or what. 

Thanks again, you're awesome!

---

### Post by chili555 on 2013-09-07
I ain't awesome yet; I don't have it solved! Let's see all of *dmesg* after a clean boot. As it is quite lengthy, paste it here and give me the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)```
dmesg
```

As I am sure you saw by reading the 17 page (!!!) thread, this device is quite tricky and success is not at all sure.

---

### Post by dunmireg on 2013-09-07
Wow that is a lot of text. Here you go 

[http://paste.ubuntu.com/6076127/](http://paste.ubuntu.com/6076127/)

---

### Post by chili555 on 2013-09-07
That is also a whole lot of horrible, nasty errors, such as:> [   15.966434] ERROR!!! RTMPSetTimer failed, Halt in Progress!
[   16.333272] RTMP_TimerListAdd: add timer obj ffffc900051fd6e0!
[   16.333274] RTMP_TimerListAdd: add timer obj ffffc900051fd758!
[   16.333275] RTMP_TimerListAdd: add timer obj ffffc900051fd7d0!
[   16.333276] RTMP_TimerListAdd: add timer obj ffffc900051fd668!
[   16.333277] RTMP_TimerListAdd: add timer obj ffffc900051fd500!
[   16.333278] RTMP_TimerListAdd: add timer obj ffffc900051fd578!
[   16.333279] RTMP_TimerListAdd: add timer obj ffffc900051c79e8!
[   16.333280] RTMP_TimerListAdd: add timer obj ffffc900051b6858!
[   16.333281] RTMP_TimerListAdd: add timer obj ffffc900051b68d8!
[   16.333281] RTMP_TimerListAdd: add timer obj ffffc900051c7b78!
[   16.333283] RTMP_TimerListAdd: add timer obj ffffc900051c78f8!
[   16.333284] RTMP_TimerListAdd: add timer obj ffffc900051c7af8!
[   16.334674] -->RTUSBVenderReset
[   16.334799] <--RTUSBVenderReset
[   16.563332] Key1Str is Invalid key length(0) or Type(0)
[   16.563340] Key2Str is Invalid key length(0) or Type(0)
[   16.563346] Key3Str is Invalid key length(0) or Type(0)
[   16.563353] Key4Str is Invalid key length(0) or Type(0)I downloaded and built the driver on my own 3.8.0-30 64-bit system, as well as a slight revision on Realtek's  (aka Mediatek) site. It built with warnings aplenty. We have built a mechanism with so many missing parts that it is no wonder it doesn't work correctly.

I then turned my attention to the excellent resource here: [http://wikidevi.com/wiki/Netgear_WNDA4100](http://wikidevi.com/wiki/Netgear_WNDA4100)  It says, in part: > and future support in rt2800usb (juhosg's patchset adding support, may be in by k3.12)I interpret k3.12 to mean kernel version 3.12.

Encouraged, I downloaded the backported drivers here: [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)  I built the latest development release with *NO* errors and *NO* warnings (!!!); however, alas, coverage for this device is not yet included in rt2800usb. > chili@Think410:~/backports-20130802$ modinfo drivers/net/wireless/rt2x00/rt2800usb.ko | grep 9012
zippo-nothing-go fishThe nature of development releases is that the device might be included in a few days...or a few weeks...or a few months.

As I said in the thread we both came from, I currently know of no way to get this device working in 13.04 and 64-bit. My best suggestion is either install the 3.2 kernel version of 12.04 LTS and 32-bit and compile the driver there or head on over to your favorite on-line retailer and buy a Linux supported device. 

I regret that I haven't a more productive answer.

---

### Post by dunmireg on 2013-09-07
That's ok, thank you for your help and sticking with this tricky situation. I am on my way to find a new adapter. I stand by the statement that you're awesome!

---

### Post by chili555 on 2013-09-08
I was happy to help. I'm sorry we couldn't (yet!) find a solution.

---

