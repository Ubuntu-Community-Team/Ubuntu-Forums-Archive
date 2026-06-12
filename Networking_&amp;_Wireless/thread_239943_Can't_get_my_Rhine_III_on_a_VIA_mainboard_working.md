---
title: "Can't get my Rhine III on a VIA mainboard working"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by mikeweezer on 2006-08-20
Hi all,

   I'm trying to make the switch out of Windows to Linux, and wow its tough. I'm pretty new, I know some command line stuff, but not alot.  On a side note, I went to Linux world and the Ubuntu guy didn't beleive me when I told him my card wouldn't work.  Oh well.

ANYWAY. Here's the deal.

When I type in ifconfig I get something that says 
lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host

It goes on for a few more lines but I'm getting tired.  I'm typing this on another computer since I obviously can't connect on my Linux PC.

The card is a Rhine IIII on a VIA Mainboard.  If anyone can offer up some help, it would be awesome.  Don't make me go back to the dark side.... :evil:

---

### Post by kenguard on 2006-09-19
I've installed and run Hoary Hedgehog and Breezy Badger on my system without any difficulties.  I've tried installing Dapper and it will not detect the network adapter.  I too have the VIA Rhine III adapter.  It's working in XP on this machine (which is how I'm accessing the support site) so I know it's not the hardware.  Has support for some of the NICs been removed in the new version?

Anyone have this network adapter working in Dapper?

---

### Post by goodmaj on 2006-09-19
I have a VIA mainboard with a Rhine II (not III) and had no problem with Dapper.

It may be that the interface is there but not activated.  Try using the Networks admin tool and make sure that it is turned on (active).

---

### Post by kenguard on 2006-10-02
I've checked that.  It's not detected when you manually install the system either.  I wish that I would have tried to upgrade from Hoary instead, maybe it would have kept the network setup and files.  I have the files that came on the disk for the NIC which has the files needed to make the driver.  I'm thinking I would not need to do that.  Previous releases found my hardware and set it up properly without any problems.  It seems Rhine II is supported and Rhine III is not anymore.

---

### Post by ketil on 2006-11-01
I have a VIA ITX with dual ethernet, both Rhine II and Rhine III.  After upgrading from Breezy (all the way to Edgy), I only get one interface working (eth1, which I believe is the Rhine II).  While dmesg prints both eth0 and eth1 when via-rhine is modprobed, ifconfig only shows eth1, and 'ifconfig eth0' gives an error.

If anybody finds a solution, please email me at <ketil at ii.uib.no>.

---

### Post by bjd on 2006-11-02
I also have a VIA itx mainboard with dual ethernet (PD10000) one of which is a Rhine-III chip and it works fine for me. This is with Ubuntu Dapper, using kernel 2.6.15-26-386.

The device is listed as:
PCI-ID:1106:3106
Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)

This is system is close to two years old, so maybe something is different with newer versions of the Rhine-III...

---

### Post by ketil on 2006-11-11
Okay, it works now.

Turns out that starting with Dapper, the file /etc/iftab is used to assign ethernet device names.

Updating that file to reflect the hardware fixed my
problems.

See also this bug report: [https://launchpad.net/distros/ubuntu/+bug/47407](https://launchpad.net/distros/ubuntu/+bug/47407)

-k

---

