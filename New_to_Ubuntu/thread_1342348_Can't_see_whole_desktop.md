---
title: "Can't see whole desktop"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by 29carriacou on 2009-11-30
I had difficulty installing 9.10 because I could only see part of the .iso display (I managed by guessing where invisible buttons were). The installed version is the same, making ubunto effectively unusable. Not the monitors I'm using, because same effect with my old CRT and borrowed newer LCD, monitors. Desktop does fit the screen of the laptop, although since my daughtef dropped it, seeing only the bottom left and top right corners is why I have to use it with an external monitor. 
 
The desktop fits the screen vertically, but even if I shrink the display to less than half the otherwise viewable part of the visible screen, both left and right, are cut off. E.g. On those occassions I can pan the desktop to the right to see buttons or navigation bars, I cannot then see the text on the left of the page. 
 
I've searched every manual and the fora and see nothing relevant to this problem, nor does changing resolution etc have any effect.
 
Please be gentle with me. I'm not only a new (potential) user, but I'm also dyslexic and 15 years past retirement. I'm not completely ga-ga yet, but treat me as if I was. 
 
Thanks, David

---

### Post by u.b.u.n.t.u on 2009-11-30
If you talking about an installed running operating system, please take a screenshot of the entire desktop as you see it. That will help in understanding what the problem is.

---

### Post by kerry_s on 2009-11-30
look in your bios, see if you can disable the laptop lcd with external hook up.

---

### Post by Johnny19734 on 2009-11-30
What video card do you have? Nvidia, ATI , Intel?

---

### Post by 29carriacou on 2009-12-01
> **kerry_s said:**
> look in your bios, see if you can disable the laptop lcd with external hook up.
Thanks. My Bios does not provide this function.

---

### Post by 29carriacou on 2009-12-01
> **Johnny19734 said:**
> What video card do you have? Nvidia, ATI , Intel?
SiS Mirage 3

---

### Post by Dr. Freeze on 2009-12-01
Hey I too had this problem...are you using an HDMI cable on an LCD tv?

---

### Post by 29carriacou on 2009-12-01
> **u.b.u.n.t.u said:**
> If you talking about an installed running operating system, please take a screenshot of the entire desktop as you see it. That will help in understanding what the problem is.
The problem you describe in your idea 22737 seems to be the explanation. Windows easilly "sees" multiple monitors and allows enabling/disabling of them individually - Perhaps a function worth including in Ubuntu in the future?
 
Until someone comes up with a solution usable by a fogey like me, I regretfully fear I must forego becoming an Ubuntu user (because I cannot afford to buy either a new widescreen monitor or computer - either of which would solve it). But since I've spent 200 hours stumbling around it, here are my observations on it in case they are of any use to anyone else:
 
Ubuntu clearly does recognise my laptop's widescreen format (did'nt realise that's what it was!) and sets the display accordingly. All other monitors are treated as if they too are widescreen. Going into Preferences>Display gives "Unknown monitor" and nothing more can be done. My screen shot gives a picture of what Ubuntu thinks I should be seeing, not what I actually can see.
 
I shall keep an eye out and see if any new releases can deal with this. In the meantime, Thanks and Good Luck in the project of which I heartily approve.

---

### Post by u.b.u.n.t.u on 2009-12-01
Do you have a file with the name xorg.conf in the location /etc/X11 ?

The full path is:

/etc/X11/xorg.conf

If you have such a file, would you please copy and paste the contents here.

---

### Post by Johnny19734 on 2009-12-01
Did you try:

sudo dpkg-reconfigure xserver-xorg

You may have to do this in recovery mode! You'll see this in the grub when booting up.

---

