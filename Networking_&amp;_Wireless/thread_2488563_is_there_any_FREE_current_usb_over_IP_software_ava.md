---
title: "is there any FREE current usb over IP software available?"
date: 2023-07-08
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2023-07-08
I need to share a USB camera from a windows 10 computer over IP in such a manner that it looks like it is a local USB camera for use in lightburn software. The only options I can find are the USB/IP Project which seems REALLY outdated and confusing; USB Network Gate; and FabulaTech USB Over Network - the latter two being expensive. I appreciate it.

---

### Post by ian-weisser on 2023-07-08
USBIP is still maintained -- it is not outdated at all. 

If found it easy to use and reliable when I used it for several years.

Some of the independent documentation grew stale when USBIP was incorporated into the Linux kernel. So install instructions may be out of date (depends where you are looking), but usage is the same.

Not much demand to duplicate kernel features outside the kernel.

---

### Post by rebeltaz on 2023-07-09
> **ian-weisser said:**
> USBIP is still maintained -- it is not outdated at all. 

If found it easy to use and reliable when I used it for several years.

Some of the independent documentation grew stale when USBIP was incorporated into the Linux kernel. So install instructions may be out of date (depends where you are looking), but usage is the same.

Not much demand to duplicate kernel features outside the kernel.

The download section ([https://usbip.sourceforge.net/#download](https://usbip.sourceforge.net/#download)) doesn't offer any downloads, it just says 

```
 For Linux, the source code of usbip was merged into the staging tree, and finally has been moved to the mainline since Linux-3.17. Development is ongoing in the kernel community, not here. Linux distributions will provide binary packages of usbip. Just for historical records, the project page keeps old download files of the Linux version. Do not use them. 
```

Further down, there is a "README for Linux." Clicking on that gives me instructions on how to install it, but there is no reference to where to actually GET the files. If I click on "Files" on the tabs bar at the top of the project, it offers a "Download Windows Version" button, but nothing for linux. Scroll down and there are links to "usbip_windows"; "usbip"; and "usbip-obsolete". The last modification to those directories are 2011-06-10, 2009-07-10 and 2005-01-19 respectively. 

If there is a more up to date source, I'd appreciate a link. 

When you say that it was incorporated into the linux kernal, what exactly does that mean? That it's already available under Ubuntu natively? I'm not really kernal savvy, so...  ¯\_(&#12484;)_/¯
 

Thanks.

---

### Post by Holger_Gehrke on 2023-07-09
Here's a nice [article in linux-magazine]("https://www.linux-magazine.com/Issues/2018/208/Tutorial-USB-IP") from 2018 that explains how to use USB/IP. Since it's part of the Kernel, all the basic parts - kernel modules - are already on your system, but you might need to install some tools to make use of the modules ('linux-tools-common'  seems to be the package). For the Windows side of your problem, the first answer to [this question on superuser.com]("https://superuser.com/questions/1720705/a-cross-platform-way-to-share-a-usb-device-over-a-network") seems relevant.

Holger

---

### Post by ian-weisser on 2023-07-09
Here's a blog post I made when I began using USBIP back in 2019: [https://cheesehead-techblog.blogspot.com/2019/08/experimenting-with-usb-devices-across.html](https://cheesehead-techblog.blogspot.com/2019/08/experimenting-with-usb-devices-across.html)

It should get you most of the way. The key is to not follow commands blindly. Understand each command in each step, and why it's needed.

I stopped using USBIP about a year ago. Nothing wrong with it -- my usage of remote USB devices changed.

---

### Post by rebeltaz on 2023-07-09
> **Holger_Gehrke said:**
> Here's a nice [article in linux-magazine]("https://www.linux-magazine.com/Issues/2018/208/Tutorial-USB-IP") from 2018 that explains how to use USB/IP. Since it's part of the Kernel, all the basic parts - kernel modules - are already on your system, but you might need to install some tools to make use of the modules ('linux-tools-common'  seems to be the package). For the Windows side of your problem, the first answer to [this question on superuser.com]("https://superuser.com/questions/1720705/a-cross-platform-way-to-share-a-usb-device-over-a-network") seems relevant.

Holger

> **ian-weisser said:**
> Here's a blog post I made when I began using USBIP back in 2019: [https://cheesehead-techblog.blogspot.com/2019/08/experimenting-with-usb-devices-across.html](https://cheesehead-techblog.blogspot.com/2019/08/experimenting-with-usb-devices-across.html)

It should get you most of the way. The key is to not follow commands blindly. Understand each command in each step, and why it's needed.

I stopped using USBIP about a year ago. Nothing wrong with it -- my usage of remote USB devices changed.

The superuser answer seems to be looking for windows client, I believe. I do have usbip-win downloaded already, though.

Thank you both for all this information. I will study this tonight and hopefully figure it out. I really appreciate it!

---

