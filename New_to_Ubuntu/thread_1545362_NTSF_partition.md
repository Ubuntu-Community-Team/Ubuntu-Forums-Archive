---
title: "NTSF partition"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Gauze on 2010-08-03
I want to install Ubuntu on my new laptop but I have a few concerns first.

I have some experience with 9.10 and 10.04 running from a flashdrive and I liked it overall.

I only had one concern.

I always had issues with NTSF formatted harddrive/partitions.

I was told that "Safely remove" is what I am supposed to do but I'll often forget and hit the icon that looks like eject or right click and select unmount. Sometimes the harddrives would also have corruption problems if I forgot to safely remove the partition and just shutdown the USB install.

I understand that the problem is related to the buffer for the partition not being finished...or something.

Is there a way so Ubuntu always ask me if I want to wait with the option of force remove regardless of whether I hit the eject icon or unmount?

Or is there an option to disable any unsafe way of removing a harddrive?

Sure I could get in the habit of always using Safely Remove but then I'd worry about other people using the wrong ways to unmount a partition and become the OCD guy that never lets anyone touch his laptop.

Also, I assume a normal install would remove any partitions safely. Would that be correct?

---

### Post by chopinhauer on 2010-08-03
> **Gauze said:**
> 
I was told that "Safely remove" is what I am supposed to do but I'll often forget and hit the icon that looks like eject or right click and select unmount. Sometimes the harddrives would also have corruption problems if I forgot to safely remove the partition and just shutdown the USB install.


The icon that “eject” icon or the unmount option **is** the way to safely remove your drive. Then you just have to wait for the icon on your desktop to disappear.

There is nothing that can stop you from physically disconnecting the Flash Drive.

---

### Post by Gauze on 2010-08-03
I'm not talking about removing a flashdrive. I'm talking about Ubuntu installed from a flashdrive interacting with NTFS partition on the computer that the flashdrive is connected to.

---

### Post by chopinhauer on 2010-08-03
> **Gauze said:**
> I'm not talking about removing a flashdrive. I'm talking about Ubuntu installed from a flashdrive interacting with NTFS partition on the computer that the flashdrive is connected to.

In this case the disk partitions will always be cleanly unmounted, whatever you do. Unless the system crashes.

---

