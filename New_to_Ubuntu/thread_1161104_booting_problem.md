---
title: "booting problem"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by mkirizarry on 2009-05-16
:p Good Morning!  I just received ubuntu 9.04 desktop edition yesterday.  I am excited to be learning all about it.

I followed the install very carefully.  I already had windows xp installed on my primary hd.  I did a side by side install.  Hoping to preserve my windows.  When I rebooted I received a message while grub (which unfamiliar with) was loading, Error 21.  I have now booted from the cd, in order to see if I can solve this problem.

I have been out of the computer loop for a few years.  I am returning to school for computer applications and computer science in about 4 weeks.  So I am a little rusty and behind the times.

Any help would be greatly appreciated. :D  Thank you very much.

:) Peace, Miki

---

### Post by akimatsu123 on 2009-05-16
i suggest you look up what that error is, but i had the same error number when i installed linux on my external hdd (so i could boot it off different computers) but the installer had modified my mbr to look for grub on my primary hard disk inside my computer. of course, it couldnt find grub, and it kept teling me error 21.

so i would make sure that grub is in the right location. if ur more familiar with the windows bootloader, you can also choose to ues that one.

---

### Post by mkirizarry on 2009-05-16
Thank you.  Unfortunately it is not giving me an option to boot windows. I am hoping it is still there.:-?

---

### Post by reevine on 2009-05-16
ok what you want to do is redirect and install grub. make sure that you have your external drive connected. go to the terminal in ubuntu (in listed programs) and type (each line is new command):

```

sudo grub
find /boot/grub/stage1

```

let me know what you get.

---

### Post by goldblattster on 2009-05-16
hello, and welcome to the ubuntu forums. ):P
please load terminal. Terminal is where you can enter BASH commands in Linux, kinda like the command prompt is where you enter DOS commands in windows. Inside the terminal when you first start it, you should see
```
yourusername@yourusername-laptop:~$
```
or, if you are using a desktop,
```
yourusername@yourusername-desktop:~$
```
I have attached an image of an example of what it might look like.
Once terminal is loaded, please post what you see after you type in
```
sudo fdisk -l
```
and hit the enter button. Also, when you his the enter button, it will probably need your password, which is ok. Cheers! ;)

---

### Post by goldblattster on 2009-05-16
Ok. First, Make sure all your windows have an orangeish colour scheme. Then, go into terminal, and right click anywhere in the terminal. Then go to profiles>profile preferences. Select the colours tab, and make sure that the "use colours from system scheme" box is checked. Then click close. If the terminal does not let you right-click or if that or changing it to the defualt colour scheme does not work, tell me (or someone else)

---

