---
title: "No WiFi after kernel update"
date: 2017-05-02
forum: Networking &amp; Wireless
---

### Post by xinuzi on 2017-05-02
Kernel and other updates have been coming in at lightning speed,
until,

linux-image-4.4.0-77,

No WiFi!

---

### Post by lisati on 2017-05-02
Which version and flavour of Ubuntu are you running?

---

### Post by xinuzi on 2017-05-02
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

---

### Post by vasa1 on 2017-05-02
> Make the title of your thread meaningful and concise. For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you.From #4 in [Suggestions on how to get your support questions answered as quickly as possible]("https://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by wildmanne39 on 2017-05-02
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

*Thread moved to **Networking & Wireless**.*

---

### Post by ajgreeny on 2017-05-03
There is a current bug about this related to that kernel version which was posted only yesterday
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623)

Try booting to a previous kernel from grub and you will, hopefully, get back your wifi.
I will be very surprised if a new kernel version does not appear very soon now this problem has been noted by several people.

---

### Post by carlo8 on 2017-05-03
You can solve by booting to a previous version of the kernel via grub, and using

```

sudo apt-get update && sudo apt-get dist-upgrade

```

Worked for me.

---

### Post by xinuzi on 2017-05-03
Fixated working kernel with:

```

sudo apt-get purge linux-generi* linux-image-generi* linux-headers-generi* linux-signed-generi* linux-signed-image-generi*

```

and with:
```

sudo apt-get purge linux-generi* linux-image-generi* linux-headers-generi*

```

My Dear Ubuntu :P

---

### Post by xinuzi on 2017-05-08
Installed 

linux-image-4.10.0-20-generic
linux-image-extra-4.10.0-20-generic

kernel-images with Synaptic in the meantime.

Everything pico bello okay!

---

