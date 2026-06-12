---
title: "Dual-Boot with 2 HDs?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by tarshoduze on 2011-04-09
Hi to all! I will be installing Ubuntu soon, so I really need to confirm this. If I have 2 HDs, one is Windows and the other is blank/formatted, if I make the Windows HD the slave (via the BIOS settings?) and the blank HD the master (via BIOS settings?), then boot Ubuntu using the LiveCD then install it in the master HD (specifically how?), will I dual-boot with Windows in GRUB?
Please also answer the questions in parentheses.
Thank you very much! I wish I can contribute, too, but I have questions, mostly...

---

### Post by loseby on 2011-04-09
I have a similar setup and except for problems with Graphic cards it works great. When you install Ubuntu on your bootable hard drive it will detect Windows and put an entry in the GRUB manager. So when you boot you can just cursor down to windows and select that

---

### Post by seawolf167 on 2011-04-11
You don't have to mark any of the drives as slave & master unless you have old school PATA drives (and even then you should be using the cable select mode). The only BIOS setting you should need to make is to ensure that your have cd booting enabled and prioritized above HDD booting.

Simply select the drive you wish to install Ubuntu on during the installation, then install GRUB to that harddrive. GRUB will boot Windows by pointing to the Windows Loader located on the Windows hdd/partition. [Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is the dual boot how-to.

If you want to run it safe, you can unplug your Windows hdd and install to the blank hdd alone, then boot up Ubuntu (after it's all installed and your Windows drive is plugged back in) then run the command

```
sudo update-grub
```

to find and add the Windows loader to the GRUB2 menu

---

### Post by seawolf167 on 2011-04-11
> **losbey said:**
> I have a similar setup and except for problems with Graphic cards it works great. When you install Ubuntu on your bootable hard drive it will detect Windows and put an entry in the GRUB manager. So when you boot you can just cursor down to windows and select that

The graphics problems are independent of hdd hardware - ensure you have the graphics drivers installed. Either from System -> Administration -> Hardware Drivers or from Nvidia/ATI's website (where you can download their proprietary graphics driver suites)

---

### Post by tarshoduze on 2011-04-17
> **seawolf167 said:**
> You don't have to mark any of the drives as slave & master unless you have old school PATA drives (and even then you should be using the cable select mode). The only BIOS setting you should need to make is to ensure that your have cd booting enabled and prioritized above HDD booting.

Simply select the drive you wish to install Ubuntu on during the installation, then install GRUB to that harddrive. GRUB will boot Windows by pointing to the Windows Loader located on the Windows hdd/partition. [Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is the dual boot how-to.

If you want to run it safe, you can unplug your Windows hdd and install to the blank hdd alone, then boot up Ubuntu (after it's all installed and your Windows drive is plugged back in) then run the command

```
sudo update-grub
```to find and add the Windows loader to the GRUB2 menu
Thank you very much!!!

---

### Post by seawolf167 on 2011-04-18
No problem - glad you got it working!

---

