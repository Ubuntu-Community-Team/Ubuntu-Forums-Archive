---
title: "New to Linux, unable to connect Ubuntu to wireless networks"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by ARCI-Phase 4 on 2010-01-08
Hi, Im trying Ubuntu for the first time. Loaded up fine, but I cant seem to connect to my wireless network. The network is showing up, as is my wireless USB device (Linksys WUSB600N) but when I enter the WEP code it just keeps asking for again for the code and showing a black disconnected box. Everything works fine on windows machines (which Im trying to escape!) Im using a 2wire 2701HG-B wireless gateway broadcasting from a nearly useless windows PC. Signal strength is maxed out. Ive tried other Linux versions as well (Puppy, PCLinuxOS.) I like Ubuntu best so far, but I cant make the internet work on any of them. Id really appreciate any help as Id love to dump windows all together. I guess i need to go get a Linux book. Thanks!:)

---

### Post by Bucky Ball on 2010-01-08
Have you plugged in an ethernet cable and gotten updates? Plug in an ethernet cable AND plug in your wireless adapter and then update. Also, System->Administration->Synaptics Package manager and search for and install:

ubuntu-restricted-extras

Also, System->Administration->Hardware Drivers after your update. Is anything there for the wireless card but disabled?

---

### Post by ARCI-Phase 4 on 2010-01-08
Thanks. I tried the two searches you suggested. The Synaptics Package manager doest return any hits for ubuntu-restricted-extras. The Hardware Drivers says there are no proprietary drivers in use on the system, and has nothing listed. As for the ethernet cable for updates, Im gonna need to move alot of things around as its on the other side of my house. Do I update drivers on the pc the gateway is connected to, or the one running Ubuntu?

---

### Post by kyuubi777 on 2010-01-08
did you make sure you switched the type of protection to the correct amount.. 128 bit vs. 40 bit etc.?

---

### Post by ARCI-Phase 4 on 2010-01-08
Yep, its set to the 128 bit Key, that was automaticly picked up. I edited the wireless that network to include the code as well.

---

### Post by Bucky Ball on 2010-01-08
Update the pc you are trying to connect wirelessly with. Bit of a catch twenty two situation. The drivers are probably there but because they are restricted/third party/proprietary drivers they can not be included in the Ubuntu install. Therefore to get wireless working you need to update with a cable, be offered the proprietary drivers, and you need to manually accept the conditions of use (as they are not open-source drivers). :)

All about licensing and copyright rubbish.

---

### Post by ARCI-Phase 4 on 2010-01-09
Thanks Bucky, that did it. Your other links to Linux are very helpfull as well.

---

### Post by Bucky Ball on 2010-01-09
Pleasure and good to hear. Hope you enjoy Ubuntu and the learning curve. :)

---

### Post by A4orce84 on 2010-01-17
Can you expand on what you did exactly ARCI-Phase 4 ?

I have the same problem with my WUSB600N adapter in Ubuntu 9.10 =(


Thanks in advance!


--Asif

---

