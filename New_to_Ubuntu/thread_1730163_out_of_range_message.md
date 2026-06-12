---
title: "out of range message"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by miz0ooo0 on 2011-04-15
[SIZE=3][B]i was user of windows but i decided to try Ubuntu on my PC so i made a bootable cd for Ubuntu 10.10 ,when installing it, i got "out of range " message 
so i switched my geforce 5200 vga card with another old one ATI 64 mb ,the installation goes without any errors and completed but this vga card is'nt good and i want to use my geforce 5200 
is there any solution to use it without out of range problem ??
    thnx for advance 
[/B][/SIZE]

---

### Post by rosencrantz on 2011-04-15
Looks like the nomodeset boot option is the thing for you:
[http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)

---

### Post by miz0ooo0 on 2011-04-16
thnx man it will be useful for me
but i tried to : change the line GRUB_CMDLINE_LINUX=""  to
 GRUB_CMDLINE_LINUX="nomodeset" 
as shown ,but i cant because it is a system file can not be edited 
if there is another method to change it plz tell me 
THNX

---

### Post by dnairb on 2011-04-16
You need to edit this file with sudo priveleges:

in terminal type:

```
gksudo gedit /etc/default/grub
```

enter your password, then edit the file and save. Then again in terminal run

```
sudo update-grub
```

then reboot

---

### Post by miz0ooo0 on 2011-04-16
when i type this code "
sudo update-grub

it ask me for password ,i tried to type my account password but i cant write anything
is there is something wrong i do ?

---

### Post by dnairb on 2011-04-16
> **miz0ooo0 said:**
> when i type this code "
sudo update-grub

it ask me for password ,i tried to type my account password but i cant write anything
is there is something wrong i do ?

That's how entering passwords in terminal work. You can't see your password as you type for security reasons.

---

### Post by miz0ooo0 on 2011-04-17
[SIZE=2][B]thnx, but there is any method to configure the nividia fx 5200 from grub menu before choosing the operating system? , because switching vga card is too pouring  work in addition to this ,the another card (ATI) has a problem in preview 
now i use the nividia fx 5200 it can only preview windows xp.
is there are any methods to configure this card to view ubuntu ?
[/B][/SIZE]

---

### Post by miz0ooo0 on 2011-04-18
[B][SIZE=2]thnx guys my problem is solved ,ubuntu 10.10 now working on nividia fx 5200 vga card ,the terminal codes solved this problem thnx too much :smile:
thnxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
[/SIZE][/B]

---

