---
title: "Different installation"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by shankhs on 2009-07-23
I have an old windows machine which I recently upgraded to core2duo, 1GB RAM ans 250GB Hard disk.I ran out of money to buy a DVD reader or writer ( I mean I dont have anything to get any CD or DVD working).
Since the BIOS is old so no USB startup option. :( 
That leaves me with only option of installing ubuntu using HTTP.
I read this [https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")

My question is can I install interpid netbook image in my machine?
I have static IP settings.

Is there a way to install Desktop interpid from HTTP with static IP?

Thanks for your help guys.

---

### Post by x33a on 2009-07-23
first of all please tell me how you installed core2duo on a motherboard that doesn't support usb boot?

on topic: it would probably be better and easier to use wubi for the time being.

[http://wubi-installer.org/](http://wubi-installer.org/)

[http://en.wikipedia.org/wiki/Wubi_(installer](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by mapes12 on 2009-07-23
I've had a read of the HowTo "Run Tftpd32.exe and click the DHCP tab" and would enter my static IP address and subnet mask into these fields. Might work.

---

### Post by shankhs on 2009-07-23
> **x33a said:**
> first of all please tell me how you installed core2duo on a motherboard that doesn't support usb boot?



I have Intel945 series of motherB and I dont see any USB option in my BIOS!
If the motherB supports then I have to find out how!

any ways I will try wubi thanks.

---

### Post by x33a on 2009-07-23
go to boot options or boot order option. There should be an option to select usb as the first boot device.

---

