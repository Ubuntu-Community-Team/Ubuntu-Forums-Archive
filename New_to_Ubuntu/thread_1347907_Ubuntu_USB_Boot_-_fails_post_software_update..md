---
title: "Ubuntu USB Boot - fails post software update."
date: 2009-12-06
forum: New to Ubuntu
---

### Post by lpmb on 2009-12-06
hi - have successfully installed and booted Ubuntu on a 4gb USB stick using "USB startup disk creator" and a version 9.10 cd .iso.  - everything works fine on my ThinkPad T60.

Fine, that is until I execute a software update via "update manager' when running the USB install.   Once the update is complete and the machine restarts (or shutsdown and restarts), the USB drive can no longer boot.  This has now happened 3 times.

I'm wondering if I'm just being an idiot assuming that I can update a USB installation or if some other problem is in play ?

I am a total noob at this.

*** SOLVED *** I simply did a full USB install (knowing the risks of USB degradation) and all updates etc worked fine.  I had btw tried all the persistent tricks mentioned below (gave 2gb to the 'slider') to no avail prior to doing a straight out install.

---

### Post by zkriesse on 2009-12-07
You cannot update a USB installation as it's basically the Ubuntu Live CD except it's on a USB Flash drive. If you make a portable version of Ubuntu on a USB Flash drive though then yes you can.

---

### Post by wilee-nilee on 2009-12-07
The usb startup disc creator has a persistent area to save updates, did you use the stored in reserved space persistent tab and use the slider to size it?

---

### Post by Ylon on 2009-12-07
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


Anyway: [http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux) this seem the one able to do the job at zero hassle.

---

