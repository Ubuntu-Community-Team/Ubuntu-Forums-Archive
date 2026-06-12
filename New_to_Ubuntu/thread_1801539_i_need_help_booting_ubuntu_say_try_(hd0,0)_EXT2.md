---
title: "i need help booting ubuntu say try (hd0,0) EXT2 ?"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by mj360 on 2011-07-10
i have ubuntu install in windows, but when i tried to boot to ubuntu, it say try (hd0,0) EXT2 this started when i tried to downgrade from 11.04 back to 10.10 cause i was having serious problems with 11.04 so that why tried to downgrade. so i uninstall wubi and reinstall and i get the same thing. i been using a program called super grub disk to boot to ubuntu, so can someone please help me with this ? 

also when i at updates to ubuntu after reinstall it, it remove the windows boot manager, when i get the windows boot manager back, ubuntu goes back to saying try (hd0,0) EXT2 :(

---

### Post by bcbc on 2011-07-10
This is caused by grub4dos hanging on an ext3 or ext4 partition - in your case the /dev/sda1 partition. The version of grub4dos used by current wubi does not handle this (this will be fixed in 11.10)

Anyway - so you cannot boot a wubi install while you have /dev/sda1 as an ext3 or ext4 partition. If you're not using it, just delete and reformat /dev/sda1 as ntfs (or just reformatting as ext2 would work as well).

But for interest sake - since you seem to have a weird setup - why don't you run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by mj360 on 2011-07-11
thanks for the reply but i tried the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript") but it's not working it say no such file ?

---

### Post by Blasphemist on 2011-07-11
Please use these instructions.
> boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.

**How to use the boot info script**

Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
Download the Boot Info Script
Extract the zip file to a directory of your choice.
Open a terminal (Applications -> Accessories -> Terminal in Gnome) and type :
```
sudo bash [path/to/the/download_folder]/boot_info_script.sh
```
For example if you downloaded the file to the desktop, use:
```
sudo bash ~/Desktop/boot_info_script.sh
```
If your operation system does not use sudo, use:
```
su 
bash ~/Desktop/boot_info_script.sh
```
You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
Open RESULTS.txt in your favorite text editor.
If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

### Post by mj360 on 2011-07-12
well i tried this but it still not working i seem to be having more problems, now it just started updating to 11.04 once i get to the desktop, on the livecd, and when i use super grue disk to boot now it say could not uodate iceauthority file.
thanks for the help everyone but i'm just going to wipe the hard drive.

thanks:D

---

