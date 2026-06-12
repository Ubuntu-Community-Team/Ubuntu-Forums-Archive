---
title: "Help Installing Updates (Complete Newbie)"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by 2soos2 on 2011-06-21
Hi, a little about myself. I just figured out how to format a computer a couple days ago with no help at all.:D I formatted Vista, partitioned the hard drive into three sections: one for windows, one that&#347; common, and one for Linux.
Then I installed Windows 7 in parallel with Wubi Ubuntu 11.04. I downloaded the updates which took quite a bit of time, but then I read on the site that if I dedicated a partition to Linux then I might as well actually install Linux on that partition instead of inside Windows, so I did that.
Instead of having to download the updates again, I backed up the updates on a USB, but I can´t paste them into the folder (archives) because I don´t have privileges to do that. How would I overcome this problem? Please give me detailed code to paste into the terminal.
 
Also, I don't know why, but it seems that Ubuntu is slower with the normal install than it was with the Wubi install. Maybe I didn't install it properly?

---

### Post by dFlyer on 2011-06-21
I don't use wubi, and I'm not sure you can install the update from wubi in a standard install of ubuntu, but if it's possible you will need to use sudo for root access. Maybe someone can add more who uses wubi.

---

### Post by 2soos2 on 2011-06-21
I know that I have to use sudo, but I need to know how. (codes) You don't need to be a Wubi user to help me. It's just a matter of knowing how to copy and paste files to and from a directory.

---

### Post by meeples on 2011-06-21
press ALT + f2 and type "gksu nautilus", enter your password and that gives you root access to the file manager

---

### Post by dFlyer on 2011-06-21
Here are some manuals to read, at the terminal enter the following to learn about the codes:

man sudo
man gksu
man bash
man cp
man move
man dpkg
man apt-get
man rm
man apt

Above is just a short list as there are many more.

---

### Post by meeples on 2011-06-21
> **dFlyer said:**
> Here are some manuals to read, at the terminal enter the following to learn about the codes:

man sudo
man gksu
man bash
man cp
man move
man dpkg
man apt-get
man rm
man apt

Above is just a short list as there are many more.

way to overcomplicate things

---

### Post by 2soos2 on 2011-06-21
Thank you meeples that did the trick. :D
I was able to install the updates.
And thank you dFlyer, I´ll be sure to check out those tutorial commands.:) I´m sure they´ll come in handy.

But it's still kinda odd that Ubuntu is slower. The boot times are significantly more than what they were when I was using Wubi. Know what might be the problem? Btw, I tried to change the GRUB boot time to 0, and I changed it, but when I boot, it still waits the normal 10 seconds.

---

### Post by dFlyer on 2011-06-21
It seems he was giving the answer in post 4. If he want to use a Linux OS it's nice to start learning the command line. Not really required now a days but nice to know.

---

### Post by dFlyer on 2011-06-21
> **2soos2 said:**
> Thank you meeples that did the trick. :D
I was able to install the updates.
And thank you dFlyer, I´ll be sure to check out those tutorial commands.:) I´m sure they´ll come in handy.

But it's still kinda odd that Ubuntu is slower. The boot times are significantly more than what they were when I was using Wubi. Know what might be the problem? Btw, I tried to change the GRUB boot time to 0, and I changed it, but when I boot, it still waits the normal 10 seconds.

I'd say 10 seconds to login screen is pretty good compared to the time it take my daughter to boot windows 7 to the login screen. It takes me 13 seconds from on to login.

---

### Post by 2soos2 on 2011-06-21
> **dFlyer said:**
> It seems he was giving the answer in post 4. If he want to use a Linux OS it's nice to start learning the command line. Not really required now a days but nice to know.


It also seems like you just point out the obvious and don't really reply to what I'm saying.
The 10 seconds wait I was talking about referred to the Boot loader page (GRUB), not the actual boot time. The point is, I set GRUB to not wait at all, but it still waits the default 10 seconds.

And currently Windows 7 on my machine loads faster than Linux which is very disappointing.

And I know that if I'm to continue with Linux, I'm to learn the commands, but I haven't made that decision yet.

---

### Post by dFlyer on 2011-06-21
> **2soos2 said:**
> It also seems like you just point out the obvious and don't really reply to what I'm saying.
The 10 seconds wait I was talking about referred to the Boot loader page (GRUB), not the actual boot time. The point is, I set GRUB to not wait at all, but it still waits the default 10 seconds.

And currently Windows 7 on my machine loads faster than Linux which is very disappointing.

And I know that if I'm to continue with Linux, I'm to learn the commands, but I haven't made that decision yet.

I believe the 10 seconds you are referring than is your system BIOS/System ram checks on boot. You should be able to turn them off in you BIOS.

---

### Post by dFlyer on 2011-06-21
Sorry for the double post. I just woke up, I believe your referring to the Grub screen to choose between Ubuntu and windows. If thats the case and you have already changed that to 0, what did you set as your default start program? did you run grub update after the change?

---

### Post by hunter99507 on 2011-06-22
The easiest way to manage grub is to install "startup-manager" from the software center. That has the timeout feature along with more features. I think that may help. Good luck and welcome to ubuntu.

---

### Post by wildmanne39 on 2011-06-22
Hi, I thought he was also booting windows if he sets it to 0 then he will not be able to choose which one to boot too. I have mine set to 3 seconds.

---

### Post by 2soos2 on 2011-06-23
> **hunter99507 said:**
> The easiest way to manage grub is to install "startup-manager" from the software center. That has the timeout feature along with more features. I think that may help. Good luck and welcome to ubuntu.

Thank you hunter. That I downloaded it and changed the boot menu time, and it worked perfectly. :D

---

