---
title: "Ubuntu 10.04 + VirtualBox 4.2 (USB again trouble)"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by NewUse on 2011-02-04
Hi all, I don't know, what wrong, but after updating Oracle VM USB devs become inactive :(

I have ubuntu as host and XP as guest OSs. I can see all USB devs, connected to Ubuntu in VM-devs--USBdevs, but all of them are inactive (mouse, mass store device, kbd and etc.. )

Kbd and mouse are working fine, but I can't get accsess to my USBFlash (guest OS doesn't see it :(()

Creating usb group with ID 85 and adding my user into it and into vmusers doesn't help, editing rules-10 file doen't help too :((

Please, help.

Sorry for my English.

Thanks.

---

### Post by SeijiSensei on 2011-02-04
I take it you're using Virtualbox?  You need to be using the "official" version at [virtualbox.org]("http://www.virtualbox.org/wiki/Downloads") and, for USB, the "Extension Pack" as well.

---

### Post by NewUse on 2011-02-04
Yes, thanks, I have installd VirtualBox from official site, but I have not installed "Extension Pack", thanks, I'll try, but in VirtulBox 3.* all was working without any "Exstations packs" is it a new feature?

---

### Post by garyjmellor on 2011-02-08
Please see my post here - USB devices working in VirtualBox OSE (4.0.2 r69518 ):
 
[http://ubuntuforums.org/showthread.php?p=10439282#post10439282](http://ubuntuforums.org/showthread.php?p=10439282#post10439282)

---

