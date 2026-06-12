---
title: "Dual Boot Windows and Ubuntu Question"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by JJuel on 2010-09-22
Okay I am currently dual booting Windows Vista and Ubuntu. I am looking, however, to upgrade to Windows 7. I would like to do this without having to do a complete new install of Ubuntu. I am not going to just to put 7 over top of Vista I am going to do a clean install. 

Currently, Vista and Ubuntu are each on a separate hard drive from each other, but the Grub is installed on the Vista hdd. I am wondering how this is going to affect the grub, and what issues I really need to watch out for while doing this?

I am still very new to Ubuntu and dual booting. Any help about doing this would be greatly appreciated.

Thanks

---

### Post by arrimapirate on 2010-09-22
Welcome to Ubuntu!
Follow this link:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2
(include the word GRUB 2 when you copy the link)
If you have any questions feel free to ask.

---

### Post by SaintDanBert on 2010-09-23
Having separate drives for WinXX and *-buntu is a good thing. Most modern hardware can boot from any available HDD or DVD.

I'm not a win-doze maven, but I know this much:
[list]
[*]Install win-doze first -- it expects to own the computer
[*]Install linux next -- it knows to step around whatever is already there
[/list]

I've also learned that Win-7 will create two [primary] partitions during its install. With your two-drive environment, this will be easier for you. 

During your linux install, it will see the winXX parts. You also get a choice about where to write GRUBx.  Jaunty uses GRUB-legacy or GRUB-1.
Lucid uses GRUB-2. Same mission; different implementation. Do you know if your BIOS will let you select any of your HDD drives as a boot source? If so, then write your GRUB to the MBR of your linux drive leaving your winXX drive alone. Set your BIOS to default boot from your linux drive and VIOLA you are good to go. At startup, GRUB will be able to load from either drive and start either linux or winXX.

You can also tinker the boot details on your winXX drive (it used to be a hidden file BOOT.INI or similar) so that winXX gives you the options to boot either winXX or linux -- either directly or through GRUB. Whether you tinker win-boot or put GRUB on both MBRs, This is not all bad since you would have two ways to boot if you managed to trash (sic) things again. 

Good luck,
~~~ 0;-Dan

---

### Post by Mark Phelps on 2010-09-23
My recommendation, learned through lots of personal experience, in a two-drive situation, is to do the following:
1) Install each OS, including its boot loaders, to a separate drive -- with only a single drive connected at a time
2) When done, connect both drives but boot from the Ubuntu drive
3) Open a terminal in Ubuntu and enter "sudo update-grub".  This will autogenerate a new GRUB menu that will include entries for both OSs on the PC.

When you reboot, you will see the GRUB menu.

This is safer than messing around with the MBR on the Windows drive regarding inserting/removing GRUB.

---

### Post by JJuel on 2010-09-23
> **Mark Phelps said:**
> My recommendation, learned through lots of personal experience, in a two-drive situation, is to do the following:
1) Install each OS, including its boot loaders, to a separate drive -- with only a single drive connected at a time
2) When done, connect both drives but boot from the Ubuntu drive
3) Open a terminal in Ubuntu and enter "sudo update-grub".  This will autogenerate a new GRUB menu that will include entries for both OSs on the PC.

When you reboot, you will see the GRUB menu.

This is safer than messing around with the MBR on the Windows drive regarding inserting/removing GRUB.

Well this sounds good, but I want to leave the currently installed Ubuntu drive alone. I really just want to upgrade from Vista to 7 on the Windows drive. 

I didn't know if I just need to reinstall grub if it gets over written by the Windows MBR. Would it be the best idea to just upgrade Windows and completely reinstall Ubuntu too?

Thanks for all of your suggestions!

---

### Post by SaintDanBert on 2010-09-23
> **Mark Phelps said:**
> My recommendation, learned through lots of personal experience, in a two-drive situation, is to do the following:
1) Install each OS, including its boot loaders, to a separate drive -- with only a single drive connected at a time
2) When done, connect both drives but boot from the Ubuntu drive
3) Open a terminal in Ubuntu and enter "sudo update-grub".  This will autogenerate a new GRUB menu that will include entries for both OSs on the PC.

When you reboot, you will see the GRUB menu.

This is safer than messing around with the MBR on the Windows drive regarding inserting/removing GRUB.

When I learned this -- the first time -- we didn't have "update-grub" and I continue to forget it will find all available OS partitions for me.
I like this idea. A LOT!

~~~ 0;-Dan

---

### Post by sandyd on 2010-09-23
> **JJuel said:**
> Well this sounds good, but I want to leave the currently installed Ubuntu drive alone. I really just want to upgrade from Vista to 7 on the Windows drive. 

I didn't know if I just need to reinstall grub if it gets over written by the Windows MBR. Would it be the best idea to just upgrade Windows and completely reinstall Ubuntu too?

Thanks for all of your suggestions!
what about this.
We now install grub on the Ubuntu drive. After installing windows, set your system to boot from the ubuntu drive.

Then, you can easily switch the bootloader when you have trouble, and windows will not wipe out grub.

---

### Post by SaintDanBert on 2010-09-24
> **JJuel said:**
> Well this sounds good, but I want to leave the currently installed Ubuntu drive alone. I really just want to upgrade from Vista to 7 on the Windows drive. 

I didn't know if I just need to reinstall grub if it gets over written by the Windows MBR. Would it be the best idea to just upgrade Windows and completely reinstall Ubuntu too?

Thanks for all of your suggestions!

Putting win-7 on drive-1 and Ubuntu on drive-2 should not affect the grub in place on drive-2. **I like the suggestion to disconnect drive-2 while doing the win-7 install.** No connection? No possibility of changes!

I'm pretty sure that Win-7 will want to have two partitions on drive-1.
One for win7 itself and one for "special sauce." Take care about other parts of drive-1 as winXX tends to be heavy handed about taking over.

Bonne chance,
~~~ 0;-Dan

---

### Post by Mark Phelps on 2010-09-24
> **SaintDanBert said:**
> ... I'm pretty sure that Win-7 will want to have two partitions on drive-1.

Yeah, that's what it WANTS by default ... but if you format an NTFS partition in advance, you can install Win7 to that partition and do without the separate boot loader partition.  That second (boot loader) partition is only needed if you intend to encrypt your entire Win7 partition.

---

### Post by SaintDanBert on 2010-09-25
> **Mark Phelps said:**
> Yeah, that's what it WANTS by default ... but if you format an NTFS partition in advance, you can install Win7 to that partition and do without the separate boot loader partition.  That second (boot loader) partition is only needed if you intend to encrypt your entire Win7 partition.

That actually makes sense.  ENCRYPT "system space". CLEAR "boot space".
BIOS boots clear space which loads parts that can read encrypted space.

Merci,
~~~ 0;-Dan

---

