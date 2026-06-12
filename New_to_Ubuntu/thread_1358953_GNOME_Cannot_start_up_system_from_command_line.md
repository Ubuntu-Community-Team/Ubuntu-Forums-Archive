---
title: "GNOME: Cannot start up system from command line"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by nd1083 on 2009-12-19
_Background:_
So I was messing around with the xorg.conf file trying to edit my monitor settings so that my s-video cable would work. I now found out that xorg.conf is automatically configured now which explains why there was nothing in it to begin with.

After I restarted I came to a black screen reading Ubuntu 9.1 at the top. It prompted for a login and when I put that in it asked for a password which i put in as well. 

[U]Issue:
[/U]After that I got a command line in a black screen. from here I cannot figure out how to start up the Ubuntu system like normal. I'm sure all I need to do is type a command to start it up or create a new xorg.conf file and delte the old one.

I am a new Ubuntu user. So advice is greatly appreciated. Thanks

- Nige

---

### Post by Elfy on 2009-12-19
You can fix x from the recovery menu - xfix - this should remove the one you have edited.

Boot the recovery mode from the menu list, will be the second option. Then find the xfix and then once it has done resume boot.

---

### Post by Perturbed Penguin on 2009-12-19
TRY FORESTPISKIE'S FIX FIRST PLEASE ;)

I am not by any means an expert in this area either but let me try to help. I think this will only be a temporary fix at best but try this, enter the following commands:

startx
gnome-session

This may or may not even do anything but these are seemingly pretty harmless commands as far as I'm aware so it shouldn't harm anything - I think at worst, and likely, it just won't do anything.

This link may at least help you onto the right path... or maybe not. lol Give it a read:
[http://www.linuxquestions.org/questions/debian-26/how-to-start-gnome-or-kde-command-line-468648/](http://www.linuxquestions.org/questions/debian-26/how-to-start-gnome-or-kde-command-line-468648/)

---

### Post by nd1083 on 2009-12-19
forestpiskie, thanks. but in the recovery menu I have:
Resume
Clean
dpkg: Repair broken packages.
grub
netroot
root

I went through each one and on resuming the normal boot I still come up to the same screen. I could not find xfix. Also it didnt work when i typed it into the command line either. :(

Thanks Perturbed Penguin. I tried "startx gnome-session" and "startx". It didnt seem to work. I got:
errno 111
errno3

any more help would be appreciated.

---

### Post by Perturbed Penguin on 2009-12-19
I'm going to bed, but now that my finals are over I will have time to look into this tomorrow - it will be a nice break. lol I'll get back to you sometime tomorrow if I find anything useful!

---

### Post by wojox on 2009-12-19
When you log in to the terminal enter:

```
sudo nano /etc/X11/xorg.conf.vesa
```

Then enter this into the empty file:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

``` 

Save ( ctrl + x ) and copy it to xorg.conf:

```
sudo cp /etc/X11/xorg.conf.vesa /etc/X11/xorg.conf
```

---

### Post by nd1083 on 2009-12-19
Thanks wojox!!!

What you posted didn't actually work but the info was crucial to solving this problem.

_Solution:_
So the xorg.conf file for 9.10 is automatically configured....which means that it should be empty right? So i typed this in the command line:

sudo nano /etc/X11/xorg.conf

Then it came to an edit screen. In that edit screen i deleted everything so it was blank.
Then I pressed (CTRL + X) which cuts the text from the edit screen and saves it to a file. In this case, I saved it to the same file. Make sure you say yes when it asks if you're sure you want to overwrite the current file. After that a new command line came up and I typed in:

startx

.....and my system loaded!!!!! I rebooted and it came right up. I would really like to thank wojox, Perturbed Penguin, and forestpiskie for helping me out. **YOU GUYS ARE THE ****! UBUNTU IS THE ****! AND LEARNING IS THE ****! **If you have a similar problem, this is what I did.

---

### Post by Elfy on 2009-12-19
Glad you are sorted - I've not needed to boot into recovery for a while - I was not aware that xfix had gone :(

---

### Post by Perturbed Penguin on 2009-12-19
Hehe, yeah Ubuntu's community rocks! Glad to hear you got it working. ;)

... oops, I really did mean to go to bed, got sucked into playing some UrT, lolz.

---

