---
title: "test-run from disc"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by wagerofwar on 2011-02-17
I'm sure this is covered somewhere, but my question is, how do you run ubuntu from a disc without installing it to your computer and jeopardizing your hard drive, so that windows(vista) is still running normally?
can it be done without changing c disc configurations?
wage

---

### Post by Scunnered on 2011-02-17
You can run a live CD when you set your boot sequence to read the CD first. Having done this you will be able to try the OS but be aware that it will not be as fast as a full install.  You will not be able to save anything when using a live CD.

Hope this assists

---

### Post by JOHNNYG713 on 2011-02-17
> **Scunnered said:**
> .  You will not be able to save anything when using a live CD.
Hope this assists
Unless you save files to your harddrive,AKA Bimbows<, Recommend ("Downloads" folder In bimdows) with a UBUNTU folder, store your stuff there. any "changes" in configuration of Ubuntu will not be saved! You may use your "Live' CD?DVD as the O/S and your harddrive (Bimbows)  as a storage unit! OR install to a flashdrive (Recommend 4 GIG or better) with persistence, and take your Ubuntu with you ! And boot Your Ubuntu in any box that boot's from USB ! Which is something windows cant and will never do ! :p Just say'n ! Great luck with your new Ubuntu ! and Welcome Home ! :KS

---

### Post by coffeecat on 2011-02-17
As Scunnered says, make sure your BIOS is set to boot from the optical drive first.

When the CD first starts to boot, you will be briefly presented with a purple screen with two small icons at the bottom. Tap the space bar and you will then see a language chooser followed by a menu. The first choice on the menu is to run Ubuntu live from the CD (I can't remember the wording offhand). In my experience there is usually a long delay after pressing enter for this menu entry before the boot process starts.

If you don't tap a key when the two little icons appear, the boot process will take you to a choice of 'try Ubuntu' and 'install Ubuntu' or words to that effect. You can use the mouse on this screen. Click on try Ubuntu and you will be taken to the live desktop where you can try all the default apps. Be warned that the live desktop (and the bootup) is very slow - much, much slower than if you install it properly.

The live CD will not affect anything on your internal drive(s) **unless** you:

1 - start the installer (the launcher icon is on the desktop). This will obviously affect your internal disc.

2 - mount any internal partitions from the Places menu. This will enable you to read and write data from/to internal partitions. Avoid writing to your Windows C: partition. Vista has been known to take exception to this.

3 - open one of the partition editors (Gparted or Disk Utility) and edit partitions. This also will affect your internal disc.

---

### Post by maqtanim on 2011-02-17
> **wagerofwar said:**
>  how do you run ubuntu from a disc without installing it to your computer and jeopardizing your hard drive, so that windows(vista) is still running normally?

I guess you are asking how can you use the live CD? Well ... for that,

[LIST=1]
[*][Download Ubuntu]("http://www.ubuntu.com/desktop/get-ubuntu/download") ISO.
[*]Burn the ISO in a disc or make usb bootable. (details step-by-step instructions are [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"))
[*]Place the disc into your drive.
[*]Go to the boot menu and select CD or USB as the first boot device.
[*]Save that option and restart the PC.
[*]Now your PC will start in Ubuntu.
[*]You'll find 2 options, choose the "TRY UBUNTU" among them
[*]Now you are running ubuntu from a live cd.
[/LIST]

---

