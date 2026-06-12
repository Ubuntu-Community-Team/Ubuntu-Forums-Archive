---
title: "Linksys Wireless G"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by MarkLori on 2007-02-13
I've got a Linksys wireless G model WPC54GS ver 2 in my Dell Latitude c640.  This was working fine until the recent kernel update went through. 
  
  I found that the files were no in the /lib/firmware/2.6.17-11-generic directory.  I redid the fwcutter extraction and modeprobe bcm43xx and rebooted.  

  The network showed up but I could not use it.  For some reason I can show signal strength, but am unable to connect through eth1.  Firestarter will not start either, saying that eth1 is not ready.  

  When I bring up the network manager, eth1 shows that it is active.  I just can't seem to use it for anything.  :confused: 

All help is MOST appreciated.  

Mark

---

### Post by MarkLori on 2007-02-13
After sitting for a half an hour it seems to have started working.  Don't know why.

---

### Post by jvonmitchell on 2007-12-20
Mark,
      How did you get your wireless card going.  Mine doesn't seem to work.

---

