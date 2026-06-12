---
title: "Intellinet Wireless USB Adapter driver ubunto"
date: 2014-03-23
forum: Networking &amp; Wireless
---

### Post by Med_Ali on 2014-03-23
Hi , I have just bought Intellinet Wireless USB Adapter 150N , I am using ubunto on oracle Virtual Machine ! So , I plug in the USB but it doesn't detect any of the wifis in the area although in windows it does !
[IMG]http://i1068.photobucket.com/albums/u448/Mohamedali_Mtibaa/bandicam2014-03-2310-24-30-740.jpg[/IMG]

[IMG]http://i1068.photobucket.com/albums/u448/Mohamedali_Mtibaa/bandicam2014-03-2310-25-28-740.jpg[/IMG]

what's the problem ? a driver issue or what ?! I need Help ASAP Plz 
Thank you :)

---

### Post by ajgreeny on 2014-03-23
A virtual machine does not use the wireless hardware of your system direct; it uses a virtual NAT connection through from your host, presumably windows in your case.

Can you use the web-browser in ubuntu without problem?

Have you got the Oracle Virtualbox guest additions installed from [http://download.virtualbox.org/virtualbox/4.3.8/Oracle_VM_VirtualBox_Extension_Pack-4.3.8-92456.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.8/Oracle_VM_VirtualBox_Extension_Pack-4.3.8-92456.vbox-extpack) which should help with lots of things in your VM?  If not download it now and install.

---

### Post by Bucky Ball on 2014-03-23
> **ajgreeny said:**
> A virtual machine does not use the wireless hardware of your system direct; it uses a virtual NAT connection through from your host, presumably windows in your case.

Can you use the web-browser in ubuntu without problem?

Have you got the Oracle Virtualbox guest additions installed from [http://download.virtualbox.org/virtualbox/4.3.8/Oracle_VM_VirtualBox_Extension_Pack-4.3.8-92456.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.8/Oracle_VM_VirtualBox_Extension_Pack-4.3.8-92456.vbox-extpack) which should help with lots of things in your VM?  If not download it now and install.

^^^
This. If your host internet is working fine, then your virtual guest OS should be using the same without issue ...

---

