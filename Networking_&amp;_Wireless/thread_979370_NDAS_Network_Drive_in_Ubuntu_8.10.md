---
title: "NDAS Network Drive in Ubuntu 8.10"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by leopavel on 2008-11-11
Hello Ubuntu lovers,

I am kind a new in this forum as well as in Ubuntu. Ubuntu outperforms for sure. But I am just wondering of using my Ximeta NDAS drive in Ubuntu 8.10. In their site, they have drivers for Ubuntu 5.10 and 6.06 <http://code.ximeta.com/trac-ndas/wiki/Ubuntu> and kernels are different (smp/up etc!!). Can I use any of these for the latest Ubuntu 8.10? Any idea or suggestion will be greatly appreciated!!

Thanks

Leo

---

### Post by leopavel on 2008-11-13
Any suggestion from NDAS users ??

---

### Post by sonic167 on 2008-11-16
I HAD been using a wireless NDAS drive myself, which has been working fine with Ubuntu (following the instructions from [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)) until .... I upgraded to 8.10.

Now I can't get the driver to install. Bummer.

Looking forward to any ideas on how to get this to work, or I'll have to go back to being wired...

Thanks,

Vince.

---

### Post by prasanna1975 on 2008-11-18
I have the same issue not able connect my Medigate Mediaplayer to Ubuntu 8.10, have any idea how to get it working under Virtual Box atleast or can the NDAS program of Windoes be run in WINE

---

### Post by poszest16 on 2009-01-15
Follow this page it worked
[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB]("http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB")

I am using Ubuntu 8.10.
All you need to do after guide is run
"ndasadmin register XXXXX-XXXXX-XXXXX-XXXXX-WWWWW -n NetDisk1"
to register your ndas!!!

Should return
```
'NetDisk1' is registered successfully.
Please find the slot # by

cat /proc/ndas/devices/NetDisk1/slots

Then execute the following command to enable the slot

For read-only mode
ndasadmin enable -s <slot#> -o r

For exclusive-write mode
ndasadmin enable -s <slot#> -o w

For GFS mode
ndasadmin enable -s <slot#> -o s
```

Then Type: cat /proc/ndas/devices/NetDisk1/slots

Mine returned: 1

Then Type: ndasadmin enable -s 1 -o [r, w or s]

Then I will let you take it from there.

---

### Post by M-athia-s on 2009-01-21
Hi,

I followed this ticket on ximetas page:
[http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)
which for me seemed simpler then the other one listed in this thread.

I have successfully set up the ndas driver and all seems fine and well.
I can do either of register and unregister my NDAS device that I have pluged in to my netgear wireless router(at least thats what the ndasadmin tools says..). I can find the NDAS device in the routers admin interface(so i know that the router is aware of the ndas device; the decvice MAC address is listed). However I am unable to retrive any slot for my newly registered ndas device hence I am unable to connect to it. Has anyone stumble across the same problem with their wireless router? I have also put the options ndas-core ndas_dev=wlan0 to /etc/modprobe.d/options to identify my interface for wireless network.

When I do a cat /proc/ndas/devs
It lists my ndas device as following:

```
Name      	ID                     Key Serial           Ver Status         Slots
NetDisk1  	********************   Yes ********         N/A Offline   
```     
       
* = blanked out by me.

I'am running kernel 2.6.27-9-generic of ubuntu 8.10 on a i686 Intel dual core laptop.

Any helping suggestion on where to go from here is highly appreciated!

BR
Mathias

---

### Post by M-athia-s on 2009-01-21
Bump.

---

### Post by sonic167 on 2009-01-30
> **M-athia-s said:**
> Hi,

I followed this ticket on ximetas page:
[http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)

Yes, there is now a patch at that location for Linux2.6.27.
The driver work fine with this patch.

Thanks for that patch.

Vince.

---

### Post by Frijolie on 2009-02-03
So, after all of this hard work...what's the verdict? Has an l33t h4x0r gotten this to work with Intrepid and the 2.6.27.x kernel?

I'm in the market for an external USB HDD enclosure and thought that I'd also look for one with some network connectivity as an option/feature. This was the first enclosure that I've came across and it doesn't appear to be working right now.

They should allow the option for TCP/IP. I'll take my chances behind a firewall and NAT. I also won't be leaving this powered 24x7...Static IP would be great!

---

### Post by joanmunoz on 2009-02-12
Hi!

I've done everything needed to have my NDAS device running under Linux and it's fine (even it works wireless through my router, wich I did not know before!), but I can't write on it. I don't know if I've to change something related to wireless connection or what.

Please help! I can't find anything helpful nowhere.

Thx!!

Joan

PS: Solved! I've done with "sudo nautilus" and then copy & paste.

---

### Post by dir32jd on 2009-02-24
I have a slightly different problem. I am able to register and connect to my ndas devices separately (i have two of them). However, whenever I try to register and enable them both, I get an odd result. When I enter the "Blkid" command, both primary partitions of both devices get assigned the same UUID. So when I mount the two paritions, it's actually pointing to the first partition of the first device. The second device doesn't get mounted.
My workaround at the moment is I can only connect to one device at one time ... I have to deregister one device in order to connect to the other device ... really.

Other than that, the driver works great.

---

### Post by sandz on 2009-05-07
It seems [http://code.ximeta.com/trac-ndas/wiki/Ubuntu](http://code.ximeta.com/trac-ndas/wiki/Ubuntu) doesn't work anymore. Emailed support at ximeta and they replied:

Dear Customer,
code.ximeta.com is maintained now by the Linux NDAS development community. So I did not hear from them the reason for the shutdown. It may be some maintenance or something.


 From David Gates
Ximeta Technical Support

What to do now to get my device mounted??

TIA, Pieter

---

### Post by kevinbeard on 2009-05-09
> **sandz said:**
> It seems [http://code.ximeta.com/trac-ndas/wiki/Ubuntu](http://code.ximeta.com/trac-ndas/wiki/Ubuntu) doesn't work anymore. Emailed support at ximeta and they replied:

Dear Customer,
code.ximeta.com is maintained now by the Linux NDAS development community. So I did not hear from them the reason for the shutdown. It may be some maintenance or something.


 From David Gates
Ximeta Technical Support

What to do now to get my device mounted??

TIA, Pieter



I've not been able to connect to the site either, Ximeta support told me the site was being moved.

I did however download the .27 and .28 patches before it went down.

My ndas box worked with .27 but I haven't got .28 working.

---

### Post by kevinbeard on 2009-05-09
BTW, they are incremental patches so you need to apply .27 first if you want .28


patch -p1 < <patchfile.patch>

---

### Post by deankelly_68 on 2009-05-11
Stop press:
 
code.ximeta.com seems to be back up again 
 
happy, happy day :)

---

### Post by joanmunoz on 2009-05-11
> **kevinbeard said:**
> BTW, they are incremental patches so you need to apply .27 first if you want .28


patch -p1 < <patchfile.patch>

Hi! I did everything you post here but still did'nt work. I used to get my Rapsody N35 working under Ubuntu Intrepid 8.1, but since I'm with 9.04 I can't make it! It's very frustrating! Some help, please!!

Thanks!

Joan

---

### Post by kevinbeard on 2009-05-12
> **joanmunoz said:**
> Hi! I did everything you post here but still did'nt work. I used to get my Rapsody N35 working under Ubuntu Intrepid 8.1, but since I'm with 9.04 I can't make it! It's very frustrating! Some help, please!!

Thanks!

Joan

Don't worry.  I've been working on it for a few days and I can't get it to work either.

it seems there is an issue in one of the libraries that the driver uses as it's crashing down there somewhere.

I'll keep plugging away at it but hopefully someone with more kernel debugging experience will fix it first.

---

### Post by deankelly_68 on 2009-05-12
Hi chaps

I've followed the code.ximeta.org instructions twice now (once for Ubuntu 8.10 and once for 9.04) and they DO work, but you really need to read them carefully. For anyone who's started and had the installation or build fail, I'd suggest starting afresh. Firstly to be sure we're all starting at the same place, I'm referring to the instructions on the following page: [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB). Clean up previous attempts: 

1) blow away everything you've built so far. 

You should have created a structure called "ndas-1.1-24" when you ran "tar zxf ndas-1.x-x.tar.gz ". Get rid of it (rm -r). If you got as far as the "dpkg-buildpackage -rfakeroot" you should have two files (your version numbers may vary slightly): 

-rw-r--r-- 1 dean dean  22118 2009-05-12 16:33 ndasadmin_1.1-24_i386.deb
-rw-r--r-- 1 dean dean 194656 2009-05-12 16:33 ndas-modules-src_1.1-24_all.deb

Get rid of them too.

2) righty: Carefully read the installation section on the page I referenced above. The order of instructions on the page is quite poor. You will find that there's a section which is slightly indented - that's the bit you want to follow (it's about 10 lines down from the start of the Installation). Take careful note of the bit immediately above the indented section: 

[LIST]
[*]as of 2008-12-20 if you are running on 2.6.27 kernel (Ubuntu 8.10) you may need a patch [#839]("http://code.ximeta.com/trac-ndas/ticket/839")
[*]For Ubuntu 9.04 on 2.6.28 kernel, download and apply the patch for the 2.6.27 kernel, and then the patch for the 2.6.28 kernel, before you start to install the package.
[/LIST]
You *MUST* obtain the patches referenced in the #839 link, unzip them and place them in the structure created when you untarred the installation tarball.

Then go through the boxed instructions in the indented bit. It WILL work. If you get stuck or something fails, your best bet is to zap everything you've done and start again. Certain steps leave bits lying around which subsequent steps pick up and use. You don't want the build to fail because it's picked up a broken bit from a previous run.

for the poster who mentioned this not working on a Rapsody N35: I did my build for a Daboda HCN1 - it's the same machine in a different case - all works perfectly well so stick with it.

Good luck all,
Dean

---

### Post by sergimunoz on 2009-05-12
Hi Dean
I've followed the instructions at least five times, cleaning-up everything between attempts, and I always get the .deb files. After following the steps and installing this cabs, I'm able to register my disk, but when I try to enable it, I got a crash in the messages.log. 
Are you able to mount the disk ???
Regards

---

### Post by deankelly_68 on 2009-05-12
Looks like I may have gotten ahead of myself with the previous post: I too am having trouble with the ndasadmin enable step: it just hangs and can't be killed (no messages or crashes in the log though)

---

### Post by sergimunoz on 2009-05-12
Hi Dean. 
I receive this error on messages.log:

2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.005958] NET: Registered protocol family 29
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.122843] 
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.122845] ndas: Initializing NDAS driver version 1.1.24
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.123599] ndas: Setting max request size to 64kbytes
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.123682] ndas: registering network interface ra0
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.224512] ndas: registered ndas device at major number 60
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.005958] NET: Registered protocol family 29
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.122843] 
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.122845] ndas: Initializing NDAS driver version 1.1.24
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.123599] ndas: Setting max request size to 64kbytes
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.123682] ndas: registering network interface ra0
2009-05-12 19:59:58    sergi-laptop    kernel    [ 4609.224512] ndas: registered ndas device at major number 60
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642289] *pde = 00000000 
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642308] Dumping ftrace buffer:
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642313]    (ftrace buffer empty)
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642317] Modules linked in: ndas_block ndas_core(P) ndas_sal usb_storage rt2860sta(C) i915 drm binfmt_misc bridge stp bnep vmnet ppdev parport_pc vmblock vmci vmmon input_polldev lp parport joydev arc4 ecb snd_hda_intel snd_pcm_oss snd_mixer_oss iwl3945 snd_pcm snd_seq_dummy snd_seq_oss mac80211 iTCO_wdt pcmcia psmouse thinkpad_acpi snd_seq_midi snd_rawmidi iTCO_vendor_support nsc_ircc led_class snd_seq_midi_event snd_seq intel_agp video nvram snd_timer snd_seq_device pcspkr usbhid serio_raw yenta_socket rsrc_nonstatic pcmcia_core agpgart irda btusb output snd soundcore snd_page_alloc cfg80211 crc_ccitt e1000e fbcon tileblit font bitblit softcursor compcache lzo_decompress lzo_compress tlsf [last unloaded: ndas_sal]
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642431] 
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642437] Pid: 10718, comm: nd/dpcd1 Tainted: P         C (2.6.28-11-generic #42-Ubuntu) 1951FEG
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642442] EIP: 0060:[<f8cf6a62>] EFLAGS: 00010202 CPU: 1
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642450] EIP is at ndop_open+0x22/0xd0 [ndas_block]
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642455] EAX: 00000000 EBX: ea32a200 ECX: f8cf6a40 EDX: 00000001
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642459] ESI: 00000001 EDI: ea32a200 EBP: e100fedc ESP: e100fecc
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642463]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642475]  c034bfc3 ea32a200 c281dc00 00000000 e100ff10 c01e377f c02c7290 e100ff08
2009-05-12 20:01:03    sergi-laptop    kernel    [ 4674.642777] ---[ end trace 01d454668a984412 ]---

Don't you get this error ????

Regards
Sergi

---

### Post by kevinbeard on 2009-05-12
> **deankelly_68 said:**
> Looks like I may have gotten ahead of myself with the previous post: I too am having trouble with the ndasadmin enable step: it just hangs and can't be killed (no messages or crashes in the log though)

Did you look in /var/log/syslog?  That's where I see the crash.

---

### Post by deankelly_68 on 2009-05-12
I get a different crash:

1734:May 12 18:53:00 CatDog kernel: [  254.861942] BUG: unable to handle kernel NULL pointer dereference at 00000058
1735:May 12 18:53:00 CatDog kernel: [  254.861949] IP: [<f7e36a62>] ndop_open+0x22/0xd0 [ndas_block]
1736:May 12 18:53:00 CatDog kernel: [  254.861959] *pde = 00000000 
1737:May 12 18:53:00 CatDog kernel: [  254.861963] Oops: 0000 [#1] SMP 
1738:May 12 18:53:00 CatDog kernel: [  254.861966] last sysfs file: /sys/devices/pci0000:00/0000:00:0f.1/host2/target2:0:1/2:0:1:0/block/sr1/size
1739:May 12 18:53:00 CatDog kernel: [  254.861971] Dumping ftrace buffer:
1740:May 12 18:53:00 CatDog kernel: [  254.861974]    (ftrace buffer empty)
1741:May 12 18:53:00 CatDog kernel: [  254.861976] Modules linked in: binfmt_misc ppdev bridge stp bnep ndas_block ndas_core(P) ndas_sal video output input_polldev lp parport snd_via82xx gameport snd_via82xx_modem snd_ac97_codec ac97_bus snd_mpu401_uart snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) dvb_usb_dib0700 dib7000p dib7000m dvb_usb pcspkr snd snd_page_alloc soundcore i2c_viapro via_agp shpchp usbhid dvb_core dib3000mc dibx000_common dib0070 agpgart usb_storage via_rhine mii floppy fbcon tileblit font bitblit softcursor
1742:May 12 18:53:00 CatDog kernel: [  254.862007] 
1743:May 12 18:53:00 CatDog kernel: [  254.862010] Pid: 2748, comm: nd/dpcd1 Tainted: P           (2.6.28-11-generic #42-Ubuntu) System Name
1744:May 12 18:53:00 CatDog kernel: [  254.862013] EIP: 0060:[<f7e36a62>] EFLAGS: 00010202 CPU: 0
1745:May 12 18:53:00 CatDog kernel: [  254.862018] EIP is at ndop_open+0x22/0xd0 [ndas_block]
1746:May 12 18:53:00 CatDog kernel: [  254.862020] EAX: 00000000 EBX: f6a36960 ECX: f7e36a40 EDX: 00000001
1747:May 12 18:53:00 CatDog kernel: [  254.862022] ESI: 00000001 EDI: f6a36960 EBP: f636dedc ESP: f636decc
1748:May 12 18:53:00 CatDog kernel: [  254.862025]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
1749:May 12 18:53:00 CatDog kernel: [  254.862027] Process nd/dpcd1 (pid: 2748, ti=f636c000 task=f6370000 task.ti=f636c000)
1750:May 12 18:53:00 CatDog kernel: [  254.862029] Stack:
1751:May 12 18:53:00 CatDog kernel: [  254.862031]  c034bfc3 f6a36960 f178d400 00000000 f636df10 c01e377f c02c7290 f636df08
1752:May 12 18:53:00 CatDog kernel: [  254.862036]  00000000 00000001 f6a3696c 03c00000 f178d430 00000000 f178d4b8 f178d400
1753:May 12 18:53:00 CatDog kernel: [  254.862041]  f6a36960 f636df18 c01e392a f636df3c c0204400 0000001c f6c28800 0000003c
1754:May 12 18:53:00 CatDog kernel: [  254.862046] Call Trace:
1755:May 12 18:53:00 CatDog kernel: [  254.862048]  [<c034bfc3>] ? get_device+0x13/0x20
1756:May 12 18:53:00 CatDog kernel: [  254.862055]  [<c01e377f>] ? __blkdev_get+0x12f/0x2d0
1757:May 12 18:53:00 CatDog kernel: [  254.862063]  [<c02c7290>] ? kobject_put+0x20/0x50
1758:May 12 18:53:00 CatDog kernel: [  254.862070]  [<c01e392a>] ? blkdev_get+0xa/0x10
1759:May 12 18:53:00 CatDog kernel: [  254.862073]  [<c0204400>] ? register_disk+0x130/0x150
1760:May 12 18:53:00 CatDog kernel: [  254.862078]  [<c02bdfa9>] ? add_disk+0xd9/0x130
1761:May 12 18:53:00 CatDog kernel: [  254.862084]  [<c02bd5c0>] ? exact_match+0x0/0x10
1762:May 12 18:53:00 CatDog kernel: [  254.862087]  [<c02bda60>] ? exact_lock+0x0/0x20
1763:May 12 18:53:00 CatDog kernel: [  254.862090]  [<f7e36769>] ? slot_enable+0x189/0x280 [ndas_block]
1764:May 12 18:53:00 CatDog kernel: [  254.862096]  [<f7e3687e>] ? ndcmd_enabled_handler+0x1e/0x70 [ndas_block]
1765:May 12 18:53:00 CatDog kernel: [  254.862102]  [<f816193e>] ? 236x+0xe/0x20 [ndas_core]
1766:May 12 18:53:00 CatDog kernel: [  254.862121]  [<f816ad55>] ? 61x+0x175/0x1d0 [ndas_core]
1767:May 12 18:53:00 CatDog kernel: [  254.862131]  [<f816ac20>] ? 61x+0x40/0x1d0 [ndas_core]
1768:May 12 18:53:00 CatDog kernel: [  254.862138]  [<c0105477>] ? kernel_thread_helper+0x7/0x10
1769:May 12 18:53:00 CatDog kernel: [  254.862144] Code: ff eb b6 8d b6 00 00 00 00 55 89 e5 83 ec 10 85 d2 89 75 f8 89 d6 89 7d fc 89 c7 b8 fb ff ff ff 89 5d f4 74 1f 8b 87 10 01 00 00 <8b> 40 58 8b 58 04 c1 fb 04 8d 4b 01 83 f9 11 7f 5d f6 42 19 08 
1770:May 12 18:53:00 CatDog kernel: [  254.862168] EIP: [<f7e36a62>] ndop_open+0x22/0xd0 [ndas_block] SS:ESP 0068:f636decc
1771:May 12 18:53:00 CatDog kernel: [  254.862175] ---[ end trace e1dd7adbfc0ba1dc ]---

I'm on 9.04 kernel 2.6.28-11-generic.

This worked fine before I upgraded from 8.10. When I run the ndasadmin enable command, the command itself just hangs. ps -ef shown no CPU time buildup so it's not looping. The process can't be killed short of rebooting the machine.

Aaargh!

---

### Post by joanmunoz on 2009-05-12
Hi again!

I've tried three times with no succeed... frustrating again! But here begin my problems:

$ ls /dev/ndas*
/dev/ndas

That's all! I've nothing more here. It must be something more, something like "/dev/ndas-30000869-0  /dev/ndas-30000869-0p1"...

The result of:

joan@joan-laptop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  156290904 sda
   8        1  150239848 sda1
   8        2          1 sda2
   8        5    6048441 sda5
  60        0  244196536 ndas-30000869-0

But I can't mount the NDAS HD...

More help, please!

Thanks

Joan

PS: I'm on 9.04 kernel 2.6.28-11-generic too.

---

### Post by kevinbeard on 2009-05-13
> **deankelly_68 said:**
> I get a different crash:
...


> **joanmunoz said:**
> Hi again!

I've tried three times with no succeed... frustrating again! But here begin my problems:

$ ls /dev/ndas*
/dev/ndas
...



Yep, that's the same as me.  

Keep an eye on this site post as it's most likely the first place a fix will appear:

[http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)

---

### Post by deankelly_68 on 2009-05-13
If it's useful to the cause of getting this fixed, I've just taken this trace:

dean@CatDog:~$ sudo strace -vfxo /tmp/ndasadmin-strace ndasadmin enable -s 1 -o w &

which hangs as always

dean@CatDog:~$ cat /tmp/ndasadmin-strace 


30589 execve("/usr/sbin/ndasadmin", ["ndasadmin", "enable", "-s", "1", "-o", "w"], ["TERM=xterm", "LS_COLORS=no=00:fi=00:di=01;34:l"..., "PATH=/usr/local/sbin:/usr/local/"..., "LANG=en_GB.UTF-8", "HOME=/home/dean", "DISPLAY=:0.0", "XAUTHORITY=/home/dean/.Xauthorit"..., "COLORTERM=gnome-terminal", "SHELL=/bin/bash", "LOGNAME=root", "USER=root", "USERNAME=root", "SUDO_COMMAND=/usr/bin/strace -vf"..., "SUDO_USER=dean", "SUDO_UID=1000", "SUDO_GID=1000"]) = 0
30589 brk(0)                            = 0x8915000
30589 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
30589 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f8f000
30589 access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
30589 open("/etc/ld.so.cache", O_RDONLY) = 3
30589 fstat64(3, {st_dev=makedev(8, 1), st_ino=295647, st_mode=S_IFREG|0644, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=176, st_size=82153, st_atime=2009/05/09-08:50:30, st_mtime=2009/05/09-08:50:29, st_ctime=2009/05/09-08:50:29}) = 0
30589 mmap2(NULL, 82153, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f7a000
30589 close(3)                          = 0
30589 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
30589 open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
30589 read(3, "\x7f\x45\x4c\x46\x01\x01\x01\x00\x00\x00\x00\x00\x00\x00\x00\x00\x03\x00\x03\x00\x01\x00\x00\x00\xd0\x68\x01\x00\x34\x00\x00\x00\xe4"..., 512) = 512
30589 fstat64(3, {st_dev=makedev(8, 1), st_ino=2375688, st_mode=S_IFREG|0755, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=2832, st_size=1442180, st_atime=2009/05/08-22:30:43, st_mtime=2009/04/09-09:20:23, st_ctime=2009/05/08-22:30:38}) = 0
30589 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f79000
30589 mmap2(NULL, 1451632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e16000
30589 mprotect(0xb7f72000, 4096, PROT_NONE) = 0
30589 mmap2(0xb7f73000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15c) = 0xb7f73000
30589 mmap2(0xb7f76000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f76000
30589 close(3)                          = 0
30589 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e15000
30589 set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e156c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
30589 open("/dev/urandom", O_RDONLY)    = 3
30589 read(3, "\x8c\x14\xbf\x7e"..., 4) = 4
30589 close(3)                          = 0
30589 mprotect(0xb7f73000, 8192, PROT_READ) = 0
30589 mprotect(0x804d000, 4096, PROT_READ) = 0
30589 mprotect(0xb7fad000, 4096, PROT_READ) = 0
30589 munmap(0xb7f7a000, 82153)         = 0
30589 getuid32()                        = 0
30589 open("/dev/ndas", O_RDONLY|O_NONBLOCK) = 3
30589 ioctl(3, 0x3c62

---

### Post by ntginson on 2009-05-14
Hello NDAS users,

any update on using NDAS in Ubuntu? This is the only thing thats keeping me boot up in windows to transfer/copy files to and from my Mediagate mg 350HD drive that is running NDAS.

---

### Post by deankelly_68 on 2009-05-15
No updates at code.ximeta.com - you can follow their progress here: [http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)
 
Cheers,
Dean

---

### Post by deankelly_68 on 2009-05-20
Has anyone heard of any progress being made on this issue? It all seems to have gone very quiet...

---

### Post by joanmunoz on 2009-05-20
Very, very quiet...

---

### Post by Cuto on 2009-05-28
> **joanmunoz said:**
> Very, very quiet...

I have a similar problem as you have... when executing ndasadmin enable -s 1 -o r nothing happens...

:(

---

### Post by deankelly_68 on 2009-06-04
Still no news on code.ximeta.org. I'm wondering if we've been forgotten about?

---

### Post by Digitallad on 2009-06-21
Have a look at this post.It work much better that the official website that show you how to first create a deb file.
[http://klimek.box4.net/blog/2007/06/10/ubuntu-gutsy-ximeta-ndas-howto/](http://klimek.box4.net/blog/2007/06/10/ubuntu-gutsy-ximeta-ndas-howto/)
(Worked well on Hardy)

---

### Post by Ispep on 2009-07-26
The HDD has ntfs-3g file system and I can't mount it with 
/usr/sbin/ndasadmin enable -s 1 -o w

Is this impossible or am I doing something wrong ?

I've finished with building the NDAS package

---

### Post by sonic167 on 2009-10-30
Has anyone tried NDAS driver with Ubuntu 9.10 yet (kernel 2.6.31)?
Given this past experience/thread with this driver, I'm hesitating in upgrading to 9.10 as I don't want to lose my wireless connection to my NDAS drive ... 
I skipped 9.4 for that same reason ... (although it seems 9.4 should work with Linux2.6.28.patch.zip).

Thanks,

Vince.

---

### Post by byronyasgur on 2010-08-25
was this ever resolved - i have an ndas drive myself

---

### Post by ecolom1269 on 2012-05-17
HI I was able to install the second file for the modules in ubunto 12.04.  however the first file ndasadmin says "dependencies not acceptable"
 
-rw-r--r-- 1 dean dean 22118 2009-05-12 16:33 ndasadmin_1.1-24_i386.deb
-rw-r--r-- 1 dean dean 194656 2009-05-12 16:33 ndas-modules-src_1.1-24_all.deb

what does that mean,
i need the admin tool to register the ndas device.
 
thanks

---

### Post by Toporagno on 2012-05-18
Hi ecolom1269,
have you seen this?
[http://freetz.org/wiki/packages/ndas](http://freetz.org/wiki/packages/ndas)
Please if this help contact me as I need to mount a NDAS device as well.

---

### Post by ecolom1269 on 2012-05-18
yes Toporagno I have.
 
These are the steps we need to take after we install ndasadmin but ndasadmin is the deb that doesn't install because of the dependencies problem.
 
WHEN the solution is found, I will post steps here... no problem we will get thru this together .. i am just scared tho that there is no ndas support for ubunto precise 12.04.
 
I search the forums everyday. I really am tired of hooking up cables accross the living room.. im driving my new wife bananas! [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

