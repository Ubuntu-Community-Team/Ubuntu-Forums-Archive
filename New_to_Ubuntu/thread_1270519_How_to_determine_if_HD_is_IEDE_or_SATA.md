---
title: "How to determine if HD is IEDE or SATA"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-19
I went to buy a 1 terabyte HD today and did not know if I needed IEDE or SATA.  How do I determine which is needed from Ubuntu

---

### Post by misfitpierce on 2009-09-19
It depends on your hardware inside computer... If its internal and your asking how to know if you need a IDE or SATA harddrive depending on what plugins your computer handles basically look at the harddrive in your computer and if its a big flat cable its IDE... If its a small little cable its SATA. IDE is the ugly fat and flat cable that goes into HDD. The pic below is IDE... Can also check the specs on your mobo to see whats supported etc.

[IMG]http://www.gshop.com.au/images/ide_133_cable.jpg[/IMG] = IDE

---

### Post by gordintoronto on 2009-09-19
from terminal, enter the command:

lspci

and look for SATA in the output.  If it appears, your motherboard supports SATA, so you can buy an SATA HD.  If not, you must buy the older IDE drive.

---

### Post by ankspo71 on 2009-09-19
Hi,

I don't know how to find out from within Ubuntu. (sorry) My computer's motherboard and case are capable of both ide and sata hard drives. It's a custom built computer btw. 

If you look inside your computer, IDE uses the flat cables, which should be about something like 2.5 inches wide (and very flat like a ribbon). SATA drives uses cables that are about the size of USB cables, but uses different connections of course. Your hard drive(s) might also say what they are right on their labels.
 
See google images for "sata cables", "IDE cables".

Oops , I see someone has beat me to the picture comparison thing.

hope this helps.
James

---

### Post by mjp29 on 2009-09-19
> **gordintoronto said:**
> from terminal, enter the command:

lspci

and look for SATA in the output.  If it appears, your motherboard supports SATA, so you can buy an SATA HD.  If not, you must buy the older IDE drive.

I'll get into opening the box and looking at it soon.

From terminal I get the below  (so is it safe to assume it is only IDE hard drive)

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet (rev 03)
michael@michael-desktop:~$

---

### Post by Paqman on 2009-09-19
> **mjp29 said:**
> I went to buy a 1 terabyte HD today and did not know if I needed IEDE or SATA.  How do I determine which is needed from Ubuntu

Either should be fine. All motherboards produced in recent years have had ports for both. SATA is the modern standard, but unless you're using a SSD won't be any faster than IDE. It just has thinner cables and you don't need to mess about with jumpers if you have multiple drives.

Tbh, I think you'd probably struggle to find a 1TB drive in IDE anyway.

---

### Post by mjp29 on 2009-09-19
ok thanks

what size drive can my system accept  (or how large of ide drives do they sell)

i know my old Mac g4 cube could only take up to around a 120 gig drive (without assistance with 3rd party software)

---

### Post by Paqman on 2009-09-19
Looks like the biggest IDE drives you can find easily are 500GB. You can get 1TB or bigger SATA drives though.

Max size for any partition formatted ext3 is 2TB, I believe (ie: 2000GB), i'm not sure if there even are drives that big yet. If you went for ext4, you could install a drive up to 1,000,000,000GB. They _definitely_ don't make those yet ;)

---

### Post by mjp29 on 2009-09-19
ok, i was looking on newegg for a seagate and could only find a 400 gb recertified drive.  Would like to get a Seagate - will keep looking - thanks

but as far as anyone knows, there isn't a restriction of how large an ide drive that unbu can recognize is there

---

### Post by Paqman on 2009-09-19
> **mjp29 said:**
> 
but as far as anyone knows, there isn't a restriction of how large an ide drive that unbu can recognize is there

Nope. If it's a properly formatted filesystem, Ubuntu will happily use it.

---

### Post by mjp29 on 2009-09-19
ok thanks

by the way - where does one click to mark these threads as solved?

---

### Post by ankspo71 on 2009-09-19
Hi
The thread solved option is located in "Tread Tools", right above your original post. 
Ahh, apparently on the second page too.
James

---

### Post by halitech on 2009-09-19
> **mjp29 said:**
> ok, i was looking on newegg for a seagate and could only find a 400 gb recertified drive.  Would like to get a Seagate - will keep looking - thanks

but as far as anyone knows, there isn't a restriction of how large an ide drive that unbu can recognize is there

there's no limit on the size that Linux can see and use but you need to confirm the size that your motherboard will support. Kinda useless to get a 500gig drive if the motherboard will only support say 137gig.

---

### Post by mjp29 on 2009-09-19
anyway to determine size motherboard will support through ubuntu or do i have to look at the computers specs online from the manufacturer

---

### Post by halitech on 2009-09-19
I think you will need to find out what board you have and check the manufacturer to find out.

---

### Post by mjp29 on 2009-09-19
ok thanks

if anyone knows a command line that i could type into ubuntu to determine this then please share

if not i will look up specs on hp website  (i'm using an older pentium 4 hp-compaq box for Ubuntu)

---

