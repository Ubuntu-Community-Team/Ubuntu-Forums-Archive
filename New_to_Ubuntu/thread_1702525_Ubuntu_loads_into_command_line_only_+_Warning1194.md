---
title: "Ubuntu loads into command line only + Warning:1194"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by monologish on 2011-03-07
Hi,

I know this question has been asked several times before but I am not able to locate a concrete answer to my problem. I installed Ubuntu on a system, during which time I could see the graphic interface clearly. But after reboot I am only able to get into the command line. 

I tried several things:

1. sudo apt-get install gdm  //said gdm is already newest version
   sudo dpkg-reconfigure gdm
   sudo gdmsetup

at this point I got a Warning:1194: cannot open display

2. echo options i915 modeset=1 
sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u

the cursor disappeared and I had to Ctrl+z out of it.

I am newbie with Ubuntu and not very familiar with kernel commands. But I am technically sound so can understand it. Now how can I fix this problem, and can someone give me clear steps on how to do this. 

I think the problem lies with my video card, or lack of it...I don't know what is inside the computer. I am trying the GTT Incoherency Patch next...don't know if it will work...any help will be greatly appreciated.

3.I tried startx and I got a pageful of errors, the last few lines which said no screens found. :confused:

Regards,

---

### Post by thegod_slayer on 2011-03-07
you can try logging through the terminal and then try this...

sudo service gdm start

this should start the graphics.

otherwise inform us.

---

### Post by mrhhug on 2011-03-08
welcome to ubuntu forums!

sorry your first post is about non GUI booting issue but lets see what we can do.

what is the video card on your system? did you enable restricted drivers before the failure reboot? 

which version of ubuntu is installed; did you do an updated right befofe this error started?

---

