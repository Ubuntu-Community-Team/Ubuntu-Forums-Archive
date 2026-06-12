---
title: "Downloading Ubuntu 10.10onto a lap top with Windows 7"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-15
How do I down load Ubuntu 10.10 onto a Laptop ASUS with Windows 7 please? In simple terms please as it looks very complicated.
Many thanks

---

### Post by Tijssiej on 2010-11-15
Do you want to dual boot? Or replace windows 7 with ubuntu?

---

### Post by Mark Phelps on 2010-11-15
If you're NOT looking to completely replace Win7 on the laptop, then BEFORE you do anything else, do the following:
1) Start the laptop
2) Go into the Backup feature
3) Select the option to create and burn a Win7 Repair CD
4) Stick in a blank CD
5) When done, set the CD aside.  You will find this invaluable later if you need to restore the Win7 boot loader as a result of problems with setting up dual-boot with Ubuntu.

---

### Post by 2un@ on 2010-11-15
Follow this here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I'm also new to it & tried it 1st in a VM in win7 but it didn't run so great,I found it better installed to the drive properly working as a dual boot.
(Laptop here also) Had no bad issues...Good Luck!
PS: i created a new partition on my HDD from within win7 1st so there was no mix up as to where the install was going to.

---

### Post by ian19jam on 2010-11-16
Thanks for the advice but I do not wish to keep WIN7 prefer to use Ubuntu 10.10. Therefore how do I download onto a USB stick or is it better with a CD? Please again in simple terms. Thanks

---

### Post by Blutkoete on 2010-11-16
Hello!

I'd use a CD, as it's easier to create the CD than the USB stick under Windows (in my opinion).

Download the ISO file here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Stick with the recommended options (10.10/32bit) if you're not sure.

When the download is done, switch to your download folder, right-click it and chose "Burn image to CD ..." from the context menu (of course you'll need an empty CD for that). Restart your computer with the CD in the drive and look if it boots from that.

If not, you'll have to switch the boot sequence in the BIOS which we can explain to you if it needs to be done.

It might be best to install Ubuntu alongside Windows first to test everything, as you won't be able to come here and ask questions if e.g. your Internet doesn't work ;).

Best regards,

Blutkoete

---

