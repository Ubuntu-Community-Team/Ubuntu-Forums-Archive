---
title: "New NIC drivers for Attansic L2 Fast Ethernet"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Master Chief on 2008-07-08
Good news fellow Ubuntu users!

Below you'll find the latest (and most importantly working) modules for your Attansic L2 NIC (this is a must have for Asus P5GC-MX/1333 owners):

[http://ubuntuforums.org/attachment.php?attachmentid=76942&d=1215557395](http://ubuntuforums.org/attachment.php?attachmentid=76942&d=1215557395)
[http://ubuntuforums.org/attachment.php?attachmentid=76945&d=1215560263](http://ubuntuforums.org/attachment.php?attachmentid=76945&d=1215560263)
[http://ubuntuforums.org/attachment.php?attachmentid=76946&d=1215560287](http://ubuntuforums.org/attachment.php?attachmentid=76946&d=1215560287)

I have compiled both modules with Ubuntu 8.04.1 (2.6.24-19-generic) on two different computers, one 32 bit and the other a 64 bit system.

I personally verified the 32 bits module, and I guaranty you that it works here! No BS

Any takers on writing up a how to document?

---

### Post by Naren Munna on 2008-08-07
> **Master Chief said:**
> Good news fellow Ubuntu users!

Below you'll find the latest (and most importantly working) modules for your Attansic L2 NIC (this is a must have for Asus P5GC-MX/1333 owners):

[http://ubuntuforums.org/attachment.php?attachmentid=76942&d=1215557395](http://ubuntuforums.org/attachment.php?attachmentid=76942&d=1215557395)
[http://ubuntuforums.org/attachment.php?attachmentid=76945&d=1215560263](http://ubuntuforums.org/attachment.php?attachmentid=76945&d=1215560263)
[http://ubuntuforums.org/attachment.php?attachmentid=76946&d=1215560287](http://ubuntuforums.org/attachment.php?attachmentid=76946&d=1215560287)

I have compiled both modules with Ubuntu 8.04.1 (2.6.24-19-generic) on two different computers, one 32 bit and the other a 64 bit system.

I personally verified the 32 bits module, and I guaranty you that it works here! No BS

Any takers on writing up a how to document?

--------

Can any one explain me the steps how to install this in (downloaded three files)Ubuntu8.  I am a new user to Ubuntu.  I dont know ABCD in this platform.  I am using ASUS p5gc-mx/1333 board.  I need step by step assistance to connect my bsnl broadband internet.  Thanking you.

---

### Post by lohamanob on 2008-08-26
plz explain the steps for installing the driver:KS

---

### Post by ssj4Gogeta on 2008-10-02
Hi
I downloaded the driver, extracted it to /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko
and ran
sudo modprobe atl2
from the terminal (as told by Master Chief in the other thread).

I still can't see the Ethernet light on my modem turning on. Please guide me.

---

### Post by ssj4Gogeta on 2008-10-04
bump!

it's been more than two months since I've been trying to set up Ubuntu properly without any luck... :( Please help if you can.

---

### Post by ssj4Gogeta on 2008-10-07
As I explained above it wasn't working. So I downloaded the source and untared it to /usr/local/src. I'm a complete Linux newbie so I don't know how to compile. I searched wherever I could and I found that I have to use "make" and then "sudo make install". "make" ran fine. then when i typed "sudo make install" it said something like "*** No rule to make target 'install'. Stop."

What am I doing wrong? Please help me. I thought I'll try "sudo make atl2" but it gave me a huge list of errors. Looking forward to replies. Thanks.

---

### Post by jeduffey on 2008-10-24
Any updates on this situation? I'm having the same problem. Without the NIC driver, I'm dead in the water.

---

### Post by ssj4Gogeta on 2008-10-25
> **jeduffey said:**
> Any updates on this situation? I'm having the same problem. Without the NIC driver, I'm dead in the water.

Hi
I downloaded the beta of the new version of Ubuntu (Intrepid Ibex). The Ethernet worked out of the box in it! :) It's just 5 days till the final release. I can finally surf the internet from Ubuntu now (after 2 months of trying different drivers. and being a complete Linux noob didn't help.)

For all the people who are having trouble with Attansic L2 Fast ethernet (especially ASUS P5GC-MX/1333 users):
**It works out of the box in Ubuntu's new version 8.10 Intrepid Ibex, which will be released in 5 days. Download it at [www.ubuntu.com](www.ubuntu.com)** The beta is available now.

---

