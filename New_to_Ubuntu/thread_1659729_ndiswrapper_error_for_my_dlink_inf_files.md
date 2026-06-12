---
title: "ndiswrapper error for my dlink inf files"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by thesnappysneezer on 2011-01-04
I have wua-2340 on an 64 bit linux and I am trying all drivers I got and all give errors, whether trhey are vista 64 32 or xp 32. What to do? I have wrapper installed and ndisgtk, utils and common, all that seems to be working fine but if I choose the driver it will not work, neta5agu.inf, agux86.inf, agux64.inf, all say error while installing

---

### Post by bkratz on 2011-01-04
> **thesnappysneezer said:**
> I have wua-2340 on an 64 bit linux and I am trying all drivers I got and all give errors, whether trhey are vista 64 32 or xp 32. What to do? I have wrapper installed and ndisgtk, utils and common, all that seems to be working fine but if I choose the driver it will not work, neta5agu.inf, agux86.inf, agux64.inf, all say error while installing




ndiswrapper is only meant to work with the XP or 2000 drivers, not Vista drivers and the 32 or 64 bit size must be correct.

---

### Post by thesnappysneezer on 2011-01-04
is there an 64 bit xp? should I get the 32 bit version oflinux then?

Alternatively, should I just get a pci wireless adaptor? Would any of those work with 64 linux out of the box, I see a cheap one asus pci-g31 and it apparently has linux drivers, it looks like I would have to order online though. Is there any as such available in stores like bestbuy that have linux drivers or if I buy something new, will I get the samew trouble I have here with the 64 bit?

What are the differences between 64 and 32, my vista was 64 before I deleted it by accident

---

### Post by lkraemer on 2011-01-05
After reading this HOWTO: (Even though it isn't for your Hardware) 
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+broadcom)

You should be able to locate your hardware, and have enough information
to download the correct Windows Drivers for your 32 or 64 bit Ubuntu install.
Just be sure you also have the correct 32 bit or 64 bit version
of the Windows Drivers.  The XP Drivers should work fine.

Even though the HOWTO: is for different hardware, the same method will work
with your hardware.


Another option I'd try first would be to connect via Ethernet to the Internet,
Update your system, then try to install the latest Hardware Drivers.
They will most likely be found and installed.  If not, then you are back at the
beginning of the HOWTO:.

Post your output of the above Terminal commands so others may assist.

lk

---

### Post by thesnappysneezer on 2011-01-05
urgggh I reinstallled 64 bit and hey it recognized and installed the driver and notices the hardware. This all being said, the little light on ther dlink is not on and I am not accessing the internet. Ir does not detect the internet connection.

---

### Post by cariboo on 2011-01-05
I have the same device, I've never been able to get it to work on a 64-bit version. It works well on  32-bit Karmic which is the last version I tried it on.

What I find amazing, is that it is a Windows only device, it won't even work on a Mac, and I can still get it to work even if it is only a 32-bit version.

I used the XP drives that came on the CD-rom with the device.

---

### Post by thesnappysneezer on 2011-01-05
wouldn't work on the 32, tried it too.

---

### Post by caseydk on 2011-01-06
***Really*** frustrating as I just bought this one an hour ago. Ugh.

---

