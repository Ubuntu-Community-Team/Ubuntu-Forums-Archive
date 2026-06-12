---
title: "Thumbdrive and partitions."
date: 2010-09-20
forum: New to Ubuntu
---

### Post by diablofatt on 2010-09-20
I recently used a company laptop to install Ubuntu to a thumb drive. All went well with the install except for when I reboot to window's. If the thumb drive is removed I cannot access XP. Its give's me a grub error which I assume is from the USB stick not being there. I need to be able to access window's without the thumbdrive any help will be appreciated.

---

### Post by mike555 on 2010-09-20
during the install you should have clicked the advanced button and told it to install grub to the usb ....... you have a couple of choices , edit grub so it doesn't look for ubuntu , then install grub to the usb  -or- use a Windows install disc to install Windows loader on the first partition , then install grub to the usb -or- leave the usb in...

---

### Post by diablofatt on 2010-09-20
How do I edit grub to not look for ubuntu?

---

### Post by C.S.Cameron on 2010-09-20
It might be necessary to use the XP install disk to open the Emergency Repair Console and do a fixmbr, (ie type "fixmbr").

There is also a Linux tool named ms-sys that can fix an XP boot record while booted from an Ubuntu Live CD or USB.

I'm not sure if ms-sys is in the repositories, It might have some Microsoft code in it.

---

### Post by diablofatt on 2010-10-23
Thank you. I ended up using a fresh window's disc and let it install the Windows loader.

---

