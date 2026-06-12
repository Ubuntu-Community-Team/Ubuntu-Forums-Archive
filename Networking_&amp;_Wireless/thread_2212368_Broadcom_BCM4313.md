---
title: "Broadcom BCM4313"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by mark.soames on 2014-03-20
I'm having serious problems with my wireless networking on 13.10.  I've tried to fix it for hours and hours but to no avail.  Previously, I would be connected for any period of time between 10 seconds and 4 or 5 hours before the connection dropped and I got the 'wireless is disabled by hardware switch' error.  A recent upgrade made the situation even worse, so I embarked on an ill-fated quest to try and put ane end to it.  Most recently, I've tried the solutions listed at  [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers) and [http://ubuntuforums.org/showthread.php?t=2191126](http://ubuntuforums.org/showthread.php?t=2191126) and [http://askubuntu.com/questions/316072/broadcom-bcm4313-on-13-04](http://askubuntu.com/questions/316072/broadcom-bcm4313-on-13-04) .  Now, through my inane attempts to resolve the problem, my wireless card isn't being recognised at all.  

Any help here would be enormously appreciated, especially in attempting to undo whatever damage I've done.  As you can probably tell, I'm a novice at this.

EDIT: I've just seen the sticky on wireless issues,

Model is Samsung s3511.

```
$ lspci


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```
```
$ lsusb


Bus 002 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 005: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1020  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub





```
```
$ ifconfig


eth0      Link encap:Ethernet  HWaddr e8:11:32:86:e9:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


usb0      Link encap:Ethernet  HWaddr 82:39:2f:96:a9:e1  
          inet addr:192.168.42.114  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::8039:2fff:fe96:a9e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182719 errors:7 dropped:0 overruns:0 frame:7
          TX packets:106474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256298106 (256.2 MB)  TX bytes:14819315 (14.8 MB)


```
```
$ iwconfig


lo        no wireless extensions.


eth0      no wireless extensions.


usb0      no wireless extensions.




```
```
$ lsmod


Module                  Size  Used by
rndis_wlan             44355  0 
rndis_host             14087  1 rndis_wlan
cdc_ether              13967  1 rndis_host
usbnet                 37607  3 rndis_host,rndis_wlan,cdc_ether
cfg80211              401762  1 rndis_wlan
usb_storage            48294  0 
parport_pc             31981  0 
ppdev                  17391  0 
bnep                   18959  2 
rfcomm                 53664  12 
binfmt_misc            13140  1 
joydev                 17097  0 
intel_powerclamp       14239  0 
coretemp               13195  0 
samsung_laptop         14062  0 
snd_hda_codec_hdmi     40402  1 
snd_hda_codec_realtek    50315  1 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39125  1 uvcvideo
videodev              107508  2 uvcvideo,videobuf2_core
snd_hda_intel          42658  8 
microcode              18894  0 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
psmouse                90642  0 
snd                    60790  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
serio_raw              13189  0 
mei_me                 13933  0 
intel_ips              18055  0 
btusb                  23443  0 
mei                    66411  1 mei_me
i915                  594442  5 
bluetooth             323656  22 bnep,btusb,rfcomm
lpc_ich                16864  0 
soundcore              12600  1 snd
drm_kms_helper         46867  1 i915
drm                   242400  6 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18777  2 i915,samsung_laptop
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
ahci                   25579  2 
libahci                26619  1 ahci
r8169                  61562  0 
mii                    13654  2 r8169,usbnet






```
```
$ dmesg


[   52.665649] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[   52.759112] usb 2-1.2: New USB device found, idVendor=0bb4, idProduct=0ff9
[   52.759121] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[   52.759127] usb 2-1.2: Product: Android Phone
[   52.759132] usb 2-1.2: Manufacturer: HTC
[   52.759137] usb 2-1.2: SerialNumber: HT2ATW501607
[   53.116758] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[   53.116830] scsi4 : usb-storage 2-1.2:1.0
[   53.116909] usbcore: registered new interface driver usb-storage
[   54.115067] scsi 4:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   54.115524] scsi 4:0:0:1: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   54.115991] scsi 4:0:0:2: CD-ROM            HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   54.119127] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   54.121299] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   54.126364] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   54.127364] sr1: scsi-1 drive
[   54.127572] sr 4:0:0:2: Attached scsi CD-ROM sr1
[   54.127896] sr 4:0:0:2: Attached scsi generic sg4 type 5
[   54.130588] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   58.865590] usb 2-1.2: USB disconnect, device number 4
[   59.318845] usb 2-1.2: new high-speed USB device number 5 using ehci-pci
[   59.416372] usb 2-1.2: New USB device found, idVendor=0bb4, idProduct=0ffe
[   59.416377] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[   59.416380] usb 2-1.2: Product: Android Phone
[   59.416382] usb 2-1.2: Manufacturer: HTC
[   59.416384] usb 2-1.2: SerialNumber: HT2ATW501607
[   59.688158] cfg80211: Calling CRDA to update world regulatory domain
[   59.691068] cfg80211: World regulatory domain updated:
[   59.691073] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   59.691075] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   59.691077] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   59.691079] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   59.691081] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   59.691082] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   59.906701] usbcore: registered new interface driver cdc_ether
[   59.993016] rndis_host 2-1.2:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.2, RNDIS device, 82:39:2f:96:a9:e1
[   59.993043] usbcore: registered new interface driver rndis_host
[   60.126659] usbcore: registered new interface driver rndis_wlan
[  458.900337] systemd-hostnamed[2983]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  499.492558] perf samples too long (2526 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1619.975030] perf samples too long (5021 > 5000), lowering kernel.perf_event_max_sample_rate to 25000




```
```
$ sudo lshw -C network


  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fc500000-fc503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: e8:11:32:86:e9:73
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:fc900000-fc900fff memory:fca04000-fca07fff
  *-network
       description: Ethernet interface
       physical id: 4
       logical name: usb0
       serial: 82:39:2f:96:a9:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.114 link=yes multicast=yes



```
```
$ iwlist scan


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


usb0      Interface doesn't support scanning.




```
```
$ lsb_release -d


Description:	Ubuntu 13.10




```
```
$ uname -mr



```
```
$ uname -mr

```
That should be everything.


With many thanks in advance.

---

### Post by jimbo6 on 2014-03-21
Sounds suspiciously like yet another Realtek wifi card issue. From my experience and reading on the topic, it appears that realtek cards are just poorly supported on Ubuntu, although they perform just about flawlessly on PCs when dual booting.

According to this site:
[h=3][SIZE=3]"Realtek wireless chipset[/SIZE][/h][COLOR=#000000][FONT=Arial]2.3. In case you have a Realtek wireless chipset that often loses connection and runs below its ordinary speed, that chipset probably runs on the buggy driver [/FONT][/COLOR][COLOR=#0000FF][FONT=Arial]rtl8192cu[/FONT][/COLOR][COLOR=#000000][FONT=Arial]. You can[/FONT][/COLOR][install an improved driver like this]("https://sites.google.com/site/easylinuxtipsproject/reserve-7")"[COLOR=#000000][FONT=Arial].[/FONT][/COLOR]
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

I'm going through an issue which is yet to be resolved:
[http://ubuntuforums.org/showthread.php?t=2212089](http://ubuntuforums.org/showthread.php?t=2212089)

First take note of your specific Realtek chipset and then read these posts which have had some success:
[http://ubuntuforums.org/showthread.php?t=2044532](http://ubuntuforums.org/showthread.php?t=2044532)
[http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)
[https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)
[http://ubuntuforums.org/showthread.php?t=2206392](http://ubuntuforums.org/showthread.php?t=2206392)

This rebuild of the driver looks most promising, but failed to work for me:
[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

However, this last post pretty much sums it up:
[http://ubuntuforums.org/showthread.php?t=2196909&page=2](http://ubuntuforums.org/showthread.php?t=2196909&page=2)

Which in essence means two things:
- [post #11]: Wait for a stable version of Ubuntu 14.04 LTS to come out (due to be release within a month, but advised to wait another four weeks to allow for the teething phase"). 
- [post #13]: Realtek wireless cards just aren't supported and are likely to encounter further problems in future. Ditch it and get another wireless card that is supported.

I know it's a rather disappointing result.

---

### Post by varunendra on 2014-03-21
Welcome to the forums Mark! :)

First of all, please always use '**Code**' tags to post commands and their outputs. It preserves the formatting and makes the post clean, compact and more readable. Please follow the "Using Code Tags" link in my signature to see how.

Onto the problem -

Please open a terminal (Ctrl-Alt-T) and try loading the driver manually -
```
sudo modprobe -v brcmsmac
```
If this makes it work, we'll need to find out why it isn't loading automatically. To help with that, please post the output of -
```
grep -R 'blacklist brcm' /etc/modprobe.d/
```


**@ jimbo,**

Your research about the Realtek issue and your desire to share it with others is really appreciable. However, the OP here has a Broadcom card, not a Realtek -
> **mark.soames said:**
> 02:00.0 Network controller: **Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter** (rev 01)
So those suggestions you linked to don't apply here.

**PS:**
@ jimbo, I couldn't get enough time to review all the posts in your thread. Hopefully, I'd be able to steal some time and will be posting my suggestions, if any, in a short while from now.

---

### Post by mark.soames on 2014-03-21
@jimbo

Thanks for all your efforts to try and help resolve my issue, but as varunedra's said, it's the wrong card!

@ varunedra

That's amazing, the first command suddenly reloaded my card

```
sudo modprobe -v brcmsmac[sudo] password for mark: 
insmod /lib/modules/3.11.0-18-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
```

The output of the second command is as follows:

```
~$ grep -R 'blacklist brcm' /etc/modprobe.d/
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac

```


Sorry about the code boxes in my first post by the way, they appeared fine when I was writing it, but apparently not.  Hopefully these ones have worked ok.

Thanks again for your help.

---

### Post by chili555 on 2014-03-21
> **jimbo6 said:**
> Sounds suspiciously like yet another Realtek wifi card issue. From my experience and reading on the topic, it appears that realtek cards are just poorly supported on Ubuntu, although they perform just about flawlessly on PCs when dual booting.

And this has exactly what to contribute to a problem with his:> Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)???

---

### Post by varunendra on 2014-03-21
So far looks as suspected - a bad side-effect of your previous attempts to fix the issue. Usually it is easy to fix though. Please do -
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
Reboot and see if the driver "brcmsmac" is loaded automatically -

```
lsmod | grep brcm
```
You should see "brcmsmac", along with its helping drivers in the above output.

If it doesn't load automatically, or if it loads but still there is some problem, please post back what it is, plus the following outputs- 
```
lsmod
dmesg | egrep 'brcm|b43|wl'
```

Let's hope removing the blacklist file is all you need. :)

---

### Post by varunendra on 2014-03-21
> **chili555 said:**
> And this has exactly what to contribute to a problem with his: ???

Hi Doc! :)

As I initially suspected, and as you might have also figured out already, jimbo most probably intended to post in this thread : [http://ubuntuforums.org/showthread.php?t=2206392](http://ubuntuforums.org/showthread.php?t=2206392) (he later has)

So a case of *"Oops! Wrong thread!!"* :p

---

### Post by mark.soames on 2014-03-21
@[B]Varunedra

[/B]Yes that seems to have done it, amazing!  Thank you so much!

lsmod | grep brcm produces the following:

```
~$ lsmod | grep brcmbrcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              517444  2 b43,brcmsmac
cfg80211              401762  3 b43,brcmsmac,mac80211
bcma                   40966  3 b43,brcmsmac

```


So it looks like removing the blacklist file did it.

I can't thank you enough for helping me fix this.  If any problems arise, I'll report back, but at the moment it looks like my problems are over.  Happy days!

Thanks again Varunedra.

---

### Post by varunendra on 2014-03-21
Glad it worked so easily. :)

If it works now, I'm pretty sure it *should* keep working later. Just keep one thing in mind - **_DON't install the proprietary "STA" driver (wl)_** if recommended by "Additional Drivers" feature. That one would break the current driver and itself is not likely to work well.

Please mark the thread as **[SOLVED]** now that it is. If the problem returns, feel free to revert that prefix and post back the update.

---

### Post by mark.soames on 2014-03-21
Alas, my problems have returned.

I'm getting this again:

```
grep -R 'blacklist brcm' /etc/modprobe.d/
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcmsmac

```

Thanks in advance.

---

### Post by varunendra on 2014-03-21
Which, thanks to some experience I gathered here, makes it even clearer :D

Here's my guess of what is happened/happening -

* You were previously using the STA driver that blacklisted the native drivers (including "brcmsmac") with the file above.
* It broke with some update, usually a bad thing, but lucky for you, since it forced you to post here and let me suggest getting rid of it ;)
* As soon as we removed the blacklist file and got you connected, you did an "update" and the previously broken "STA" driver package got updated too - thus also updating its black deeds (blacklisting).
* Regardless of whether it works or not, it certainly broke your "moments-ago-working-driver" by blacklisting it again.

The fix : Quite simple (hopefully) -

Please run the following command to purge the sta driver -
```
sudo apt-get purge bcmwl-kernel-source
```

Then check -
```
grep -R 'blacklist brcm' /etc/modprobe.d/
```
It shouldn't return any outputs this time. If it does, and it is the same file again, my above story fails (:( ) and we'll need to dig deeper.

But IF I'm correct, reboot and you'll have your wifi back. Keep in mind the precaution in my last post (DON't install the STA driver), and you'll be good.. :)

---

### Post by mark.soames on 2014-03-21
@[B]Varunedra
[/B]
Unfortunately, it seems not to have worked.  I haven't done any updates today.

Here are the outputs as requested. 

```
sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 350567 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-18-generic

```
and

```
grep -R 'blacklist brcm' /etc/modprobe.d/
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf~:blacklist brcmsmac



```

But when I use the code to remove that file as previously suggested, I get this:

```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory

```


Thanks in advance.

---

### Post by varunendra on 2014-03-21
Okay, not EXACTLY the same turn of events, but the story still seems to be what I told. But, I didn't notice this before -
> **mark.soames said:**
> ```
grep -R 'blacklist brcm' /etc/modprobe.d/
/etc/modprobe.d/blacklist-bcm43.conf**[COLOR="#FF0000"]~[/COLOR]**:blacklist brcm80211

```

Notice the part in RED? That means a backup file, usually created when you save the source file using a GUI text editor.

These were not present in your first output of "grep.." command.

Are you manually creating/editing those files using a text editor?
Are you trying something else simultaneously?

In any case, more than half the work is done with purging of the sta driver, but PLEASE don't try anything else while we are following my suggestions!

Now to delete the backup file -
```
[s]sudo rm blacklist-bcm43.conf~[/s] *[COLOR="#696969"]# missing path[/COLOR]*
sudo rm /etc/modprobe.d/blacklist-bcm43.conf~
```
Reboot and check the wifi.

---

### Post by mark.soames on 2014-03-21
@**Varunedra**

Still no joy.  Here's the output:

```
sudo rm blacklist-bcm43.conf~
[sudo] password for mark: 
rm: cannot remove ‘blacklist-bcm43.conf~’: No such file or directory

```
I tried rebooting and it worked for about 5 minutes before disappearing again.  I'm also fairly sure that I haven't tried doing anything else, but I could be wrong. 

Thanks for all your help so far.

---

### Post by varunendra on 2014-03-21
> **mark.soames said:**
> ```
sudo **[COLOR="#FF0000"]rm blacklist-bcm43.conf~[/COLOR]**
```

My mistake #-o

It should have been -
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf~
```
:redface:

Please try the corrected command.

Although "works for 5 minutes" part is freaking me out. If it happens after removing the above file (correctly this time) and a reboot, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by mark.soames on 2014-03-21
@[B]Varunendra

[/B]Apologies for the delay in getting back to you.  I put in the corrected command, rebooted, and it now seems to be working ok after a few hours use, so I'm going to mark it as solved.  Anyway, your help has been invaluable and I can't express my gratitude enough.  Thank you!

---

### Post by varunendra on 2014-03-21
No problem at all! :)

Troubleshooting this card that you have is usually as easy as purging the STA driver (if was installed). But sometimes we do need extra steps, so feel free to post back if the problem returns again.

---

### Post by mark.soames on 2014-03-26
Unfortunately the problem seems to have returned.  The problem is now that the wireless card disconnects from the network at some random point in time after I login.  Sometimes it's as soon as I login; others it's up to half an hour.  If I use the command 'rfkill list all', it tells me that the wireless interface is hard blocked, but I have no way of unblocking it ('sudo rfkill unblock all' achieves nothing).  

I took the liberty of running the script you've recommended.  

```
########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux mark-RV411-RV511-E3511-S3511-RV711-E3411 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:13:28 UTC 2014 i686 i686 i686 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7179]
	Kernel driver in use: bcma-pci-bridge
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c581]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1020  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: samsung-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 194.168.4.100
nameserver 194.168.8.100


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


wlan0     No scan results


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### lsmod #####


brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
cfg80211              401762  3 b43,brcmsmac,mac80211
ssb                    51596  1 b43
bcma                   40966  3 b43,brcmsmac


##### modinfo #####


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     0ECB94B5938E7066ED68753
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     78379A0109AF2689B4F6028
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 686 


##### modules #####


loop
lp


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# USB device 0x050d:0x705a (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #####


[   15.739786] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   15.739814] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   15.739837] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   15.739881] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   15.760161] bcma: bus0: Bus registered
[   16.597863] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   17.606110] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   17.606202] b43: probe of bcma0:0 failed with error -524
[   18.763298] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   18.772818] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   20.920472] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.920550] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.920769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.921265] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.447082] wlan0: authenticate with <MAC address removed>
[   22.450087] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.456379] wlan0: authenticated
[   22.458597] wlan0: associate with <MAC address removed> (try 1/3)
[   22.461847] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[   22.462553] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   22.462623] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   22.462692] wlan0: associated
[   22.462712] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.412641] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1777.505266] brcmsmac bcma0:0: wl0: brcms_c_suspend_mac_and_wait: dead chip
[ 1777.505374] WARNING: CPU: 0 PID: 2915 at /build/buildd/linux-3.11.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:2730 brcms_c_enable_mac+0x130/0x1a0 [brcmsmac]()
[ 1777.505378] Modules linked in: parport_pc ppdev arc4 brcmsmac bnep rfcomm cordic brcmutil binfmt_misc b43 mac80211 intel_powerclamp coretemp joydev cfg80211 ssb samsung_laptop snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel snd_hda_codec microcode snd_hwdep snd_pcm bcma i915 snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb drm_kms_helper psmouse bluetooth serio_raw intel_ips snd_seq_device drm snd_timer lpc_ich snd soundcore i2c_algo_bit mei_me mei video mac_hid lp parport ahci libahci r8169 mii
[ 1777.505591]  [<f9457ee0>] ? brcms_c_enable_mac+0x130/0x1a0 [brcmsmac]
[ 1777.505611]  [<f9457ee0>] ? brcms_c_enable_mac+0x130/0x1a0 [brcmsmac]
[ 1777.505638]  [<f9457ee0>] brcms_c_enable_mac+0x130/0x1a0 [brcmsmac]
[ 1777.505661]  [<f9459afa>] brcms_c_set_channel+0xea/0x100 [brcmsmac]
[ 1777.505677]  [<f9450de2>] brcms_ops_config+0x112/0x1b0 [brcmsmac]
[ 1777.505838] WARNING: CPU: 0 PID: 2915 at /build/buildd/linux-3.11.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:2731 brcms_c_enable_mac+0x144/0x1a0 [brcmsmac]()
[ 1777.505841] Modules linked in: parport_pc ppdev arc4 brcmsmac bnep rfcomm cordic brcmutil binfmt_misc b43 mac80211 intel_powerclamp coretemp joydev cfg80211 ssb samsung_laptop snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel snd_hda_codec microcode snd_hwdep snd_pcm bcma i915 snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb drm_kms_helper psmouse bluetooth serio_raw intel_ips snd_seq_device drm snd_timer lpc_ich snd soundcore i2c_algo_bit mei_me mei video mac_hid lp parport ahci libahci r8169 mii
[ 1777.506016]  [<f9457ef4>] ? brcms_c_enable_mac+0x144/0x1a0 [brcmsmac]
[ 1777.506036]  [<f9457ef4>] ? brcms_c_enable_mac+0x144/0x1a0 [brcmsmac]
[ 1777.506063]  [<f9457ef4>] brcms_c_enable_mac+0x144/0x1a0 [brcmsmac]
[ 1777.506085]  [<f9459afa>] brcms_c_set_channel+0xea/0x100 [brcmsmac]
[ 1777.506101]  [<f9450de2>] brcms_ops_config+0x112/0x1b0 [brcmsmac]
[ 1777.506256] WARNING: CPU: 0 PID: 2915 at /build/buildd/linux-3.11.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:2738 brcms_c_enable_mac+0x16c/0x1a0 [brcmsmac]()
[ 1777.506259] Modules linked in: parport_pc ppdev arc4 brcmsmac bnep rfcomm cordic brcmutil binfmt_misc b43 mac80211 intel_powerclamp coretemp joydev cfg80211 ssb samsung_laptop snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel snd_hda_codec microcode snd_hwdep snd_pcm bcma i915 snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb drm_kms_helper psmouse bluetooth serio_raw intel_ips snd_seq_device drm snd_timer lpc_ich snd soundcore i2c_algo_bit mei_me mei video mac_hid lp parport ahci libahci r8169 mii
[ 1777.506432]  [<f9457f1c>] ? brcms_c_enable_mac+0x16c/0x1a0 [brcmsmac]
[ 1777.506452]  [<f9457f1c>] ? brcms_c_enable_mac+0x16c/0x1a0 [brcmsmac]
[ 1777.506479]  [<f9457f1c>] brcms_c_enable_mac+0x16c/0x1a0 [brcmsmac]
[ 1777.506501]  [<f9459afa>] brcms_c_set_channel+0xea/0x100 [brcmsmac]
[ 1777.506517]  [<f9450de2>] brcms_ops_config+0x112/0x1b0 [brcmsmac]
[ 1777.506671] WARNING: CPU: 0 PID: 2915 at /build/buildd/linux-3.11.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:2743 brcms_c_enable_mac+0x11f/0x1a0 [brcmsmac]()
[ 1777.506674] Modules linked in: parport_pc ppdev arc4 brcmsmac bnep rfcomm cordic brcmutil binfmt_misc b43 mac80211 intel_powerclamp coretemp joydev cfg80211 ssb samsung_laptop snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev snd_hda_intel snd_hda_codec microcode snd_hwdep snd_pcm bcma i915 snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb drm_kms_helper psmouse bluetooth serio_raw intel_ips snd_seq_device drm snd_timer lpc_ich snd soundcore i2c_algo_bit mei_me mei video mac_hid lp parport ahci libahci r8169 mii
[ 1777.506847]  [<f9457ecf>] ? brcms_c_enable_mac+0x11f/0x1a0 [brcmsmac]
[ 1777.506867]  [<f9457ecf>] ? brcms_c_enable_mac+0x11f/0x1a0 [brcmsmac]
[ 1777.506894]  [<f9457ecf>] brcms_c_enable_mac+0x11f/0x1a0 [brcmsmac]
[ 1777.506916]  [<f9459afa>] brcms_c_set_channel+0xea/0x100 [brcmsmac]
[ 1777.506932]  [<f9450de2>] brcms_ops_config+0x112/0x1b0 [brcmsmac]
[ 1777.507074] brcmsmac bcma0:0: ops->tx called while down
[ 1777.704940] brcmsmac bcma0:0: ops->tx called while down
[ 1777.732912] brcmsmac bcma0:0: ops->tx called while down
[ 1777.788889] brcmsmac bcma0:0: ops->tx called while down
[ 1777.816868] brcmsmac bcma0:0: ops->tx called while down
[ 1777.816898] brcmsmac bcma0:0: ops->tx called while down
[ 1779.352252] brcmsmac bcma0:0: ops->tx called while down
[ 1779.972128] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1779.972145] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1779.972151] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1779.972157] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[ 1779.972162] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[ 1779.972167] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[ 1779.972172] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[ 1780.099917] brcmsmac bcma0:0: ops->tx called while down
[ 1780.099934] brcmsmac bcma0:0: ops->tx called while down
[ 1780.155843] brcmsmac bcma0:0: ops->tx called while down
[ 1780.155857] brcmsmac bcma0:0: ops->tx called while down
[ 1780.211880] brcmsmac bcma0:0: ops->tx called while down
[ 1780.211897] brcmsmac bcma0:0: ops->tx called while down
[ 1780.267837] brcmsmac bcma0:0: ops->tx called while down
[ 1780.267851] brcmsmac bcma0:0: ops->tx called while down
[ 1780.323789] brcmsmac bcma0:0: ops->tx called while down
[ 1780.323803] brcmsmac bcma0:0: ops->tx called while down
[ 1780.379798] brcmsmac bcma0:0: ops->tx called while down
[ 1780.379814] brcmsmac bcma0:0: ops->tx called while down
[ 1780.435760] brcmsmac bcma0:0: ops->tx called while down
[ 1780.435777] brcmsmac bcma0:0: ops->tx called while down
[ 1780.491745] brcmsmac bcma0:0: ops->tx called while down
[ 1780.491759] brcmsmac bcma0:0: ops->tx called while down
[ 1780.547737] brcmsmac bcma0:0: ops->tx called while down
[ 1780.547751] brcmsmac bcma0:0: ops->tx called while down
[ 1780.603674] brcmsmac bcma0:0: ops->tx called while down
[ 1780.603688] brcmsmac bcma0:0: ops->tx called while down
[ 1780.659663] brcmsmac bcma0:0: ops->tx called while down
[ 1780.659677] brcmsmac bcma0:0: ops->tx called while down
[ 1780.904099] wlan0: authenticate with <MAC address removed>
[ 1780.904177] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1780.904190] brcmsmac bcma0:0: ops->tx called while down
[ 1782.362954] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1782.362980] brcmsmac bcma0:0: ops->tx called while down
[ 1783.350532] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1783.350557] brcmsmac bcma0:0: ops->tx called while down
[ 1784.350109] wlan0: authentication with <MAC address removed> timed out
[ 1784.490061] brcmsmac bcma0:0: ops->tx called while down
[ 1784.490079] brcmsmac bcma0:0: ops->tx called while down
[ 1784.546017] brcmsmac bcma0:0: ops->tx called while down
[ 1784.546032] brcmsmac bcma0:0: ops->tx called while down
[ 1784.602007] brcmsmac bcma0:0: ops->tx called while down
[ 1784.602019] brcmsmac bcma0:0: ops->tx called while down
[ 1784.657977] brcmsmac bcma0:0: ops->tx called while down
[ 1784.657990] brcmsmac bcma0:0: ops->tx called while down
[ 1784.713956] brcmsmac bcma0:0: ops->tx called while down
[ 1784.713969] brcmsmac bcma0:0: ops->tx called while down
[ 1784.769935] brcmsmac bcma0:0: ops->tx called while down
[ 1784.769950] brcmsmac bcma0:0: ops->tx called while down
[ 1784.825910] brcmsmac bcma0:0: ops->tx called while down
[ 1784.825923] brcmsmac bcma0:0: ops->tx called while down
[ 1784.881896] brcmsmac bcma0:0: ops->tx called while down
[ 1784.881913] brcmsmac bcma0:0: ops->tx called while down
[ 1784.937840] brcmsmac bcma0:0: ops->tx called while down
[ 1784.937852] brcmsmac bcma0:0: ops->tx called while down
[ 1784.993816] brcmsmac bcma0:0: ops->tx called while down
[ 1784.993829] brcmsmac bcma0:0: ops->tx called while down
[ 1785.049818] brcmsmac bcma0:0: ops->tx called while down
[ 1785.049830] brcmsmac bcma0:0: ops->tx called while down
[ 1790.323611] brcmsmac bcma0:0: ops->tx called while down
[ 1790.323629] brcmsmac bcma0:0: ops->tx called while down
[ 1790.379579] brcmsmac bcma0:0: ops->tx called while down
[ 1790.379597] brcmsmac bcma0:0: ops->tx called while down
[ 1790.435551] brcmsmac bcma0:0: ops->tx called while down
[ 1790.435564] brcmsmac bcma0:0: ops->tx called while down
[ 1790.491498] brcmsmac bcma0:0: ops->tx called while down
[ 1790.491512] brcmsmac bcma0:0: ops->tx called while down
[ 1790.547512] brcmsmac bcma0:0: ops->tx called while down
[ 1790.547524] brcmsmac bcma0:0: ops->tx called while down
[ 1790.603478] brcmsmac bcma0:0: ops->tx called while down
[ 1790.603491] brcmsmac bcma0:0: ops->tx called while down
[ 1790.659451] brcmsmac bcma0:0: ops->tx called while down
[ 1790.659464] brcmsmac bcma0:0: ops->tx called while down
[ 1790.715446] brcmsmac bcma0:0: ops->tx called while down
[ 1790.715460] brcmsmac bcma0:0: ops->tx called while down
[ 1790.771405] brcmsmac bcma0:0: ops->tx called while down
[ 1790.771418] brcmsmac bcma0:0: ops->tx called while down
[ 1790.827393] brcmsmac bcma0:0: ops->tx called while down
[ 1790.827405] brcmsmac bcma0:0: ops->tx called while down
[ 1790.883381] brcmsmac bcma0:0: ops->tx called while down
[ 1790.883397] brcmsmac bcma0:0: ops->tx called while down
[ 1795.713349] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1795.785630] brcmsmac bcma0:0: ops->tx called while down
[ 1795.841229] brcmsmac bcma0:0: ops->tx called while down
[ 1795.897253] brcmsmac bcma0:0: ops->tx called while down
[ 1795.953196] brcmsmac bcma0:0: ops->tx called while down
[ 1796.009198] brcmsmac bcma0:0: ops->tx called while down
[ 1796.065140] brcmsmac bcma0:0: ops->tx called while down
[ 1796.121149] brcmsmac bcma0:0: ops->tx called while down
[ 1796.177140] brcmsmac bcma0:0: ops->tx called while down
[ 1796.233082] brcmsmac bcma0:0: ops->tx called while down
[ 1796.289086] brcmsmac bcma0:0: ops->tx called while down
[ 1796.345059] brcmsmac bcma0:0: ops->tx called while down
[ 1799.383783] brcmsmac bcma0:0: ops->tx called while down
[ 1799.439749] brcmsmac bcma0:0: ops->tx called while down
[ 1799.495719] brcmsmac bcma0:0: ops->tx called while down
[ 1799.551694] brcmsmac bcma0:0: ops->tx called while down
[ 1799.607684] brcmsmac bcma0:0: ops->tx called while down
[ 1799.663615] brcmsmac bcma0:0: ops->tx called while down
[ 1799.719610] brcmsmac bcma0:0: ops->tx called while down
[ 1799.775605] brcmsmac bcma0:0: ops->tx called while down
[ 1799.831574] brcmsmac bcma0:0: ops->tx called while down
[ 1799.887555] brcmsmac bcma0:0: ops->tx called while down
[ 1799.943527] brcmsmac bcma0:0: ops->tx called while down
[ 1822.374068] brcmsmac bcma0:0: ops->tx called while down
[ 1822.430041] brcmsmac bcma0:0: ops->tx called while down
[ 1822.486017] brcmsmac bcma0:0: ops->tx called while down
[ 1822.541982] brcmsmac bcma0:0: ops->tx called while down
[ 1822.597959] brcmsmac bcma0:0: ops->tx called while down
[ 1822.653915] brcmsmac bcma0:0: ops->tx called while down
[ 1822.709920] brcmsmac bcma0:0: ops->tx called while down
[ 1822.765899] brcmsmac bcma0:0: ops->tx called while down
[ 1822.821864] brcmsmac bcma0:0: ops->tx called while down
[ 1822.877858] brcmsmac bcma0:0: ops->tx called while down
[ 1822.933833] brcmsmac bcma0:0: ops->tx called while down
[ 1855.364118] brcmsmac bcma0:0: ops->tx called while down
[ 1855.420102] brcmsmac bcma0:0: ops->tx called while down
[ 1855.476074] brcmsmac bcma0:0: ops->tx called while down
[ 1855.532054] brcmsmac bcma0:0: ops->tx called while down
[ 1855.588031] brcmsmac bcma0:0: ops->tx called while down
[ 1855.644007] brcmsmac bcma0:0: ops->tx called while down
[ 1855.699981] brcmsmac bcma0:0: ops->tx called while down
[ 1855.755944] brcmsmac bcma0:0: ops->tx called while down
[ 1855.811921] brcmsmac bcma0:0: ops->tx called while down
[ 1855.867917] brcmsmac bcma0:0: ops->tx called while down
[ 1855.923883] brcmsmac bcma0:0: ops->tx called while down
[ 1898.345969] brcmsmac bcma0:0: ops->tx called while down
[ 1898.401930] brcmsmac bcma0:0: ops->tx called while down
[ 1898.457916] brcmsmac bcma0:0: ops->tx called while down
[ 1898.513889] brcmsmac bcma0:0: ops->tx called while down
[ 1898.569866] brcmsmac bcma0:0: ops->tx called while down
[ 1898.625845] brcmsmac bcma0:0: ops->tx called while down
[ 1898.681819] brcmsmac bcma0:0: ops->tx called while down
[ 1898.737803] brcmsmac bcma0:0: ops->tx called while down
[ 1898.793775] brcmsmac bcma0:0: ops->tx called while down
[ 1898.849744] brcmsmac bcma0:0: ops->tx called while down
[ 1898.905696] brcmsmac bcma0:0: ops->tx called while down
[ 1951.323591] brcmsmac bcma0:0: ops->tx called while down
[ 1951.379553] brcmsmac bcma0:0: ops->tx called while down
[ 1951.435518] brcmsmac bcma0:0: ops->tx called while down
[ 1951.491506] brcmsmac bcma0:0: ops->tx called while down
[ 1951.547479] brcmsmac bcma0:0: ops->tx called while down
[ 1951.603459] brcmsmac bcma0:0: ops->tx called while down
[ 1951.659434] brcmsmac bcma0:0: ops->tx called while down
[ 1951.715402] brcmsmac bcma0:0: ops->tx called while down
[ 1951.771371] brcmsmac bcma0:0: ops->tx called while down
[ 1951.827367] brcmsmac bcma0:0: ops->tx called while down
[ 1951.883313] brcmsmac bcma0:0: ops->tx called while down
[ 2014.292928] brcmsmac bcma0:0: ops->tx called while down
[ 2014.348936] brcmsmac bcma0:0: ops->tx called while down
[ 2014.404920] brcmsmac bcma0:0: ops->tx called while down
[ 2014.460892] brcmsmac bcma0:0: ops->tx called while down
[ 2014.516863] brcmsmac bcma0:0: ops->tx called while down
[ 2014.572807] brcmsmac bcma0:0: ops->tx called while down
[ 2014.628798] brcmsmac bcma0:0: ops->tx called while down
[ 2014.684805] brcmsmac bcma0:0: ops->tx called while down
[ 2014.740756] brcmsmac bcma0:0: ops->tx called while down
[ 2014.796751] brcmsmac bcma0:0: ops->tx called while down
[ 2014.852722] brcmsmac bcma0:0: ops->tx called while down
[ 2077.270361] brcmsmac bcma0:0: ops->tx called while down
[ 2077.326323] brcmsmac bcma0:0: ops->tx called while down
[ 2077.382325] brcmsmac bcma0:0: ops->tx called while down
[ 2077.438274] brcmsmac bcma0:0: ops->tx called while down
[ 2077.494518] brcmsmac bcma0:0: ops->tx called while down
[ 2077.550246] brcmsmac bcma0:0: ops->tx called while down
[ 2077.606206] brcmsmac bcma0:0: ops->tx called while down
[ 2077.662151] brcmsmac bcma0:0: ops->tx called while down
[ 2077.718550] brcmsmac bcma0:0: ops->tx called while down
[ 2077.774153] brcmsmac bcma0:0: ops->tx called while down
[ 2077.830127] brcmsmac bcma0:0: ops->tx called while down
[ 2140.267560] brcmsmac bcma0:0: ops->tx called while down
[ 2140.323569] brcmsmac bcma0:0: ops->tx called while down
[ 2140.379585] brcmsmac bcma0:0: ops->tx called while down
[ 2140.435584] brcmsmac bcma0:0: ops->tx called while down
[ 2140.491588] brcmsmac bcma0:0: ops->tx called while down
[ 2140.547589] brcmsmac bcma0:0: ops->tx called while down
[ 2140.603597] brcmsmac bcma0:0: ops->tx called while down
[ 2140.660259] brcmsmac bcma0:0: ops->tx called while down
[ 2140.715580] brcmsmac bcma0:0: ops->tx called while down
[ 2140.771608] brcmsmac bcma0:0: ops->tx called while down
[ 2140.827605] brcmsmac bcma0:0: ops->tx called while down
[ 2203.243903] brcmsmac bcma0:0: ops->tx called while down
[ 2203.299867] brcmsmac bcma0:0: ops->tx called while down
[ 2203.355844] brcmsmac bcma0:0: ops->tx called while down
[ 2203.411803] brcmsmac bcma0:0: ops->tx called while down
[ 2203.467781] brcmsmac bcma0:0: ops->tx called while down
[ 2203.523745] brcmsmac bcma0:0: ops->tx called while down
[ 2203.579716] brcmsmac bcma0:0: ops->tx called while down
[ 2203.635723] brcmsmac bcma0:0: ops->tx called while down
[ 2203.691690] brcmsmac bcma0:0: ops->tx called while down
[ 2203.747685] brcmsmac bcma0:0: ops->tx called while down
[ 2203.803636] brcmsmac bcma0:0: ops->tx called while down
[ 2266.217297] brcmsmac bcma0:0: ops->tx called while down
[ 2266.273259] brcmsmac bcma0:0: ops->tx called while down
[ 2266.329205] brcmsmac bcma0:0: ops->tx called while down
[ 2266.385206] brcmsmac bcma0:0: ops->tx called while down
[ 2266.441175] brcmsmac bcma0:0: ops->tx called while down
[ 2266.497161] brcmsmac bcma0:0: ops->tx called while down
[ 2266.553140] brcmsmac bcma0:0: ops->tx called while down
[ 2266.609113] brcmsmac bcma0:0: ops->tx called while down
[ 2266.665093] brcmsmac bcma0:0: ops->tx called while down
[ 2266.721029] brcmsmac bcma0:0: ops->tx called while down
[ 2266.777018] brcmsmac bcma0:0: ops->tx called while down
[ 2329.186627] brcmsmac bcma0:0: ops->tx called while down
[ 2329.242657] brcmsmac bcma0:0: ops->tx called while down
[ 2329.298622] brcmsmac bcma0:0: ops->tx called while down
[ 2329.354590] brcmsmac bcma0:0: ops->tx called while down
[ 2329.410583] brcmsmac bcma0:0: ops->tx called while down
[ 2329.466554] brcmsmac bcma0:0: ops->tx called while down
[ 2329.522531] brcmsmac bcma0:0: ops->tx called while down
[ 2329.578522] brcmsmac bcma0:0: ops->tx called while down
[ 2329.634469] brcmsmac bcma0:0: ops->tx called while down
[ 2329.690451] brcmsmac bcma0:0: ops->tx called while down
[ 2329.746473] brcmsmac bcma0:0: ops->tx called while down
[ 2392.164052] brcmsmac bcma0:0: ops->tx called while down
[ 2392.220070] brcmsmac bcma0:0: ops->tx called while down
[ 2392.276015] brcmsmac bcma0:0: ops->tx called while down
[ 2392.331973] brcmsmac bcma0:0: ops->tx called while down
[ 2392.387967] brcmsmac bcma0:0: ops->tx called while down
[ 2392.443929] brcmsmac bcma0:0: ops->tx called while down
[ 2392.499906] brcmsmac bcma0:0: ops->tx called while down
[ 2392.555884] brcmsmac bcma0:0: ops->tx called while down
[ 2392.611831] brcmsmac bcma0:0: ops->tx called while down
[ 2392.667866] brcmsmac bcma0:0: ops->tx called while down
[ 2392.723809] brcmsmac bcma0:0: ops->tx called while down
[ 2455.133429] brcmsmac bcma0:0: ops->tx called while down
[ 2455.189430] brcmsmac bcma0:0: ops->tx called while down
[ 2455.245408] brcmsmac bcma0:0: ops->tx called while down
[ 2455.301380] brcmsmac bcma0:0: ops->tx called while down
[ 2455.357373] brcmsmac bcma0:0: ops->tx called while down
[ 2455.413333] brcmsmac bcma0:0: ops->tx called while down
[ 2455.469312] brcmsmac bcma0:0: ops->tx called while down
[ 2455.525293] brcmsmac bcma0:0: ops->tx called while down
[ 2455.581270] brcmsmac bcma0:0: ops->tx called while down
[ 2455.637242] brcmsmac bcma0:0: ops->tx called while down
[ 2455.693219] brcmsmac bcma0:0: ops->tx called while down
[ 2518.106822] brcmsmac bcma0:0: ops->tx called while down
[ 2518.162836] brcmsmac bcma0:0: ops->tx called while down
[ 2518.218796] brcmsmac bcma0:0: ops->tx called while down
[ 2518.274774] brcmsmac bcma0:0: ops->tx called while down
[ 2518.330727] brcmsmac bcma0:0: ops->tx called while down
[ 2518.386726] brcmsmac bcma0:0: ops->tx called while down
[ 2518.442705] brcmsmac bcma0:0: ops->tx called while down
[ 2518.498691] brcmsmac bcma0:0: ops->tx called while down
[ 2518.554645] brcmsmac bcma0:0: ops->tx called while down
[ 2518.610642] brcmsmac bcma0:0: ops->tx called while down
[ 2518.666609] brcmsmac bcma0:0: ops->tx called while down
[ 2581.084202] brcmsmac bcma0:0: ops->tx called while down
[ 2581.140221] brcmsmac bcma0:0: ops->tx called while down
[ 2581.196189] brcmsmac bcma0:0: ops->tx called while down
[ 2581.252164] brcmsmac bcma0:0: ops->tx called while down
[ 2581.308136] brcmsmac bcma0:0: ops->tx called while down
[ 2581.364113] brcmsmac bcma0:0: ops->tx called while down
[ 2581.420080] brcmsmac bcma0:0: ops->tx called while down
[ 2581.476072] brcmsmac bcma0:0: ops->tx called while down
[ 2581.532037] brcmsmac bcma0:0: ops->tx called while down
[ 2581.588035] brcmsmac bcma0:0: ops->tx called while down
[ 2581.643999] brcmsmac bcma0:0: ops->tx called while down
[ 2644.057598] brcmsmac bcma0:0: ops->tx called while down
[ 2644.113609] brcmsmac bcma0:0: ops->tx called while down
[ 2644.169577] brcmsmac bcma0:0: ops->tx called while down
[ 2644.225566] brcmsmac bcma0:0: ops->tx called while down
[ 2644.281540] brcmsmac bcma0:0: ops->tx called while down
[ 2644.337484] brcmsmac bcma0:0: ops->tx called while down
[ 2644.393481] brcmsmac bcma0:0: ops->tx called while down
[ 2644.449454] brcmsmac bcma0:0: ops->tx called while down
[ 2644.505418] brcmsmac bcma0:0: ops->tx called while down
[ 2644.561388] brcmsmac bcma0:0: ops->tx called while down
[ 2644.617382] brcmsmac bcma0:0: ops->tx called while down
[ 2707.030992] brcmsmac bcma0:0: ops->tx called while down
[ 2707.086991] brcmsmac bcma0:0: ops->tx called while down
[ 2707.142969] brcmsmac bcma0:0: ops->tx called while down
[ 2707.198943] brcmsmac bcma0:0: ops->tx called while down
[ 2707.254922] brcmsmac bcma0:0: ops->tx called while down
[ 2707.310846] brcmsmac bcma0:0: ops->tx called while down
[ 2707.366872] brcmsmac bcma0:0: ops->tx called while down
[ 2707.422840] brcmsmac bcma0:0: ops->tx called while down
[ 2707.478811] brcmsmac bcma0:0: ops->tx called while down
[ 2707.534786] brcmsmac bcma0:0: ops->tx called while down
[ 2707.590799] brcmsmac bcma0:0: ops->tx called while down
[ 2770.004352] brcmsmac bcma0:0: ops->tx called while down
[ 2770.060329] brcmsmac bcma0:0: ops->tx called while down
[ 2770.116425] brcmsmac bcma0:0: ops->tx called while down
[ 2770.172307] brcmsmac bcma0:0: ops->tx called while down
[ 2770.228321] brcmsmac bcma0:0: ops->tx called while down
[ 2770.284256] brcmsmac bcma0:0: ops->tx called while down
[ 2770.340244] brcmsmac bcma0:0: ops->tx called while down
[ 2770.396204] brcmsmac bcma0:0: ops->tx called while down
[ 2770.452179] brcmsmac bcma0:0: ops->tx called while down
[ 2770.508147] brcmsmac bcma0:0: ops->tx called while down
[ 2770.564116] brcmsmac bcma0:0: ops->tx called while down
[ 2794.498050] brcmsmac bcma0:0: ops->tx called while down
[ 2794.554007] brcmsmac bcma0:0: ops->tx called while down
[ 2794.610008] brcmsmac bcma0:0: ops->tx called while down
[ 2794.665972] brcmsmac bcma0:0: ops->tx called while down
[ 2794.721947] brcmsmac bcma0:0: ops->tx called while down
[ 2794.777919] brcmsmac bcma0:0: ops->tx called while down
[ 2794.833901] brcmsmac bcma0:0: ops->tx called while down
[ 2794.889878] brcmsmac bcma0:0: ops->tx called while down
[ 2794.945866] brcmsmac bcma0:0: ops->tx called while down
[ 2795.001853] brcmsmac bcma0:0: ops->tx called while down
[ 2795.057822] brcmsmac bcma0:0: ops->tx called while down


########## wireless info END ############

```


With many thanks.

---

### Post by varunendra on 2014-03-26
> **mark.soames said:**
> If I use the command 'rfkill list all', it tells me that the wireless interface is hard blocked
But the script output says otherwise? -
```
##### rfkill #####
....
1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
....
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

However, it also shows another problem -
```
##### lsmod #####

brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356429  0 
mac80211              517444  2 b43,brcmsmac
cfg80211              401762  3 b43,brcmsmac,mac80211
ssb                    51596  1 b43
bcma                   40966  3 b43,brcmsmac
```
As you can see above, the driver "b43" has also been loaded (it shouldn't) and is conflicting with brcmsmac over resources.

Accordingly, please try this -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

The first code will append two lines "blacklist b43" and "blacklist ssb" into your blacklist file thus preventing them from loading since next boot.
The second command will remove the current udev rules file for network. It'll be automatically regenerated when required - with only relevant entries this time.

Reboot after this and see if you can connect now.

---

### Post by mark.soames on 2014-03-26
That seems not to have worked.  Rfkill is listing it as blocked:

```

1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: samsung-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by varunendra on 2014-03-26
Please confirm if you have tried the hardware switch (a physical switch or a Fn+ key combo etc., whatever it is).

In the script output, it was shown as unblocked, was it an older report?

Lastly, have you tried resetting the BIOS? Your installation is 32 bit, which means you most probably have a 'Legacy Mode' installation, not UEFI. As such, it should be perfectly safe to reset the BIOS to factory defaults and see if the hard-block is removed.

---

### Post by mark.soames on 2014-03-26
Yes, I've tried that.  It's a key combination which used to not work at all.  I managed to assign a shortcut to it, which does in fact work before the wifi shuts down, but won't work after it has. 

The script output showing it was blocked was after I had unchecked and then rechecked 'Enable Networking' in my dashboard applet.  

I'll try the reset now and let you know how I get on.

---

### Post by varunendra on 2014-03-26
> **mark.soames said:**
> I'll try the reset now and let you know how I get on.

I'll be waiting curiously. If this doesn't work, I guess my next move will be to try a backported driver, although so far I don't have the slightest hint that it is needed or would work any better for this kind of problem.

---

### Post by mark.soames on 2014-03-27
So, I wasn't quite sure how to go about a BIOS reset, but using my boot menu I loaded default settings which seemed like broadly the right thing to do.  That hasn't had any effect.  If that's not the right way of going about it though, please let me know.

---

### Post by varunendra on 2014-03-27
> **mark.soames said:**
> So, I wasn't quite sure how to go about a BIOS reset, but using my boot menu I loaded default settings which seemed like broadly the right thing to do.  That hasn't had any effect.  If that's not the right way of going about it though, please let me know.

Sorry, I'm currently travelling with low battery and almost no signal. May not be able to dig deeper and reply back for a little more time (could be a few hours to a day or two!)

Any of the wireless gurus, if you notice this thread, please jump in!

**@mark.soames,**

In the meanwhile, you may try the instructions in this post to try installing a newer driver like I mentioned in my previous post : [http://ubuntuforums.org/showthread.php?t=2213337&p=12970055#post12970055](http://ubuntuforums.org/showthread.php?t=2213337&p=12970055#post12970055)

Although I have never tested this one before, so can't assure of any better performance.

---

### Post by mark.soames on 2014-03-31
@Varunendra

Thank you for all your kind help so far. It's absolutely invaluable.  As suggested, I tried following the instructions you linked to, but with no luck.  After doing some more research, the best I could come up with was to add the following lines to my blacklist.conf file, in case there was some kind of clash:

```

blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper

```

That had no effect.  The page at [http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211) suggests that for some unknown reason, brcmsmac just doesn't work with some editions of the 4313 chipset.  It looks like mine is probably within this category.  

If you have any ideas for where to go from here, I'd be really grateful.  The current situation is that my wireless just isn't working (it doesn't even show up in the dashboard applet).  I've tried going over your suggestions in this thread again, but they haven't produced any change.  

Thanks again!

---

### Post by chili555 on 2014-03-31
Varun is away on business and I'm filling in. First, it's not correct to blacklist bcma; it is one of the dependencies of brcmsmac. Please open a terminal and do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Please change the lines you added to read:```
blacklist b43
blacklist b43legacy
#blacklist bcma
blacklist ndiswrapper
```Proofread, save and close gedit. Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then, set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Of course, substitute your country code if not Iceland. Proofread carefully, save and close gedit. 

Now reboot and let us hear your report. If these changes are ineffective, we plunge into backports!

---

### Post by mark.soames on 2014-03-31
Hi Chili, thanks for the assistance.

I followed your instructions.  There's some improvement.  After rebooting, it connected to my router at the login screen.  However, after I'd logged in, it immediately disconnected.  Now my applet is showing one network (not my own).  

Thanks for your help!

---

### Post by chili555 on 2014-03-31
Before we take the backports plunge, let's just confirm that all available settings are as good as we can get them. Please run and post the wireless script in Varun's signature.

---

### Post by mark.soames on 2014-03-31
Thanks for your help Chili.  Here's the output:

```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy


##### kernel #####


Linux mark-RV411-RV511-E3511-S3511-RV711-E3411 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:32 UTC 2014 i686 i686 i686 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7179]
	Kernel driver in use: bcma-pci-bridge
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c581]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1020  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: samsung-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 194.168.4.100
nameserver 194.168.8.100


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


##### iwlist #####


wlan0     No scan results


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


##### lsmod #####


brcmsmac              529716  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
mac80211              517444  1 brcmsmac
cfg80211              401762  2 brcmsmac,mac80211
bcma                   40966  2 brcmsmac


##### modinfo #####


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 686 


##### modules #####


loop
lp


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist ndiswrapper


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   16.168590] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   16.168619] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   16.168640] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   16.168684] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   16.181199] bcma: bus0: Bus registered
[   17.125749] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   18.498115] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   18.577948] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   22.915711] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.915792] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   22.916041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.916481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.969833] wlan0: authenticate with <MAC address removed>
[   24.973679] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.977043] wlan0: authenticated
[   24.977328] wlan0: associate with <MAC address removed> (try 1/3)
[   24.980594] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[   24.981190] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   24.981195] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   24.981204] wlan0: associated
[   24.981227] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.000533] brcmsmac bcma0:0: phyerr 0x8, rate 0xb00
[   26.717211] brcmsmac bcma0:0: phyerr 0x8, rate 0xb00
[   26.717259] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.727844] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   27.900331] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   27.900337] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.900466] brcmsmac bcma0:0: phyerr 0x8, rate 0x903
[   27.900469] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.900572] brcmsmac bcma0:0: phyerr 0x8, rate 0x903
[   27.900577] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.900695] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   27.900702] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.900859] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   27.900867] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.901032] brcmsmac bcma0:0: phyerr 0x8, rate 0x903
[   27.901039] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.901175] brcmsmac bcma0:0: phyerr 0x8, rate 0x903
[   27.901182] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   27.901342] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   27.901349] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   28.081365] brcmsmac bcma0:0: phyerr 0x80, rate 0x903
[   28.081381] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: supr_status 0x18
[   28.409966] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: supr_status 0x18
[   29.911144] brcmsmac bcma0:0: phyerr 0x80, rate 0x906
[   29.911150] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: supr_status 0x18
[   29.914866] brcmsmac bcma0:0: phyerr 0x80, rate 0x906
[   29.914881] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: supr_status 0x18
[   32.194464] brcmsmac bcma0:0: phyerr 0x4, rate 0x905
[   32.194471] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x4)
[   32.468467] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   32.468474] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   32.469162] brcmsmac bcma0:0: phyerr 0x8, rate 0x906
[   32.469165] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x8)
[   32.543472] brcmsmac bcma0:0: phyerr 0x10, rate 0x906
[   32.543479] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: ampdu tx phy error (0x10)
[   38.975226] brcmsmac bcma0:0: phyerr 0x80, rate 0x905
[   38.975235] brcmsmac bcma0:0: brcms_c_ampdu_dotxstatus_complete: supr_status 0x18
[   42.395007] brcmsmac bcma0:0: wl0: brcms_c_watchdog: dead chip
[   42.478952] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   42.478960] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   42.478962] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   42.478966] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[   42.478968] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[   42.478970] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[   42.478972] brcmsmac bcma0:0: wl0: brcms_c_wme_setparams : no-clock
[   42.606805] brcmsmac bcma0:0: ops->tx called while down
[   42.606824] brcmsmac bcma0:0: ops->tx called while down
[   42.662707] brcmsmac bcma0:0: ops->tx called while down
[   42.662719] brcmsmac bcma0:0: ops->tx called while down
[   42.718655] brcmsmac bcma0:0: ops->tx called while down
[   42.718661] brcmsmac bcma0:0: ops->tx called while down
[   42.774597] brcmsmac bcma0:0: ops->tx called while down
[   42.774603] brcmsmac bcma0:0: ops->tx called while down
[   42.830575] brcmsmac bcma0:0: ops->tx called while down
[   42.830587] brcmsmac bcma0:0: ops->tx called while down
[   42.886496] brcmsmac bcma0:0: ops->tx called while down
[   42.886505] brcmsmac bcma0:0: ops->tx called while down
[   42.942465] brcmsmac bcma0:0: ops->tx called while down
[   42.942481] brcmsmac bcma0:0: ops->tx called while down
[   42.998404] brcmsmac bcma0:0: ops->tx called while down
[   42.998416] brcmsmac bcma0:0: ops->tx called while down
[   43.054357] brcmsmac bcma0:0: ops->tx called while down
[   43.054368] brcmsmac bcma0:0: ops->tx called while down
[   43.110636] brcmsmac bcma0:0: ops->tx called while down
[   43.110645] brcmsmac bcma0:0: ops->tx called while down
[   43.166217] brcmsmac bcma0:0: ops->tx called while down
[   43.166226] brcmsmac bcma0:0: ops->tx called while down
[   43.414349] wlan0: authenticate with <MAC address removed>
[   43.414426] wlan0: send auth to <MAC address removed> (try 1/3)
[   43.414439] brcmsmac bcma0:0: ops->tx called while down
[   44.896624] wlan0: send auth to <MAC address removed> (try 2/3)
[   44.896642] brcmsmac bcma0:0: ops->tx called while down
[   45.907710] wlan0: send auth to <MAC address removed> (try 3/3)
[   45.907735] brcmsmac bcma0:0: ops->tx called while down
[   46.906807] wlan0: authentication with <MAC address removed> timed out
[   47.146575] brcmsmac bcma0:0: ops->tx called while down
[   47.202530] brcmsmac bcma0:0: ops->tx called while down
[   47.258498] brcmsmac bcma0:0: ops->tx called while down
[   47.314414] brcmsmac bcma0:0: ops->tx called while down
[   47.370378] brcmsmac bcma0:0: ops->tx called while down
[   47.426282] brcmsmac bcma0:0: ops->tx called while down
[   47.482224] brcmsmac bcma0:0: ops->tx called while down
[   47.538188] brcmsmac bcma0:0: ops->tx called while down
[   47.594196] brcmsmac bcma0:0: ops->tx called while down
[   47.650094] brcmsmac bcma0:0: ops->tx called while down
[   47.706047] brcmsmac bcma0:0: ops->tx called while down
[   48.245564] brcmsmac bcma0:0: ops->tx called while down
[   48.245582] brcmsmac bcma0:0: ops->tx called while down
[   48.301498] brcmsmac bcma0:0: ops->tx called while down
[   48.301511] brcmsmac bcma0:0: ops->tx called while down
[   48.357448] brcmsmac bcma0:0: ops->tx called while down
[   48.357456] brcmsmac bcma0:0: ops->tx called while down
[   48.413401] brcmsmac bcma0:0: ops->tx called while down
[   48.413414] brcmsmac bcma0:0: ops->tx called while down
[   48.469386] brcmsmac bcma0:0: ops->tx called while down
[   48.469399] brcmsmac bcma0:0: ops->tx called while down
[   48.525330] brcmsmac bcma0:0: ops->tx called while down
[   48.525345] brcmsmac bcma0:0: ops->tx called while down
[   48.581233] brcmsmac bcma0:0: ops->tx called while down
[   48.581238] brcmsmac bcma0:0: ops->tx called while down
[   48.637223] brcmsmac bcma0:0: ops->tx called while down
[   48.637236] brcmsmac bcma0:0: ops->tx called while down
[   48.693109] brcmsmac bcma0:0: ops->tx called while down
[   48.693118] brcmsmac bcma0:0: ops->tx called while down
[   48.749084] brcmsmac bcma0:0: ops->tx called while down
[   48.749092] brcmsmac bcma0:0: ops->tx called while down
[   48.805038] brcmsmac bcma0:0: ops->tx called while down
[   48.805044] brcmsmac bcma0:0: ops->tx called while down
[   54.072206] brcmsmac bcma0:0: ops->tx called while down
[   54.072223] brcmsmac bcma0:0: ops->tx called while down
[   54.128143] brcmsmac bcma0:0: ops->tx called while down
[   54.128159] brcmsmac bcma0:0: ops->tx called while down
[   54.184118] brcmsmac bcma0:0: ops->tx called while down
[   54.184131] brcmsmac bcma0:0: ops->tx called while down
[   54.240038] brcmsmac bcma0:0: ops->tx called while down
[   54.240051] brcmsmac bcma0:0: ops->tx called while down
[   54.295975] brcmsmac bcma0:0: ops->tx called while down
[   54.295990] brcmsmac bcma0:0: ops->tx called while down
[   54.351888] brcmsmac bcma0:0: ops->tx called while down
[   54.351895] brcmsmac bcma0:0: ops->tx called while down
[   54.407915] brcmsmac bcma0:0: ops->tx called while down
[   54.407931] brcmsmac bcma0:0: ops->tx called while down
[   54.463816] brcmsmac bcma0:0: ops->tx called while down
[   54.463828] brcmsmac bcma0:0: ops->tx called while down
[   54.519788] brcmsmac bcma0:0: ops->tx called while down
[   54.519800] brcmsmac bcma0:0: ops->tx called while down
[   54.575739] brcmsmac bcma0:0: ops->tx called while down
[   54.575749] brcmsmac bcma0:0: ops->tx called while down
[   54.631681] brcmsmac bcma0:0: ops->tx called while down
[   54.631696] brcmsmac bcma0:0: ops->tx called while down
[   58.328299] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.380187] brcmsmac bcma0:0: ops->tx called while down
[   58.436171] brcmsmac bcma0:0: ops->tx called while down
[   58.492117] brcmsmac bcma0:0: ops->tx called while down
[   58.548059] brcmsmac bcma0:0: ops->tx called while down
[   58.604004] brcmsmac bcma0:0: ops->tx called while down
[   58.659955] brcmsmac bcma0:0: ops->tx called while down
[   58.715898] brcmsmac bcma0:0: ops->tx called while down
[   58.771858] brcmsmac bcma0:0: ops->tx called while down
[   58.827801] brcmsmac bcma0:0: ops->tx called while down
[   58.883778] brcmsmac bcma0:0: ops->tx called while down
[   58.939695] brcmsmac bcma0:0: ops->tx called while down
[   62.108842] brcmsmac bcma0:0: ops->tx called while down
[   62.164695] brcmsmac bcma0:0: ops->tx called while down
[   62.220663] brcmsmac bcma0:0: ops->tx called while down
[   62.276624] brcmsmac bcma0:0: ops->tx called while down
[   62.332563] brcmsmac bcma0:0: ops->tx called while down
[   62.388517] brcmsmac bcma0:0: ops->tx called while down
[   62.444460] brcmsmac bcma0:0: ops->tx called while down
[   62.500429] brcmsmac bcma0:0: ops->tx called while down
[   62.556343] brcmsmac bcma0:0: ops->tx called while down
[   62.612301] brcmsmac bcma0:0: ops->tx called while down
[   62.668285] brcmsmac bcma0:0: ops->tx called while down
[   85.083612] brcmsmac bcma0:0: ops->tx called while down
[   85.139477] brcmsmac bcma0:0: ops->tx called while down
[   85.195440] brcmsmac bcma0:0: ops->tx called while down
[   85.251432] brcmsmac bcma0:0: ops->tx called while down
[   85.307323] brcmsmac bcma0:0: ops->tx called while down
[   85.363290] brcmsmac bcma0:0: ops->tx called while down
[   85.419298] brcmsmac bcma0:0: ops->tx called while down
[   85.475246] brcmsmac bcma0:0: ops->tx called while down
[   85.531112] brcmsmac bcma0:0: ops->tx called while down
[   85.587102] brcmsmac bcma0:0: ops->tx called while down
[   85.643022] brcmsmac bcma0:0: ops->tx called while down
[  118.057195] brcmsmac bcma0:0: ops->tx called while down
[  118.113099] brcmsmac bcma0:0: ops->tx called while down
[  118.169063] brcmsmac bcma0:0: ops->tx called while down
[  118.225024] brcmsmac bcma0:0: ops->tx called while down
[  118.280978] brcmsmac bcma0:0: ops->tx called while down
[  118.336913] brcmsmac bcma0:0: ops->tx called while down
[  118.392883] brcmsmac bcma0:0: ops->tx called while down
[  118.448818] brcmsmac bcma0:0: ops->tx called while down
[  118.504727] brcmsmac bcma0:0: ops->tx called while down
[  118.560686] brcmsmac bcma0:0: ops->tx called while down
[  118.616668] brcmsmac bcma0:0: ops->tx called while down
[  161.017553] brcmsmac bcma0:0: ops->tx called while down
[  161.073489] brcmsmac bcma0:0: ops->tx called while down
[  161.129413] brcmsmac bcma0:0: ops->tx called while down
[  161.185381] brcmsmac bcma0:0: ops->tx called while down
[  161.241333] brcmsmac bcma0:0: ops->tx called while down
[  161.297289] brcmsmac bcma0:0: ops->tx called while down
[  161.354230] brcmsmac bcma0:0: ops->tx called while down
[  161.409178] brcmsmac bcma0:0: ops->tx called while down
[  161.465116] brcmsmac bcma0:0: ops->tx called while down
[  161.521060] brcmsmac bcma0:0: ops->tx called while down
[  161.577010] brcmsmac bcma0:0: ops->tx called while down
[  213.968693] brcmsmac bcma0:0: ops->tx called while down
[  214.024636] brcmsmac bcma0:0: ops->tx called while down
[  214.080562] brcmsmac bcma0:0: ops->tx called while down
[  214.136500] brcmsmac bcma0:0: ops->tx called while down
[  214.192459] brcmsmac bcma0:0: ops->tx called while down
[  214.248418] brcmsmac bcma0:0: ops->tx called while down
[  214.304370] brcmsmac bcma0:0: ops->tx called while down
[  214.360311] brcmsmac bcma0:0: ops->tx called while down
[  214.416272] brcmsmac bcma0:0: ops->tx called while down
[  214.472198] brcmsmac bcma0:0: ops->tx called while down
[  214.528163] brcmsmac bcma0:0: ops->tx called while down
[  276.906608] brcmsmac bcma0:0: ops->tx called while down
[  276.962513] brcmsmac bcma0:0: ops->tx called while down
[  277.018498] brcmsmac bcma0:0: ops->tx called while down
[  277.074413] brcmsmac bcma0:0: ops->tx called while down
[  277.130403] brcmsmac bcma0:0: ops->tx called while down
[  277.186343] brcmsmac bcma0:0: ops->tx called while down
[  277.242293] brcmsmac bcma0:0: ops->tx called while down
[  277.298241] brcmsmac bcma0:0: ops->tx called while down
[  277.354170] brcmsmac bcma0:0: ops->tx called while down
[  277.410134] brcmsmac bcma0:0: ops->tx called while down
[  277.466076] brcmsmac bcma0:0: ops->tx called while down
[  339.852452] brcmsmac bcma0:0: ops->tx called while down
[  339.908428] brcmsmac bcma0:0: ops->tx called while down
[  339.964363] brcmsmac bcma0:0: ops->tx called while down
[  340.020314] brcmsmac bcma0:0: ops->tx called while down
[  340.076273] brcmsmac bcma0:0: ops->tx called while down
[  340.132261] brcmsmac bcma0:0: ops->tx called while down
[  340.188212] brcmsmac bcma0:0: ops->tx called while down
[  340.244125] brcmsmac bcma0:0: ops->tx called while down
[  340.300057] brcmsmac bcma0:0: ops->tx called while down
[  340.359984] brcmsmac bcma0:0: ops->tx called while down
[  340.415945] brcmsmac bcma0:0: ops->tx called while down
[  402.790445] brcmsmac bcma0:0: ops->tx called while down
[  402.846378] brcmsmac bcma0:0: ops->tx called while down
[  402.902326] brcmsmac bcma0:0: ops->tx called while down
[  402.958242] brcmsmac bcma0:0: ops->tx called while down
[  403.014200] brcmsmac bcma0:0: ops->tx called while down
[  403.070176] brcmsmac bcma0:0: ops->tx called while down
[  403.126119] brcmsmac bcma0:0: ops->tx called while down
[  403.182063] brcmsmac bcma0:0: ops->tx called while down
[  403.238012] brcmsmac bcma0:0: ops->tx called while down
[  403.293965] brcmsmac bcma0:0: ops->tx called while down
[  403.349878] brcmsmac bcma0:0: ops->tx called while down
[  465.732352] brcmsmac bcma0:0: ops->tx called while down
[  465.788308] brcmsmac bcma0:0: ops->tx called while down
[  465.844247] brcmsmac bcma0:0: ops->tx called while down
[  465.900185] brcmsmac bcma0:0: ops->tx called while down
[  465.956151] brcmsmac bcma0:0: ops->tx called while down
[  466.012084] brcmsmac bcma0:0: ops->tx called while down
[  466.068050] brcmsmac bcma0:0: ops->tx called while down
[  466.123960] brcmsmac bcma0:0: ops->tx called while down
[  466.179919] brcmsmac bcma0:0: ops->tx called while down
[  466.235887] brcmsmac bcma0:0: ops->tx called while down
[  466.291814] brcmsmac bcma0:0: ops->tx called while down
[  528.674247] brcmsmac bcma0:0: ops->tx called while down
[  528.730181] brcmsmac bcma0:0: ops->tx called while down
[  528.786128] brcmsmac bcma0:0: ops->tx called while down
[  528.842064] brcmsmac bcma0:0: ops->tx called while down
[  528.898041] brcmsmac bcma0:0: ops->tx called while down
[  528.953978] brcmsmac bcma0:0: ops->tx called while down
[  529.009938] brcmsmac bcma0:0: ops->tx called while down
[  529.065917] brcmsmac bcma0:0: ops->tx called while down
[  529.121840] brcmsmac bcma0:0: ops->tx called while down
[  529.177756] brcmsmac bcma0:0: ops->tx called while down
[  529.233726] brcmsmac bcma0:0: ops->tx called while down
[  591.621761] brcmsmac bcma0:0: ops->tx called while down
[  591.677728] brcmsmac bcma0:0: ops->tx called while down
[  591.733672] brcmsmac bcma0:0: ops->tx called while down
[  591.789662] brcmsmac bcma0:0: ops->tx called while down
[  591.845643] brcmsmac bcma0:0: ops->tx called while down
[  591.901631] brcmsmac bcma0:0: ops->tx called while down
[  591.957618] brcmsmac bcma0:0: ops->tx called while down
[  592.013580] brcmsmac bcma0:0: ops->tx called while down
[  592.069562] brcmsmac bcma0:0: ops->tx called while down
[  592.125532] brcmsmac bcma0:0: ops->tx called while down
[  592.181500] brcmsmac bcma0:0: ops->tx called while down
[  654.591163] brcmsmac bcma0:0: ops->tx called while down
[  654.647104] brcmsmac bcma0:0: ops->tx called while down
[  654.703142] brcmsmac bcma0:0: ops->tx called while down
[  654.759069] brcmsmac bcma0:0: ops->tx called while down
[  654.815054] brcmsmac bcma0:0: ops->tx called while down
[  654.871028] brcmsmac bcma0:0: ops->tx called while down
[  654.926979] brcmsmac bcma0:0: ops->tx called while down
[  654.982961] brcmsmac bcma0:0: ops->tx called while down
[  655.038938] brcmsmac bcma0:0: ops->tx called while down
[  655.094937] brcmsmac bcma0:0: ops->tx called while down
[  655.150878] brcmsmac bcma0:0: ops->tx called while down
[  717.568512] brcmsmac bcma0:0: ops->tx called while down
[  717.624465] brcmsmac bcma0:0: ops->tx called while down
[  717.680443] brcmsmac bcma0:0: ops->tx called while down
[  717.736419] brcmsmac bcma0:0: ops->tx called while down
[  717.792392] brcmsmac bcma0:0: ops->tx called while down
[  717.848358] brcmsmac bcma0:0: ops->tx called while down
[  717.904335] brcmsmac bcma0:0: ops->tx called while down
[  717.960311] brcmsmac bcma0:0: ops->tx called while down
[  718.016290] brcmsmac bcma0:0: ops->tx called while down
[  718.072266] brcmsmac bcma0:0: ops->tx called while down
[  718.128271] brcmsmac bcma0:0: ops->tx called while down
[  780.537878] brcmsmac bcma0:0: ops->tx called while down
[  780.593865] brcmsmac bcma0:0: ops->tx called while down
[  780.649826] brcmsmac bcma0:0: ops->tx called while down
[  780.705857] brcmsmac bcma0:0: ops->tx called while down
[  780.761833] brcmsmac bcma0:0: ops->tx called while down
[  780.817790] brcmsmac bcma0:0: ops->tx called while down
[  780.873755] brcmsmac bcma0:0: ops->tx called while down
[  780.929725] brcmsmac bcma0:0: ops->tx called while down
[  780.985738] brcmsmac bcma0:0: ops->tx called while down
[  781.041684] brcmsmac bcma0:0: ops->tx called while down
[  781.097668] brcmsmac bcma0:0: ops->tx called while down
[  843.515307] brcmsmac bcma0:0: ops->tx called while down
[  843.571274] brcmsmac bcma0:0: ops->tx called while down
[  843.627215] brcmsmac bcma0:0: ops->tx called while down
[  843.683239] brcmsmac bcma0:0: ops->tx called while down
[  843.739195] brcmsmac bcma0:0: ops->tx called while down
[  843.795194] brcmsmac bcma0:0: ops->tx called while down
[  843.851119] brcmsmac bcma0:0: ops->tx called while down
[  843.907115] brcmsmac bcma0:0: ops->tx called while down
[  843.963101] brcmsmac bcma0:0: ops->tx called while down
[  844.019040] brcmsmac bcma0:0: ops->tx called while down
[  844.075085] brcmsmac bcma0:0: ops->tx called while down
[  906.484688] brcmsmac bcma0:0: ops->tx called while down
[  906.540674] brcmsmac bcma0:0: ops->tx called while down
[  906.596629] brcmsmac bcma0:0: ops->tx called while down
[  906.652601] brcmsmac bcma0:0: ops->tx called while down
[  906.708563] brcmsmac bcma0:0: ops->tx called while down
[  906.764558] brcmsmac bcma0:0: ops->tx called while down
[  906.820551] brcmsmac bcma0:0: ops->tx called while down
[  906.876513] brcmsmac bcma0:0: ops->tx called while down
[  906.932510] brcmsmac bcma0:0: ops->tx called while down
[  906.988467] brcmsmac bcma0:0: ops->tx called while down
[  907.044471] brcmsmac bcma0:0: ops->tx called while down
[  969.462057] brcmsmac bcma0:0: ops->tx called while down
[  969.518125] brcmsmac bcma0:0: ops->tx called while down
[  969.574043] brcmsmac bcma0:0: ops->tx called while down
[  969.630033] brcmsmac bcma0:0: ops->tx called while down
[  969.685953] brcmsmac bcma0:0: ops->tx called while down
[  969.742242] brcmsmac bcma0:0: ops->tx called while down
[  969.797949] brcmsmac bcma0:0: ops->tx called while down
[  969.853907] brcmsmac bcma0:0: ops->tx called while down
[  969.909883] brcmsmac bcma0:0: ops->tx called while down
[  969.965858] brcmsmac bcma0:0: ops->tx called while down
[  970.021834] brcmsmac bcma0:0: ops->tx called while down
[ 1032.431434] brcmsmac bcma0:0: ops->tx called while down
[ 1032.487413] brcmsmac bcma0:0: ops->tx called while down
[ 1032.543449] brcmsmac bcma0:0: ops->tx called while down
[ 1032.599389] brcmsmac bcma0:0: ops->tx called while down
[ 1032.655343] brcmsmac bcma0:0: ops->tx called while down
[ 1032.711365] brcmsmac bcma0:0: ops->tx called while down
[ 1032.767318] brcmsmac bcma0:0: ops->tx called while down
[ 1032.823309] brcmsmac bcma0:0: ops->tx called while down
[ 1032.879302] brcmsmac bcma0:0: ops->tx called while down
[ 1032.935277] brcmsmac bcma0:0: ops->tx called while down
[ 1032.991206] brcmsmac bcma0:0: ops->tx called while down
[ 1095.408830] brcmsmac bcma0:0: ops->tx called while down
[ 1095.464839] brcmsmac bcma0:0: ops->tx called while down
[ 1095.520801] brcmsmac bcma0:0: ops->tx called while down
[ 1095.576809] brcmsmac bcma0:0: ops->tx called while down
[ 1095.632736] brcmsmac bcma0:0: ops->tx called while down
[ 1095.688763] brcmsmac bcma0:0: ops->tx called while down
[ 1095.744751] brcmsmac bcma0:0: ops->tx called while down
[ 1095.800723] brcmsmac bcma0:0: ops->tx called while down
[ 1095.856672] brcmsmac bcma0:0: ops->tx called while down
[ 1095.912665] brcmsmac bcma0:0: ops->tx called while down
[ 1095.968642] brcmsmac bcma0:0: ops->tx called while down
[ 1108.643276] brcmsmac bcma0:0: ops->tx called while down
[ 1108.699269] brcmsmac bcma0:0: ops->tx called while down
[ 1108.755205] brcmsmac bcma0:0: ops->tx called while down
[ 1108.811211] brcmsmac bcma0:0: ops->tx called while down
[ 1108.867186] brcmsmac bcma0:0: ops->tx called while down
[ 1108.923162] brcmsmac bcma0:0: ops->tx called while down
[ 1108.979148] brcmsmac bcma0:0: ops->tx called while down
[ 1109.035108] brcmsmac bcma0:0: ops->tx called while down
[ 1109.091084] brcmsmac bcma0:0: ops->tx called while down
[ 1109.147077] brcmsmac bcma0:0: ops->tx called while down
[ 1109.203048] brcmsmac bcma0:0: ops->tx called while down
[ 1158.378229] brcmsmac bcma0:0: ops->tx called while down
[ 1158.434243] brcmsmac bcma0:0: ops->tx called while down
[ 1158.490201] brcmsmac bcma0:0: ops->tx called while down
[ 1158.546163] brcmsmac bcma0:0: ops->tx called while down
[ 1158.602189] brcmsmac bcma0:0: ops->tx called while down
[ 1158.658151] brcmsmac bcma0:0: ops->tx called while down
[ 1158.714137] brcmsmac bcma0:0: ops->tx called while down
[ 1158.770104] brcmsmac bcma0:0: ops->tx called while down
[ 1158.826079] brcmsmac bcma0:0: ops->tx called while down
[ 1158.882026] brcmsmac bcma0:0: ops->tx called while down
[ 1158.937998] brcmsmac bcma0:0: ops->tx called while down
[ 1181.684408] brcmsmac bcma0:0: ops->tx called while down
[ 1181.740403] brcmsmac bcma0:0: ops->tx called while down
[ 1181.796374] brcmsmac bcma0:0: ops->tx called while down
[ 1181.852351] brcmsmac bcma0:0: ops->tx called while down
[ 1181.908325] brcmsmac bcma0:0: ops->tx called while down
[ 1181.964304] brcmsmac bcma0:0: ops->tx called while down
[ 1182.020280] brcmsmac bcma0:0: ops->tx called while down
[ 1182.076252] brcmsmac bcma0:0: ops->tx called while down
[ 1182.132203] brcmsmac bcma0:0: ops->tx called while down
[ 1182.188211] brcmsmac bcma0:0: ops->tx called while down
[ 1182.244164] brcmsmac bcma0:0: ops->tx called while down


########## wireless info END ############

```

---

### Post by chili555 on 2014-03-31
Alright then; here we go. Ideally with a working wired ethernet connection, download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz) Right-click it and select 'Extract Here.' Open a terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.13.2-1
make defconfig-brcmsmac
make
sudo make install
sudo modprobe -r brcmsmac
sudo modprobe brcmsmac
```You may get a warning about signing that you may safely ignore. It may take a reboot. 

Any improvement?

---

### Post by mark.soames on 2014-03-31
This looks promising!  The wireless connected at the login screen, and didn't disconnect after I'd logged in.  I'll leave it running and post back here if it disconnects.

Thank you!

---

### Post by mark.soames on 2014-03-31
It's now disconnected, which looks like it was up and running for about 5 minutes.  If you had any more input I'd be very grateful.  Thanks for all your help so far.

---

### Post by chili555 on 2014-03-31
Thank you for being our test pilot! We strive to find a workable solution for every device and, so far, I think we only know what _doesn't_ work! Let's try a completely new approach. Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Change the blacklist wl line to instead blacklist brcmsmac. Proofread, save and close gedit.

Now do:```
sudo apt-get install bcmwl-kernel-source
```When it finishes, immediately reboot, cross your fingers and hope! 

We are quickly running low on ideas/mojo/talent.

---

### Post by monkeybrain20122 on 2014-03-31
I have the same card and actually  brcmsmac works really well. I have purged bcmwl-kernel-source and removed the blacklist file it generates.bcmwl-kernel-source blacklists brmsmac and activates/installs wl which is garbage.
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
```
```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f5500000-f5503fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 10
       serial: 78:2b:cb:ce:1d:92
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5761e-v3.73 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2d10000-f2d1ffff memory:f2d00000-f2d0ffff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 68:a3:c4:2f:07:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.13.0-17-generic firmware=610.812 ip=192.168.2.18 link=yes multicast=yes wireless=IEEE 802.11bgn

```

---

### Post by chili555 on 2014-03-31
> I have the same card and actually brcmsmac works really well.If you have read this entire thread, you'll see that we've tried everything and every version of brcmsmac and, in this case, for some reason, it *doesn't* work really well. We do, however, appreciate your help. It is always helpful to hear from someone who owns one.

---

### Post by mark.soames on 2014-04-02
Sorry for the silence; I've been really busy recently.  Your help has been amazing.

The good news is that this seems to be working a bit better - it lasts about 20 minutes before shutting down.  There's a lot of stuff in the blacklist file and something was interfering with it, so it's all hashed out at the moment apart from one entry, but something is clearly interfering still; perhaps you have a suggestion as to what it could be?

```

blacklist bcm43xx
# blacklist b43
# blacklist b43legacy
# blacklist bcma
# blacklist ndiswrapper
# blacklist brcm80211
# blacklist brcmsmac

```

Thanks again for your help, and Varun's.  I wouldn't have been able to make any progress at all otherwise.

---

### Post by varunendra on 2014-04-03
With Dr. Chili being on thread, you don't need me anyway, but I think it would be interesting to see a fresh 'wireless_script' report of your current setup.

---

