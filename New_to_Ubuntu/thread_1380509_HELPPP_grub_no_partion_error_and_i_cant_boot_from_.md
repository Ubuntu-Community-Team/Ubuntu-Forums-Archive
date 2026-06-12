---
title: "HELPPP grub no partion error and i cant boot from live disk"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by sean00197 on 2010-01-13
Hi i deleted my ubuntu partition in windows 7 this also deleted the grub bootloader.. i looked at the other threads and they said to boot into a live cd the big problem is i cant boot into a cd .... ive tried the windows 7 disk and ubuntu and it just loads up grub i have in my bios to check for a cd first.... PLEASE HELP

---

### Post by Gone fishing on 2010-01-13
Bios vary it is usually the Del or F2 key (on some F11 to get to a boot menu)you need to click during boot to get into the Bios control program. You are then looking for boot order and changing it to boot from CD drive first.

---

### Post by sean00197 on 2010-01-13
yeah i did that.... cd loads first but any option i choose i get the grub error no partion so basically grub is loading before andyhting else no matter what the order is

---

### Post by Gone fishing on 2010-01-13
Sorry I miss understood, however it doesn't quite make sense if you boot from the Windows 7 install CD it shouldn't do anything with grub as it's booting from the CD (you can even boot with the HDs disconnected) you should then be able to select click 'Repair Your Computer'.
Click Command Prompt from the System Recovery Options.
and run BootRec.exe /fixmbr and you should be done

If it **attempts** to boot from the CD and fails then you will get back to grub. If this is the problem - is the CD scratched, dirty is the CD Drive faulty old? if so borrow an another. 

Are you selecting the right boot device in Bios? not USB CD or something strange like that?

---

### Post by sean00197 on 2010-01-13
Srry if im making this computer ill try to re-explain
first off im on a IBM thinkpad x41 tablet
I installed windows 7 on it and shrunk the primary partition so i could install linux ubuntu.
I installed ubuntu 9.10 ran perfectly fine.
I never used it so i went into the mangement option in my computer (windows) and erased the partitions that ubuntu was on.
I then restarted my computer and got the grub error no partition.
I have set the bios to load the cd first, but even tho i set that grub still runs.
So if i put in a windows or linux cd it does not give me the option to run from the cd.
When i turn on my computer the lenovo thing shows up loading all the bios and other stuff then goes straight to the grub error.

So far i have tried to run windows cd and a linux cd, i have also tried to run ubuntu from a usb flash drive with no luck idk if i set the usb drive up wrong but please help me THanks

P.S i have set the order that things load in the bios so that the cd boots first

---

