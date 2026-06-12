---
title: "Ubuntu will not load to Desktop"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by diamondshark on 2009-06-12
[B]Ok, I thought I would ask the smartest people I know when it comes to linux things. Basically I've had the same exact problem occur 3 times now. After I install Ubuntu (9.04) it installs successfully and whatnot and I use it, but then after about a week of usage when I boot up my computer and get to the login screen. I get [this image]("http://img366.imageshack.us/img366/369/photop.jpg")....




[/B]**After I reinstall my operating system things go back to normal, but this screen always comes up and will freeze my computer. I have NO idea what is going on and as far as I know no one else has had this problem. My theory is that a graphic driver isn't loading, but I have no idea how I would fix that. Input is much appreciated! Thanks.**

---

### Post by nandemonai on 2009-06-12
My first thought is video card overheating or dying but the times you mention don't seem to add up. Perhaps an update is causing this?

What video card are you running?

---

### Post by diamondshark on 2009-06-17
It's an ATI radeon 200M. I dual boot, and I know the card is fine. Actually, I was having an error earlier on where I could only do a "Partial System Update" and when I did sudo apt-get update, it would always hang on one of the repositories then give me an error.

---

### Post by Bölvaður on 2009-06-17
I had a similar problem couple of years ago with ati video card. But It actually was ok after it got through this screen (isn't it called up splash?).

What I would recommend is to check what updates you do and make sure NOT to update the kernel. It might be breaking the comparability with the modules that control the video card (so in short... your theory was probably correct).

There is no need to constantly update the kernel, at least not as frequently as ubuntu is doing. It might be safe to install the kernels though, as they each get a special item in the grub list, so you can boot with older kernels (if you have only ubuntu you will need to press ESC to get into grub when you boot your computer and press the arrow down to get to an older kernel, you will find the number of the kernels at the end of the item name).
You can edit grub with this (if you will need to edit grub):

press: Alt+F2
```
gksu gedit /boot/grub/menu.lst
```
at the top of the file is a line saying something like Default = 0
if you change the number to.. say 2, grub will select the third (n-1 as the first item is number 0) item on the list from the top.

---

### Post by wpshooter on 2009-06-17
Are you checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, if you are installing from the desktop/live CD have you tried installing using the safe graphics mode parameter.

And if the above does not fix the problem, try installing from the ALTERNATE (text based) CD version instead of the live CD version.

---

### Post by LewRockwell on 2009-06-17
> **wpshooter said:**
> Are you checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, if you are installing from the desktop/live CD have you tried installing using the safe graphics mode parameter.

And if the above does not fix the problem, try installing from the ALTERNATE (text based) CD version instead of the live CD version.

subject equipment runs the install for approx. a week then goes bad(as per OP)

---

