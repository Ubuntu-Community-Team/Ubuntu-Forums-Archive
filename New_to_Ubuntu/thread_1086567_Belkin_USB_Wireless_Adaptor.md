---
title: "Belkin USB Wireless Adaptor"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-04
Hi

Attaching a Belkin 54g USB wireless adaptor onto my laptop with Ubuntu 8.10 but the system does not apparently recognise it at all. Attaching a digital camera to the same port and it is recognised immediately. Appreciate any assistance in getting the adaptor to work.

Thanks

---

### Post by jaminux on 2009-03-04
Assuming this is a driver question. 

A driver is a piece of software that controls the interaction of a computer with a hardware device.

Devices like these require drivers to work. Ubuntu comes with some drivers by default, hence your digital camera works. The Belkin wireless adapter obviously does not have a driver that can be used on Ubuntu by default.

If you want to use it you will have to find one, assuming one is available. If you can't find one you can't use this device.

In future make sure you check whether a device is Linux compatible or not before you purchase it, if you want to use it with Ubuntu that is.

---

### Post by gdn1947 on 2009-03-04
Thanks for that info. I have a Windows driver but the Belkin website does not appear to have a Linux driver available. Can anything be done with that? What does Wine do?

Thanks

---

### Post by jaminux on 2009-03-04
Wine is a compatibility layer for windows. Basically it converts windows program "commands" into Linux program "commands" so they can be understood by Linux.

Wine does not work 100% though, and can be a pain sometimes. It is worth giving it a go though, I have never tried it with something like a driver.

It might work, but I am quite doubtful.

---

### Post by FreewheelinFrank on 2009-03-04
What's the model number?

I have a Belkin 54g USB wireless adaptor which works in 8.10.

---

### Post by jaminux on 2009-03-04
Just googled belkin linux drivers and looks like there might be some available, will take a closer look.

---

### Post by jaminux on 2009-03-04
Ah we might have been going about it the wrong way. Linux just might not have been using the device by default.

Take a look at:

[http://windowsrefugee.blogspot.com/2008/05/belkin-54g-usb-wireless-adapter.html]("http://windowsrefugee.blogspot.com/2008/05/belkin-54g-usb-wireless-adapter.html")

This should hopefully solve your problem.

---

### Post by FreewheelinFrank on 2009-03-04
This might be useful:

[http://spikeymikey.net/2008/11/04/belkin-f5d7050/](http://spikeymikey.net/2008/11/04/belkin-f5d7050/)

I'm pretty sure I have the same model and it's "plug'n'play" although maybe they introduced a new model- I don't have mine to hand.

---

### Post by FreewheelinFrank on 2009-03-04
> **jaminux said:**
> Ah we might have been going about it the wrong way. Linux just might not have been using the device by default.

Take a look at:

[http://windowsrefugee.blogspot.com/2008/05/belkin-54g-usb-wireless-adapter.html]("http://windowsrefugee.blogspot.com/2008/05/belkin-54g-usb-wireless-adapter.html")

This should hopefully solve your problem.

I'd go with that first- check that wireless is actually enabled.

---

### Post by abn91c on 2009-03-04
> **FreewheelinFrank said:**
> What's the model number?

I have a Belkin 54g USB wireless adaptor which works in 8.10.
I also have a Belkin 54G USB and worked plug and play with kubuntu 8.10 Belkin model [COLOR="Blue"]f5d7050[/COLOR], [COLOR="Red"]**gdn1947**[/COLOR],if you installed ndiswrapper before using the adapter you may want to remove them.

---

