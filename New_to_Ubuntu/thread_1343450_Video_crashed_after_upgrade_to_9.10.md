---
title: "Video crashed after upgrade to 9.10"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by ubergeekin on 2009-12-01
I recently made the leap to 9.10 and in the process I lost my video. I have tried to recover but all I get is garbled video with Ubuntu across the top of the screen and corrupted video at the bottom of the screen. I'm using an ATI Radeon Mobility HD 2400 in a Toshiba Satellite A215-S7472 laptop. 

Initially I was hoping to recover the installation, but at this point I would be happy if someone could help me get my USB HDD connected using the root console. I see the device come up as: SDB but when trying to MOUNT SDB it says SDB does not exist in /etc/fstab. I've tried adding in the device to fstab but it doesn't work. I'm no rocket scientist with ubuntu, so I could use some basic coaching to get through this crisis.

---

### Post by Mark Phelps on 2009-12-02
Perhaps you would be able to get decent video again if you installed the open source video drivers.  The link for doing that is below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Zoot7 on 2009-12-02
Have a look at the guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

It guides you through doing a package based install of the ATi driver under Ubuntu. This is always the way I set up the ATi driver with my HD4870 under Ubuntu, hasn't failed on me yet.
Granted it's for Jaunty but it should work with Karmic too, the only difference is that you'll have to build the packages for Karmic as opposed to Jaunty so the following line:
```
sh ati-driver-installer-9-11-x86.x86_64.run --buildpkg Ubuntu/jaunty 
```
would become
```
sh ati-driver-installer-9-11-x86.x86_64.run --buildpkg Ubuntu/karmic 
```

---

