---
title: "32 bit vs. 64 bit WiFi Driver Conflict--Maybe?"
date: 2018-06-29
forum: Networking &amp; Wireless
---

### Post by wmeler on 2018-06-29
I have a dual boot on my computer.  In Windows 7, Device Manager calls my USB WiFi device: "NETGEAR WNDA3100v2 N600 Wireless Dual Band USB Adapter"

I installed this just fine in Windows 7.  It works.  I then tried to install it in Ubuntu 16.04.  I could "kinda" get it working *if* I did a "sudo ndiswrapper -e bcmn43xx32" and then installed with a "sudo ndiswrapper -i bcmn43xx64.inf".

However, when I did this it didn't completely work -AND- it was no longer working in Windows 7.  So, I went back into Windows 7, uninstalled it via Control Panel, and re-installed all over again (with the installation disks). It's working again in Windows 7, but *not* working in Linux.  Obviously, I want to get it working in both.  I really have no idea what to try.  Thanks in advance!

Starting from a directory that I got here:
[https://ubuntuforums.org/attachment.php?attachmentid=216486&d=1335215580](https://ubuntuforums.org/attachment.php?attachmentid=216486&d=1335215580)

I found that here:
[https://ubuntuforums.org/showthread.php?t=1964173](https://ubuntuforums.org/showthread.php?t=1964173)


Here's the output I get from a terminal:

thomas@canisius ~/Desktop/downloads/broadcom-driver $ ls
bcmn43xx32.inf        bcmn43xx32.sys    bcmn43xx64.inf        bcmn43xx64.sys

thomas@canisius ~/Desktop/downloads/broadcom-driver $ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 04b3:3005 IBM Corp. 
Bus 007 Device 002: ID 04b3:3006 IBM Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thomas@canisius ~/Desktop/downloads/broadcom-driver $ sudo ndiswrapper -i bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...

thomas@canisius ~/Desktop/downloads/broadcom-driver $ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed
    device (0846:9011) present

thomas@canisius ~/Desktop/downloads/broadcom-driver $ dmesg | grep ndis
[  129.337689] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  129.340705] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  129.632685] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  129.632695] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[  129.633430] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[  129.633511] usbcore: registered new interface driver ndiswrapper

thomas@canisius ~/Desktop/downloads/broadcom-driver $ iwconfig
lo        no wireless extensions.

enp0s25   no wireless extensions.



Again...thanks in advance!

---

### Post by chili555 on 2018-06-29
Let me play out the next four or five replies on this thread.

Reply #1: Chili: This will never work with the 32-bit driver. Delete it, reboot and run: sudo modprobe ndiswrapper. Look for errors in the log: dmesg | grep ndis

Reply #2: wmeler: Well it came to life for a few moments but never connected, never pulled a web page and now it's dead again. What do we do, Doc Chili?

Reply #3: Chili: Let's try some other driver from a different website here: [www.ubuntu-blah-blah](www.ubuntu-blah-blah)

Reply #4: wmeler: Same deal,  it came to life for a few moments but never connected and now it's dead again. What do we do now?

Reply #5: Chili: The truth is, it won't work never ever. We haven't seen ndiswrapper work successfully in several years. Get a different device.

TL;DR: Get a different device.

Sorry.

---

### Post by wmeler on 2018-06-29
chili555, 

Hmm.  Sad to hear.  Any way to get an old and previously-working ndiswrapper?

By the way, read a lot of your stuff earlier today in trying to get this to work.  Thanks for being so helpful to everyone.


For what it's worth...before I saw your response, I did the following:
ndiswrapper -r bcmn43xx32

And it broke my Windows 7 WiFi.  As expected.  That said...before I fixed it in Windows 7 again by utterly re-installing...while it was still broken it Windows, I did the following.

First, I typed the command &#8220;ndiswrapper -l&#8221;, I got this output:

bcmn43xx64 : driver installed
    device (0846:9011) present 

In other words, that does indeed deal with the 32-bit.  That said, with the 64-bit driver, I can see all the WiFi networks, and even manage to connect to an unprotected network that I could care less about.

However, there is a network&#8212;call it FOM&#8212;which I *cannot* connect to.  I have typed the correct password probably 100 times, restarted, and everything else I can think of.  I know it&#8217;s the right password, because I connect without any issue when I manually type in the exact same password on Windows 7. Here&#8217;s my current output now:


thomas@canisius ~/Desktop/downloads/broadcom-driver $ dmesg | grep ndis
[  312.307527] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  312.310773] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  312.575864] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  313.123975] usbcore: registered new interface driver ndiswrapper
[  313.131805] ndiswrapper 1-6:1.0 enxe0469aab7e97: renamed from wlan0
[  313.136363] ndiswrapper: interface renamed to 'enxe0469aab7e97'

thomas@canisius ~/Desktop/downloads/broadcom-driver $ iwconfig
lo        no wireless extensions.

enp0s25   no wireless extensions.

enxe0469aab7e97  IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thomas@canisius ~/Desktop/downloads/broadcom-driver $ sudo service network-manager restart

thomas@canisius ~/Desktop/downloads/broadcom-driver $ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 02
       serial: 00:1d:09:7c:d9:36
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=1.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:25 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: enxe0469aab7e97
       serial: e0:46:9a:ab:7e:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.59+,08/26/2009, 5.10.79.30 ip=192.168.223.117 link=yes multicast=yes wireless=IEEE 802.11g

thomas@canisius ~/Desktop/downloads/broadcom-driver $ dmesg | grep ndis
[  312.307527] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  312.310773] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  312.575864] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  313.123975] usbcore: registered new interface driver ndiswrapper
[  313.131805] ndiswrapper 1-6:1.0 enxe0469aab7e97: renamed from wlan0
[  313.136363] ndiswrapper: interface renamed to 'enxe0469aab7e97'
[  380.986659] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  437.501878] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  587.995971] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 5797.979935] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 5890.008713] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 6046.016403] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 6140.029833] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)

thomas@canisius ~/Desktop/downloads/broadcom-driver $ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present 


Cheers.

---

### Post by chili555 on 2018-06-29
> I can see all the WiFi networks, and even manage to connect to an unprotected network that I could care less about.

However, there is a network—call it FOM—which I *cannot* connect to. I have typed the correct password probably 100 times, restarted, and everything else I can think of. Exactly as I predicted.> Any way to get an old and previously-working ndiswrapper?
Not that works with any modern kernel version. It would be foolish to install, say Ubuntu 12.04, hunt down an old ndiswrapper and compile it and hope that it maybe works. If it did work, the old Ubuntu version lacks support and patches for security and other flaws.

There are quite a few US$12-15 USB wireless devices that will plug and play.

Sorry.

---

### Post by wmeler on 2018-07-01
Thanks anyway.  :)

Which USB wireless device(s) would you recommend?

---

### Post by chili555 on 2018-07-02
Here at my post #22, are some suggestions: [https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

---

