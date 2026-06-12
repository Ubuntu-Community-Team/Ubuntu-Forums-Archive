---
title: "Wubi .. Any help"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by Maz7006 on 2011-08-24
So before i get hammered with the Wubi megathread and the FAQ i already read though them extensively

I own a Netbook, Asus Eee 1005HA if it makes any difference, and i wanted to install 11.04 

I go ahead, download the ISO, and make my bootable USB, yet for some reason i can't boot from USB, i tried multiple USB's, sizes, and format types in addition to many "usb-making" software (other than the one that ubuntu links you to) and i still couldn't boot via USB

ill just use Wubi, but the problem is when i run it, select the settings and what not, some data extracts and then Wubi wants to download 11.04 and from what i can tell it wont do do it via P2P torrents. 

Torrents and any sort of P2P interactions are blocked on my network (its an educational institute) so obviously the install failed and exited.

if i remember, last time i used ubuntu was with the LTS and i had no problem with wubi and and offline installation ? How can i fix this problem ? 

Thanks for any help.

Bottom line: i have my Ubuntu 11.04 ISO image, how can i install this via wubi if for some strange reason it WANTS to download the ISO again ?

---

### Post by seawolf167 on 2011-08-24
Regarding the "cannot boot from USB" - did you change your BIOS settings to enable USB booting and give it a higher priority than your hard drive? This could likely be the cause of not being able to boot off the LiveCD to install.

You should have the option to install via Wubi from the image (.iso) directly after you download it without having to download any additional items. If you use a program like [Virtual Clonedrive ]("http://www.slysoft.com/en/virtual-clonedrive.html")you can mount the .iso file and run it as if the cd were in your computer.

---

### Post by Frogs Hair on 2011-08-24
You may know this , but you may have to change the boot device priority in the bios to the device you are trying to boot with. I drove myself crazy trying to get a Linux Peppermint cd to boot from Windows after making 2 copies of the ISO , I remembered that .

---

### Post by Rex Bouwense on 2011-08-24
I have an ASUS netbook also and it recognizes a flash drive as another hard drive.  Perhaps yours is the same.  Check your BIOS and just move the flash drive (recognized as a hard drive) ahead of the hard drive from your netbook.  That should solve the problem.

---

### Post by seawolf167 on 2011-08-24
Another option which I forgot to mention - there should be a keystroke that gives you a boot menu during POST. It is usually [F8] through [F12]. Then you can select which device to boot from regardless of the boot order priority.

---

### Post by bcbc on 2011-08-24
I'd be surprised if the usb boot doesn't work on that netbook. However, to install wubi, download wubi.exe and save it in the same directory as your ISO. Then remove any USBs containing Ubuntu from your computer.

Then run wubi.exe from the location that contains the ISO. Provided you got matching releases for both - it works. If it doesn't post the *%temp%\wubi-11.04-rev211.log*

---

