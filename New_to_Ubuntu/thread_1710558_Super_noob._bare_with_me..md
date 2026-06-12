---
title: "Super noob. bare with me."
date: 2011-03-20
forum: New to Ubuntu
---

### Post by powerupmario on 2011-03-20
Well here is my story. I was cleaning out my garage and i found a notebook i had from 2 years ago. I was gonna throw it out because the thing would not boot. It was stuck on a black screen. At that point i figured it was done for and I recovered the hard drive and made it in to an external and saved my precious pictures and forgot about it and today i decided i would see if wiping the HD and installing this ubuntu ive heard of from every computer savvy person i know. I managed to install ubuntu 10.10 net book edition. Everything seemed to work fine i was stoked. It had seemed i fixed my laptop! Then it told me that i should upgrade my nividia driver. so I did and let it load and left for a few hours. i came back and said i needed to restart so i did and then nothing booted. When i reboot i get the same black screen i was encountering before. i attached my monitor from my desk top and i get this error message    graphics initilization failed error setting up gfxboot so i type in help and i get the help menu. now the funny thing is that this only shows up on my desk top monitor. once the cde starts to go to the purple splash screen it shows up on both monitors. it will load then i get this screen. it then just sits there and does nothing. any ideas what this could be? it worked fine before i tried to update the stupid driver.

---

### Post by pi3.1415926535... on 2011-03-20
One option is to reinstall, though less drastically, you could change some of the graphics settings, which you should be able to do from the command line, which can be accessed without the graphical interface.

---

### Post by Rasa1111 on 2011-03-20
hmm, 

 Nice you recovered it!
Ive saved multiple old computers from certain death, using Ubuntu!  lol :) <3

Im really not sure what is going on there..

is the nvidia driver absolutely necessary? anyone know?
I wouldnt think so.. but i may be wrong. (quite possibly). lol

If the nvidia driver isnt absolutely needed,
and it worked fine before you installed it all..
if it were me, i might just reinstall the OS, and leave the nvidia out of it next time.. :???:
hmm. sorry im not very helpful.. lol

Someone more knowledgeable will be by soon, im sure. 

Hope you get it going soon!
COngrats, and good luck. 

ohh, and welcome!

---

### Post by kerry_s on 2011-03-20
On netbook, yes unity is 3d. he should install the desktop version.

---

### Post by fabricator4 on 2011-03-20
> **pi3.1415926535... said:**
> One option is to reinstall, though less drastically, you could change some of the graphics settings, which you should be able to do from the command line, which can be accessed without the graphical interface.

Would 10.04 LTS be a better choice?  I though the NVidia drivers for 10.04 had been sorted out. (problems with 10.10 would therefore be a regression?)

Chris

---

### Post by terry_gardener on 2011-03-20
> **powerupmario said:**
> it then just sits there and does nothing. any ideas what this could be? it worked fine before i tried to update the stupid driver.

i am guessing you can still see the grub menu. select the recovery option. goto the command line interface and type "sudo nano /etc/X11/xorg.conf" and find the driver section and change the driver to NV instead of nvidia this will revert the driver back to the old driver. save the file using ctrl-x and then selecting yes to save.
reboot the system to do this type "sudo reboot now". 

this should then hopefully get you back to your desktop using the old NV driver.

---

### Post by powerupmario on 2011-03-20
now.. considering that nothing happens when i boot up with out a cd how would i get to the grub menu? it just sits at a black screen.

---

### Post by kerry_s on 2011-03-20
After your bios, hold the shift key that takes you to grub menu.

Just a thought, have you tried pressing ctrl+alt+f1 when the screen is black, see if the terminal is there?

---

### Post by powerupmario on 2011-03-20
> **kerry_s said:**
> After your bios, hold the shift key that takes you to grub menu.

Just a thought, have you tried pressing ctrl+alt+f1 when the screen is black, see if the terminal is there?


Is this with the boot disc in our out? with out the disc no command works. nothing shows up on screen. with the disc im and able to get to the help menu. From there it goes to the purple splash screen, some music and then get that screen from my original post. im going to try and see if maybe an earlier version will work. ill be back. i am determined to fix it because it obviously worked even if it was for a few hours. at this point i want to throw it out a window,

---

### Post by terry_gardener on 2011-03-21
if all else fails just reinstall and dont install the new drivers and use the default drivers. at least you know it works from default install install.

---

### Post by powerupmario on 2011-03-21
> **terry_gardener said:**
> if all else fails just reinstall and dont install the new drivers and use the default drivers. at least you know it works from default install install.
ive tried doing that multiple times already. when every i try i get that screen from my first post. would installing an earlier version help?


edit: i tried to install 10.04 and i get the same screen. but this time i actually get the boot menu. what can i do from there?

---

### Post by powerupmario on 2011-03-24
sigh. im glad this was helpful. :-(

---

