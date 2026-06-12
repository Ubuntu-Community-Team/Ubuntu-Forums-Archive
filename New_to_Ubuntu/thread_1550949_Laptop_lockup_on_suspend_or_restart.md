---
title: "Laptop lockup on suspend or restart"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by xhepera on 2010-08-11
I have installed Ubunto 10.04, in a dual-boot configuration on a laptop also running Windows XP Pro.
 
I have a couple of problems that none of my searches have been able to resolve. I understand that there are problems with Ubuntu and hibernation, so I've not attempted that. However, if I put the computer into a suspended state, I get a black screen, the computer never goes into suspend (I'm assuming the behavior should be like Windows "standby"), and I cannot get back into the desktop. No key combinations or strokes work. I have to press the on/off switch for 4 seconds until the computer turns off.
 
This also happens whenever I close the lid, because the software is supposed to put the computer into a suspended state when the lid is closed.
 
Lastly, if I instruct the computer to restart it reboots but then sits at a screen that's preliminary to GRUB . . . can't recall all that's there, but it references "PXE." Again, power switch time. :(
 
The laptop is an HP 8510p. The graphic card is a Radeon HD2600. I've had no video or graphic issues since installing Ubuntu.
 
Thanks for any pointers! Oh, and I am one of the noobiest of the noobs. This is my first Linux install and it's less than a week into it. :) So be gentle! lol!

---

### Post by xhepera on 2010-08-11
Further digging has uncovered a couple of things. . .first of all I installed acpitool and invoking it with the -s switch will send the computer into suspend. I also read that Ubuntu doesn't like an sd card to be slotted when going into suspend mode. Removing the card which is pretty much always in its slot until now, also allowed the machine to go into suspend. Both these methods allowed me to reliably wake up the computer. . .BUT in both instances the display is dimmed as though the computer is in power-saving mode and doesn't want to come out of it. Sooooo, is there a way to kick it out of power saving?

edited to add: It seems as though after it comes out of suspension the computer thinks it's on battery, so a simple removal and reinsertion of the ac connector fixes the problem. Inelegant, but I can live with it if it's the price of getting suspend to work.

---

