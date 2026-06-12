---
title: "Ubuntu froze and won't start up"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by mastadon89 on 2009-04-05
Well my Pc is dual booting Xp and Ubuntu. Any way so im on Ubuntu and I tried to open an .exe file with Wine. Next thing I know Everything freezes and stays that way. So i had to do a Hard shut down. When I restart my comp and try to load Ubuntu again I get an screen that sys it cant read secondary drive (im guessing it's not reading the partition) then when i choose Ubuntu to load I get a grub command line to type commands. I don't understand grub or better yet what the heck went wrong.

---

### Post by spiderbatdad on 2009-04-05
problem caused by hard shut down probably. Try to fix grub from the prompt you get grub>

enter: ```
 root (hdo, 
```
You should get a list of partitions:
For example if your ubuntu is #2 then run

```
root (hd0,2)
setup (hd0)
```

---

### Post by mastadon89 on 2009-04-05
This didn't work

When I typed 

root (hdo  I got an error

sothen I typed 

root(hd0  and i got "Error11: unrecognized device string or you ommitted the required DEVICE part which should lead to filename"

---

### Post by spiderbatdad on 2009-04-05
ok check this out.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
just start at step 4 "find /boot/grub/stage1" from the grub prompt.

---

### Post by mastadon89 on 2009-04-05
after i type "find /boot/grub/stage1" it says file not found

---

### Post by mastadon89 on 2009-04-05
If there is nothing else that'll work I'll just reinstall and plz tell what to do if Ubuntu freezes because i have re-installed this 4x already because of freezing.

---

### Post by mastadon89 on 2009-04-05
if its any help im runnin 8.10

---

### Post by presence1960 on 2009-04-05
> **mastadon89 said:**
> This didn't work

When I typed 

root (hdo  I got an error

sothen I typed 

root(hd0  and i got "Error11: unrecognized device string or you ommitted the required DEVICE part which should lead to filename"

that was a typo it should be root (hd0) not root (hd0

to restore GRUB try this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

You might have messed up your filesystem with the hard shutdown. If restoring GRUB does not work try running fsck from Live Cd in terminal ```
sudo fsck -CM /dev/sda1
``` where a is your HDD & 1 is your ubuntu partition. change to your setup accordingly.

---

