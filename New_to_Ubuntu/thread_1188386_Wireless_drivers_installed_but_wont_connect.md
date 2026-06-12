---
title: "Wireless drivers installed but wont connect"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by downhiller2010 on 2009-06-15
I installed the windows driver for my card that has a texas instruments acx100 chipset. Ubuntu 9.04 can see all the networks but when i try to connect the two balls just keep spinning and a connection is never established. Any help?

---

### Post by ugm6hr on 2009-06-15
More detail please.

Wifi security?

Which Windows driver?

---

### Post by downhiller2010 on 2009-06-15
i have no security on my wireless.  They were the xp drivers for my card.  I just went to system-add windows wireless driver-and added the .inf file and it recognized the hardware

---

### Post by ugm6hr on 2009-06-15
If you have no security on your wifi, there is a perfectly good Linux ACX driver.

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

I would presume that Ubuntu has it included as default, and just requires firmware.

Why did you install an XP driver?

---

### Post by downhiller2010 on 2009-06-15
So in linux where do I install this driver instead of the windows one?

---

### Post by ugm6hr on 2009-06-15
> **downhiller2010 said:**
> So in linux where do I install this driver instead of the windows one?

You will have to remove ndiswrapper (and the XP driver) first.

```
sudo apt-get remove ndiswrapper
```

Then try looking in System -> Administartion -> Hardware Drivers

---

### Post by downhiller2010 on 2009-06-15
Ndiswrapper is removed. When I follow the filepath you showed me to install it ubuntu says searching for drivers and doesnt do anything.

---

### Post by ugm6hr on 2009-06-16
> **downhiller2010 said:**
> Ndiswrapper is removed. When I follow the filepath you showed me to install it ubuntu says searching for drivers and doesnt do anything.

Ensure you are connected to the internet by another route when you run the Hardware Drivers dialogue.

Does it list any hardware there?

If you cannot connect to internet via ethernet cable, try downloading and double-clicking this: [http://packages.ubuntu.com/jaunty/all/linux-firmware/download](http://packages.ubuntu.com/jaunty/all/linux-firmware/download)

You may also need a **linux-restricted-modules** package (and its dependencies).

I have not had an ACX card in a long time, but I recall Network Manager (the default Ubuntu wifi applet with the spinning green dots) used to not like that driver.  It is possible you might need to try something else.

---

