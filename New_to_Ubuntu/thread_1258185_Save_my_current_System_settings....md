---
title: "Save my current System settings..."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-09-04
I want to save my current system settings onto a USB drive. I have compiz, nexuiz, wine, and several other things that took me forever to download. It took me around 8 hours to download nexuiz. I recently got another computer, and i want to install ubuntu on it. My version that i customized with all the eye candy and games

Is there a way to save the ubuntu i am using on my first computer onto a usb drive, so i can install it on my second computer?


Essentially, a massive file transfer

---

### Post by zerhacke on 2009-09-04
If you want an exact copy you could play with dd but I find remastersys to be more useful.  Thing is, unless both systems are identical in hardware remastersys is going to make a few fudges here and there.

I'm under the impression that you just want to save configuration files, so if you don't mind redoing any special things you have done in /etc you can just open nautilus, check the box to show hidden files, and copy everything you see to a USB stick.

Any packages you downloaded from the net, well, sorry, but I think you'll have to redownload them unless for some reason the apt cache is not cleared.

---

### Post by Koobelakahn on 2009-09-04
> **zerhacke said:**
> 
Any packages you downloaded from the net, well, sorry, but I think you'll have to redownload them unless for some reason the apt cache is not cleared.

That is what i really wanted. I wanted to transfer all the packages and software that i downloaded through Synaptic and Add/Remove (in the Applications menu) Is there a way to do that?

What is the apt-cache, and how do i access it?

---

### Post by zerhacke on 2009-09-04
If that's the case, look on google for the program called remastersys.  It will allow you to clone the entire contents of your current Ubuntu install.  A quick read of the help files will get you started.  When it's done doing its thing you will have an ISO file you can burn to CD/DVD and copy your system to your new computer.

---

### Post by linux6994 on 2009-09-04
You could always just copy out your /home/user directory out onto a usb drive and copy it back in when needed. Be sure to copy all hidden files.
You will need to re-install all of the packages that you like for instance after reinstalling from scratch.

---

### Post by Koobelakahn on 2009-09-04
can remaster be downloaded VIA synaptic or Add/Remove programs?

---

### Post by marshmallow1304 on 2009-09-04
> **Koobelakahn said:**
> can remaster be downloaded VIA synaptic or Add/Remove programs?

Instructions [here]("http://www.geekconnection.org/remastersys/ubuntu.html").  You'll have to add the remastersys repository.

---

### Post by Koobelakahn on 2009-09-04
In windows, when you install a program, it is saved in Program Files by default

In ubuntu, where is the "program files"

---

### Post by marshmallow1304 on 2009-09-13
> **Koobelakahn said:**
> In ubuntu, where is the "program files"

Generally,
/usr/bin

That's where remastersys is, but it should also be in the menu: System -> Administration.

---

