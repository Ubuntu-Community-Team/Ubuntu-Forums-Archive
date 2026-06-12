---
title: "VirtualBox - no USB devices unless you pay?"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-10-14
Hello:

Is it correct that free VirtualBox will not allow, i.e. see, USB devices attached to the host?

Thanks,

---

### Post by JustinR on 2010-10-14
> **Robert.Thompson said:**
> Hello:

Is it correct that free VirtualBox will not allow, i.e. see, USB devices attached to the host?

Thanks,

Hi,

Not the open-source version. But the closed-source version - which is free - does.

Just go to [www.virtualbox.org](www.virtualbox.org) and download the latest version.

---

### Post by DarthScape on 2010-10-14
What you are seeing is "Free" as in freedom. There is no paid version. The non-OSE version is still "Free" as in price, but not open source. So, if you use the proprietary version, you can use usb.

---

### Post by Ctrl-Alt-F1 on 2010-10-15
If you download the closed source version (the only one with usb support), you must add yourself to the vboxusers group in order to pass the usb devices to the guest operating system.

---

### Post by Robert.Thompson on 2010-10-15
> **JustinR said:**
> Hi,

Not the open-source version. But the closed-source version - which is free - does.

Just go to [www.virtualbox.org](www.virtualbox.org) and download the latest version.

Thank you!

I just downloaded & installed: virtualbox-3.2_3.2.10-66523~Ubuntu~lucid_amd64.deb.

I still do not see any USB devices. Is there something else that I must do?

Thanks,

---

### Post by Ctrl-Alt-F1 on 2010-10-15
As I posted earlier:

> **Ctrl-Alt-F1 said:**
> If you download the closed source version (the only one with usb support), you must add yourself to the vboxusers group in order to pass the usb devices to the guest operating system.

System > Administration > Users and Groups
Manage Groups
Scroll down to vboxusers
Click Properties (on vboxusers)
Click the checkbox next to your username
Click OK.

To access device:
Click Devices -> USB Devices -> Device Name

You can also create a filter in the virtual box settings (when the vm is off) that will pass a usb device to the vm every time it is turned on (if you want to).

---

### Post by TNT1 on 2010-10-15
> **Robert.Thompson said:**
> Thank you!

I just downloaded & installed: virtualbox-3.2_3.2.10-66523~Ubuntu~lucid_amd64.deb.

I still do not see any USB devices. Is there something else that I must do?

Thanks,

You must also go to administration/users, and make sure you are added to the vboxusers group.

---

### Post by Ctrl-Alt-F1 on 2010-10-15
You may have to log out and back in again (to ubuntu) once you add yourself to the vboxusers group.  Not sure about that though.

---

### Post by TNT1 on 2010-10-15
> **Ctrl-Alt-F1 said:**
> You may have to log out and back in again (to ubuntu) once you add yourself to the vboxusers group.  Not sure about that though.

Yeah, I find that a random thing. On the Toshiba, I had to log out, on the HP, I didn't have to...

---

