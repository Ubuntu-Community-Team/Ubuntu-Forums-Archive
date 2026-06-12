---
title: "Help! Stuck with easypeasy ubuntu, can't boot into windows xp"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by zarboga on 2010-06-16
Hye..
I was trying to install ubuntu  easyPeasy on my asus EEEpc 1005HA, and I thought I was being able to  boot to my Windows XP after finish installation, but it didn't happen as  I thought, and unfortunately there is NO boot selection for Windows XP,  as it only has 4 selections which are :

ubuntu blablabla 
ubuntu  blablabla (recovery)
memory test
memory test

please  someone guide me, how to get into my Windows XP, I'm totally lost and I  don't know anything about the code/terminal/script/whatsoever, I'm just  playing around with Ubuntu as attracted to their interfaces and themes.

Help  Help!

P/S: I didn't formatted my hard disk , and the Windows partition is still untouched during the installation

---

### Post by eriktheblu on 2010-06-16
1. Boot Ubuntu.

2. Open a terminal (typically Applications>>Accessories)

3. Enter this command:
```
sudo update-grub
```

4. Enter your password (the password will *not* display, there will be no placeholders)

5. Wait for the process to complete, report any errors.

6. If there are no errors, reboot and select MS Windows from the Grub menu.


<assumption>I'm assuming you are using a recent version with Grub2</assumption>

---

