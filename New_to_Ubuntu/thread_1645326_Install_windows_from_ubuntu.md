---
title: "Install windows from ubuntu"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by bprins on 2010-12-14
Hi,

I am trying to install windows 7 back onto my hard drive (after trying to get games up and running from within virtual machine with virtual box).

So, I created a 150GB NTFS partition on my hard drive, downloaded the Windows 7 ISO, wrote the ISO file to an USB disk using unetbootin. So far, no problems.

Then I rebooted and was hoping that the USB device would boot into the windows installer, no luck. I got into the "boot from USB" menu and then unetbootin fails to start the windows installer. As far as I understand that's a windows installer issue, which is not capable of booting from USB drive.

OK, fair enough. I thought, lets be a complete idiot and start the "setup.exe" in Ubuntu by simply double clicking it. And wtf, it actually loads the windows 7 installer (hurray for Wine). Next, I pressed the "Install" button, but then received an error message that there is no available partition to install windows 7 on. That's strange, since I have a (mounted) 150GB NTFS partition waiting to be used.

1) Does anybody know the solution for installing windows 7 from Ubuntu?
2) Is there a different way to install windows 7 without writing the ISO to a DVD (I ran out of writable DVDs and I prefer not to buy new ones.. :)).

Looking forward to your help!

Thanks in advance.

Bas

---

### Post by Verbeck on 2010-12-14
afaik, windows iso's can't be downloaded legally..

---

### Post by bprins on 2010-12-14
Is Microsoft MSDN subscriber legal enough for you?

Anyway, I am still looking for help.

---

### Post by oldfred on 2010-12-14
Is the NTFS a primary partition with the boot flag (active partition in windows)?

---

### Post by sikander3786 on 2010-12-14
Unetbootin might not be able to create a Win 7 Startup Usb as it is intended for Linux Distros only (till the moment) ;-)

However, that shouldn't be too difficult either. See this.

[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

Win 7 can be installed from a USB drive. The only reason I see why it was not booting from the USB is that it wasn't created properly. And your system should obviously support booting from USB drive.

---

### Post by bprins on 2010-12-14
You are from this moment on the man I worship for the rest of my days.

gparted > boot flag for NTFS partition > reboot > windows installer.

Thank you very much :)

Cheers.

Bas

---

