---
title: "Screen gone haywire"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by misswham on 2009-06-17
I left the room for 30 mins and came back and my screen was in hibernation mode.  When i clicked the mouse the screen resolution was waaayyyy off.  It had quadrupled in size and i couldnt log off because I couldnt get to the button to log off.  I had to turn off the pc at the tower.  When I logged back on 2 hrs later the grub froze.  I logged off again and started over and instead of choosing the first application of ubuntu, i went down to the 3rd one that said recovery.  It went through some test and i hit repair then after that I went to resume normal boot.  It booted fine but now the screen resolution is fuzzy looking.  I now rebooted the right way at the top right corner but now when it went to log off my desktop pic stayed up but now it is flashing and the ubuntu page as u log off was at the top left corner of the screen moving very nervously.  It rebooted on its on but now I have my desktop pic at the bottom right part of the screen and the grub menu at the top left.  I choose the first one as normal this time and I put in my username and password and it booted normally but now my resolution is still funny looking.  I didnt do anything but left the room and like I said when i came back and hit the mouse, My screen had quadrupled in size and was lopsided.  What can I do to get it back to normal?

---

### Post by misswham on 2009-06-17
also the fonts arent as bold as they were before and the colors are too bold now.  i didnt change anything myself.

---

### Post by misswham on 2009-06-17
the fonts are a little fuzzy also.

---

### Post by Steelmourne on 2009-06-17
What graphics card do you have?

---

### Post by misswham on 2009-06-17
How do I find that out?

---

### Post by misswham on 2009-06-17
Does NVIDIA G-Force 6150 LE 

SOUND RIGHT?

---

### Post by Steelmourne on 2009-06-17
You might try reinstalling the drivers: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400). This should provide all the options. You might have to check nvidia's website to see if that driver is still supported.

---

### Post by misswham on 2009-06-17
Ok I am totally confused.  I just read all of the link above and dont know what to run.  I dont know why it changed when it went into hibernation mode.  I am totally confused now.  In administration now I see an Nvidia part was that there always?  i dont remember seeing it.

---

### Post by Steelmourne on 2009-06-17
That nvidia part is probably from hardware drivers. If you follow the thread, step by step that will get rid of all nvidia traces from the system and install new, most likely more stable drivers. Then in system preferences and power management disable hibernation.

---

### Post by misswham on 2009-06-17
ok do i start putting all of the stuff in the terminal starting at

Reset Xorg back to Failsafe Defaults?

or do i start at

Ubuntu and Hardware Drivers
If you run Ubuntu and have an NViDIA card, you more than likely used the 'Hardware Drivers' utility to install them. This can lead to conflicts later down the line, as New drivers/Old drivers will cause API conflicts that will prevent X from starting.
So you are required to uninstall/remove any nvidia modules and references before beginning.


how do i find out if i am running 32 or 64 bit?

When there are more than one sudo command do i copy n paste all of them at once or do I do them one at a time and press enter then go to the second one?

While all of this is going on will i still be able to see my screen?

When I reboot when I put the reboot command in the terminal will i be able to see the screen since I have another step to go to?

---

### Post by misswham on 2009-06-17
Woke up this morning and the problem had rectified itself.  This was a bizarre thing that happened.  I was waiting on a response again and didnt get one so I thought I would tackle it today.  It booted properly as normal and the resolution was back to normal.  I am just curious to know what could have possibly happened yesterday when it went into hibernation which it has been doing for the past 2 years uneventfully?

---

