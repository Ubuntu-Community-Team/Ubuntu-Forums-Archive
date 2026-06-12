---
title: "reinstall with dual-boot and separate /home partition"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by jkrtest on 2009-08-08
I would like go to a newer version with a re-install of Ubuntu.
I currently have a dual-boot setup with Vista. It's all on one physical disk:

/dev/sda1	ntfs	
/dev/sda2	ntfs (Vista)
/dev/sda4	>extended
/dev/sda5	ext3 (root)
/dev/sda6	ext3 (/home)
/dev/sda7	swap
/dev/sda3	ntfs (all my data)

Through terminal, I found grub on hd0,4

The live CD runs fine, and I'd like to wipe out the root partition and reinstall.
I have trouble understaning what I have to select in the manual partition UI. I think that's screen 4/7.

1) I assume, at minimum, I have to select and edit /dev/sda5, so that "/" shows up in that partition list. Correct?

2) If I feel so inclined, I could select to format that drive as ext3, but I don't necessarily have to. Correct? There are some threads I read aboout this, and there was some disagreement. To keep things simple, let's say I choose that option, so I have ext3, format yes, and mount as root selected in that dialog.

3) Since my /home is on another partion, do I have to do anything with this entry? Or does the install figure out that /dev/sda6 is my /home and reconnects all the wires during the install?

4) Grub: do I need to select anything, since it's already there and configured an works fine. I am not changing anything that GRUB should be concerned about. Correct? On install screen 7/7 I have that option to specify a grub install partition - I think the button is "Advanced..." The default is hd0 and the checkbox is selected. I assume for my purposes, I have to unselect it and the install will nt touch my old grub configuration, right?


Thanks for the help. I checked other threads for a few hours, but couldn't find a definitive answer for my configuration.

---

### Post by sam_delta on 2009-08-08
when you reinstall, ull have to do the following when the partition editor comes up:

select manual paritioning

select the old root partition "/", select format it to whatever filesystem you want, and select mount point "/" (root)
also, make sure you set the "boot option" to this partition

then, select your old home partition, and without formatting it, select mount point "home"

u might also want to reformat swap, as "swap"

grub will be reinstalled no problem, it'll detect window$ again. and will be installed in your new system root partition

anything else, ill be glad to help
if anything was unclear, ask again, ill explain w/ more detail!!:)
sam

---

### Post by jkrtest on 2009-08-08
Thanks for the quick reply!

If I understand correctly, I have to tell the installer that /dev/sda6 is my home partition, but by unselecting "format" the install will leave that partition alone, and I will have all my settings in place when the install is finished?

Do I have to select anything within the grub settings? I think the default is hd0. Is that the same as what I found (hd0,4)?
Or should I uncheck the "install grub" option?

---

### Post by sam_delta on 2009-08-08
> **jkrtest said:**
> Thanks for the quick reply!

If I understand correctly, I have to tell the installer that /dev/sda6 is my home partition, but by unselecting "format" the install will leave that partition alone, and I will have all my settings in place when the install is finished?
thats correct, itll only mount the partition as home without deleting its content (formatting)
> **jkrtest said:**
> 
Do I have to select anything within the grub settings? I think the default is hd0. Is that the same as what I found (hd0,4)?
Or should I uncheck the "install grub" option?
yes, select reinstall grub, and if im not wrong, the default entry (hd0,4) is your root partition, so leave it like that. you might want to get a second opinion on this, but im almost sure that that would be your new root.

i gotta go now, ill be back in a couple of  hours, i think i have some visual aid (video) on installing and leaving the home partition alone, ill see if i can find it
sam

---

### Post by jkrtest on 2009-08-08
Resolved!

All I had to do was run the updates and automount the ntsf partitions.

I'm up and running.

That was exactly what I needed - thanks for your help!

---

### Post by sam_delta on 2009-08-08
glad its working
enjoy ubuntu

sam

---

