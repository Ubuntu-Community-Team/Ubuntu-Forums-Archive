---
title: "Two HDD, XP Pro and Ubuntu"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-04-17
HP Pavilion a1125c- 1gig Ram- 3.20 GHz- C:XP Pro 200gig- & [No Drive letter] 80gig, new HD. I installed the new SATA 80gig HD yesterday and installed Ubuntu, thinking the system would use [Boot.INI] to select the HD. I want Ubuntu to be primary drive to browse the internet and use email, and let the kids use XP to play their games OFF LINE.  My XP guy told me this morning, NOT SO.  He said that function would now be in GRUB.  I don't know if it matters now or not but the Ubuntu sys never got assigned a drive letter, according to windows it is a Primary Basic Drive.  On bootup I have to hit "Esc" to bring up the Boot Sequence and select the Ubuntu HD.  This is not the end of the world, I was hoping to go there automaticaly though.

---

### Post by sadaruwan12 on 2009-04-17
Hi,

  I might be able to help you 'cos Im doing the same thing with my PC XP on 160 GB SATA and Ubuntu on 80Gb PATA but I don't have any problem booting in to Ubuntu. Before I can help you like to know what is the Ubuntu version you're using. And like to know witch HDD is your boot hard disk you can check this in your BIOS under hard disk priority.

---

### Post by Bachstelze on 2009-04-17
> **Yed Ied said:**
> On bootup I have to hit "Esc" to bring up the Boot Sequence and select the Ubuntu HD.  This is not the end of the world, I was hoping to go there automaticaly though.

Probably you just need to go in your BIOS and select your Ubuntu hard drive as the primary boot device and all will be fine.

---

### Post by LowSky on 2009-04-17
How did you install Ubuntu, Live CD or Wubi?

When I installed Ubuntu from the LiveCD, it install just fine, and GRUB allows me to pick and choose between XP and Ubuntu.. Just make sur ethe Ubuntu hard drive is set to be the bootable hard drive from the Computer's BIOS.

---

### Post by Yed Ied on 2009-04-17
Ubuntu 8.10.  I have it on my laptop and have installed it on several other machines.  When I get Boot Sequence, the Windows HD is Primary, and I have to select the Ubuntu sys.  I've gone into Bios and haven't been able to get the Ubuntu disk out of second place.  I don't know if not having a Drive Letter would have anything to do with it, but I would think not.  When I disconnect the Windows HD, it boots into Safe Mode.  
Thanks for input.

---

### Post by sadaruwan12 on 2009-04-17
What do you mean by booting into safe mode. When you disconnect the windos XP drive system will not detect it and will take your 80GB as the primary boot disk and will show the GRUB OS selection screen so I think there must be some thing wrong with your BIOS or the hard disk MBR. when you go to your BIOS you'll see both your drives under Hard disk priority and select you UBUNTU installed HDD and press page up and down buttons or the Plus and Minus buttons on the number pad that'll help you to move your SATA drive as your primary boot disk and one other thing is your both HDDs SATA ?

---

### Post by eriqjaffe on 2009-04-17
Are you getting into GRUB at all?  Or does your computer just boot straight into Windows?

If you're getting into GRUB, you can edit the /boot/grub/menu.lst in Ubuntu to make Ubuntu the default.

As far as why you don't get a drive letter on the Ubuntu volume in Windows, that's because Windows doesn't natively support the EXT2/3 file system.  You can install [Ext2 IFS](http://www.fs-driver.org/) in Windows, which will let Windows assign a drive letter.

---

### Post by LowSky on 2009-04-17
Drive letters have nothing to do withh your bios. Infact only windows uses drive letters.

---

### Post by Yed Ied on 2009-04-17
Thanks everyone, I've learned from you all.  I went into setup and selected BOOT.  The Windows disk still in Primary.  I disabled it and it automatically dropped into second position.  The Ubuntu disk was in Primary and Windows in Secondary Disabled.  I went into that and enabled it, PROBLEM SOLVED.  I'm sure it probably wasn't proper Geek protocol, but I'll copy everything you all have suggested and be better at it next time.
thanks

---

