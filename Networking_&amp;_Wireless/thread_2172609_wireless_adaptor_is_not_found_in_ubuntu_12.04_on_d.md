---
title: "wireless adaptor is not found in ubuntu 12.04 on dell xps 13"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by pQNmyG4 on 2013-09-05
Dear Ubuntu community,

I have recently installed Ubuntu 12.04 lts on dell xpl 13 laptop. at the beginning ubuntu could found wireless adaptor and wireless worked but only for the first couple of hours from switching the laptop. then the wireless connection dropped and the only way to get it back was to restart the laptop. Then I found a similar problem on the forum ([http://ubuntuforums.org/showthread.php?t=2012228](http://ubuntuforums.org/showthread.php?t=2012228)) and followed therein instruction. Namely I have carried out the following code:

```
gksudo gedit /etc/pm/power.d/wireless
```

this has created a text file wireless
in which I have put the following:

```
/sbin/iwconfig wlan0 power off
exit 0

```

then I saved it. and next I have run the following commands:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

and restarted my laptop.
But afterwards the wireless has completely disappeared from ubuntu. I mean there is now wireless in the network settings, only wired connection. 

Here is what iwcongig says:

```
:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
```

And here is what lspci reports:

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
```

I would be infinitely grateful for any help and hints on what I have done with my laptop. I am a newcommer to ubuntu and need desparately a wireless connection in oder to be able to participate in tutorials at the scientific school abroad. 

Thank you very much in advance!

---

### Post by chili555 on 2013-09-05
Why did you add 'exit 0' when it was not in Wild Man's instructions? I'd remove it and reboot. If you don't have any wireless, look for clues here:```
dmesg | grep iwl
```

---

### Post by pQNmyG4 on 2013-09-05
Thanks for the respond! I've added exit 0, because Wild Man mentioned that the line
```
/sbin/iwconfig wlan0 power off
```

has to be above exit0.
I removed and rebooted, it doesn'e help.
then thried to repeat the whole procedure (according to Wild Man) one again.
And on the last stage I've got a Fatal error:

```
:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n disable=1
FATAL: Error inserting iwlwifi (/lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Invalid argument
```

I've run dmesg:

```
:~$ dmesg | grep iwl
[    1.880741] iwlwifi: `' invalid for parameter `11n'
```

Could you please say what should I use instead of 11n?

Here is additionally the output of lshw and ifconfig respectively:

```
:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d0401fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 9c:eb:e8:0d:78:f8
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=10.10.20.10 link=yes multicast=yes port=MII speed=100Mbit/s



```

```
:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 9c:eb:e8:0d:78:f8  
          inet addr:10.10.20.10  Bcast:10.10.23.255  Mask:255.255.252.0
          inet6 addr: fe80::9eeb:e8ff:fe0d:78f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33584934 (33.5 MB)  TX bytes:2402734 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97560 (97.5 KB)  TX bytes:97560 (97.5 KB)
```

---

### Post by chili555 on 2013-09-05
> insmod /lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n disable=1
FATAL: Error inserting iwlwifi (/lib/modules/3.5.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Invalid argumentIt looks as if there is a typo. It is not 11n disable=1; it is, instead 11n[COLOR="#FF0000"]**_**[/COLOR]disable=1. Let's fix it:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change it to:```
options iwlwifi 11n_disable=1
```Proofread carefully twice, save and close gedit.

Reboot and let us have your report.

---

### Post by pQNmyG4 on 2013-09-06
Dear chili555, thank you! it works now. Whether the wireless connection keeps dropping I will report after monitoring its performance.

---

### Post by pQNmyG4 on 2013-09-06
Unfortunatelly, the old problem remains. At the beginning when the laptop has just been switched on wireless connection works, but after about an hour it drops and doesn't want to connect again. Only reboot helps.  How could one eliminate this problem?

---

### Post by chili555 on 2013-09-06
> **pQNmyG4 said:**
> Unfortunatelly, the old problem remains. At the beginning when the laptop has just been switched on wireless connection works, but after about an hour it drops and doesn't want to connect again. Only reboot helps.  How could one eliminate this problem?When it drops, please check the power setting:```
iwconfig
```Here is mine:> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:off[/COLOR]
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0Also see if there any clues as to the drops here:```
dmesg | grep -e wlan -e iwl -e 80211 | tail -n25
```Thanks.

---

### Post by pQNmyG4 on 2013-09-07
The power managment is off, but there is something wrong with the driver. In addition after the wireless drops the item "Wireless Networks" in the network manager menu becomes inactive. I mean it is still there, but not highlighted,so that when I click on it nothing happens. Here is the result of the above mentioned commands:
```
tony@skyfirer:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
tony@skyfirer:~$ dmesg | grep -e wlan -e iwl -e 80211 | tail -n25
[ 1227.043737] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1228.043800] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1229.044018] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1230.044454] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1231.044767] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1232.044824] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1233.044894] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1234.045070] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1235.044082] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1236.044182] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1237.044357] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1238.044412] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1239.044588] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1240.044988] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1241.045165] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1242.045563] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1243.045735] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1244.045919] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1245.045456] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1246.045829] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1247.046008] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1248.046363] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1249.046648] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1250.046859] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1251.046917] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
```

---

### Post by chili555 on 2013-09-07
> [ 1227.043737] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1228.043800] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1229.044018] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 1230.044454] iwlwifi 0000:01:00.0: Request scan called when driver not ready.We need to see the sequence of events leading up to this. By this time, the driver is already dormant. Let's see:```
dmesg | grep -e wlan -e iwl -e 80211
```...In other words, *all* the lines, not just the last 25. As this is likely to be quite lengthy, please paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Do you have an earlier kernel version on you system? Can you interrupt the boot process to get the GRUB menu and try an earlier kernel? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You might also try reinstalling the firmware:```
sudo apt-get install --reinstall linux-firmware
```

---

### Post by pQNmyG4 on 2013-09-07
I have reinstalled the firmware, at first the general performance of ubuntu has improved. Some ubuntu features has started to work (for example the print screen key). The wireless has held on longer (around 5 hours) but then again dropped and didn't want to re-connect (just as before). I have another laptop with windows, where wifi has worked normaly, so this is not a wifi network breakdown. The linux kernel version is 3.5.0-37-generic. I have changed it to 3.5.0-23-generic (via Grub2 booting menu). Unformunately this has not helped. [Here]("http://paste.ubuntu.com/6076942/") is what dmesg says. If this is not a problem with firmware nor kernel, then should be probably the driver issue?

---

### Post by chili555 on 2013-09-08
>  If this is not a problem with firmware nor kernel, then should be probably the driver issue? ...or a hardware issue??

You have one unhappy device there:> [16662.744340] iwlwifi 0000:01:00.0: fail to flush all tx fifo queues
[16664.745682] iwlwifi 0000:01:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[16664.745695] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 127 write_ptr 128
[16664.745708] ieee80211 phy0: failed to remove key (0, e0:91:f5:a6:5c:f1) from hardware (-110)
[16666.743168] iwlwifi 0000:01:00.0: Error sending REPLY_QOS_PARAM: time out after 2000ms.
[16666.743190] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 127 write_ptr 129
[16666.743228] iwlwifi 0000:01:00.0: Failed to update QoS
[16668.740580] iwlwifi 0000:01:00.0: Error sending REPLY_RXON: time out after 2000ms.
[16668.740594] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 127 write_ptr 130
[16668.740603] iwlwifi 0000:01:00.0: Error clearing ASSOC_MSK on BSS (-110)
[16670.737948] iwlwifi 0000:01:00.0: Queue 0 stuck for 10000 ms.
[16670.737960] iwlwifi 0000:01:00.0: Current SW read_ptr 78 write_ptr 79
[16670.741953] iwlwifi 0000:01:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[16670.741969] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 127 write_ptr 131
[16670.741988] ieee80211 phy0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-110)
[16670.756815] WARNING: at /build/buildd/linux-lts-quantal-3.5.0/drivers/net/wireless/iwlwifi/iwl-io.c:127 iwl_grab_nic_access.part.0+0x6f/0x8e [iwlwifi]()
[16670.756825] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek joydev coretemp kvm_intel arc4 kvm snd_hda_intel ghash_clmulni_intel cryptd snd_hd...and on and on. I see one thing we might address here:> Queue 0 stuck for 10000 ms.Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the file to add a new parameter:```
options iwlwifi 11n_disable=1 wd_disable=1
```Proofread carefully twice, save and close gedit. Unload and reload the driver:```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```Any improvement?

If not, we can build a newer driver but I am skeptical because i own and use Intel wireless devices on two laptops every day; both are perfect. My strong suspicion is that it's a hardware issue.

---

### Post by pQNmyG4 on 2013-09-09
I've tried it. Does not work :(. could you please say what ieee80211 is? from what I've read on the web I understood that this is a firmware of the wireless device. If this a problem with hardware then it is strange, because previously I had windows on this laptop and it worked.

---

### Post by chili555 on 2013-09-09
> could you please say what ieee80211 is? Please see: [http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11) 

In the message logs, it refers to: [http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)> A generic ieee80211 networking stack for the Linux kernel. In other words, the mechanism by which Linux implements the wireless protocol. The firmware for your wireless device is called up by the driver. Here is it's specification:```
chili@Think410:~$ modinfo iwlwifi
filename:       /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-6.ucode
firmware:       iwlwifi-7260-6.ucode
<snip>
```The firmware is included in the package linux-firmware which is included in Ubuntu by default and which we, as a troubleshooting step, reinstalled. 

The particular firmware file that the hardware requires is pulled up automatically. In your case, you have:> product: Centrino Advanced-N 6235According to this page: [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm) your 6235 device needs iwlwifi-6000g2b-6.ucode. The version listed is 18.168.6.1 and that is what we see loading in dmesg:> [    2.023173] iwlwifi 0000:01:00.0: loaded firmware version [COLOR="#FF0000"]18.168.6.1[/COLOR]Would you like to try building a more recent driver? I will be very happy to help. May I assume you can get a temporary wired ethernet connection?

---

### Post by pQNmyG4 on 2013-09-09
Dear Chili, yes I would love to try to build a newer driver. And yes I have the wired connection. There is one thing I am confused about. Namely, here [ATTACH]246136[/ATTACH] is the result of "modinfo iwlwifi" on my system. There is no mentioning of 18.168.6.1 version, but as you said accoding to dmesg linux still loads this version, I do not understand this.

---

### Post by pQNmyG4 on 2013-09-09
oops, it was wrong file (but also with some info on my wireless). here is the right file: [http://paste.ubuntu.com/6085149/](http://paste.ubuntu.com/6085149/)

---

### Post by pQNmyG4 on 2013-09-09
P.S.: the file [wireless-info.txt]("http://ubuntuforums.org/attachment.php?attachmentid=246136&d=1378759678") was created before we have  reinstalled the firmware. so the information in it is obsolete. just in  case here is the newer version: [ATTACH]246138[/ATTACH]

---

### Post by pQNmyG4 on 2013-09-09
Maybe we can try to tell  linux kernel (set manually) which driver version it should load?

---

### Post by chili555 on 2013-09-09
It is loading the correct version. Opposite your 6235 device on the Intel page I linked, it calls for kernels 3.2+ the file iwlwifi-6000g2b-ucode-18.168.6.1.tgz. You have kernel version 3.5.0-xx; clearly higher than 3.2. If you download and extract the file on Intel's site, it contains a README and license file and iwlwifi-6000g2b-6.ucode. It is called up by the kernel with its version number, 18.168.6.1 and not its file name. There is no confusion in that regard.

Let's get building. Please obtain a temporary wired ethernet connection. Download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2)  Right-click it and select 'Extract Here.' Now open a terminal and do:```
cd Desktop/backports-3.11-rc3-1
make defconfig-iwlwifi
make
sudo make install
```You might get one warning during make. If you get several or an error, stop and post them for our inspection.

Reboot and let us have your report. Please let us see:```
dmesg
```Paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by pQNmyG4 on 2013-09-10
Done! it looks like the kernel loads again the same version:
```
[    2.003022] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
```
Here is the full dmesg output: [http://paste.ubuntu.com/6087050/](http://paste.ubuntu.com/6087050/)
In the end of the day I will report on how wireless performs.
Thank you for the guidance!

---

### Post by pQNmyG4 on 2013-09-10
P.S.: there were no warnings nor errors during the make.

---

### Post by chili555 on 2013-09-10
> **pQNmyG4 said:**
> Done! it looks like the kernel loads again the same version:
```
[    2.003022] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
```
Here is the full dmesg output: [http://paste.ubuntu.com/6087050/](http://paste.ubuntu.com/6087050/)
In the end of the day I will report on how wireless performs.
Thank you for the guidance!Looks mighty clean! I suspect your troubles are over.

When a newer kernel is installed by Update Manager, you will need to recompile for the new kernel once you reboot:```
cd Desktop/backports-3.11-rc3-1
make clean
make defconfig-iwlwifi
make
sudo make install
```Please retain these instructions and the file for that time.

---

### Post by pQNmyG4 on 2013-09-11
Unfortunately the wireless still drops. Here is what dmesg reports just after the breakdown: [http://paste.ubuntu.com/6093969/](http://paste.ubuntu.com/6093969/)
I have such a filling that now the wireless connection goes down even faster (after starting ubuntu) then with the old driver.

---

### Post by chili555 on 2013-09-11
>  3355.263315] iwlwifi 0000:01:00.0: Q 19 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
[ 3357.257118] iwlwifi 0000:01:00.0: Error sending POWER_TABLE_CMD: time out after 2000ms.
[ 3357.257132] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 152 write_ptr 157
[ 3357.257141] iwlwifi 0000:01:00.0: set power fail, ret = -110
[ 3359.254479] iwlwifi 0000:01:00.0: Error sending REPLY_RXON: time out after 2000ms.
[ 3359.254485] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 152 write_ptr 158
[ 3359.254488] iwlwifi 0000:01:00.0: Error clearing ASSOC_MSK on BSS (-110)
[ 3361.251973] iwlwifi 0000:01:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[ 3361.251987] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 152 write_ptr 159
[ 3361.251999] wlan0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-110)
[ 3363.249422] iwlwifi 0000:01:00.0: Error sending REPLY_ADD_STA: time out after 2000ms.
[ 3363.249447] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 152 write_ptr 160
[ 3363.249461] wlan0: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-110)> [ 3449.485076] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[ 3451.422716] iwlwifi 0000:01:00.0: Unable to initialize device.
[ 3451.423523] [sched_delayed] sched: RT throttling activated
[ 3452.422948] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3453.423183] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3454.422611] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3455.422576] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3456.422597] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3457.422643] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3458.422744] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3459.422995] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3460.423284] iwlwifi 0000:01:00.0: Request scan called when driver not ready.
[ 3461.422677] iwlwifi 0000:01:00.0: Request scan called when driver not ready.Looks mighty ugly, doesn't it? I still suspect a hardware issue. Have you had any heat issues? Does it seem to work OK when the computer is cold and fail when it's nicely warmed up (read: HOT!)? Do the fans seem to run and not run as expected?

---

### Post by pQNmyG4 on 2013-09-11
The laptop works pretty soundlessly. Sometimes I hear that the cooler starts to rotate faster than usual but this is rather rare.
This the temperature of the laptop accoding to lm-sensors:
```
:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +106.0°C)
temp2:        +49.0°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +48.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +52.0°C  (high = +87.0°C, crit = +105.0°C)
```

---

### Post by pQNmyG4 on 2013-09-11
strangly, the output doesn't yield any info on fans.

---

### Post by pQNmyG4 on 2013-09-11
P.S.; the dmesg output looks ugly. So many errors. It seems with the old driver we have gotten lesser amount of error. And looks to me that with the new driver wireless drops faster. Maby it would make sence to reinstall the previous driver?

---

### Post by chili555 on 2013-09-12
Your temperatures are a bit warmer that I see, but not alarmingly so; certainly not high enough to suspect that your wireless card was fried. Just for comparison, here are mine:```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  (crit = +86.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3573 RPM
temp1:        +48.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +45.0°C  (high = +80.0°C, crit = +90.0°C)
Core 2:       +41.0°C  (high = +80.0°C, crit = +90.0°C)
```> Maby it would make sence to reinstall the previous driver? Maybe not. What was happening at post #1? >  the wireless has completely disappeared from ubuntu.Is that what you want to take affirmative steps to go back to? It's easy enough if you really think it's worthwhile to go from 'it doesn't work with the new driver' to 'it doesn't work with the *old* driver.'```
cd Desktop/backports-3.11-rc3-1
sudo make uninstall
```Reboot and there you are.

I still think it's a hardware issue.

---

