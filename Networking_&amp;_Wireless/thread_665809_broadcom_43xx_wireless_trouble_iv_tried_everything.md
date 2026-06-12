---
title: "broadcom 43xx wireless trouble iv tried everything! i think"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by templa edhel on 2008-01-12
i have had ubuntu for about 2 weeks on my dell inspiron e1505. when i first go it i used the restricted drivers manerger to instal the firmare for my card. tht worked ok... i couldnt get wireless upstairs(awya from router) but i could sort of live with tht. but now its cut out comletely!!! i have no idea what to do! iv tried every guide i could find and even reinstalled ubuntu! nothing works, il get wireless sometimes after i do something for like a minute then it stops again(signal meter still says its getting wireless) i know its my computer because i have another laptop right next to it and it works. im a linux noob and so i could benifite from Very detailed walkthoughs or w/e. thanks for any help:)

---

### Post by ios_base on 2008-01-12
Im in the same boat man... I don't know what to do.  This problem is supposed to be automatically resolved.  It's supposed to be as easy as going to the restricted driver menu and click a checkbox.  But NO!  Things have to be twisted!  I have a bcm4310 wireless card and my restricted driver menu doesn't list it.  Ndiswrapper told me bcmwl5 is the incorrect driver when I typed "ndiswrapper -l" 

I wish I could help, but I'm just as lost.  Send me a message if you find something that worked for you.

---

### Post by dicecca112 on 2008-01-12
Could be one of two problems.  I have noticed that the lastest network-manager update killed my wireless.  revert back to the previous package and it should work.  If it doesn't try this deb.  I use this to install my wireless and it works flawlessly,

---

### Post by rustybronco on 2008-01-12
> **ios_base said:**
> Im in the same boat man... I don't know what to do.  This problem is supposed to be automatically resolved.  It's supposed to be as easy as going to the restricted driver menu and click a checkbox.  But NO!  Things have to be twisted!  . using the restricted drivers and having them downloaded and installed by the restricted driver manager, and a ndiswrappper install+the windows drivers for your device are two different things. sounds like you tried a few different methods to try to get your device to work...

I don't know if it will work but give these directions a spin. [http://ubuntuforums.org/showpost.php?p=3749742&postcount=4](http://ubuntuforums.org/showpost.php?p=3749742&postcount=4)
let me know if it worked.

---

### Post by templa edhel on 2008-01-12
i actually fixed it by going to the restricted drivers manerger and clincking enable but when it asks where to get it from, i navigate to my home folder (where i have the windows bcmwl5.inf and bcmwl5.sys and click on the bcmwl5.sys. then it works just as well as windows. thanks though.

---

### Post by brunoscunha on 2008-02-21
> **dicecca112 said:**
> Could be one of two problems.  I have noticed that the lastest network-manager update killed my wireless.  revert back to the previous package and it should work.  If it doesn't try this deb.  I use this to install my wireless and it works flawlessly,

Does it works with BCM 4312?

>  Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1371
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e4000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0


---

