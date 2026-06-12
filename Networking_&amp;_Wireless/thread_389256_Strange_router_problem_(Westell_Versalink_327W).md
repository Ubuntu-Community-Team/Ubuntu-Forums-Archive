---
title: "Strange router problem (Westell Versalink 327W)"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Tab on 2007-03-20
I'm having an odd problem with wifi here. For some reason, Ubuntu (Edgy) refuses to connect to my Westell Versalink 327W wireless router. It is an open network, Windows and OS X both connect fine, and Ubuntu can connect to other nearby wireless routers with no problems. It is only when trying to connecting to this router that I experience problems. Specifically, trying to connect with ifup results in many DHCP connection tries, and finally gives up with no DHCP offers recieved. Has anyone had any similar problems and found a solution? Ideas? I can't for the life of me figure this one out. Thanks in advance.

---

### Post by Last User Name Available on 2007-04-01
Same problem here on a ThinkPad T42 with Atheros card. Using Windows, i can connect to the router; in Linux, I can connect to any other access point except the Westell 327W. Verizon tech support was no help. Time to get a new DSL router.

---

### Post by Luigi Boccabella on 2007-04-02
I had the exact same problem with my Verizon DSL, here's how I solved it. 

1) Downloaded the latest firmware for the 327W here: 

[http://download.verizon.net/webdownload/firmware/upgrades/westell/A90-327W15_VER_03_02_01.exe](http://download.verizon.net/webdownload/firmware/upgrades/westell/A90-327W15_VER_03_02_01.exe)

2) Removed an IPSEC ALG entry that was in the routers custom-defined services list.

I'm not sure if both of these were necessary but I can now connect running the Feisty Beta. If you have a different version of the 327W you might find the proper firmware here, but proceed with caution:

[http://www.fastaccess.drivers.bellsouth.net/#westell](http://www.fastaccess.drivers.bellsouth.net/#westell)

---

### Post by ablakefl on 2007-08-02
I am having a similar strange problem since I got a new westell versalink 327w router from att.  I used to have a linksys wrt54g that worked great with linux/wireless  (currenty on Feisty).I have an older Dell Latitiude x200 that I had setup with a dual boot XP/Kubuntu Edgy that was working great until I switched routers, now it can't get a dhcp ip assigned under linux.  I have since upgraded to feisty, but that didn't make a difference.  The weirdest part is that if I boot the laptop  under the livecd (both feisty and knoppix), the wireless works fine if I have security disabled.  If I boot up from the hard disk, it doesn't work at all.  I have tried updating the firmware, but I am already at the latest version.  I also deleted the custom service per the above suggestion, but to no avail.  Has anyone else solved a similar westell router issue?

Andy

---

