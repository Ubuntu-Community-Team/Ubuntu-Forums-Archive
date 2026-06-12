---
title: "No grub !!!"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by squrl on 2009-07-01
Is there a way to install 8.04 without grub from a standard 8.04 distro disk.

All of the problems I have had with ubuntu seem to revolve around grub and I would like to be shed of it.

Thanks

---

### Post by ivanvajar on 2009-07-01
What problems did you have? Please, be more specific with subjects.

---

### Post by squrl on 2009-07-04
I just want to be rid of grub.

---

### Post by presence1960 on 2009-07-04
> **squrl said:**
> I just want to be rid of grub.

GRUB does a great job of managing multiple OS boots. Compared to Neosmart BCD, windows bootmanager, etc GRUB is light years ahead of those. Maybe you just don't know how to configure GRUB, if that is the case that's what this forum is for.

Of course you can use what you want to load your OSs. You said you want to be rid of GRUB, what do you plan on using in it's place?

---

### Post by alphacrucis2 on 2009-07-04
I suppose you could install lilo instead of grub. You will have to manually configure it though every time Ubuntu does a kernel update though.

---

### Post by chaosdesigner on 2009-07-04
Normally you dont remove Grub, the only thing you could do is replace it. Maybe with NTLDR.

Same Thread: [http://ubuntuforums.org/showthread.php?t=115788](http://ubuntuforums.org/showthread.php?t=115788)

---

### Post by 7raTEYdCql on 2009-07-04
Won't setting up grub again be helpful. You can do that by booting into Live CD. THis should be of some help.[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Set_up_Grub_by_hand](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Set_up_Grub_by_hand)

Hope this is helpful

---

### Post by Don1500 on 2009-07-04
Of course if you just want to boot right into Ubuntu without the requests poised by Grub (Which OS do you want?) you can just change menu.lst to remove the time out.

Change to this:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0
```

---

### Post by squrl on 2009-07-05
The bios on my machine gives me the option of booting from whichever installed drive I choose as long as there is an OS on it. Grub has a different idea and does as it sees fit. My idea is to get rid of grub and I'll decide which drive or OS should boot. Thanks

---

### Post by Don1500 on 2009-07-05
> **squrl said:**
> The bios on my machine gives me the option of booting from whichever installed drive I choose as long as there is an OS on it. Grub has a different idea and does as it sees fit. My idea is to get rid of grub and I'll decide which drive or OS should boot. Thanks

same answer, use your system to select which OS to boot, 
1. Install your XP and Ubuntu on separate drives, without the other drive pluged in during install.

2. If you choose Ubuntu just have the timeout set to "0".

3. The XP drive will have a good MBR if you installed it with the Ubuntu drive unplugged.

This might do what you want. But I would use grub, it's much easier.

---

### Post by presence1960 on 2009-07-05
> **squrl said:**
> The bios on my machine gives me the option of booting from whichever installed drive I choose as long as there is an OS on it. Grub has a different idea and does as it sees fit. My idea is to get rid of grub and I'll decide which drive or OS should boot. Thanks

And so does practically everyone else's BIOS do this. The fact of the matter remains that you are not configuring GRUB properly and/or your boot order in BIOS does not match the order of your disks in ```
sudo fdisk -l
``` But it is your machine so you can do as you wish. I think you are making a mistake!

---

### Post by synapsys on 2009-07-05
> **squrl said:**
> The bios on my machine gives me the option of booting from whichever installed drive I choose as long as there is an OS on it. Grub has a different idea and does as it sees fit. My idea is to get rid of grub and I'll decide which drive or OS should boot. Thanks

I think you mis-understand the whole boot process.

Your bios can choose what drive to boot to, but it cannot physically boot an os. This job is done by a bootloader. Grub is a bootloader. Windows has it's own bootloader that works silently in the background. It loads windows the same way grub loads ubuntu, you just don't know that it's happening. Grub can also work silently in the background if you configure it properly.

---

