---
title: "Monitor Goes out of Range"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by vikas barnes on 2011-08-23
Hi,
Yesterday I installed Ubuntu 11.04 on my upgraded PC along with Windows 7 (dual boot).
I have been using Ubuntu for quite a long time now but I did'nt encounter the problem which I am facing this time.  
The problem is -
[COLOR=Red]At the time of display of Grub Menu (dual boot menu) my Montior goes **out of range. **We can't see the menu but we can operate the menu using arrow and enter keys. [/COLOR]Here is the Configuration of my PC -

Processor - AMD dual Core (Athelon X2 250) 3.0 ghz
Mother Board - Asus with Nvidia Graphics 
RAM - 2 GB
Monitor - 17" LG (LCD)

Previously I was using AMD but had no problems.
After Installing Restricted NVidea Drivers I am not facing any problem in running unity also, but grub problem is not fixed.
plz help.

Vikas:confused:

---

### Post by 123456789123456789123456 on 2011-08-23
I have a simular problem with xubuntu 11.04, but it happens when the system is loading up, tries to use several different screen resolutions until it conpinsates.  have you tried adjusting the monitors settings to display the screen in a readable manner?  have to admit my knowledge is limited with lcd, plasma, flat screen monitors, I deal mostly with crt screens.  just a suggestion though.

---

### Post by egomezcana on 2011-08-23
I've faced the same problem a couple of times now. I always thought it was due my oldie machine and its oldie GPU and it is always related to the GRUB. I solved it trough modifying /etc/default/grub, there is a section of the file with:

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

I just delete the comment on the parameter and/or change the resolution, I just left it like:

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

Then you need to run:

sudo update-grub

ans that's it! I hope I have been helpful

---

### Post by vikas barnes on 2011-08-23
Thnk,
I tired to tweak monitor settings but no use.
I installed xubutu also but same prblem is coming.

---

### Post by vikas barnes on 2011-08-23
thnx,
I did that an now it works. 

u rock!!!!!!!!

---

