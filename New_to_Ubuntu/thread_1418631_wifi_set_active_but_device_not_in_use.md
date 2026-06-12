---
title: "wifi set active but device not in use?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by baron76 on 2010-02-28
Can't get my wifi connection to work using Ubuntu 9.10 on my HP TouchSmart tx2.

So far I have run the update manager and installed the Broadcom driver one of the two and set it active. After reboot it reads driver set active but not in use??? Still not able to connect. Also wifi radar shows no connections. 

Card using: Broadcom 4322AG

Bluetooth works fine which is part of the same card I believe.

How do I get it to use the device?

---

### Post by redbook4574 on 2010-03-01
> **baron76 said:**
> Can't get my wifi connection to work using Ubuntu 9.10 on my HP TouchSmart tx2.

So far I have run the update manager and installed the Broadcom driver one of the two and set it active. After reboot it reads driver set active but not in use??? Still not able to connect. Also wifi radar shows no connections. 

Card using: Broadcom 4322AG

Bluetooth works fine which is part of the same card I believe.

How do I get it to use the device?

Install backports and wireless backports may help.

---

### Post by baron76 on 2010-03-02
Thank you for the hint, but can you provide more detail I can not locate any information on backports. Beginner as you can see.

CG

---

### Post by coffeecat on 2010-03-02
The backports packages won't help. The problem is that, for licensing reasons, the Broadcom firmware can't be included in a default installation.

> **baron76 said:**
> So far I have run the update manager and installed the Broadcom driver one of the two and set it active.

I presume you mean the bcmwl-kernel-source package, which gives you the STA driver. Is that right? According to [this community page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), you should just need to restart the machine for that to work.

But if you scroll down lower, you'll come to an alternative. Install the b43-fwcutter package (you can do this from Synaptic - you don't have to use the command line), and that will extract the firmware for you from a downloaded file.

---

