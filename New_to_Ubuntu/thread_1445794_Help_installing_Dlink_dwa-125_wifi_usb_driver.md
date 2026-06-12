---
title: "Help installing Dlink dwa-125 wifi usb driver"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by jbeily on 2010-04-03
about me: zero ubuntu experience. zero comprehension (currently) of command lines/terminal. I just need that internet connection and the derivatives.
I spent the last two days searching and reading, but every solution (if they even are solutions) is beyond my experience/too complex for my level.
I installed Ubuntu 9.10 two days ago.
I need help targeted for a COMPLETE dummy on all the levels you can think of to install the Dlink driver.
Btw, the ubuntu pocket guide was no help concerning the wireless connection issues.
Based on earlier posts and threads, my Dlink chip seems to be R3070.
I would not post this here, or even register, if i weren't pissed by the problem to the extreme...I usually search and read.
Thank you. Feel free to ignore me, i won't even notice.

---

### Post by cariboo on 2010-04-04
Even if you don't know much about Ubuntu, you can do some basic troubleshooting, to help us solve your problem.

Plug in your device, then go to System->Administration->Log File Viewer->dmesg. Scroll down to the bottom and copy the last 10 lines of the log file and paste it into a text file. The text editor is located under Applications-->Accessories-gedit.

Once you have saved the text file, copy it to your Windows partition, and paste it into your next post.

---

### Post by anewguy on 2010-04-04
Perhaps also do the following with the device plugged in:

-click applications, scroll to accessories and then over and down to terminal and click

- when the terminal window opens, do the following:

type:  lsusb <press enter>

Copy the output from that for posting back here.

Just type exit and press enter, or use the "X" box to close the terminal window.

Dave ;)

---

### Post by jbeily on 2010-04-05
thanks for the replies, sorry i ddnt have the laptop with me ( toshiba satellite, i have on it apart from the Ubuntu 9.10 Windows Xp Sp3 professional x86 32-bit) to check them.

what cariboo asked for :

[    9.815197] type=1505 audit(1270494897.483:13): operation="profile_replace" pid=847 name=/sbin/dhclient3
[    9.815832] type=1505 audit(1270494897.483:14): operation="profile_replace" pid=847 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.816207] type=1505 audit(1270494897.487:15): operation="profile_replace" pid=847 name=/usr/lib/connman/scripts/dhclient-script
[    9.820930] type=1505 audit(1270494897.491:16): operation="profile_replace" pid=848 name=/usr/bin/evince
[    9.831545] type=1505 audit(1270494897.499:17): operation="profile_replace" pid=848 name=/usr/bin/evince-previewer
[    9.839539] type=1505 audit(1270494897.507:18): operation="profile_replace" pid=848 name=/usr/bin/evince-thumbnailer
[    9.847965] type=1505 audit(1270494897.515:19): operation="profile_replace" pid=850 name=/usr/lib/cups/backend/cups-pdf
[    9.848743] type=1505 audit(1270494897.519:20): operation="profile_replace" pid=850 name=/usr/sbin/cupsd
[    9.851281] type=1505 audit(1270494897.519:21): operation="profile_replace" pid=851 name=/usr/sbin/tcpdump
[   12.025840] ppdev: user-space parallel port driver



what anewguy asked for :


Bus 002 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c0d D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



thank you in advance if u get the chance to help me more.

---

### Post by bkratz on 2010-04-05
Hopefully this thread may be of some help

[http://newyork.ubuntuforums.org/showthread.php?t=1412533](http://newyork.ubuntuforums.org/showthread.php?t=1412533)

It goes into a lot of detail

---

### Post by jbeily on 2010-04-05
the thread does not help at all...
the guy tried some things i ddnt understand, and his problems are specific to him. He tried blacklisting and the likes, which i understand nothing of.

---

### Post by anewguy on 2010-04-05
Do you have a Windows driver installation CD (or can you download the drivers?) for the adapter?  If so, considering everything that went on in that other post, we could try ndiswrapper and see if we have any luck with that.

SerialMonkey seems to stopped rt driver builds except for in-kernel ones.  However, ralink itself appears to have a linux driver.  I believe you need the one for the rt3070usb.  A quick glance at the webpage ([http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")) suggests these are source code.  I can look more at that later.  

For now, see if you have the Windows drivers and post back.

Dave ;)

---

### Post by sgerrand on 2010-06-02
i've written a [blog post on this very subject]("http://sasha.gerrand.id.au/2010/06/03/resolving-driver-problems-for-d-link-dwa-125-wireless-150-usb-adapter-in-ubuntu/") - in summary, you need to update the usb driver.

hope it helps. :)

---

### Post by Nevada77 on 2010-06-09
Can someone please help me as well. My info is:

Bus 004 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0ace:1215 ZyDAS WLA-54L 802.11bg
Bus 002 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 003: ID 045e:0728 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by David006 on 2010-08-06
> **Nevada77 said:**
> Can someone please help me as well. My info is:

  :
Bus 001 Device 006: ID 07d1:3c16 D-Link System 
  :


You have the device attached and recognized as a USB device.  Now refer to:

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9632897&postcount=15](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9632897&postcount=15)

---

### Post by mwangarch on 2010-08-10
Same issue with the DWA-125.  No joy, yet.
dmesg gives the following:
[   15.180273] rtusb init --->
[   15.180343] usbcore: registered new interface driver rt2870
[   15.188334] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.189790] dell-wmi: No known WMI GUID found
[   15.193512] Disabling lock debugging due to kernel taint
[   15.237531] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.257872] ppdev: user-space parallel port driver
[   15.545955] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.596151] usb 1-4: reset high speed USB device using ehci_hcd and address 4
[   15.713328] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.713382] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.811990] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   15.812442] ndiswrapper (load_sys_files:206): couldn't prepare driver 'drt2870'
[   15.813408] ndiswrapper (load_wrap_driver:108): couldn't load driver drt2870; check system log for messages from 'loadndisdriver'
[   15.813498] usbcore: registered new interface driver ndiswrapper
[   16.143581] intel8x0_measure_ac97_clock: measured 56400 usecs (2717 samples)
[   16.143591] intel8x0: clocking to 48000
[   20.410989] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[   20.443351] EXT4-fs (loop0): internal journal on loop0:8
[   21.021738] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.049701] __ratelimit: 3 callbacks suppressed
[   21.049708] type=1505 audit(1281480615.335:12): operation="profile_replace" pid=854 name=/usr/share/gdm/guest-session/Xsession
[   21.096566] type=1505 audit(1281480615.383:13): operation="profile_replace" pid=855 name=/sbin/dhclient3
[   21.097487] type=1505 audit(1281480615.383:14): operation="profile_replace" pid=855 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.097990] type=1505 audit(1281480615.383:15): operation="profile_replace" pid=855 name=/usr/lib/connman/scripts/dhclient-script
[   21.141540] type=1505 audit(1281480615.427:16): operation="profile_replace" pid=863 name=/usr/bin/evince
[   21.252505] type=1505 audit(1281480615.539:17): operation="profile_replace" pid=863 name=/usr/bin/evince-previewer
[   21.329691] type=1505 audit(1281480615.615:18): operation="profile_replace" pid=863 name=/usr/bin/evince-thumbnailer
[   21.390371] type=1505 audit(1281480615.675:19): operation="profile_replace" pid=890 name=/usr/lib/cups/backend/cups-pdf
[   21.391457] type=1505 audit(1281480615.675:20): operation="profile_replace" pid=890 name=/usr/sbin/cupsd
[   21.426858] type=1505 audit(1281480615.711:21): operation="profile_replace" pid=891 name=/usr/sbin/tcpdump
[   23.038875] render error detected, EIR: 0x00000010
[   23.038886] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[   23.038907] render error detected, EIR: 0x00000010
[   23.816182] b44: eth0: Link is up at 100 Mbps, full duplex.
[   23.816189] b44: eth0: Flow control is off for TX and off for RX.
[   23.816846] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.392012] eth0: no IPv6 routers present

do I need to disable or unload the ndiswrapper?

---

