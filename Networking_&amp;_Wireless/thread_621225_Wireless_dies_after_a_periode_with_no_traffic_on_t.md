---
title: "Wireless dies after a periode with no traffic on the link"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by mkalle on 2007-11-23
Hello

I got a motherboard from asus, p5w delux with integrated wireless on it, with an external antenna.
If i do a ping <ip> -s 1300 and keep traffic flowing on the link, it does not drop the connection.
if i dont have the ping running, it drops the connection shortly after startup, and i have to reboot to get it going again.

i am not quite sure how to debug this, so hopefully, someone can tell me which commands to run to generate helpful output.

here is some from dmesg.
root@workstation:~# dmesg |grep wlan
[   98.584764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  101.339694] wlan0: Initial auth_alg=0
[  101.339700] wlan0: authenticate with AP 00:1a:70:a9:76:09
[  101.341306] wlan0: RX authentication from 00:1a:70:a9:76:09 (alg=0 transaction=2 status=0)
[  101.341309] wlan0: authenticated
[  101.341311] wlan0: associate with AP 00:1a:70:a9:76:09
[  101.343424] wlan0: RX AssocResp from 00:1a:70:a9:76:09 (capab=0x401 status=0 aid=1)
[  101.343426] wlan0: associated
[  101.344953] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  101.847073] wlan0: duplicate address detected!

This is from daemon.log
Nov 23 17:50:41 workstation avahi-daemon[6969]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 23 17:50:41 workstation avahi-daemon[6969]: Successfully dropped root privileges.
Nov 23 17:50:41 workstation avahi-daemon[6969]: avahi-daemon 0.6.20 starting up.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Successfully called chroot().
Nov 23 17:50:41 workstation avahi-daemon[6969]: Successfully dropped remaining capabilities.
Nov 23 17:50:41 workstation avahi-daemon[6969]: No service file found in /etc/avahi/services.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.92.
Nov 23 17:50:41 workstation avahi-daemon[6969]: New relevant interface wlan0.IPv4 for mDNS.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Network interface enumeration completed.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Registering new address record for fe80::215:afff:fe04:4853 on wlan0.*.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Registering new address record for 192.168.1.92 on wlan0.IPv4.
Nov 23 17:50:41 workstation avahi-daemon[6969]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 23 17:50:42 workstation avahi-daemon[6969]: Server startup complete. Host name is workstation.local. Local service cookie is 4257112256.

lspci output:
root@workstation:/var/log# lspci
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

---

### Post by defishguy on 2007-11-23
Are you using DHCP or are you assigning your IP address manually?

---

### Post by mkalle on 2007-11-25
right now i have configured a ip for the adapter, but its the same story etiher way.

---

### Post by defishguy on 2007-11-25
Wow.  You have the Realtek 8187 wireless on board.  Sorry it took so long to get that.  There are already several threads on this problem.  After reading a few it  looks like a solution [_was found here._]("http://ubuntuforums.org/showthread.php?t=333586")

If you need help directly using ndiswrapper or anything you can feel free to email me or better yet you can  find help in the evenings (U.S. EST) on #ubuntu-kentucky on irc.freenode.net.

Good luck!

---

### Post by mkalle on 2007-11-27
alright.

i installed the ndiswrapper, downloaded the driver from asus.com
installed the driver,

root@workstation:~# ndiswrapper -l
netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)


How do i force my wlan0 device to use that driver?

i assume that its currently running on the rtl8187 driver, i tried to blacklist the driver by typing "blacklist rtl8187" into /etc/modprobe.d/blacklist

after a reboot, there was no wireless working.

how do i see what driver a device is using?

Morten

---

### Post by defishguy on 2007-11-27
When you blacklist a driver it means that it won't be available when you boot.

Type

sudo ndiswrapper -i rtl8187

You may have to replace rtl8187 with the name of the driver that you're using.  You would type the command in the directory where the driver file is located.

---

### Post by mkalle on 2007-11-28
yes, i have the driver installed. look at my previous message.

but its configured to use an alternate driver, as i can read on the ndiswrapper page, thats not good.

but i dont know how to pull that driver out of my kernel, id rather not recompile.

---

### Post by panurge77 on 2007-12-08
It will always tell rtl8187 is the alternate driver, no matter if it's loaded or not. If you blacklisted rtl8187, then you can forget about it. Now the problem seems to be that ndiswrapper is not loading. Add ndiswrapper to /etc/modules and make sure you have an alias setting nidswrapper as wlan0. You can do that with the command "sudo ndiswrapper -m"

Hope it helps

You can take a look here: [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

---

