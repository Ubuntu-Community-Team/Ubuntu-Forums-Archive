---
title: "Disable GRUB or Bypass?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by elresleff on 2011-07-14
I have an issue with GRUB Loader... I dual boot my system with Win 7 and Ubuntu 10.04 and I am looking to boot to CD in order to rebuild  my Windows boot partition but the GRUB loader keeps coming up, not letting me get to the setup program on the DVD. I have  made my CD/DVD drive the first boot device, but GRUB just loads and  there is no way to do what I need to do on my Windows partition.

I have Win 7 Pro 32 bit on Partition 1 and want to rebuild this  partition with Win 7 Ultimate 64 bit. I also want to keep my Ubuntu  partition the way it is. I do NOT want to uninstall and start over. I  would like to know how to rearrange the boot order in the GRUB menu - if  that is possible...

Any step-by-step instructions would be appreciated...

---

### Post by wildmanne39 on 2011-07-14
> **elresleff said:**
> I have an issue with GRUB Loader... I dual boot my system with Win 7 and Ubuntu 10.04 and I am looking to boot to CD in order to rebuild  my Windows boot partition but the GRUB loader keeps coming up, not letting me get to the setup program on the DVD. I have  made my CD/DVD drive the first boot device, but GRUB just loads and  there is no way to do what I need to do on my Windows partition.

I have Win 7 Pro 32 bit on Partition 1 and want to rebuild this  partition with Win 7 Ultimate 64 bit. I also want to keep my Ubuntu  partition the way it is. I do NOT want to uninstall and start over. I  would like to know how to rearrange the boot order in the GRUB menu - if  that is possible...

Any step-by-step instructions would be appreciated...
Hi, when your system starts up you can change boot order in the bios the screen will tell you the key you need to enter do it, but it will go by quick so watch closely.

---

### Post by alphacrucis2 on 2011-07-14
> **elresleff said:**
> I have an issue with GRUB Loader... I dual boot my system with Win 7 and Ubuntu 10.04 and I am looking to boot to CD in order to rebuild  my Windows boot partition but the GRUB loader keeps coming up, not letting me get to the setup program on the DVD. I have  made my CD/DVD drive the first boot device, but GRUB just loads and  there is no way to do what I need to do on my Windows partition.

I have Win 7 Pro 32 bit on Partition 1 and want to rebuild this  partition with Win 7 Ultimate 64 bit. I also want to keep my Ubuntu  partition the way it is. I do NOT want to uninstall and start over. I  would like to know how to rearrange the boot order in the GRUB menu - if  that is possible...

Any step-by-step instructions would be appreciated...

Grub has nothing to do with booting CD or DVD. That is done by boot order setting in the BIOS.

---

### Post by Wim Sturkenboom on 2011-07-14
The often used keys to access the BIOS are <del> and <F2>. <F12> is often used to change the boot order once.

And that is indeed before Grub starts.

PS
When you install windows, it will overwrite the MBR and is a result you will loose grub. Before you start the exercise, look up how you can recover grub after windows has wiped it. Else you can't access Ubuntu

---

### Post by elresleff on 2011-07-14
Thanks for the quick responses...

I've already gone into the BIOS and made my CD/DVD Drive the first boot device.

Any other suggestions?

---

### Post by Snowboi on 2011-07-14
> **elresleff said:**
> Thanks for the quick responses...

I've already gone into the BIOS and made my CD/DVD Drive the first boot device.

Any other suggestions?

Upon startup it should be a key in order to switch between boot devices, when booting up look for a key (like f12 on my computer).
If it does not work ill post another solution i have.

---

### Post by sixthwheel on 2011-07-15
The OP is asking how to change the boot order in GRUB.


> I would like to know how to rearrange the boot order in the GRUB menu - if that is possible...


---

### Post by elresleff on 2011-07-15
Yes, upon boot up I hit the appropriate key to get the boot menu and selected CD/DVD and it begins to read the DVD in the drive and then at approx 2-3 seconds the GRUB Loader displays....

Question: If I am running 64bit Win 7, should I run 64bit Ubuntu? Or - if I run 64bit Windows... must I run 64bit Ubuntu?

If so, I could just start over from scratch. I just wanted to avoid having to do this.

---

### Post by westie457 on 2011-07-15
Have you double-checked that your computer is capable of running a 64-bit operating system. Mine cannot and the last time I tried to install 64-bit in ignorance the Install program was thrown away and the system rebooted into Windows. This was before I had installed Ubuntu on it.

---

### Post by elresleff on 2011-07-15
Yes, It's capable. Lenovo ThinkPad T500

---

### Post by westie457 on 2011-07-15
Another silly mistake I have made with Windows install discs is ignored the line of text on the screen which states 'Press any key to boot from CD/DVD .....'. 

You have about 5 seconds to decide, otherwise the box hands booting over to the 1st hard drive.

One other thing to mention is Windows install discs override whatever settings are in the bios and are read regardless. Hence the line of text.

---

### Post by Wim Sturkenboom on 2011-07-16
> **elresleff said:**
> Yes, upon boot up I hit the appropriate key to get the boot menu and selected CD/DVD and it begins to read the DVD in the drive and then at approx 2-3 seconds the GRUB Loader displays....
Might be a corrupt CD/DVD; do you have the option to check in another PC?

> **elresleff said:**
> Question: If I am running 64bit Win 7, should I run 64bit Ubuntu? Or - if I run 64bit Windows... must I run 64bit Ubuntu?

No, you can use any combination (32/32, 64/64, 32/64 and 64/32 (windows/ubuntu respectively)

---

### Post by amjjawad on 2011-07-16
> **elresleff said:**
> Yes, upon boot up I hit the appropriate key to get the boot menu and selected CD/DVD and it begins to read the DVD in the drive and then at approx 2-3 seconds the GRUB Loader displays....
[/qupte]

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

GRUB2 is a Boot-Loader which is supposed to boot an OS, it has NOTHING to do with Booting Devices.

If you go to your BIOS and disable booting from HDD, there will be no GRUB menu.

If your machine is skipping booting from CD/DVD that means either your CD/DVD Drive is not working OR the CD/DVD is NOT bootable, period.



[QUOTE]Question: If I am running 64bit Win 7, should I run 64bit Ubuntu? Or - if I run 64bit Windows... must I run 64bit Ubuntu?

If your CPU is 64-bit then >> You can use either 32-bit OS or 64-bit OS.

If your CPU is 32-bit then >> You MUST use 32-bit OS.

---

### Post by elresleff on 2011-07-16
amjjawad... Great suggestions... I'll give that a try...

---

### Post by amjjawad on 2011-07-16
> **elresleff said:**
> amjjawad... Great suggestions... I'll give that a try...

Waiting for your feedback :)

---

### Post by elresleff on 2011-08-07
Hi amjjawad...

Finally got around to responding. Your suggestion worked... but the issue I really had was getting the USB to format correctly as a bootable device. Once I had that taken care of, and then pressed F12 for the boot menu, I was able to select the usb and launched the setup with no problem. 

The other suggestion of doing the Windows Easy Transfer was great also (whoever suggested that).

Appreciate all the suggestions!

Ed

---

### Post by amjjawad on 2011-08-07
> **elresleff said:**
> Hi amjjawad...

Finally got around to responding. Your suggestion worked... but the issue I really had was getting the USB to format correctly as a bootable device. Once I had that taken care of, and then pressed F12 for the boot menu, I was able to select the usb and launched the setup with no problem. 

The other suggestion of doing the Windows Easy Transfer was great also (whoever suggested that).

Appreciate all the suggestions!

Ed

Glad to know that :)
If you have another Q, please don't hesitate to ask :)

---

