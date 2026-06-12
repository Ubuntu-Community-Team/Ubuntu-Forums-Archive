---
title: "What plugins do I need and how to configure sound?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-02-25
Ever since I had to reinstall Ubuntu on my Dell Mini 9, there has been no sound. It says I either don't have the right gstreamer plugins or the sound card is not configured. How do I do that?

---

### Post by greenleaves123 on 2009-02-25
I found this comprehensive sound problem solver and am following it, I got this:

jenny@jenny:~$ aplay -l
aplay: device_list:215: no soundcards found...
jenny@jenny:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0
	Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f0100000-f01fffff
	Prefetchable memory behind bridge: 0000000050000000-00000000500fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 50100000-501fffff
	Prefetchable memory behind bridge: 00000000f0600000-00000000f06fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 02b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Dell Device 02b0
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

02:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0100000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 50000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Dell Device 02b0
	Flags: fast devsel, IRQ 16
	Memory at f0100400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

02:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at f0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Broadcom Corporation Device 04b5
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: r8169
	Kernel modules: r8169

jenny@jenny:~$ 

Does this mean I have sound cards detected? I am stuck. I don't understand what it means.

---

### Post by greenleaves123 on 2009-02-25
This is too confusing for me, I don't understand any of this. I think I may have to pay someone to get this done for me. I hope someone will be able to figure this out. 

Does anyone have any directions for me? Anyone?

---

### Post by sandyd on 2009-02-25
hi, its me again :)

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Dell Device 02b0
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0540000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```
thats your sound card...

could you do

```

sudo modprobe snd-hda-intel

```
?

---

### Post by metallicamike on 2009-02-25
go to add/remove and install all of the gstreamer plugins

---

### Post by anjilslaire on 2009-02-25
[http://ubuntuforums.org/showpost.php?p=6480044&postcount=2](http://ubuntuforums.org/showpost.php?p=6480044&postcount=2)

getting sound back on your mini 9 is well known with a simple fix :)

---

### Post by sandyd on 2009-02-25
whoops
just saw posts above me.....


nvm....
many people having problems with hdaintel sound....

do all of this
these are modified instructions from ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto))
```

sudo aptitude install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`
```Download the latest version of alsa from [Alsa project]("http://www.alsa-project.org/") (driver, lib, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14. Please change this in accordance with the one you downloaded from the Alsa project site.

```

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2

sudo tar xjf alsa-utils*.tar.bz2

``````

cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

``````

cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

``````

cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

```

---

### Post by greenleaves123 on 2009-02-25
There was an error to that modprob line and I don't know how to get the plugins, I went to add/remove and I saw gstreamer but no plugin.

I already added that line, it doesn't work for me. I found that fix on dell.

---

### Post by sandyd on 2009-02-25
> **greenleaves123 said:**
> There was an error to that modprob line and I don't know how to get the plugins, I went to add/remove and I saw gstreamer but no plugin.

I already added that line, it doesn't work for me. I found that fix on dell.

remove the "woops" from the post above yours and try the instructions :p

---

### Post by greenleaves123 on 2009-02-25
I download the 3 files, they didn't specify where to go. I tried the next sudo steps but there were errors. It wasn't jenny@jenny anymore, there was this stuff after it. I had to close the terminal.

I don't know what to do.

---

### Post by greenleaves123 on 2009-02-25
I am too frustrated right now. I'm going to cool off a bit. Thanks for trying to help. I really appreciate it.

---

### Post by sandyd on 2009-02-25
oops, sorry. forgot you were newbie...

replace the first step with this
```

sudo mkdir /usr/src/alsa
cd Desktop
sudo mv alsa* /usr/src/alsa
cd /usr/src/alsa
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

```

---

### Post by greenleaves123 on 2009-02-25
It didn't work. I got this:

jenny@jenny:~$ sudo mkdir /usr/src/alsa
[sudo] password for jenny: 
mkdir: cannot create directory `/usr/src/alsa': File exists
jenny@jenny:~$ sudo mkdir /usr/src/alsa
mkdir: cannot create directory `/usr/src/alsa': File exists
jenny@jenny:~$ sudo mv alsa* /usr/src/alsa
mv: cannot stat `alsa*': No such file or directory
jenny@jenny:~$ cd /usr/src/alsa
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2

---

### Post by sandyd on 2009-02-26
> **greenleaves123 said:**
> It didn't work. I got this:

jenny@jenny:~$ sudo mkdir /usr/src/alsa
[sudo] password for jenny: 
mkdir: cannot create directory `/usr/src/alsa': File exists
jenny@jenny:~$ sudo mkdir /usr/src/alsa
mkdir: cannot create directory `/usr/src/alsa': File exists
jenny@jenny:~$ sudo mv alsa* /usr/src/alsa
mv: cannot stat `alsa*': No such file or directory
jenny@jenny:~$ cd /usr/src/alsa
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jenny@jenny:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2

fixed.

see instructions again.

---

### Post by greenleaves123 on 2009-02-27
I got everything and it installed, I restarted, but it still doesn't work. :/

---

### Post by markbuntu on 2009-02-27
Just go here, it is a total sound troubleshooting an set up guide

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

