---
title: "USB-stick: Disabling all network devices and local HDD access"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by bushtor on 2009-12-01
Hi,

I need to boot ubuntu from a USB stick.  When booted a local user should have no access to the computer's local harddrive and all networking devices (cabled, wireless, bluetooth, dialup) should be disabled.

We just want/need access to OpenOffice and the possibility to save files to the ubuntu USB stick.

Thanks a lot for tips on how to disable networking and local HDD access.

Btw which tool / procedure is the best to get ubuntu over to a memory stick?

regards tor

---

### Post by wesleybailey on 2009-12-01
If you are creating the usb drive from within Linux.

Then I would recommend using Ubuntu's built in USB Startup Disk Creator(System->Administration->USB Startup Disk Creator). 

You can also use unetbootin from with Linux.

---

### Post by ukripper on 2009-12-01
> **bushtor said:**
> Hi,

I need to boot ubuntu from a USB stick.  When booted a local user should have no access to the computer's local harddrive and all networking devices (cabled, wireless, bluetooth, dialup) should be disabled.




Create limited user account to give limited privileges. see this link: [http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

---

### Post by gradinaruvasile on 2009-12-01
Take a USB stick at least 2GB
Make 2 partitions on the USB stick:
One 800 MB partition, the other the remaining space.


Download the .iso.
Use the usb disk creator to write the .iso to the first partition.

On boot, you will have a USB disk partition that is accessible for read/write. 
The first one is not accessible! The file system (/) is an image in the memory, not from the first partition of the stick. thsts why you need 2 of them. 
Also bear in mind that the second partition of the stick IS NOT mounted by default on Windows (XP) - in fact i dont know how CAN be done, if its possible.

The problem is that you want a custom made thing here (no local HDD access n stuff on boot) if i understood correctly. 
That would require to make a custom squashfs. And thats not simple AFAIK.

---

