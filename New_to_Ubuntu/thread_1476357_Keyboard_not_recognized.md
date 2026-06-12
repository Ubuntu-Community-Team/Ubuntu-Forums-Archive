---
title: "Keyboard not recognized"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by mayagrafix on 2010-05-07
Just updated to 10.o4 LTS and after the purple screen with Ubuntu 10.04 logo shows, the log in screen comes up but the keyboard and mouse cease to respond. So I am stuck at the log in prompt unable to input the password to continue boot up. 

PC only has input for USB keyboard + mouse, no PS/2 connectors available.

Boot with recovery mode is possible, and after log in I have a command prompt available.

Thanks in advance to all the unsung heroes of Ubuntu Tech Support:KS

---

### Post by _0R10N on 2010-05-07
> **mayagrafix said:**
> Just updated to 10.o4 LTS and after the purple screen with Ubuntu 10.04 logo shows, the log in screen comes up but the keyboard and mouse cease to respond. So I am stuck at the log in prompt unable to input the password to continue boot up. 

PC only has input for USB keyboard + mouse, no PS/2 connectors available.

Boot with recovery mode is possible, and after log in I have a command prompt available.

Thanks in advance to all the unsung heroes of Ubuntu Tech Support:KS

Are you capable of these things?

1- navigate your BIOS using the keyboard.
2- Change boot option on GRUB
3- Use your keyboard with another OS (in the same PC)
4- Once in the login screen, ctrl+alt+F1 to drop to a terminal.

I'm asking this because I would like to have an approximate idea of when your keyboard stops being recognized.

Kind regards!

---

### Post by mayagrafix on 2010-05-07
1- YES
2- YES
3- YES
4- NO

:idea:

---

### Post by mayagrafix on 2010-05-08
Good Morning! anybody have any ideas how to activate a USB keyboard on start-up?

:KS

---

### Post by mayagrafix on 2010-05-09
When I get to log in mouse and keyboard are inactive. Does anybody have any ideas how to activate a USB keyboard from the command line?

Using Ubuntu 10.04 LTS on a Dell PC with no PS/2 connectors. Only USB

Thanks for any info.

---

### Post by mayagrafix on 2010-05-10
Red face  Re: Keyboard not recognized
When I get to log in mouse and keyboard are inactive. Does anybody have any ideas how to activate a USB keyboard from the command line?

Using Ubuntu 10.04 LTS on a Dell PC with no PS/2 connectors. Only USB

Thanks for any info.

---

### Post by mayagrafix on 2010-05-11
Okay, if after 4 days and over a hundred views no one can tell me how to fix 10.04 LTS, the could someone please tell me how to revert to the previous version which was working well?

---

### Post by bredman on 2010-05-11
The reason that you are getting no answers is because this is a very strange problem.

A normal keyboard or mouse will use the HID (Human Interface Device) drivers which are in the Linux kernel and which have been stable for years. This is something which should just work.

There is a chance that your keyboard and mouse are not using HID and the correct driver cannot be found. You could try the following...

1. Try booting without the keyboard/mouse connected, and plug them in after the desktop is displayed. There is a -very- small chance that this may help.

2. After step 1, from another computer, use ssh (or PuTTY from Windows) to log into your Ubuntu PC. Enter command dmesg and check if there are any messages relating to a keyboard/mouse being detected. Enter command lsmod to check which modules are loaded.

Step 2 may be difficult if you use DHCP to assign IP addresses. You may have to ping your local addresses to find your Ubuntu PC.

Have you tried booting from a live CD? If this works, there may be a configuration problem on your installation.

---

### Post by zlot on 2010-05-12
Go here, and all will be well. It's a problem with VMWare.


[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

---

### Post by hhidalgo on 2010-05-13
In my case everything was fine after I  installed Ubuntu 10.04 for the first time in a new dual-boot computer win windows 7. Then I updated to Kubuntu 10.04 and the problems started with the USB keyboard (the USB mouse works fine).  Tried many things to solve it, but finally opted for reformatting the partition for the OS and reinstall the original Ubuntu 10.04 again. But to my surprise this didn't work. After the unbuntu re-install (using the same USB stick that I used the first time),  the keyboard works for typing the password at logon, but freezes afterwards (once the desktop appears).  No caps-lock even, completely dead. Fortunately I can make it work again by removing the keyboard from the USB socket and plug-in it again, so I can at least can access the computer to try to solve the problem.  

Since I specifically formatted the Ubuntu partition on this last installation I am suspecting that the problem is not on Ubuntu files in the root mounting point (/), but somehow is contained in the information in /home (?) that is kept after each re-installation (I am relatively new to Ubuntu, but I think this is possible, since I noticed that certain things are not changed after re-installation like the desktop background and current theme, so I am assuming some info is saved not in the / mounting point). The other alternative is a GRUB problem that I am not sure if the GRUB is re-installed every time.  This is very weird and I am not an expert but just speculating what could be happening.

---

### Post by mayagrafix on 2010-05-13
Thanks for your answers. I had no idea that this was such a strange problem, and will give the boot up without USB peripherals a try first. I guess I will put on hold my back up plan of doing a clean re install of 10.04 from a CD. BTW, everything works fine from Live CD when used to boot PC.

---

### Post by hhidalgo on 2010-05-13
> **hhidalgo said:**
> In my case everything was fine after I  installed Ubuntu 10.04 for the first time in a new dual-boot computer win windows 7. Then I updated to Kubuntu 10.04 and the problems started with the USB keyboard (the USB mouse works fine).  Tried many things to solve it, but finally opted for reformatting the partition for the OS and reinstall the original Ubuntu 10.04 again. But to my surprise this didn't work. After the unbuntu re-install (using the same USB stick that I used the first time),  the keyboard works for typing the password at logon, but freezes afterwards (once the desktop appears).  No caps-lock even, completely dead. Fortunately I can make it work again by removing the keyboard from the USB socket and plug-in it again, so I can at least can access the computer to try to solve the problem.  

Since I specifically formatted the Ubuntu partition on this last installation I am suspecting that the problem is not on Ubuntu files in the root mounting point (/), but somehow is contained in the information in /home (?) that is kept after each re-installation (I am relatively new to Ubuntu, but I think this is possible, since I noticed that certain things are not changed after re-installation like the desktop background and current theme, so I am assuming some info is saved not in the / mounting point). The other alternative is a GRUB problem that I am not sure if the GRUB is re-installed every time.  This is very weird and I am not an expert but just speculating what could be happening.

Ok, today I logged in and now the keyboard works fine. I don't know what I did that I didn't do yesterday but I won't mess it with any update for a while.

---

### Post by mayagrafix on 2010-05-13
I tried to boot with no USB keyboard plugged in (had to scramble to use KB with GRUB to choose Linux OS) and still no joy at Ubuntu Log In screen :(

So now I'm typing this using 10.04 Live CD which works great.

Back to square one, oh great Ubuntu Help Desk Wizards! :KS

RECAP: Updated to 10.04 and PC boots OK until log in screen when Keyboard + Mouse stop responding (so I can't input password). PC does not have PS/2 connectors, only for USB keyboard + mouse.

(Mayagrafix lights incense, does a quick dance, rattles his amulets and chants in front of PC altar for good luck, considers sacrifice to appease PC gods bad humor)

---

### Post by mayagrafix on 2010-05-13
> **mayagrafix said:**
> RECAP: Updated to 10.04 and PC boots OK until purple log in screen when Keyboard + Mouse stop responding (I can't input password). PC does not have PS/2 connectors, only for USB keyboard + mouse.

(Mayagrafix lights incense, does a quick dance, rattles his amulets and chants in front of PC altar for good luck, considers sacrifice to appease PC gods bad humor)

So the curse of Bill Gates has bedeviled my PC, and no matter how many java chip Frappuccino light blended beverages I offer to the powers that be at the Information technology house of worship (Starbucks), the solution to my problem is no closer today than four days hence.  TRANSLATION: I'm loosing faith in you, Ubuntu wizards! prove me wrong!!!

:guitar:

---

