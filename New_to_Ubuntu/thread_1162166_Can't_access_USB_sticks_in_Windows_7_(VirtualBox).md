---
title: "Can't access USB sticks in Windows 7 (VirtualBox)"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-05-17
I've tried reading my USB drives in Windows 7 using VirtualBox but for some reason VB says that they're unavailable. I added them in the settings and noticed that it says unavailable. Do I need to configure VB or do something else in Windows 7?

Also in W7, the internet icon says that I don't have access but I actually do. Anyone had something similar?

Thanks!

---

### Post by jimmy the saint on 2009-05-17
Did you follow the instructions here:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

to enable USB support in VitualBox?  It does not work out of the box, you need to tweek a config file to allow it.

---

### Post by Ptero-4 on 2009-05-17
for internet you need to use the bridged mode in VirtualBox.

---

### Post by jimmy the saint on 2009-05-17
I believe that in order to act as part of your local LAN you need to use bridged mode, but I have never actually set up bridged mode to use the internet.  I set it up once to use my network printer and had nothing but headaches.  I get the internet just fine with the default network setup, but no access to my local LAN.

---

### Post by stuart.reinke on 2009-05-17
Did you install VirtualBox ose or VirtualBox 2.2.2 

To have usb support you need to download VirtualBox 2.2.2 form Sun Microsystems website. (not available through synaptic package manager)

---

### Post by sylvainrb on 2009-05-17
@jimmy: I will look into the link and see if I can get it to work.

As for the internet, it works fine. It's just that the icon in the taskbar says that I don't have access. Jimmy, I'm in the same situation as I'm trying to access my printer and other computer on my local network without success...

@Ptero-4: Thanks. I'll try using the bridged mode.

@stuart: I downloaded VB 2.2.2 from the website.

---

### Post by sylvainrb on 2009-05-17
> **jimmy the saint said:**
> Did you follow the instructions here:

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

to enable USB support in VitualBox?  It does not work out of the box, you need to tweek a config file to allow it.

That did the trick. Thanks!

---

