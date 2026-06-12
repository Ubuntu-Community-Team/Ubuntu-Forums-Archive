---
title: "Ubuntu From USB"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Andrew Jeyaraj on 2011-01-29
Sorry to be posting problems all the time.But recently ive been getting a large number of problems.

I installed ubuntu on a usb drive. I tried booting from it.
It worked fine until i got to the boot menu. when i selected ubuntu from the menu,the following error message came up.

"Error 17 Cannot Mount Selected Partition"

i used ubuntu "hardy heron"

i need to boot from the usb in order to help my friend get rid of a virus on his windows machine.

Configuration
Intel Core 2 Duo 2.3
1 gb ram
Simtronics Motherboard
:confused:

---

### Post by Andrew Jeyaraj on 2011-01-29
help would be greatly appreciated:)

---

### Post by C.S.Cameron on 2011-01-29
Try the following with 10.10:

Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 10 to 50 GB, Beginning, Ext4, and Mount point = "/" then OK.
Confirm "Device for boot loader installation" points to the correct drive. Default should be ok.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Wait until install is complete.

---

