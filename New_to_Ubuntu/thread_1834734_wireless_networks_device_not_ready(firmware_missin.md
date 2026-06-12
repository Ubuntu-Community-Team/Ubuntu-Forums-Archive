---
title: "wireless networks: device not ready(firmware missing)"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by ankit prashar on 2011-08-28
hi,
Recently i've updated my UBUNTU from 10.10 to 11.04, nd in both of the formats i was 

having the same problem with my network wireless.

I m having problems with my wireless connection,i've read some one else's posts nd it 

asks to do some command work: it may help you knowing the problem

 lspci -vnn |grep 14e4

the lspci commands says:

03:00.0 network controller [0280] : Broadcom corporation BCM4312 802.1lb/g LP-PHY

[14e4:4315] (rev 01)

hopefully it does not sounds foolish to you:]

if i do need to do some thing plz suggest

please help,itz getting onto my nerves:@ 

thanks for any suggestion:)

---

### Post by anewguy on 2011-08-28
If you can connect via a hard-wired connection to your router, do so.  Then do the following:
[LIST]
[*]open a terminal window 
[*]type: sudo apt-get update <press enter>
[*]wait for the above to complete
[*]go to system/administration/additional drivers (may be called something different if you are using the Unity desktop).  This should run for a while and connect to the net to try to download drivers.
[*]when the above finishes, if there is a driver shown that is for your wireless but is not enabled, try enabling it.
[/LIST]

---

### Post by gandaran on 2011-08-28
> 03:00.0 network controller [0280] : Broadcom corporation BCM4312 802.1lb/g LP-PHY
and if by any chance the driver enabled from additional drivers still doesn't work (sometime happens) you can follow this thread to install the right firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by anewguy on 2011-08-28
> **gandaran said:**
> and if by any chance the driver enabled from additional drivers still doesn't work (sometime happens) you can follow this thread to install the right firmware
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Thanks for posting that link!  I've used it before to get a 4306 working using the "all" firmware package, and I wanted to post a link but I couldn't find the thread!  So....THANKS!!

Dave ;)

---

