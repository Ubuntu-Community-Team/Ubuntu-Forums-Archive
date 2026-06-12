---
title: "Can't get past the login sequence in 10.10"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Jamface on 2010-11-23
Here's the problem: I have just (yesterday) installed 10.10 as dual boot with Puppy Linux on my Sony laptop PCG-FX109K. When I installed 10.10 I set login to automatic and I think I put in a password as well. But when I try to boot now after the install I can't get past the password login sequence, whether I put in the password or not. Ubuntu does not seem to recognise my password and keeps coming back to the login window. How can I get round this? I can access all the 10.10 files from Puppy Linux.

---

### Post by sikander3786 on 2010-11-23
> **Jamface said:**
> Here's the problem: I have just (yesterday) installed 10.10 as dual boot with Puppy Linux on my Sony laptop PCG-FX109K. When I installed 10.10 I set login to automatic and I think I put in a password as well. But when I try to boot now after the install I can't get past the password login sequence, whether I put in the password or not. Ubuntu does not seem to recognise my password and keeps coming back to the login window. How can I get round this? I can access all the 10.10 files from Puppy Linux.
Press Ctrl + Alt + F1 and type in your username and password. If you can login there, your password is definitely correct. Then press Ctrl + Alt + F7 to return to the GUI.

So if it is correct, you need to provide some more info. You hardware specs, graphics card, is compiz enabled and do you see any errors while it reverts you back to the Login Screen?

---

### Post by Jamface on 2010-11-24
Ctrl+Alt+F1 produces a blank screen.
I can get past the login screen by selecting Safe Mode from the options at the bottom of the password login screen.  10.10 then boots.  Using the Recovery Console at the login screen also works, but when I exit the console I am taken back to the login screen I left.
What is going on here and how can I put it right?

If I select Recovery Mode from the startup boot menu when I switch on the machine I get a few lines of process 'events' then a blinking cursor and nothing more.  Ctrl+Alt+Del restarts the machine and boots as far as the login screen.  It is very difficult to see what is happening on the screen because the resolution and refresh rate is all wrong - the window is small and flickering.  A picture is steady when boot processing stops while the machine waits for me to log in.  At the password request screen, if I keep the default option to log into the 'Ubuntu Desktop Edition' and put in my password the purple background continues to be displayed.  After about 15 seconds the Ubuntu main window appears momentarily - with its Applications, Places System stuff in the top bar, then the screen goes blank for about 3 seconds.  Then the purple background window appears again with the login frame in the centre.  I can repeat this cycle as often as I like without variation.

The laptop is a Vaio PCG-FX109K with a Pentium III processor.  The screen is designed to handle 1400X1050 resolution and the display adapter is Intel(R) 82815 Graphics Controller (Microsoft Corporation).  The machine has 254 RAM.  

If sorting this out is likely to be long and complicated, perhaps too complicated for my limited knowledge of Linux, I wonder if would not be better to reinstall Ubuntu as the only OS and then try to run Puppy from within Ubuntu?  I like the speed at which Puppy boots and runs on this rather old machine but I would like to use Ubuntu for running some software that is more more difficult to run with Puppy.

Any advice would be much appreciated.

---

### Post by Hippytaff on 2010-11-24
This happend when I installed Lubuntu with the option to log in automatically...I had to log in with
Username:root
Password:the password I gave at installation

Then create a new user, give them root priveledges by adding them to the sudouers file, then log in as that user.

This, however, may not be the same issue, and I might get a telling off for suggesting you log in as **root** to create a new user :-)

---

### Post by QLee on 2010-11-25
[QUOTE=Jamface]...
The laptop is a Vaio PCG-FX109K with a Pentium III processor.  The screen is designed to handle 1400X1050 resolution and the display adapter is Intel(R) 82815 Graphics Controller (Microsoft Corporation).  The machine has 254 RAM.  

If sorting this out is likely to be long and complicated, perhaps too complicated for my limited knowledge of Linux, I wonder if would not be better to reinstall Ubuntu as the only OS and then try to run Puppy from within Ubuntu?  I like the speed at which Puppy boots and runs on this rather old machine but I would like to use Ubuntu for running some software that is more more difficult to run with Puppy.

Any advice would be much appreciated.[/QUOTE]
Hello Jamface,
Looking at the specs of that old (approx 2001) computer, I'm not sure you will have a good user experience with a GNOME desktop environment version of Ubuntu. The RAM is pretty low (even though you've probably added some to the basic unit). Is it an 850Mhz processor? That Intel 82815 chipset has been problematic and, if I remember correctly, users had to use the vesa driver and/or settle for 16bit colour. 

Did you notice any problems when you tried the system with the live CD before you installed?

"Long and complicated"? Well, it would be my guess that the answer to that question would be yes.

However, if you choose to try, I imagine someone here will try to help. I suggest you start with the live CD and make sure you can get a usable system with it first, that process might show some command line arguments (don't worry if you don't understand that) which will allow you to have a good X window. 

On the other hand, there might be a good hint in Hippytaff's reply, maybe Lubuntu would work well on your system or another lighter desktop.

As always, good luck whatever you choose.

---

