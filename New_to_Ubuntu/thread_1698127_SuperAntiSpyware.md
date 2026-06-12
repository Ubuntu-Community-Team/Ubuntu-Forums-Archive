---
title: "SuperAntiSpyware"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-03-01
Hello , I have been experimenting with this program to see if is functional using wine to run it .  It is a little quirky . It will do both quick and full scans .

  It has come up with three Trojans , one in memory  and two  in files .

The program has quarantined  them , but I did not remove them from there as yet . 

  This is the log :  



  SUPERAntiSpyware Scan Log
[http://www.superantispyware.com](http://www.superantispyware.com)

Generated 03/01/2011 at 07:46 PM

Application Version : 4.31.1000

Core Rules Database Version : 6510
Trace Rules Database Version: 4321

Scan type       : Complete Scan
Total Scan Time : 00:18:35

Memory items scanned      : 46
Memory threats detected   : 1
Registry items scanned    : 780
Registry threats detected : 0
File items scanned        : 3794
File threats detected     : 2

Trojan.Dropper/Sys-ExplorerFake
    C:\WINDOWS\SYSTEM32\EXPLORER.EXE
    C:\WINDOWS\SYSTEM32\EXPLORER.EXE

Trojan.SVCHost/Fake
    Z:\USR\LIB\WINE\FAKEDLLS\SVCHOST.EXE



 Anyone have any thoughts on this ??   Good or bad  !


COMPUTIAC

---

### Post by COMPUTIAC on 2011-03-01
> **COMPUTIAC said:**
> Hello , I have been experimenting with this program to see if is functional using wine to run it .  It is a little quirky . It will do both quick and full scans .

  It has come up with three Trojans , one in memory  and two  in files .

The program has quarantined  them , but I did not remove them from there as yet . 

  This is the log :  



  SUPERAntiSpyware Scan Log
[http://www.superantispyware.com](http://www.superantispyware.com)

Generated 03/01/2011 at 07:46 PM

Application Version : 4.31.1000

Core Rules Database Version : 6510
Trace Rules Database Version: 4321

Scan type       : Complete Scan
Total Scan Time : 00:18:35

Memory items scanned      : 46
Memory threats detected   : 1
Registry items scanned    : 780
Registry threats detected : 0
File items scanned        : 3794
File threats detected     : 2

Trojan.Dropper/Sys-ExplorerFake
    C:\WINDOWS\SYSTEM32\EXPLORER.EXE
    C:\WINDOWS\SYSTEM32\EXPLORER.EXE

Trojan.SVCHost/Fake
    Z:\USR\LIB\WINE\FAKEDLLS\SVCHOST.EXE



 Anyone have any thoughts on this ??   Good or bad  !




COMPUTIAC             Some people just don't have anything better to do !

---

### Post by PcMojo on 2011-07-28
I am fixing an XP machine by loading Ubuntu and Wine on so I can run Spybot, Mbam, SuperAntiSpy and others. I noticed the same thing, after just installing linux/wine 5 minutes before, superantispy had that same thing tagged as a trojan. :(  
I don't think it is. Many exploits have used svchost in the past to control Windows and trash the system -- and it is, after all, a fake one. Wine uses fake dll's (like copies of the real windows dll's) and other files to emulate a windows session. (It's in a directory called FakeDlls!) :D  I'm surprise that the different antispyware detectors don't tag more Wine files as being infected. My SAS is still running now, but I don't think I'm going to treat it as a trojan. 

I will say that I am very impressed with Linux's Live Cd's and the ability to repartition the drive and install side by side!. I have yet to have a problem with lost data or functionality during the repartition/install of Ubuntu. Whomever wrote that code rocks! I have about a dozen people's computers I fix on a regular basis and lately I've been putting Ubuntu on all of them. That way when Ms gets totally whacked I can just jump into Linux and start scanning!

---

### Post by Paqman on 2011-07-28
You'll probably have much better luck running a proper Linux antivirus program than trying to run Windows ones through Wine. Avast and AVG both have Linux versions available, they should be able to find any Windows viruses on the machine. There's also an open source package called ClamAV in the Ubuntu repos, but it's not as good. 

You could even run Ubuntu from a Live CD or USB, you don't have to install it to the drive just to clean up a Windows install.

---

### Post by anewguy on 2011-07-28
Depending what you do in Windows in Wine, it will be possible to pick up a Windows virus or trojan.  But remember that for Linux itself, these virus or trojans won't do anything.  At worst, you might hose up your Windows "C" drive, but since that is in Wine, it's actually just a folder itself to Linux.  Remember that the chances of getting anything harmful to Linux is EXTREMELY remote.

---

