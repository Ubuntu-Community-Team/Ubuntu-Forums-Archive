---
title: "pen drive password persistence prob"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by nnjond on 2010-03-22
Hi,

I'm trying to establish login and password protection on my pen drive. but it doesn't remember the pssword i tap in under Users and Groups; so it loads without needing to login every time?

Does anyone know what the prob is?

Thanks

---

### Post by Alias1407 on 2010-03-22
I am not 100% sure of what your talking about however I assume that you want your system to ask for a password before it lets you access the files stored on your USB.

If this is the case then I would suggest encrypting it using luks. The problem with this is that you will only be able to use the USB on computers running linux that have the dm-crypt kernel module loaded. If you plan to do this I would suggest partitioning your usb half with FAT and half with a journalised file system like ext3 or such.

A good tutorial of how to encrypt a USB is here [http://www.mattmckimmy.com/blog/2009/09/21/setting-up-luks-encryption-on-usb-drives/](http://www.mattmckimmy.com/blog/2009/09/21/setting-up-luks-encryption-on-usb-drives/)

---

### Post by quinnten83 on 2010-03-22
> **Alias1407 said:**
> I am not 100% sure of what your talking about however I assume that you want your system to ask for a password before it lets you access the files stored on your USB.

If this is the case then I would suggest encrypting it using luks. The problem with this is that you will only be able to use the USB on computers running linux that have the dm-crypt kernel module loaded. If you plan to do this I would suggest partitioning your usb half with FAT and half with a journalised file system like ext3 or such.

A good tutorial of how to encrypt a USB is here [http://www.mattmckimmy.com/blog/2009/09/21/setting-up-luks-encryption-on-usb-drives/](http://www.mattmckimmy.com/blog/2009/09/21/setting-up-luks-encryption-on-usb-drives/)

No, he means he installed his OS to a USB stick and turned on the option for persistance.
The thing is that a pendrive install is just a live cd. Everything previous to login uses the live CD password. Everything before login is not saved. You can see this, there is only user Ubuntu to log into.
You can try creating another user and making him the owner of all the files you use when in the live session, but I don't think that will work.

---

### Post by Alias1407 on 2010-03-22
> **quinnten83 said:**
> No, he means he installed his OS to a USB stick and turned on the option for persistance.

Lol missed that :cry:

---

### Post by quinnten83 on 2010-03-22
> **Alias1407 said:**
> Lol missed that :cry:

No problem, man :)
You've been helping a lot around here, so a few missers here and there should not bring the wrath of the heavens down upon thee... :)

---

