---
title: "Ralink RT5390 not being seen in hardware"
date: 2019-05-11
forum: Networking &amp; Wireless
---

### Post by d-pc-user on 2019-05-11
Product: Pavilion p7-1207c       
                Operating System: Ubuntu 18.04.2 LTS

     
                                                                                                                                                                    System is setup to switch between Windows 7,  Windows 10,  and  Ubuntu by hardware switch selecting which disk drive to boot from.  All OSs are up to date.

  About a year ago I entered commands  under UBUNTU to turn off the Ralink RT5390 so it wouldn't try to connect  when network cabled.  I got the commands from a Ubuntu post on the Internet.  Unfortunately I did not save a link to the original post.

The RT5390 was turned off and did not appear on  any of the OSs.  I want to move the computer to a location where I will  need the wireless connection.  I cannot find the instructions that I  found on the Internet to turn off RT5390 and restart it.  The RT5390  does not show up in any of the OS hardware configurations when I look at  "Control Panel - System - Device Manager - Network Adapters" .   I have  removed the RT5390 from the Motherboard and rebooted the system, then  reinstalled it and rebooted the system to see if the BIOS and system  would recognize it, but still not seen by any of the OSs.  Does anyone  know how to turn the RA5390 back on?

I installed "pastebinit", executed the wireless-info and have included the wireless-info.txt as an attachment
 

Thank you
d-pc-user

---

### Post by praseodym on 2019-05-12
Check the BIOS settings. If it is a real BIOS -and not an UEFI system- reset it to default

---

### Post by d-pc-user on 2019-05-13
praseodym,

Thank you for the suggestion, this is what I did prior to posting the request for help on this forum.

I reset the BIOS and booted the system, no change.
I disabled the mini card slot in the BIOS, booted the system; shut dow, then enabled the mini card slot in the BIOS and booted the system, still no change.
I removed the RT5390 than booted the system.  Installed the RT5390 than booted the system.  The RT5390 does shot show up in any of the OS's.

It's interesting that someone provided instructions on how to turn off the RT5390 in Ubuntu, which made it invisible to all three OSs, but now can't find a way to turn it back on.

d-pc-user

---

### Post by praseodym on 2019-05-14
Windows is still available? Check a BIOS update, if available

---

### Post by d-pc-user on 2019-05-15
There is no BIOS update available, and HP doesn't provide a copy of the installed BIOS for re-installation.

---

