---
title: "Need My Graphics Back :( HELP!!!"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by tommo12 on 2009-05-17
Hey

i was trying to roll back my ATI driver because i was getting some issues with the video playback. So I went to the Hardware driver section and went remove... Now I have no drivers to display video at all :(

How can I fix this problem, because the driver install from ATI is graphical? Ive been trying to mount a usb or ipod and cdrom and install it from there but i think its graphical...

Anyhelp even to get my a basic graphical display so I can do the rest 

thanks :)

---

### Post by tommo12 on 2009-05-17
Because there are errors and jitters when I tried to play Video and have Compiz running I decided to disable the Proprietry driver... or Click the "Removal" Button.
 
I did so rebooted and now I have no graphics. It comes up with a distorted coloured/sized logos up the top of the screen when i boot up.
 
I tried editing the xorg.conf file added in the line (Driver "vesa") and the same results happened.
 
What can i do any help would be much appreciated :)

---

### Post by Bölvaður on 2009-05-17
> **tommo12 said:**
> Because there are errors and jitters when I tried to play Video and have Compiz running I decided to disable the Proprietry driver... or Click the "Removal" Button.

Disabling compiz by System &#8594; Preferences &#8594; Appearance and click Effects
click disable



To get your driver back:
In GRUB boot loader (may need to press ESC) press E to edit the boot option
Add xforcevesa at the end
Press ESC and now B

Go and add the driver now =)

---

### Post by goldblattster on 2009-05-17
Hello. I will need to ask you these questions:
What version of ubuntu are you using?
Is your graphics card ATI/AMD-manufactured?
If yes, is it a ATI/AMD-manufactured Radeon card?
If yes, what is the model number? Does it have tv-out functionality?

---

### Post by tommo12 on 2009-05-17
Ok i tried adding xforcevesa at the end, that was after copying back the xorg.conf-failsafe file back, so that the Driver "vesa" would hpoefully work. It did not.
 
Nor did the xforcevesa I put that in at the bottom and that did not seem to work, it just froze on a screen saying
Boot from Hdd... etc etc
 
My computer is AMD Athlon x2 with an ATI Radeon 4570 512mb graphics card, I had 9.4 catalyst running then i removed it.. I am guessing it removed some other cruicial files as well?
 
I have tried using the failsafe, and a couple of other backups from the X11 directory which had... "ati" and "flgrx..."(cant member the exact name) and they didn't seem to work, I am not sure what to do. 
 
If I can't get it working correctly I will have to do a reinstall completely... But I am not sure hwo to backup my files ontop my usb device either... In a world of hurt and pain.

---

### Post by tommo12 on 2009-05-17
got it working...
 
typed in sudo apt-get install xorg-driver-fglrx
 
then
 
sudo aticonfig --initial -f

---

### Post by goldblattster on 2009-05-17
Hmmm... I was thinking you could install xserver-xorg-video-ati (the open-source ati driver) through the non-graphical command line, but I couldn't find it in the repos. Good thing you found a fix anyway!

---

