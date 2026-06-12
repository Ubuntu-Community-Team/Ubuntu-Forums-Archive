---
title: "Help with Wifi please"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by Derek_Anderson on 2014-10-22
Hi all,

I'm relatively new to Ubuntu.  I'm not new to computers, have been working with them my forever.  I'm having trouble getting my USB Wifi N adapter to work properly.  I installed Ubuntu 14.04 LTS on to a computer I have that had a spare hard drive in it.  Ubuntu seemed to install properly.  However my wifi connection in Ubuntu really sucks.  This computer dual boots and when in Win 7 is seems to work properly, I get good download speeds from SpeedTest.net.  However, in Ubuntu the download speed maxes out at 0.48 mbps!!  Terrible.  And when I do apt-gets from the Terminal window its extremely slow at 35-45 kB/sec.  Also, while websurfing, the connection is very sporadic.  Sometimes it works, but slow, and other times it just times out when going from site to site.  At that point I have to disconnect from the wifi router and reconnect.  Then it works for a bit then stops and I have to repeat the procedure.  Very irritating.

The USB wifi N unit I'm using contains a RealTek RTL 8188CU chip in it.  I'm guessing that Ubuntu discovered it and loaded an incorrect driver?  Everything else on my wifi network works fine, so the trouble must be in Ubuntu.  Is there anyway I can manually change the driver for it?  Like I said, I'm relatively new to Linux and didnt see anything equivalent to the Windows Hardware Device Manager, where you can just manually update drivers and such.  I can't even find in Ubuntu where it's telling me what model of Wifi chipset that it detected (very frustrating).

So, if any of you could provide me with some guidance on how to manually update the drivers, I'd appreciate it.  I think I found an online site to download Linux(Unix) drivers for the USB dongle but they are for kernel version 2.6.x.  Will that work with the newer kernel in Ubuntu 14.04 64 Bit??

---

### Post by grahammechanical on 2014-10-22
Here is the wireless trouble shooting guide. It may help you fix things. It will help you collect information that will help others help you.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards

---

### Post by slickymaster on 2014-10-22
Hi Derek_Anderson, welcome to the forums.

I'm moving your thread to the **Networking & Wireless** sub-forum, which is the proper place for it and where helpfully you'll get a more adequate help for your issue.

---

### Post by Derek_Anderson on 2014-10-22
Ok guys, I read through the wireless trouble shooting guide and everything checks out.  The driver is loaded (although its a generic driver).  wlan0 is on and connected and driver loaded and its communicating with the kernel but the performance is absolutely terrible!!  I cannot get more than 0.50-1.00 mbps in speedtest.  Also the connection randomly drops and I have to continually disconnect from the router and then reconnect.  I'm pretty sure there's nothing wrong with the USB wifi dongle as it works flawlessly when I boot to windows.  I'm pretty sure its some kind of driver error.

Here is a cut and paste from me running lshw -C network and from me running lsmod:

```
derek@derek-linux:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 8c:89:a5:36:2f:4d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:21:2f:3b:1b:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=rtl8192cu** **driverversion=3.13.0-37-generic** firmware=N/A ip=192.168.1.122 link=yes multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
derek@derek-linux:~$ lsmod
Module                  Size  Used by
ctr                    13049  3 
ccm                    17773  3 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
arc4                   12608  2 
[B]rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu[/B]
hid_generic            12548  0 
snd_hda_codec_hdmi     46368  1 
cfg80211              484040  2 mac80211,rtlwifi
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
gpio_ich               13476  0 
coretemp               13435  0 
kvm_intel             143109  0 
kvm                   451552  1 kvm_intel
serio_raw              13462  0 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
lpc_ich                21080  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
radeon               1522526  3 
parport_pc             32701  1 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
ttm                    85150  1 radeon
drm_kms_helper         55071  1 radeon
mac_hid                13205  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
r8169                  67581  0 
mii                    13934  1 r8169

```

If anybody here has any general ideas on what's going on, I'd love to hear them. 

Thanks!!

---

### Post by Derek_Anderson on 2014-10-22
Just to let everyone know, as I suspected the drivers that Ubuntu loads as default are defective.  After Googling around for two days (yesterday and today) I found this article that contains explicit instructions on how to rectify the problem.  This method uses newer drivers from the RealTek website and compiles the new driver and blacklists the stock driver.  Apparently its an issue on the following versions of OS:
- Ubuntu 14.04
- Linux Mint 17
- Ubuntu 12.04
- Linux Mint 13

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I did this and the new driver works much better.  Its still not quite flawless, but at least I can get 9.0-10.0 mbps through the wifi dongle now (win 7 still gets the full 16.0 mbps of my ISP connection).  At least its usable now, whereas before it completely wasnt.

The board moderator may want to leave this up as I'm sure lots of people are experiencing this issue, the RTL8188 and RTL8192 wifi chipsets are used in hundreds of cheaper wifi dongles.

Thanks.

---

### Post by Bucky Ball on 2014-10-22
We leave them up and you mark them as solved to help others. ;)

Please see the second link in my signature. Thanks.

---

