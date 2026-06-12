---
title: "Trouble with BCM4318 on Hardy"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by snakep on 2008-10-05
Hello, I have just installed Hardy on my fiance's laptop, and I'm having lots of trouble with the wireless.  I have been going through these forums and trying many of the suggestions here, but so far nothing has worked, and some of the suggestions seem to be conflicting.  The laptop is not connected to a wired network.  I am posting this from my own desktop, which is running Gutsy and has no problems with wireless (my Ralink2500 chipset seemed much easier to set up than this bcm4318).

So far, I have installed ndiswrapper, ndisgtk, and b43-fwcutter.  I have installed the bcmwl5.inf driver, and configured it via System->Admin->Windows Wireless Drivers.  I have tried to use b43-fwcutter on both bcmwl5.inf and bcmwl5.sys, and I get an error that the input file is either wrong or not supported.  Following the suggestions from [this]("http://ubuntuforums.org/showthread.php?t=767372&highlight=b43-cutter") thread, I downloaded a tar file which had a bunch of files I didn't understand, and ran b43-fwcutter on "wl_apsta.o".  Again, this did not work; I think that this was meant to work with the b43 driver, but I have been trying to use the Windows driver per [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Configuring%20Wireless%20Network%20Settings%20using%20command%20line") wiki and several threads.

Here is the output of lshw -C network:

```
scoats@selenas:~/.drivers$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:be:4e:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

```

Following [this]("http://ubuntuforums.org/showthread.php?t=885847") troubleshooting guide, I tried to remove the modules that are associated with the card so that ndiswrapper would be used instead, but I can't find anything called b43-pci-bridge, and I have already added b43, b43-legacy, etc. to the /etc/modprobe.d/blacklist.

Here is the output from various commands:

```
scoats@selenas:~/.drivers$ lspci | grep Network
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

```
scoats@selenas:~/.drivers$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-key XXXXXXXXXX
wireless-essid Mountain Home











auto wlan0

```

```
scoats@selenas:~/.drivers$ lsmod | grep -e ndis -e b43 -e b44 -e bcm43xx -e wl -e ssb
ndiswrapper           192920  0 
ssb                    34308  0 
usbcore               146028  7 usb_storage,libusual,ndiswrapper,usbhid,ehci_hcd,ohci_hcd

```

```
scoats@selenas:~/.drivers$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

As you can see, it doesn't even seem to recognize the wireless card right now.

```
scoats@selenas:~/.drivers$ uname -a
Linux selenas 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```

Should I be using the b43 driver instead of the Windows driver?  If not, what do I need to do to get the windows driver working?

Thanks for the help.

Jeremiah

---

### Post by berthiggins on 2008-10-05
You can use either really I was using b43 and ndiswrapper on hardy ( obviously not at the same time !
To get ndiswrapper going you will need to blacklist ssb as well as b43 and possibly b43 legacy
but b43 should work fine when you install it thru restricted drivers click on the show details bit at the bottom of the window and you should see an option to download the firmware then it should just work.

---

### Post by snakep on 2008-10-08
Well, I don't have a wired connection, so I can't download firmware.  Every time I've tried to just click on the restricted drivers to select the Broadcom driver, it doesn't work.  So I am trying the ndiswrapper route.  Now I am following [this how-to]("http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318+firmware") which has told me to download and install some files.  I have successfully installed the driver through ndiswrapper, and I am to the point where I am adding and removing modules.  I have removed b44, b43, b43legacy, ssb, and ndiswrapper.  The problem is that every time I go to reload ndiswrapper, the machine locks up -- no mouse, no cursor, nothing.  I have to force it to power off.

Any ideas?

Jeremiah

EDIT: Here is the command that locks everything up:

sudo modprobe ndiswrapper

---

### Post by snakep on 2008-10-09
Bump.

---

