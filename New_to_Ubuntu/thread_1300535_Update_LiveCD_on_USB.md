---
title: "Update LiveCD on USB"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-25
Hi Forum,

Can I update an Ubuntu installation on USB (Karmic installed from AMD64 Desktop ISO using "create USB" from the start menu)?

I see that the update function is able to download updated packages for use in the live environment but I want to know whether an installation to harddisk from the updated USB will automatically include the updates.

Thanks


Richard

---

### Post by mike555 on 2009-10-25
If you installed Ubuntu to the USB drive it's just like installing to your HD , if you update it , then make a new install .iso , like with reconstructor , it would have the updates included.

---

### Post by RichardCL on 2009-10-25
Thanks.

From the liveUSB, there is an icon on the desktop that allows the installation of Ubuntu to the host system.

I'm assuming then that if I update the USB installation and then install Ubuntu on the hard disk of the host system using the install icon on the USB's desktop, the packages installed will be the newest versions.

Is that also correct?

---

### Post by NCLI on 2009-10-25
By the "USB installation," do you mean that you've installed Ubuntu to your USB drive, or that you've just copied the LiveCD to it?

---

### Post by RichardCL on 2009-10-25
I created a USB disk (installed Ubuntu to the disk) using the standard app available from the Gnome desktop

system>adminsitrationY>create USB startup disk

I can run Ubuntu from the USB without modifying the host PC (the host recognises the USB as bootable). When updates become available for packages I can use the command apt-get update to bring the system on the USB up to date.

I can also install Ubuntu to the host PC using an install program on the Gnome desktop within the USB.

What I want to know is whether the update process also means that the packages installed to host are updated by the update process.

---

### Post by mike555 on 2009-10-25
When you update your USB install that's it ........ you will still need to update whatever you have installed on your computers HD ,........ I'm not sure what you mean "Host" , that is a term usually used in virtualbox .... if your somehow running the USB in a virtualbox then the same would apply , you would still need to update your host separately .if that is what your asking?

---

### Post by LewRockwell on 2009-10-25
> **RichardCL said:**
> I created a USB disk (installed Ubuntu to the disk) using the standard app available from the Gnome desktop

system>administration>create USB startup disk

I can run Ubuntu from the USB without modifying the host PC (the host recognises the USB as bootable). When updates become available for packages I can use the command apt-get update to bring the system on the USB up to date.

I can also install Ubuntu to the host PC using an install program on the Gnome desktop within the USB.

What I want to know is whether the update process also means that the packages installed to host are updated by the update process.

you have and are using a "LiveCD" and/or a "LiveUSB" which is a "static" edition

What you are attempting(in our estimation) is a PERSISTENT installation

Maybe something like this:

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

.

---

### Post by RichardCL on 2009-10-25
Thanks, great tutorial. Just what I needed. I'd thought the normal USB where persistent. Seems that I need to follow the advice in your link.

---

