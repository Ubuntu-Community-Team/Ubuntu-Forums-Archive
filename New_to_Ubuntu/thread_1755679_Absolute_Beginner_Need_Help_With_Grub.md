---
title: "Absolute Beginner Need Help With Grub"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by dan1981football on 2011-05-11
Hey everybody..!

So made the jump and got 11.04 ubuntu.. I've created a dual boot for Windows 7 and Ubuntu.  Wow what a jump!!

Anyways.. all seems okay, i've installed UBUNTU okay updated everything, figured out a little about terminal and just learning how to use synaptic manager..

I'd love to change the GRUB screen to something prettier than the horrible purpley pink thingy,,

I have tried GRUB customizer and downloaded at 1280 x 1024 pic and placed it in the root grub, i've as well changed the colour and the file names to what it reads..

When i restart, the file names have changed but its still the horrible pinky colour like nothing has happened.  The background pic is also not there

I'm going despair over it.. i've tried everything, i've read forum posts but its all rather complicated..

Please can somebody help me.. i admit i'm a complete newbie so may need help explained to me in plain easy to understand english please..

Many thanks for taking the time to read this :D

Dan

---

### Post by TAspr on 2011-05-11
> **dan1981football said:**
> Hey everybody..!

So made the jump and got 11.04 ubuntu.. I've created a dual boot for Windows 7 and Ubuntu.  Wow what a jump!!

Anyways.. all seems okay, i've installed UBUNTU okay updated everything, figured out a little about terminal and just learning how to use synaptic manager..

I'd love to change the GRUB screen to something prettier than the horrible purpley pink thingy,,

I have tried GRUB customizer and downloaded at 1280 x 1024 pic and placed it in the root grub, i've as well changed the colour and the file names to what it reads..

When i restart, the file names have changed but its still the horrible pinky colour like nothing has happened.  The background pic is also not there

I'm going despair over it.. i've tried everything, i've read forum posts but its all rather complicated..

Please can somebody help me.. i admit i'm a complete newbie so may need help explained to me in plain easy to understand english please..

Many thanks for taking the time to read this :D

Dan


Right Click on the desktop, then select "Change Desktop Background."  By clicking on "Add" to the right, you should be able to add your own background.

---

### Post by dan1981football on 2011-05-11
Hello

Many thanks for the quick reply..

I've figured that out.. it was just like WINDOWS..

My question was for the boot screen where you choose to either boot Linux or Win 7..

I've tried everything :(

---

### Post by grahammechanical on 2011-05-11
Open Grub Customizer. go to Preferences and select the Advanced tab and look in the list for GRUB_MENU_PICTURE. In the Value column do you see the name of the picture that you have chosen? If not then that is why the image is not showing behind the Grub menu.

It might help if you not only saved the changes made by this program but also used File>Install to MBR. I do not know if this makes a differences but it is something that I always do when I use Grub customizer to make changes.

Did you use the copy to grub directory button to copy the image file into the Grub folder? That is what I did and it worked.

Regards.

P.S. something else I have just thought of. I placed my selection of Grub background images in /usr/share/images/grub and browsed grub customizer to there to make my selection. In 11.04 you will find it under Places>File System. The image that you have chosen, is in tga format. The ones that I am using are. Could that be the reason your image is not been used?

---

### Post by rosencrantz on 2011-05-11
Did you see this thread?
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)
Apparently there is a problem with natty and grub 1.99's submenu feature. I didn't try the workaround yet, but it doesn't seem to be too difficult.

---

