---
title: "Booting issue"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-18
hi.. i have ubuntu and xp both loaded in my system.. 

ubuntu is the second option in the boot menu..

whenever i select ubuntu in the boot menu,one more screen appears asking me if want to go back to the ubuntu menu,which has five options.. it says press ESC if u want to go back to menu
normal mode
recovery mode
some other kernel version normal mode
some other kernel version recovery mode
winXP

it takes some 7 or 8 sec to just check if i did or did not press an ESC key

can someone please help me on how to get rid of these and make ubuntu the default OS, so that when i press the power button on my system, ubuntu should load automatically without any of these hiccupps.... thank you

---

### Post by PurposeOfReason on 2009-01-18
In a terminal type:
```
gksudo gedit /boot/grub/menu.lst
```
Find the lines "timeout   xx
default   0"

Timeout is how long it takes for GRUB to select something on its own. Defaults is which it wants by default. You should have entries like this:
# (0) Arch Linux
title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/sda2 ro
initrd /boot/kernel26.img

The (0), is the entry. Change the default 0 to whichever one that corresponds with your Ubuntu install. BEFORE you do any of this run this command to make a backup

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

### Post by 73ckn797 on 2009-01-18
> **chethankrish said:**
> hi.. i have ubuntu and xp both loaded in my system.. 

ubuntu is the second option in the boot menu..

whenever i select ubuntu in the boot menu,one more screen appears asking me if want to go back to the ubuntu menu,which has five options.. it says press ESC if u want to go back to menu
normal mode
recovery mode
some other kernel version normal mode
some other kernel version recovery mode
winXP

it takes some 7 or 8 sec to just check if i did or did not press an ESC key

can someone please help me on how to get rid of these and make ubuntu the default OS, so that when i press the power button on my system, ubuntu should load automatically without any of these hiccupps.... thank you

It may help to see your grub menu choices also. Enter the following in Applications/Accessories/terminal

```
gksudo gedit /boot/grub/menu.lst
```You need to copy and paste the following similar info in a reply:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10
```and:```

## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Home Edition sp3
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```You will have something similar.

---

### Post by diablo75 on 2009-01-19
Sounds like you're working with a Wubi installation, which means you're dealing with a Wubi boot menu, plus the GRUB menu after selecting Ubuntu.  You'll have to make edits as noted above to reduce the timer on the GRUB menu, but if you want the timer reduced on the first menu that appears with the original 2 options:

"To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well."

Found that here:  [http://ubuntuforums.org/archive/index.php/t-759903.html](http://ubuntuforums.org/archive/index.php/t-759903.html)

---

### Post by chethankrish on 2009-01-19
> **PurposeOfReason said:**
> In a terminal type:
```
gksudo gedit /boot/grub/menu.lst
```
Find the lines "timeout   xx
default   0"

Timeout is how long it takes for GRUB to select something on its own. Defaults is which it wants by default. You should have entries like this:
# (0) Arch Linux
title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/sda2 ro
initrd /boot/kernel26.img

The (0), is the entry. Change the default 0 to whichever one that corresponds with your Ubuntu install. BEFORE you do any of this run this command to make a backup

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```


i typed  gksudo gedit /boot/grub/menu.list in terminal.. i got an empty menu.list window.. there was absolutely nothing in it.. i tried to close tat window and it gave me with 3 options...

close without saving       cancel        save

i selected close withot saving.. could you please tell me what is wrong with my system...

---

### Post by PurposeOfReason on 2009-01-19
Did you use wubi? If so read the other posts.

---

### Post by caljohnsmith on 2009-01-20
It sounds like you are probably using a Wubi install of Ubuntu (Ubuntu installed inside of Windows). How about looking in your Windows partition to see if you have a menu.lst:
```
C:\ubuntu\disks\boot\grub\menu.lst
```
If you have a C:\ubuntu directory and also the above menu.lst, you definitely have a Wubi install. You can modify that menu.lst and change the "timeout" time (look for that line near the top of the menu.lst file). If you want to modify the timeout time of the first menu you see where you choose between Ubuntu and Windows, you would need to modify the "timeout" line in the C:\boot.ini file. Let us know how it goes or if you run into problems.

---

