---
title: "Two grub menu"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by jmfa59 on 2009-06-12
Hello
I have three operating system Vista Mandriva and Ubuntu now I have to Grubs one comes after another when I choose a system to boot instead of booting that system it goes to another Grub menu and from there I can choose what system to boot.
THANKS

---

### Post by oldfred on 2009-06-12
I also have two grub menus, but I did this intentionally as I have 3 hard drives and Windows XP, ubuntu 32 bit and just installed on a new drive ubuntu 64 bit for testing. I was suprised that the clean install of the new 64 bit version found all the operating systems on my machine. I manually edited my initial grub to chainload to the new grub since I am only experimenting with the 64 bit version. 

If you want to remove for revise your grub I found an old thread the shows how to fix this: [http://ubuntuforums.org/showthread.php?t=671395]("http://ubuntuforums.org/sudo%20grub-install%20/dev/sda%20%28or%20whatever%20the%20disk%20is%29.") main command to edit is:
sudo grub-install /dev/sda  (or whatever the disk is).

---

