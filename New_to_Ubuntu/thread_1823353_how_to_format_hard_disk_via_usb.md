---
title: "how to format hard disk via usb?"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by paker on 2011-08-11
I have an old hard disk that I want to use as external storage via usb. It used to be a main HD and still has ubuntu. When I connect it to my ubuntu desktop via usb, it does not pop on desktop. But I see it in System > Administration > Disk Utility. 

I think I need to format it before using it as external storage. But it wouldn't format (after unmounting from PC).

I tried usb connection to a Windows laptop. It doesn't get recognized by Windows, either.

**Bottom line question: how can I use it as a usb storage device?** (I have a usb-based serial hard drive dock). Thanks.

---

### Post by Paqman on 2011-08-11
> **paker said:**
> But I see it in System > Administration > Disk Utility. 


You can use that same tool to format it.

---

### Post by Sef on 2011-08-11
[Gparted]("http://gparted.sourceforge.net/liveusb.php") can be installed to a Live CD and used to reformat your hard drive.

---

### Post by wojox on 2011-08-11
> **Paqman said:**
> You can use that same tool to format it.

Same way I do it as well. Choose "No partitions" from the drop down box.

---

### Post by Paqman on 2011-08-11
> **Sef said:**
> [Gparted]("http://gparted.sourceforge.net/liveusb.php") can be installed to a Live CD

It's actually pre-installed on the Ubuntu LiveCD.

---

### Post by paker on 2011-08-16
Thanks. The 2-HD docking station was unreliable. I switched to a single HD Serial-USB converter cable and it worked as you said: System > Administration > Disk Utility. Thanks again.

---

