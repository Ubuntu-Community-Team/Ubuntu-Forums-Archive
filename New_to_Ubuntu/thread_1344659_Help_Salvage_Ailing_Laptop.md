---
title: "Help Salvage Ailing Laptop"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by daniell59 on 2009-12-03
I am now in possession of a less than perfect laptop. I would like to install Ubuntu in it.
Here are the problems. There is no optical drive. The previous owner, removed it by force leaving a  broken ribbon cable. So I do not think that I can replace it. It has one GIG of RAM.
Now the difficult part. How can I install Ubuntu without an optical drive? I was wondering whether I can boot off an external optical drive. My knowledge is limited, but I am anxious to learn. Thanks in advance for the constructive comments that I am sure that I will get.

---

### Post by Cheesemill on 2009-12-03
Your best bet would be to use [unetbootin]("http://unetbootin.sourceforge.net/") to install from a USB stick.

---

### Post by daniell59 on 2009-12-03
> **daniell59 said:**
> I am now in possession of a less than perfect laptop. I would like to install Ubuntu in it.
Here are the problems. There is no optical drive. The previous owner, removed it by force leaving a  broken ribbon cable. So I do not think that I can replace it. It has one GIG of RAM.
Now the difficult part. How can I install Ubuntu without an optical drive? I was wondering whether I can boot off an external optical drive. My knowledge is limited, but I am anxious to learn. Thanks in advance for the constructive comments that I am sure that I will get.

Thanks
I hope that I will be able to boot from the USB.
Also, do you think that 1 GIG of ram is enough for Ubuntu 9.10?

---

### Post by yeats on 2009-12-03
> Also, do you think that 1 GIG of ram is enough for Ubuntu 9.10? 

1 Gig is *plenty* for Ubuntu.

---

### Post by MelDJ on 2009-12-03
> **chrissharp123 said:**
> 1 Gig is *plenty* for Ubuntu.

+1

> **Cheesemill said:**
> Your best bet would be to use [unetbootin]("http://unetbootin.sourceforge.net/") to install from a USB stick.

and +1
bare requirement for ubuntu is 64 mb

---

### Post by daniell59 on 2009-12-03
I am sorry to say that I find it somewhat confusing. If someone could outline the steps, it would be helpful. Also, is it necessary to be able to boot off the flash drive? I don't know whether I can with this laptop.

Thanks

---

### Post by MelDJ on 2009-12-03
it is since you do not have a cd drive.

this should help you out: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yeats on 2009-12-03
Booting from USB may "just work", but if it doesn't, you'll need to access the BIOS of the machine.  When turning the computer on, you'll see a "hit F-2 for settings" or something like that.  It may even have a "Boot Options."  Either way, you'll need to hit the key while the splash screen is still up.  Once in the BIOS screen, find the boot options and see if USB is supported.

---

### Post by daniell59 on 2009-12-03
> **chrissharp123 said:**
> Booting from USB may "just work", but if it doesn't, you'll need to access the BIOS of the machine.  When turning the computer on, you'll see a "hit F-2 for settings" or something like that.  It may even have a "Boot Options."  Either way, you'll need to hit the key while the splash screen is still up.  Once in the BIOS screen, find the boot options and see if USB is supported.

I see the boot options

USB FDD
USB HDD
USB CDROM
These are among the boot options. Is it possible that I can boot off a USB external hard drive?

Thanks

---

### Post by MelDJ on 2009-12-03
try booting from USB HDD

---

