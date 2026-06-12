---
title: "how to load songs to iphone"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by som1special2 on 2009-06-13
anyone know how in 9.04?

---

### Post by jbrown96 on 2009-06-13
I have an iphone, and it's not very easy. [Here's the community doc]("https://help.ubuntu.com/community/PortableDevices/iPhone") on how to do it.

I recommend using Virtualbox and running XP. You will need to closed source version to support usb pass-through. Then you can run iTunes. There are two drawbacks; 1) you CANNOT update your iphone. DON'T TRY IT. It will start the update but when the phone resets it gets stuck in an infinite loop. Each time it reboots it gets a new USB identifier, so Virtualbox can't keep the device "pass-throughed" to XP. 2) iTunes for Windows is an awful program. It's so freaking slow. I have a Core2Duo @ 2GHz with 2GB ram, and it's practically impossible to use. You need to be very patient. 


Good luck.

---

