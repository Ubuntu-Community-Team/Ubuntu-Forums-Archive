---
title: "Trouble with reattempted install"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by whatyeah3 on 2009-03-04
I have just finished building a computer running windows xp home. I installed ubuntu from the boot menu once, and it worked fine, but then I had hard drive trouble, so I had to reformat and try again. Now when I boot from the ubuntu disk, i get past the loading screen and just get a black screen with a blinking non responsive cursor in the top left corner. I used partion magic to create a linux swap space, thinking it would help, but to no avail. What went wrong?

---

### Post by dbbolton on 2009-03-04
> **whatyeah3 said:**
> I have just finished building a computer running windows xp home. I installed ubuntu from the boot menu once, and it worked fine, but then I had hard drive trouble, so I had to reformat and try again. Now when I boot from the ubuntu disk, i get past the loading screen and just get a black screen with a blinking non responsive cursor in the top left corner. I used partion magic to create a linux swap space, thinking it would help, but to no avail. What went wrong?
Which version are you trying to install?

This page might help you out: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by whatyeah3 on 2009-03-04
The version is 8.10.

Additionally, I used PartionMagic to create a Linux Swap partition, which is what I had before the reformat.

I checked the link you listed, but nothing there pertains to my problem. I can't find anything like this problem anywhere. Any other suggestions?

---

### Post by dbbolton on 2009-03-04
> **whatyeah3 said:**
> The version is 8.10.

Additionally, I used PartionMagic to create a Linux Swap partition, which is what I had before the reformat.

I checked the link you listed, but nothing there pertains to my problem. I can't find anything like this problem anywhere. Any other suggestions?
Well, the reason I suggested the boot options is that there could be a hardware issue that is preventing the CD from booting. I thought you meant that a Live CD was hanging during boot (like you were trying to install Ubuntu after reformatting), but you mean that you were trying to boot Ubuntu from your hard drive after reformatting the swap partition?

Even so, you can try a couple boot options in GRUB. Rather than hitting enter after selecting Ubuntu in Grub, type 'e' to edit the entry. Probably the second or third line will end with something like "ro quiet splash". Edit it to "ro noapic nolapic acpi=off" and see if Ubuntu will boot then. Note- this edit will not permanently alter your Grub menu entry.

---

### Post by whatyeah3 on 2009-03-06
No, I am trying to boot from the CD, not the hard drive. I simply reformatted because of an interrupted installation of XP. Not I can't install from the CD. GRUB doesn't even load.

---

### Post by indytim on 2009-03-06
So, if you can't boot to the LiveCD, 1 or 3 possibilities:
1.  Defective LiveCD (download and re-burn at slooow speed - do the md5 checksum).
2.  A hardware problem (multiple areas).
3.  BIOS not set to boot to CD-DVD (unlikely as you were able to boot to the partition editor.

Since you did not complete your XP installation, Ubuntu will probably default to installing on your first partition (may make Mr Redmond very un-happy if/when you decide to let him join the party).  

My advice is to resolve whatever is going on in your new PC and do the XP installation through completion.  Once that is done, either carve out some un-allocated space on the h/d for Ubuntu or get a copy of GParted Live and do the manual partition of (minimum) 1 ext3 partition and 1 swap.  Then select the "Manual partition option" on the installation.

IndyTim

---

### Post by whatyeah3 on 2009-03-06
I've checked my hardware, and there are no diagnosable problems or symptoms. I did check the CD for defects, and it turned up fine (using the Ubuntu boot menu and another XP program. Like I said, I had installed it once successfully, but then reformatted the entire HD. My XP installation is complete and functioning entirely fine (except that its the Home edition). It cant make it to the partition editor.

---

### Post by dbbolton on 2009-03-06
> **whatyeah3 said:**
> I've checked my hardware, and there are no diagnosable problems or symptoms. I did check the CD for defects, and it turned up fine (using the Ubuntu boot menu and another XP program. Like I said, I had installed it once successfully, but then reformatted the entire HD. My XP installation is complete and functioning entirely fine (except that its the Home edition). It cant make it to the partition editor.
Try booting the CD with these options too:
```

noapic nolapic acpi=off

```

---

### Post by sneeks on 2009-03-06
just a quickie,u said that xpdidnt install,where did it hang?

---

