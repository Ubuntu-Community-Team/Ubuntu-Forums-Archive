---
title: "Live Usb Types"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by 13k on 2010-05-12
Hello,

The reason why i started this thread is because i'm somewhat concerned of the well-being of my usb.  What is the difference between "Live CD Derived" and "Full Install" live Usb's.  Do Live CD derived or Full Install usbs, have persistence or not?  Are Full Install Usbs, literally what they mean, to actually install through the usb?  Thank you for the time for reading this. 
**Live CD derived**

 The first type of live USB is created by simply taking the ISO image file from a live CD distribution and placing it on USB storage  device and then making it bootable.


Advantages Disadvantages    
[LIST]
[*]Can be simple to install with no risk to other systems on hard  disks.
[*]The compressed format allows many applications within the limited  storage available.
[*]Updating the system can be as easy as replacing a single file.
[*]An installation can be as small as 50MB.
[*]Many live CDs are set up to be USB-aware, and write changes to a  second partition on the USB device
[/LIST]
   
[LIST]
[*]Some live CDs are not set up to write to their own filesystem  because a CD is typically read-only, thus it can sometimes be difficult  to enable a live USB OS to store changes.
[*]Making the ISO image bootable, and partitioning the USB device  correctly(especially if persistence is desired[such as the ability to  save changes to the filesystem]), can be difficult.
[/LIST]
    **Full install**

 The second type of live USB is closely related to a traditional  operating system hard drive install with minor modifications like the  elimination of swap partitions and files.
   Advantages Disadvantages    
[LIST]
[*]Updating applications or the whole thing is as easy as the parent  distribution used to create it.
[*]Full system encryption possible.
[*]Easier to customize with the user's preferred Windows Mangers and applications.
[*]Base install usually starts at approximately 200MB (although some  can be as little as 40MB) and grows as the user adds applications.
[/LIST]
   
[LIST]
[*]Only easy to install if the operating system provides support.
[*]Will wear through the USB faster.
[/LIST]

-Wikipedia.org/wiki/Live_usb
****

---

### Post by warfacegod on 2010-05-12
A derived LiveUSB can have persistence if you choose to have it. The USB Startup Disk Creator gives you the option (assuming you are using an Ubuntu derivative) of using the leftover space to store documents and settings.

Yes, a full install is literally installed to the USB as though it were simply another HDD.

I imagine that after using a LiveUSB (.iso) with persistence file a few times that the difference between the two would be fairly superficial. Although a derived would still generally be for the purpose of installing to a computer. I *believe* that changes (settings and such) made to a derived LiveUSB will carry over to a computer it is installed to but I'm not sure.

---

