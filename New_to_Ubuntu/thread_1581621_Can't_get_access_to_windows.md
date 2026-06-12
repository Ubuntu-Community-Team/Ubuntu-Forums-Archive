---
title: "Can't get access to windows"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by Azhargola on 2010-09-25
hi
i've winXp and ubuntu 9.10 installed in my PC. at first i was able to dual boot both OS.
lately i've upgraded to ubuntu 10.04 via the internet, and now when my PC switch on, i can't boot into winXP. infact the WinXP option doesn't appear on the grub menu list when the system start up.
any idea how to solve this problem please. i'm a newbie.

---

### Post by Jakey_TheSnake on 2010-09-25
Try running "sudo update-grub" from the terminal, then restarting.

---

### Post by Rubi1200 on 2010-09-25
Hi and welcome to the forums :)

Did you install Ubuntu on a separate partition or inside Windows via Wubi?

---

### Post by Azhargola on 2010-09-27
@ Rubi1200
Hi,
I have install it on another partition

---

### Post by jtarin on 2010-09-27
Then do as Jakey_TheSnake suggest. In Ubuntu open a terminal and issue the comand ```
sudo update-grub
```watch the output of the command and it should list Windows.

---

