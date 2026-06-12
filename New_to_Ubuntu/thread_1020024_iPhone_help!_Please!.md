---
title: "iPhone help! Please!"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by iNeeed on 2008-12-23
I was trying to update my iphone in windows xp in a virtual machine and now its stuck in this recovery state?  It won't work.  I keep getting a message that I need to disconnect it from the driver in the host manchine.  I don't know how to do this.  I'm freaking out because its my phone and I can't use it and I need to make phone calls!

Help???

---

### Post by Delvien on 2008-12-23
More information please?

What Virtualization software? Is your iphone saying that it needs to disconnect? Have you reboot the guest OS? Have you disabled and enabled the USB? Have you rebooted your Host machine?

---

### Post by bhaverkamp on 2008-12-23
I have this very same problem. Really my only issue with running XP in a VM. I was using VMware workstation. If anyone knows of a fix for this or for a different virtualization software where this is know to work; I would love to hear about it.

---

### Post by iNeeed on 2008-12-24
I was using VMware workstation.  I tried rebooting both.  

"The specified device appears to be claimed by another driver (snd-usb-audio) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver."  

This was one of the messages. I tried disconnecting the soundcard in the vm but that didn't work.  And finding the driver.

I read online somewhere that someone didn't have a problem with their USB device in Vmware Workstation 6.5.1, so I installed that but still had the problem.

Being that I neeed my phone and couldn't/can't spend a lot of time messing around with this. I was able to reset the iPhone on another computer using itunes in Windows.

I am going to partition my disk and run XP for iTunes and odds and ends.

I feel no need to risk frying all of the data on my iphone again.

---

### Post by astathios on 2008-12-26
first of all excuse me for my english.
i had the same problem in virtuall box,while iphone is reseting and update it cuts the comunication for a moment, u can solve it easy , you have only to be fast to reconect the usb in vmware manually excactly the moment when it is possible cause by default conects first to the host maschine and not in console. in virtuall box it can be happen automatically by making it enable from the usb settings . Not sure in vmware

---

