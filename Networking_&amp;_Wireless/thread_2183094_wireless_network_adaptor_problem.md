---
title: "wireless network adaptor problem"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by htbmHJ4 on 2013-10-23
Hi everyone, 
this is my first post here so please be nice, i have installed backtrack5r3 on my win7 laptop using using VM virtualbox,  I have no problem as such with the use of it but no matter what i do i cannot get it to recognise my wireless adaptor,i'm using a TP Link TL-WN725n v2, it has the **Realtek** RTL8188EUS chip set. I have been to devices and added it to my network under bridged adaptors and also in the usb section but what ever i do i cannot make it get recognised. It works fine when i'm not in the vm box environment but as soon as i try to use it on backtracks....nothing. Am i doing something wrong ? and is their anybody that could guide me through trying to get it working,thanks in advance for any imput.
Thanks in advance Matt.

---

### Post by varunendra on 2013-10-25
Hi Matt, Welcome to the forums ! :)

> **htbmHJ4 said:**
> I have been to devices and added it to my network under bridged adaptors and also in the usb section but what ever i do i cannot make it get recognised.

Do you have "Guest Additions" and "Virtualbox Extension pack" installed? Without the Extension pack, you can not have USB2 support within a virtualbox VM, so won't be able to use any USB device in it (probably legacy USB 1.1 devices would work, but that doesn't matter here).

As for 'bridging' the USB, it means you are using the USB in the host, and the guest (VM) is talking to it 'through' its 'virtual' adapter which is an ethernet adapter. A virtual machine can 'see' only the virtualised hardware that the platform (virtualbox in this case) presents to it. Only USB devices can be directly seen by a guest OS and USB support in virtualbox is added only via installing Extension Packs. These packs can be downloaded from VirtualBox's official site, just make sure you download the version suitable to your version of VirtualBox.

If this doesn't help, post back the problem. Or if I am not understanding your problem correctly, please elaborate on it.

---

### Post by ddeogratus on 2013-10-25
i have the same problem on Windows 7 VM

---

