---
title: "Ubuntu 10.04/Broadcom 4311....NO INTERNET!!"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Mike.Flintjer on 2010-05-09
I installed Ubuntu 10.04.  Booted up.  Tried to go online....no go.

Drove around the forums for about 3 hours, doing everything i could find that i thought was relavent to my situation...i think i managed to install ndiswrapper and the drivers for the broadcom 4311 wireless card onboard my old computer.  I even get this from the ifconfig...

Link encap:Ethernet HWaddr 00:1bblahblahblah
inet6 addr: blahblahblah/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets 209 errors:0 dropped:0 overruns:0 frame:0
TX packets 16 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txquelen:1000
RX bytes:27400 (27.4 KB) TX:bytes:2368 (2.3 KB)
Interrupt:19 Base address:0xa000

and yet Firefox will not connect to the internet...AT ALL...while it's hardwired!!

Something in those lines is telling me that the internet is actually  working...but i can't get online while i'm hard-wried to the  router...and the other computer (the one i am typing this from) is  hooked to the same router, at the same time, and running just fine....

Can someone put together a tutorial with pretty pictures showing me exactly what I am doing wrong??  I am on a different computer typing this, and it is tied to the same router and works just fine.  Why won't FF get online for me??

---

### Post by micmon on 2010-05-09
I had the same problem. I installed 10.4 and Firefox did not access the Internet. I was able to access the Internet using Update Manager and the Synaptic Package Manager -- but I could not browse using Firefox. I have since rolled back to 9.04, but I'm hoping to re-install 10.04...

---

### Post by Mike.Flintjer on 2010-05-09
I wish I could get online with the update manager!!  Can't even do that...i may go find a 9.0 version and get rid of this piece of crap 10.04...

---

### Post by cariboo on 2010-05-09
Did either of try installing the driver from System->Administration->Hardware Drivers?

---

### Post by micmon on 2010-05-09
Yes -- the only driver that came back was for my graphics card. By the way, I access the Internet via a DSL modem. So I don't believe that my problem is identical to the original post because I can use the Update Manager and the Synaptic Package Manager but the original post-person can't.

---

### Post by Old Codger on 2010-05-09
I've experimented with Linux OS a few times. My first experiment was with RedHat. I hated it, but liked the idea of an open source, free OS.  I'm not a geek, developer, or programmer; I'm just looking for a good, reliable desktop OS as an alternative to Windows and Mac. I've been running Mac OS 10.6 on my MacBook and wanted to try Ubuntu. After partitioning the drive and installing Ubuntu 9.10 successfully, I was satisfied that most, if not +90%, worked "out of the box."

This evening, I made the mistake of downloading and installing Ubuntu 10.04 LTS. What a mistake! Now, little works as Iexpected and I've lost all my settings. I can't connect to the internet and I have no patience to reinstall 9.10 and recreate, so I'll uninstall Ubuntu. So much for Linux--in retrospect, I think SUSE was better--but it's a shame that with all the talent out there in the Linux world, you folks can't develop a truly user-friendly desktop alternative OS to Windows and Mac. You folks came close, but no cigar. 

Sorry, but I have better things to do with my time than to figure out work around installing your OS and apps.

---

### Post by Mike.Flintjer on 2010-05-10
Well, I am closing this thread...at least I am letting you all know that I have gotten my problems solved.  And here is the link to the solution.

[http://ubuntuforums.org/showthread.php?t=1390979&page=3](http://ubuntuforums.org/showthread.php?t=1390979&page=3)

Don't worry, the link is here on the forums, and not off-site -- wouldn't do that.  Regardless, the instructions by themselves do not work fully...i had to install all the stuff from the Synaptic repositories that had ANYTHING to do with networking/WLAN and anything I thought might be helpful....including the entire ndiswrapper stuff...including ndisgtk....what can it hurt...

---

### Post by Kafubie on 2010-05-10
Can you use ethernet from your desktop or anything???
I think it is as easy as updating from the Update Manager.:idea:

---

### Post by Mike.Flintjer on 2010-05-10
> **Kafubie said:**
> Can you use ethernet from your desktop or anything???
I think it is as easy as updating from the Update Manager.:idea:
I have fully working wireless Broadcom BCM4311 WLAN card...operational.  Have not tried hard-wiring...but if my wireless is working, not in a hurry to test the hard-wire ethernet port...but i will test it and fix accordingly ;)

---

