---
title: "Still having problems with Marvell Topdog cards."
date: 2014-02-11
forum: Networking &amp; Wireless
---

### Post by jamesbeckjr on 2014-02-11
I have tried several tutorials with no success. Some have broken links, some their files don't work, others I get errors while performing.

I am running Win7 Home Premium with a dual boot of Ubuntu 12.04 on a Gateway M-6750. Ethernet works great, wireless works on the Windows side. I know that the vista driver WILL NOT work on ubuntu. So if someone could help me by giving a link to download the xp inf and sys files, or help me get the NetMW14x driver working, that would be great. 

This is what I get with sudolshw -C network

daichiandkaname@daichiandkaname-M-6750:~$ sudo lshw -C network
[sudo] password for daichiandkaname: 
  *-network               
       description: Ethernet controller
       product: 88W8362e [TopDog] 802.11a/b/g/n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ndiswrapper latency=0
       resources: irq:11 memory:f6000000-f600ffff memory:f4000000-f400ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e6:9d:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.187 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:4000(size=256) memory:fa200000-fa200fff memory:c0000000-c001ffff


This is what I get when I try to install the netmw14x.inf

daichiandkaname@daichiandkaname-M-6750:~/Desktop/ugh$ sudo ndiswrapper -i netmw14x.inf
installing netmw14x ...
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
daichiandkaname@daichiandkaname-M-6750:~/Desktop/ugh$

---

### Post by chili555 on 2014-02-11
Let's start by identifying the card more exactly:```
lspci -nn | grep 0280
```

---

### Post by jamesbeckjr on 2014-02-11
daichiandkaname@daichiandkaname-M-6750:~/Desktop/ugh$ lspci -nn 
|00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless [11ab:2a08] (rev 03)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

---

### Post by chili555 on 2014-02-11
Did you try the file at this site? [http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu](http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu) The zip contains the .inf and .sys files and covers your device.

[http://www.kevinschicken.com/downloads/NetMW14x.zip](http://www.kevinschicken.com/downloads/NetMW14x.zip)

---

### Post by jamesbeckjr on 2014-02-11
Yes. When I run that I get this: 

daichiandkaname@daichiandkaname-M-6750:~/Desktop/ugh$ sudo ndiswrapper -i netmw14x.inf
installing netmw14x ...
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
couldn't find "NETMW146.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete

---

### Post by chili555 on 2014-02-11
It appears there is no 146 at all in the files. Let's try this, then:```
cd ~/Desktop/ugh
sudo cp netmw145.sys NETMW146.sys
sudo ndiswrapper -e netmw14x
sudo ndiswrapper -i netmw14x.inf
ndiswrapper -l
```


----------
Possible reference: [http://ubuntuforums.org/showthread.php?t=575785&page=2&p=4233401#post4233401](http://ubuntuforums.org/showthread.php?t=575785&page=2&p=4233401#post4233401)

---

### Post by jamesbeckjr on 2014-02-11
I was able to successfully install the driver this time. When I restarted, ndiswrapper started on startup, but threw an can't prepare driver. Did it send it to the syslog so that I can see the errors or?

---

### Post by chili555 on 2014-02-11
> Did it send it to the syslog so that I can see the errors or? Probably. That's always the best place to start:```
cat /var/log/syslog | grep ndis | tail -n20
```syslog gets archived and a new page started from time to time, so if the result is sparse or empty, then check the just previous:```
cat /var/log/syslog**.1** | grep ndis | tail -n20
```

---

### Post by jamesbeckjr on 2014-02-11
It was there and after putting in that code, this is what I got:


daichiandkaname@daichiandkaname-M-6750:~$ cat /var/log/syslog | grep ndis | tail -n20
Feb 11 11:51:51 daichiandkaname-M-6750 kernel: [    9.909677] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
Feb 11 11:51:51 daichiandkaname-M-6750 kernel: [    9.911230] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
Feb 11 11:51:52 daichiandkaname-M-6750 loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver netmw14x
Feb 11 11:51:52 daichiandkaname-M-6750 kernel: [   11.092393] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Feb 11 11:51:52 daichiandkaname-M-6750 kernel: [   11.092449] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netmw14x'
Feb 11 11:51:52 daichiandkaname-M-6750 kernel: [   11.092561] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netmw14x'
Feb 11 11:51:52 daichiandkaname-M-6750 kernel: [   11.096207] usbcore: registered new interface driver ndiswrapper
Feb 11 11:54:03 daichiandkaname-M-6750 kernel: [  142.804088] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev snd_hda_codec_idt i915 snd_hda_intel snd_hda_codec uvcvideo drm_kms_helper videobuf2_core videodev videobuf2_vmalloc videobuf2_memops snd_hwdep snd_pcm drm joydev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd ndiswrapper(OF) soundcore i2c_algo_bit wmi snd_page_alloc lpc_ich serio_raw mac_hid video lp parport binfmt_misc ums_realtek usb_storage ahci libahci r8169 mii
Feb 11 11:54:03 daichiandkaname-M-6750 kernel: [  142.804395] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev snd_hda_codec_idt i915 snd_hda_intel snd_hda_codec uvcvideo drm_kms_helper videobuf2_core videodev videobuf2_vmalloc videobuf2_memops snd_hwdep snd_pcm drm joydev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse snd ndiswrapper(OF) soundcore i2c_algo_bit wmi snd_page_alloc lpc_ich serio_raw mac_hid video lp parport binfmt_misc ums_realtek usb_storage ahci libahci r8169 mii

---

### Post by chili555 on 2014-02-11
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BThat's the whole answer! >  wireless works on the Windows side. If you look around on the Windows side, can you find files for XP and 64-bit, or shall I put on my camo and get out my binoculars and go hunting again?


----------------

Possible bummer: [http://ubuntuforums.org/showthread.php?t=1134279&p=10443346#post10443346](http://ubuntuforums.org/showthread.php?t=1134279&p=10443346#post10443346)

---

### Post by jamesbeckjr on 2014-02-11
I have no idea where the xp files would be. I know the drivers are stored under windows/system32/driverstore, but i have no idea where it would be under there.

---

### Post by jamesbeckjr on 2014-02-11
I did a little searching myself, and found this: [http://www.driverscape.com/download/marvell-topdog-%28tm%29-pci-express-802.11n-wireless-%28ec85%29](http://www.driverscape.com/download/marvell-topdog-%28tm%29-pci-express-802.11n-wireless-%28ec85%29)

The first is an exe, I didn't bother with it.
The second installed just fine, but when I looked at it, it said invalid driver.
The third threw back this:

daichiandkaname@daichiandkaname-M-6750:~/Desktop/XP32bit$ sudo ndiswrapper -i netmw147.inf
installing netmw147 ...
couldn't find models section "Marvell" -
installation may be incomplete
daichiandkaname@daichiandkaname-M-6750:~/Desktop/XP32bit$ 


I still got nothing.

---

### Post by chili555 on 2014-02-11
> **jamesbeckjr said:**
> I have no idea where the xp files would be. I know the drivers are stored under windows/system32/driverstore, but i have no idea where it would be under there.I suggest you search for netmw14x.inf. Be sure to include system files and see if anything looks like a possibility.> /Desktop/XP32bitWhy are you trying the XP32bit files? I thought you had a 64-bit system:> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B If you get the same error, we can give it a Marvell section.

---

### Post by jamesbeckjr on 2014-02-11
I thought that error meant that the part doesn't support 64-bit drivers.

> **chili555 said:**
> If you get the same error, we can give it a Marvell section.

What do you mean by this?

I did a search of my C: partition through Ubuntu, and nothing popped up relating to NetMW14.

---

### Post by chili555 on 2014-02-11
> **jamesbeckjr said:**
> I thought that error meant that the part doesn't support 64-bit drivers.I'm pretty sure it means you have a 64-bit system and tried to install a 32-bit driver file. What does this tell us?```
arch
```

---

### Post by jamesbeckjr on 2014-02-11
daichiandkaname@daichiandkaname-M-6750:~$ arch
x86_64

---

### Post by chili555 on 2014-02-11
> **jamesbeckjr said:**
> daichiandkaname@daichiandkaname-M-6750:~$ arch
[COLOR="#FF0000"]x86_64[/COLOR]So you have a 64-bit system and 32-bit files will not work.> daichiandkaname@daichiandkaname-M-6750:~/Desktop/[COLOR="#FF0000"]XP32bit[/COLOR]Do you have an XP64bit folder? Can you please try those files instead?

---

### Post by jamesbeckjr on 2014-02-11
It did come with a 64 bit driver and it installed with no errors. I restarted and Ndiswrapper didn't throw any errors. But..... Now have no networking, atty all. Not even ethernet. Ndiswrapper/ndstk won't load. I tried running a few commands and the terminal freezes without completing the process. 
Syslog didn't show any errors besides it couldn't accolate some memory.

---

### Post by jamesbeckjr on 2014-02-12
I uninstalled ndiswrapper and now my ethernet works again. I am really confused and close to being fed up with this. Do you have any more ideas or are we sticking a fork in it?

---

### Post by chili555 on 2014-02-12
> **jamesbeckjr said:**
> I uninstalled ndiswrapper and now my ethernet works again. I am really confused and close to being fed up with this. Do you have any more ideas or are we sticking a fork in it?ndiswrapper is always tricky and a gamble with 64-bit. I am not too surprised that it didn't work, but we've got to try!

I hate to solve problems by throwing money at it, but I'd research on this forum and buy a supported out of the box USB wireless. Sorry I couldn't be of further help.

---

### Post by jamesbeckjr on 2014-02-12
Alright. And if this CPU wasn't 64 bit, I would not have been able to install 64 bit Ubuntu, correct? I only ask because this computer was given to me, and I had no prior knowledge of it's components.

---

### Post by chili555 on 2014-02-12
> And if this CPU wasn't 64 bit, I would not have been able to install 64 bit Ubuntu, correct?Exactly. You could, however, install 32-bit: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)  There is, however, no guarantee of success. You could go to the trouble of doing so only to find that the not well supported TopDog and its no longer maintained XP inf and sys files just won't work. As we say here in the US south, you pays your money and you takes your chances.

I will be happy to help in any event.

---

### Post by jamesbeckjr on 2014-02-12
That's a good line. I guess I will just remained tethered to the router, and get a different computer for Windows. Thank god it's Tax time!

---

