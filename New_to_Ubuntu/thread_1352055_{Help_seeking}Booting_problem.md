---
title: "{Help seeking}Booting problem"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by YuSheng Hu on 2009-12-11
haha, got it lol.
original chinese article: [http://narmy.cn/linux/read.php/105.htm](http://narmy.cn/linux/read.php/105.htm)

grub>ls
grub>ls (hd0,x)/               #find out the wubi installation partition x, which has /ubuntu folder
grub>insmod ntfs             #load ntfs module, bcoz WUBI installed ubuntu on ntfs-formatted partition
grub>set root=(hd0,5)      #here (hd0,5) is the partition where the /ubuntu folder locates
grub>ls $Boot                     #find out the UUID which will be used for the next step
grub>search --no-floppy --fs-uuid --set *2250018e50016a3d*      #the italic number is the UUID above that we have found out
grub>loopback loop0 /ubuntu/disks/root.disk     #set loop0
grub>set root=(loop0)         #reset root
grub>linux /boot/vmlinuz*[tab]* root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash      #load kernal
grub>initrd /boot/initrd.img*[tab]*                 
gurb>boot

after entering the system, open the terminal, type the below commands:

sudo update-grub2
sudo reboot

-----------------------------------------------------------------------------------------------------

I am a newbie, i met power cut suddenly during updating my system using update manager. After i restarted my computer, my system directly entered into "GRUB" mode (no OS is found for booting). 
The version of GRUB i have is 1.97~beta4. there even has no* find* command.

How to recover from it? THX

---

