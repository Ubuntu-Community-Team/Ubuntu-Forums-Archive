---
title: "madwifi"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by Branta on 2006-11-04
Edgy with D-Link DWL-G630 wireless card.

WIFI worked on dapper but fails on edgy.

How do I **SIMPLY** install madwifi?

Is there a **_.deb package_**.

I have downloaded: ```
madwifi/madwifi-0.9.2.tar.bz2
```
'INSTALL' says to 'make' from the extracted directory but I get errors.

Is there a simple **_madwifi install,deb package, or instructions_**?

--- Bob ---

---

### Post by wieman01 on 2006-11-05
According to this thread, you need to install "ndiswrapper" and use the Windows driver. There seems to be a problem with Edgy & madwifi...

[http://www.ubuntuforums.org/showthread.php?t=290231]("http://www.ubuntuforums.org/showthread.php?t=290231")

---

### Post by spd106 on 2006-11-05
Madwifi is in the linux-restricted-modules package. If you did a clean install from the alternative cd then this isn't installed by default (a known bug).

The new driver in edgy is the latest madwifi-ng 0.9.2 as far as I can tell, but it doesn't contain the extra tools i.e. wlanconfig etc. It will create both a wifi0 and an ath0 interface, though you only need to configure ath0.

I would suggest that you try madwifi from the above package first, then compile your own, for that you will need to download the kernel headers, build-essential etc. There is an older wiki guide for dapper that should still work on edgy.

If you can't get it working then go to ndiswrapper + windows driver as a last resort.

---

### Post by wieman01 on 2006-11-05
Nice "ndiswrapper"guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

You need to blacklist the madwifi driver if you use "ndiswrapper"...

---

### Post by Branta on 2006-11-06
I went back to Dapper and will wait until Edgy produces a product as good as it.

Thank you for your interest, help and trouble.

WIFI is working fine on Dapper.

--- Bob ---

---

### Post by wieman01 on 2006-11-06
> **Branta said:**
> I went back to Dapper and will wait until Edgy produces a product as good as it.

Thank you for your interest, help and trouble.

WIFI is working fine on Dapper.

--- Bob ---
I think that's the right decision. Edgy is experimental, Dapper is the current stable release of Ubuntu. :-)

---

### Post by mikkelwe on 2006-11-22
FYI edgy has been the current stable release since october.
"The product" is just as good or better than dapper though you may need to install restricted-modules yourself after installing if you use the alternate cd by placing the cd in the drive and typing sudo apt-get install linux-restricted-modules-$(uname -r) and reboot.

---

### Post by FrodoB on 2006-11-22
Several folks have had the experience of installing from the Alternate CD for Edgy Eft and many wireless devices just work out of the box, and then after installation they disappear. This is a problem especially if you do not yet have internet access. 

Here is the procedure for getting wireless back after and install from the Alternate CD for Edgy, even with internet access:

1) Have the Alternate CD ready for use.

2) Open a terminal command prompt and type the following:

$ sudo apt-get install linux-restricted-modules-`uname -r`

The system should present a prompt asking you to insert the install CD, put it in the CD driver that you used for installation and then press enter. 

Apt will find the .deb archives and install them for you. A reboot should result in a system that now sees the cards that worked during the install.

---

### Post by rvickers on 2006-11-22
Yep, I fought battle after wireless battle with edgy and finally loaded Dapper and happy I did. I still have to manually config for static ip & WEP at work and dhcp at home but I have no disconnects in ether place. :D

---

### Post by kent41 on 2006-11-23
> **rvickers said:**
> Yep, I fought battle after wireless battle with edgy and finally loaded Dapper and happy I did. I still have to manually config for static ip & WEP at work and dhcp at home but I have no disconnects in ether place. :D

I use a Toshiba M35X-S111 and I use Edgy and a D-link DWL-G630 and don't have any problems. I have not used ndiswrapper or anything else. The DWL-G630 also worked with Breezy with no problems.

I guess my question is why would you use ndiswrapper what is the advantage other than using the System > Administration > Networking setup ?

---

