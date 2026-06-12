---
title: "Ethernet is not working"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by pruett57 on 2005-10-25
I have an old IBM TP 600E with a Xircom card.
Ubuntu found the card. Once it booted up I configured the card for DHCP but I don't an IP. I know everything is setup correctly because I have other PCs on this router (Windows PCs).

I thought there was another step in Ubuntu to get it up and going but I can't remember.

Thank you,

jp

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=pruett57]I have an old IBM TP 600E with a Xircom card.
Ubuntu found the card. Once it booted up I configured the card for DHCP but I don't an IP. I know everything is setup correctly because I have other PCs on this router (Windows PCs).

I thought there was another step in Ubuntu to get it up and going but I can't remember.

Thank you,

jp[/QUOTE]
Try running:
```

$ sudo dhclient

```
to get a dynamic IP address.

---

### Post by mlomker on 2005-10-25
**ifconfig eth0** should show you some info if the driver is loaded.  **sudo dhclient eth0** should renew an address.

---

### Post by pruett57 on 2005-10-26
Okay, I did the above things and it doesn't work still.

ifconfig eth0:
It shows the hardware address, inet6 address, backets and so on.
If you go to the device manager the correct driver is loaded.

sudo dhclient eth0:
runs but says it can't find anything.

---

### Post by pruett57 on 2005-10-26
I found the fix.

I had to add the lines to grub and to disable ipv6.

---

### Post by mlomker on 2005-10-26
> I had to add the lines to grub and to disable ipv6.

That's interesting.  I hadn't heard of that being an issue with DHCP before (just DNS).

---

### Post by viuks on 2005-11-04
[quote=pruett57]I found the fix.

I had to add the lines to grub and to disable ipv6.[/quote]

Ihave same problem. Can You show us please, theese grub lines?

---

### Post by MKS on 2005-11-06
Similarly, I'd be really interested to know how as well.  I'm having trouble with my Stinkpad600E and networking.  Ifconfig sees the card, dhclient gets an IP address from the router but no route between the Stinkpad and the router (when using ping etc).

Thinkpad 600E with a Dlink 690TXD PCMCIA ethernet card.

---

### Post by mips on 2005-11-06
Check out  [http://ubuntuforums.org/showthread.php?t=85375&highlight=mips](http://ubuntuforums.org/showthread.php?t=85375&highlight=mips)

REInvestors solution was to add **acpi=off** to the linux boot line in GRUB.

Dont know if this will help you guys seeing he had a speed problem...

---

### Post by mlomker on 2005-11-06
> Ifconfig sees the card, dhclient gets an IP address from the router but no route between the Stinkpad and the router (when using ping etc).

Do you mean that you can't ping the router itself or that you can't ping something on the Internet?

```

route -n

```

---

### Post by MKS on 2005-11-06
Thanks for the replies.  I have followed Mips' thread, changed etc/modprobe.d/aliases to set ipv6 to **off**, and rebooted but still no joy in getting the network card to "see past" my router.  My initial interpretation of the checks below are that the laptop has picked up an IP address from my router, but when I open Firefox and enter [http://www.google.com](http://www.google.com) it times out.  

I have also tweaked Firefox with the settings mentioned in other threads.

I'd really appreciate any advice.
Many thanks!
Mike

EDIT: I should also add that I can ping my router 192.168.2.1 but it is very slow (high ms delay and 16% packet loss).

Here are some more details:
Laptop: Thinkpad 600E
Network card: DLink DFE-690TXD PCMCIA
Running Ubuntu Breezy
Router: Belkin ADSL wireless g modem / router F5D7632-4

Results of the usual battery of network checks:

**catherine@ubuntu:~$ cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        network 192.168.2.0
        broadcast 192.168.2.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1
        address 192.168.2.5
        netmask 255.255.255.0
        gateway 192.168.2.1

auto eth0

**catherine@ubuntu:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:40:05:3C:CB:3D
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13639 (13.3 KiB)  TX bytes:9332 (9.1 KiB)
          Interrupt:9 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:375032 (366.2 KiB)  TX bytes:375032 (366.2 KiB)

**catherine@ubuntu:~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


**catherine@ubuntu:~$ sudo mii-diag**
Using the default interface 'eth0'.
Basic registers of MII PHY #32:  1100 782d 0000 0000 01e1 45e1 0001 0000.
 The autonegotiated capability is 01e0.
The autonegotiated media type is 100baseTx-FD.
 Basic mode control register 0x1100: Auto-negotiation enabled.
 You have link beat, and everything is working OK.
 Your link partner advertised 45e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control.
   End of basic transceiver information.

**catherine@ubuntu:~$ sudo mii-tool**
eth0: negotiated 100baseTx-FD, link ok

---

### Post by mlomker on 2005-11-06
> EDIT: I should also add that I can ping my router 192.168.2.1 but it is very slow (high ms delay and 16% packet loss).


Does your hardware work properly in another operating system?  Lost packets tend to make me think there's a bad ethernet cable, generally.

---

### Post by MKS on 2005-11-06
To be honest I haven't tried all the hardware in other operating systems on the Thinkpad.  I *have* checked the network cable and card under WindowsXP on my Vaio laptop and it seems to be working fine, so I'm not sure it's hardware (unless it's particular to the Thinkpad).

---

### Post by mlomker on 2005-11-06
If your Thinkpad has a CDROM drive then I'd suggest downloading a copy of Knoppix and seeing if the networking behaves when running another linux distro.

---

### Post by no_geek on 2005-11-08
I have had a somewhat similar problem on my Acer laptop with onboard Realtek 8139 - weird thing was, networking worked as long as X wasn't started :confused: . I found the solution by accident  - had to comment out the "load dri" line in the modules section of /etc/X11/xorg.conf. Don't know if this is helpful. 
Oh, and by the way, does anybody have an explanation for that?

---

### Post by mlomker on 2005-11-08
> Oh, and by the way, does anybody have an explanation for that?

No.  That would actually disable 3D acceleration.

---

### Post by MKS on 2005-11-08
Strangely, networking with this card (Dlink 690TXD) works under Debian Sarge netinstall CD.  I really can't figure out why it should work on this and not in Ubuntu (given that Ubuntu is Debian-based).  Any ideas?

It didn't work off the bat with Knoppix, but *did* work under XFLD and DSL.  Weird...

---

### Post by mlomker on 2005-11-08
I'd boot the Debian disc and look at the output of ifconfig and lsmod.  

I had a problem once where Linspire detected my card on the wrong IRQ/port number and wouldn't work.  I gave up and switched to Ubuntu.  It's generally a bad sign when cards don't work in Knoppix, though.

---

### Post by MKS on 2005-11-09
Weirder and weirder... Knoppix now picks up my Ethernet...

IRQ under Debian is 11 for the ethernet PCMCIA card.  Ubuntu Server install still fails to recognise DHCP (where Debian does).  Is there anything I can do to help pass this info on to Ubuntu developers?  i.e. Would it help to run ifconfig, lsmod etc. under both and post?  It's a shame because I'd *really* like to work with Ubuntu / Xubuntu if I can.  It seems like a better developed distro than some others...

EDIT: One thing that may have helped is that I disabled Quickboot on BIOS.

---

### Post by mlomker on 2005-11-09
> ifconfig, lsmod etc. under both and post?  It's a shame because I'd *really* like to work with Ubuntu / Xubuntu if I can.  It seems like a better developed distro than some others...


You'd actually want to search at the Bugzilla link (top of the page) and make a report there if it isn't already reported.  The developers don't read the forums...they're too busy coding.  :)

Which kernel are you using?  If there's another one (linux-686 perhaps) that you can try then that might be worth a shot.

```

uname -r

```

---

### Post by rolfpal on 2005-11-14
I have a similar problem.

I have a sony pcg-f650  I have a 3com ethernet pcmcia card that has worked well but the dongle broke.  I got a Xircom cbe2-100 pcmcia card to replace it and  it will not work on a cold boot, if I boot with the 3com then disable the 3com card and load the xircom card it works almost fine.  It is a little slower, movies that are in an NFS share are jerky on it but not on the 3com card, but otherwise it is OK.

I found that the Xircom causes 2 drivers to load, xircom_tulip_cb and xircom_cb, I blacklisted xircom_tulip_cb, since it is deprecated, but it made no difference.

I am stumped.  I will try turning off ipv6 and acpi since they do not seem to work in any case.

Tried that, now it will boiot the computer but the speed is still a problem.

---

