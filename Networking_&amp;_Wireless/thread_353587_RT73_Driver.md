---
title: "RT73 Driver"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by Mavvy on 2007-02-04
Just setup my old pc with ubuntu 6.10 alternate.. Finally managed to get it installed on gfx portion especially with my old old 3dfx card.
running only 640x480 resolution since higher will hung during xwindow exit.

I guess most of us have problems making RT73 wifi driver..

I read almost every single links I can find via google/ubuntu/linux forums for instructions..

Some recommend debian, some recommend direct from ralink..

There is 1 particular instruction where we need to download the kernel headers..
Instructions from [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC?highlight=%28wusb54gc%29](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC?highlight=%28wusb54gc%29)

**sudo apt-get install linux-headers-`uname -r` **

but without wifi/ethernet link to internet ( presume only wifi router exists ) .. there is no way we can do that.. Has anybody done offline installation for RT73 driver without much hiccups ?

I'm having WUSB54GC ( LinkSys 802.11g USB )

Thanks in advance if you have answers.

---

### Post by p!=f on 2007-02-04
You may try the package (built for Dapper) found here
[http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/](http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/)

You will need to download the package from another computer and get it on yours, though. 
I'm not sure but I think kernel-headers could be found on installation DVD.

---

### Post by Mavvy on 2007-02-04
Try the debian method also..

don't seems to work..

have spent 5 days just to get this WUSB54GC working but doesn't.. ha..

or anybody using the same with compiled rt73.ko and it works? can send me that file.. I only need that..

---

### Post by Mavvy on 2007-02-06
Hi fellas,

Thanks for any help rendered.. I managed to get it up and running fine now...
Woohoo !!

---

### Post by nibsa1242 on 2007-02-08
Please share what you did to make it work. Others could benefit from your knowledge.

---

### Post by Mavvy on 2007-02-08
I simply follow the steps from

[http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/](http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/)

I only download the module-assistant from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install it with debi packager before starting any compilation.

FYI , I installed on a fresh 6.10 Ubuntu alternative (edgy) installation

---

