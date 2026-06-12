---
title: "Wubi worked but iso won't boot from CD or USB?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by Iminister on 2010-09-17
After using Wubi I thought the rest of learning Ubuntu would be easy. Wrong so far.

I have a 2004 or so Walmart box Emachine (T2862) with 500mb Ram on which I am trying to get the hang of Ubuntu. It has the original Windows XP and I used Wubi to install Kubuntu 10.04. Kubuntu works fine... finds my home wireless better than XP. I tried Ubuntu 10.04 on another computer and liked that better. I wanted to take the plunge and just put Ubuntu on the machine but I can't get it to read the image.

When I don't let it boot from the hard disk it says the following.

Intel(R) Boot Agent Version 4.1.08
Copyright (C) 1997-2002, Intel Corporation

Intel (R) Boot Agent PXE Base Code (BA1210BC)
Copyright (C) 1997-2003, Intel Corporation

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent


I followed the USB drive information to the letter when downloading Ubuntu. Now, that is not the only thing on the drive but I don't know what difference that would make. The CD however is only the iso I burned from Windows Vista without going through the directions. 

Everything is plugged in by the way because it works when I boot up to Kubuntu and can see the CD and the USB drive.

Well, what's next. Do I have to erase the hard drive. If I do I want to know the iso will work!

Thanks for your time. I'm really trying to understand.

---

### Post by rcayea on 2010-09-17
Sorry if you made this clear, but are you booting from the cd(iso) you want to install?

---

### Post by Iminister on 2010-09-17
> **rcayea said:**
> Sorry if you made this clear, but are you booting from the cd(iso) you want to install?

Thanks for your response rcayea! I am trying to boot from either a cd which has Ubuntu 10.04 on it or the USB drive that has the same version of Ubuntu on it. I have tried either by switching how the computer boots. I even turned off the HD and it gives me this error with either the cd drive ore the USB drive.

---

### Post by rcayea on 2010-09-17
> **Iminister said:**
> Thanks for your response rcayea! I am trying to boot from either a cd which has Ubuntu 10.04 on it or the USB drive that has the same version of Ubuntu on it. I have tried either by switching how the computer boots. I even turned off the HD and it gives me this error with either the cd drive ore the USB drive.

Have you tried updating BIOS?

This definitely is interesting.

---

### Post by Iminister on 2010-09-18
> **rcayea said:**
> Have you tried updating BIOS?

This definitely is interesting.

No, I expected Ubuntu to be a bit easier than this. Updating BIOS might be beyond my understanding. I tried overclocking and that hurt my brain.

---

### Post by beew on 2010-09-18
> I am trying to boot from either a cd which has Ubuntu 10.04 on it or the USB drive that has the same version of Ubuntu on it.

What do you get? Nothing boot or does it just booting back into Windows? If it is the latter you need to set your bios to boot from CD or usb (Press F10 or some other special key to get into bios while booting, the exact key depends on your machine but it will tell you on boot)  In some cases (like my Samsung) even that wouldn't work, you would have to press a special key (like esc, or F12 or whatever depending on your hardware, but usually they will tell you when the computer boots) to bring up the one time boot menu and reset the boot sequence on booting.

Wubi is not a good way to try Linux IMO. It runs inside Windows and its behaviour would probably depend somehow on the Windows host.

---

### Post by bcbc on 2010-09-19
> **beew said:**
> Wubi is not a good way to try Linux IMO. It runs inside Windows and its behaviour would probably depend somehow on the Windows host.

You're entitled to your opinion, however you are incorrect regarding wubi. It does not 'run in windows' (other than the initial installation) and its behaviour does not depend on windows in any way. In fact, it's a real Ubuntu install that runs natively; what is different is that it uses a virtual disk that is stored on an ntfs or fat32 partition. If you feel the need to criticize it, at least get your facts straight.

To the OP, if you are trying to create a live USB do it from Kubuntu: System, Administration, USB Startup disk creator. If you can't boot a live USB or CD, then odds are there is either something wrong with the medium, the hardware, or the way the CD/USBs have been created.

---

