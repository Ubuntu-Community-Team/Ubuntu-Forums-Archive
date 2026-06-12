---
title: "Erratic Mouse Pointer"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-06-26
My Logitech USB mouse seems to have become possessed. I have been using this model for many years while still using windoz XP and through the change to Ubuntu up through 10.04.
Seems like in the last few months and even more so in the last few weeks my mouse arrow will just fly up/over to the top/side/bottom and stick there and travel along the edge of the screen, until I move the mouse around and get control of it. I thought it might be some failing connections inside the mouse so I swapped it for an identical model (I bought several new because I like them so much) with very low hours and it did not make a difference.

Logitech MouseMan Optical Dual Sensor USB mouse
Mostly I use this computer for internet so I am using Firefox and Thunderbird

Could this be an Ubuntu/Firefox software issue?

---

### Post by jtarin on 2011-06-26
I had this same problem until I upgraded to 10.10. I'm not saying you should,but I searched high and low for an answer and never got one.I'm extremely happy with 10.10.

---

### Post by Greg Mueller on 2011-06-27
Just upgraded to 10.10
We'll see what happens next.

---

### Post by Greg Mueller on 2011-06-27
Nope, that didn't fix it......

---

### Post by AZinOH on 2011-06-27
Just for chuckles...change your mouse settings. Make it faster or slower, change the double-click speed. Reply whether or not it makes a difference.

---

### Post by jtarin on 2011-06-27
Is it a USB mouse? Try unplugging it and pl know it sounds simple but at times it works.

---

### Post by Greg Mueller on 2011-06-28
Changed the mouse settings and unplugged and replugged the mouse with no change

---

### Post by jtarin on 2011-06-28
Try cleaning or changing the surface you use your mouse on. An old-fashioned mouse-pad would do the trick or 
try a piece of plain cardboard ,if it works fine then it's whatever surface you were using before.

---

### Post by Greg Mueller on 2011-06-29
Tried that.
No joy.

I wrote to Logitech but no response yet

---

### Post by Greg Mueller on 2011-06-29
As an experiment I switched to another Logitech Mouse
A Mouseman non-USB model M-CW47

It seems much more stable so far.

---

### Post by Greg Mueller on 2011-06-29
Using this mouse (plugs in next to the keyboard plugin) has cured the problem.

The difference (in my mind) is the USB part of it. Perhaps there is interference to the mouse operation from the way USB works? 

I don't know enough about that to make such a judgement. I sure hate losing the use of my favorite mouse

---

### Post by Greg Mueller on 2011-06-29
Heard back from Logitech
They said to take the batteries out for a minute?????

Batteries????

---

### Post by crustydusty on 2011-06-29
Fixing this problem would require quite a bit of knowledge in the area of logic sniffing and code write up.  I have had this problem with many different USB controlled devices In linux and window$.  It seems to me as though its a very strange and intermittent problem with the communication between the device and the computer and I don't think it has anything to with the fact that it is wireless due to the fact that this has happened with a couple of my wired mouses and keyboards (random sticky keys).  The hexadecimal signal output could be getting warped by some kind of interference.  The problems for me almost always go away with a reformat or upgrade to new dist.  I guess what I am ultimately trying to say is you won't likely find a fix for this and you definitely won't get any help from Logisuck especially if they know you are using linux.  I have contacted them before on use of G13 game pad and they basically told me my OS was inferior and to use something that wasmore widely excepted or get screwed.  Sorry man the only thing I can suggest to find out if its a driver side issue or not is to hook up identical unit and see if the problem persists.

---

### Post by jtarin on 2011-06-29
> **Greg Mueller said:**
> Using this mouse (plugs in next to the keyboard plugin) has cured the problem.

The difference (in my mind) is the USB part of it. Perhaps there is interference to the mouse operation from the way USB works? 

I don't know enough about that to make such a judgement. I sure hate losing the use of my favorite mouseWith your mouse plugged in as you wanted it, enter the command ```
lsusb
``` in a terminal and post the results. We'll see.

---

### Post by Greg Mueller on 2011-06-29
I replugged in the offending mouse and unplugged the mouse that does not give me a problem and entered the command and here is what I got


greg@Ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c012 Logitech, Inc. Mouseman Dual Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
greg@Ubuntu:~$

---

### Post by jtarin on 2011-06-29
Not too hopeful [here]("http://www.techsupportforum.com/forums/f25/mouse-jumping-around-randomly-506178.html"), but enlightening....notice this is in a Windows install.

---

### Post by Greg Mueller on 2011-06-29
I gave the same terminal command with the non USB mouse and got this

greg@Ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
greg@Ubuntu:~$

---

### Post by jtarin on 2011-06-29
post results from command "lsmod"

---

### Post by jtarin on 2011-06-29
OK...here's my last shot at this......How bad do you want that mouse to work?[ Read through this]("http://ubuntuforums.org/showthread.php?t=4357") and decide. Not terribly difficult.

---

### Post by Greg Mueller on 2011-06-30
Thanks for that research.
I am having good luck with the non optical mouse so I think I will stay with that for a while. I have book marked the thread you linked to and will keep that and may try it down the road a bit.

Thanks for your effort

---

### Post by createdcreature on 2011-06-30
That mouse has serious problems in Linux. Use a PS2 ball mouse if you can, then a basic USB optical one.

---

