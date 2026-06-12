---
title: "booting ubuntu from usb external drive"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Metul Burr on 2011-01-31
I have a Laptop HP Pavilion dv6700 with BIOS: Ver 1.00PARTTBL PHOENIX. 
My cd/dvd drive does not work, so i bought an HP external drive and tried to boot ubuntu from that...but just goes to windows. I went into my BIOS and tried to rearange the USB drive to before the inteernal or HD...BUT there is no option for USB drive in my BIOS
I dont want wubi virtual...I was originally trying to dual boot... I already set up a seperate partition for ubuntu ...but right now i dont care...i just want ubuntu to work....please help
we tried to do a USB stick installation but it hung at a certain point

---

### Post by cariboo on 2011-02-01
How did you install Ubuntu on the external drive? If you have a floopy drive, you can get a boot disk, that will allow you to boot from usb. Have a look [here]("http://www.bootdisk.com/pendrive.htm")

---

### Post by rosencrantz on 2011-02-01
I'd try again booting from a thumb drive. 
Regarding drive selection in BIOS, I once found a thumb drive  listed under "Hard Drives" instead of "Removable devices" in the Samsung BIOS, which is a tad counterintuitive.
Also, the drive has to be bootable, and I'd format it to Fat32 before transferring the live image.
On Windows, I had good results with [www.pendrivelinux.com's](www.pendrivelinux.com's) [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").
You mentioned an installation hangup - can you boot from the stick?
Maybe the partition you are trying to use is corrupted somehow. And if the hangup persists, it would be good to know more details.

Good luck,
rosencrantz

---

