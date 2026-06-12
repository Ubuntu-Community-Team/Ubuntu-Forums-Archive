---
title: "Monitor Resolution"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Dnmac on 2010-11-22
Hi I have just done a clean installation of Ubunto10.10. If I set the monitor resolution to the highest 1366x768 I have hundreds of small black horizontal lines across the screen. Only when I go down to 800x600 do they go away, but then the picture is really low res. Please note I am an absolute beginner so step by step help would be appreciated. Thanks

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]Can you tell about your monitor **Max-support resolution** to us..

so that it will help others to trace your problem..

however... See the link [/SIZE][http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

Good Luck:p
[SIZE=2]
[/SIZE]

---

### Post by Dnmac on 2010-11-22
Max resolution I have where the monitor works without lines is 800x600 (4:3) Refresh rate 60hz
Thanks

---

### Post by tajiknomi on 2010-11-22
[SIZE=2]First paste it in terminal"**xrandr**" and it will show  you the **range** of  your monitor resolution min & max.[/SIZE]

[SIZE=2]Am not able to fix this problem yet(because m also new to linux), but my suggestion will be...1st you should check your graphics card whether its drivers are installed or not, most Graphics are Installed by **Default** in Ubuntu But some may not...
Go to...

System>Administration>Hardware driver(Click on it)

it will scan your hardware,if it Trace driver for your **Video-card**,it will show you and u just has to **enable** it.
Moreover , If you get a Message "**No Proprietary Driver's for this system**"
then this means that Ubuntu hasn't such **Driver's **in it cache, you should Download it from **manufacturer web-site**,and install it manually...

You should also find it Helpful.... [/SIZE][https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution")
[SIZE=2]
And let other to see this thread,hope someone fix this...
[/SIZE]

---

