---
title: "Ubuntu 8.10 How to force a higher resolution"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by ageorge39 on 2009-03-01
I have a fresh install of Ubuntu 8.10 on Dell Optiplex GX 280.
The video card is Intel 81915 embedded on the motherboard and I use a generic 19" LCD panel (1280x1024/60Hz). The problem is that the autodetectin does not work through the KVM switch I am using. When LCD is connected directly to computer, the resolution is correctly detected, but when conected to KVM it only detects a lover resolution. I tried editing the xorg.conf file and using the xfix option at boot, but none worked.
Is there a way to avoid/disable autodetection and permanently set the resolution to 1280x1024?
That is very easy to do on Windows XP! :lolflag:

---

### Post by SunnyRabbiera on 2009-03-01
8.10 isnt that great for this very reason, there used to be a tool to easily change screen resolution that was better then the standard gnome monitor detector but its gone and probably wont be replaced anytime soon.

---

### Post by ageorge39 on 2009-03-01
> **SunnyRabbiera said:**
> 
8.10 isnt that great for this very reason, there used to be a tool to easily change screen resolution that was better then the standard gnome monitor detector but its gone and probably wont be replaced anytime soon.

Thank you! I don't have any valuable data so far, should I go to 8.04?
Or to Windows XP? :oops:

---

### Post by Panzor on 2009-03-01
Well, I see no reason to upgrade to 8.10 because my 8.04 installation does everything I want and is stable. It's your call on that one, though I would definitely pick that over xp...

There's a program called "Resolution Switcher" in the 'add/remove' dialog that might do what you desire. I've never tried it though.

Also, I'm pretty sure that xorg will work if you do it right, although I've had my quarrels with it myself. Good luck.

---

### Post by paydaydaddy on 2009-03-01
Don't know if this applies to your situation, but I have found that if I leave my kvm set to a particular machine while booting, then I can switch between machines without problems. If I start the boot process then switch to a different machine while the process completes, resolution will be wrong and the mouse will not act quite right. For me it is a very minor inconvenience to make sure that each machine is completely booted before switching. YMMV.

---

### Post by ageorge39 on 2009-03-01
I tried both suggestions, thanks; but none worked.
Resolution Switcher doesn't start, and my KVM is an old one, probably doesn't transmit any codes from LCD. Doesn't make any difference if I keep it on while booting.
I should not be messing with xorg.conf for such a simple problem.

---

### Post by ageorge39 on 2009-03-02
I tried 8.04, same problem. It seems this distribution is not ready for average end-user deployment. I moved to CentOS, they have a nice graphical utility to change the display type. Problem solved.

---

### Post by jfab199 on 2009-03-05
I have a gx 260 and am having a similar problem, I can't even install because the buttons are off the screen. The max resolution is 600x480.  It has an agp slot on the mb, if I were to put another video card in it could that work, or am I out of luck?

---

### Post by achase79 on 2009-03-05
what you need to do is edit your /etc/X11/xorg.conf file to change the resolution, but I can't remember what to edit it to.

---

### Post by ageorge39 on 2009-03-05
> **jfab199 said:**
> I have a gx 260 and am having a similar problem, I can't even install because the buttons are off the screen. The max resolution is 600x480.  It has an agp slot on the mb, if I were to put another video card in it could that work, or am I out of luck?

From what I read before giving up on xconf surgery, the Nvidia driver may be more suitable for modification. See if you can get an nvidia card. I didn't try because I didn't have one.

---

### Post by burneverything on 2009-03-10
Funnily enough I have a similar problem on 7.10
thing is:
older KVM switch don't pass on DDC1 or DDC2 parameters so that the computer does not see the screen during bootup and leaves you with the absolute minimal resolutions available  (800x600 max at a handfull of colours...).

I tried following 
[http://ubuntuforums.org/showthread.php?t=423438](http://ubuntuforums.org/showthread.php?t=423438)  
but it still won't work. 
Booting with the screen plugged into the computer than switching cables works but it sorts of defeat the point of having a KVM

there has got to be a way and an idiot guide would be much welcome at my end.

Edit:
After a good few hours it only took me 55 minutes to get round this, not sure if it will work for later versions but on my machine:

Plug your monitor into the computer and reconfigure xorg.conf

backup your xorg.conf
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bakup

select the resolution you want (1280x1024@75Hz for me)
in a terminal type:
gtf 1280 1024 75
copy the output
sudo open xorg.conf in your favourite text editor
paste the output of the gtf command in the
                    Section "Monitor"
Add the two following lines in that same section:
Option		"ignorEDID"	"on"
Option		"NoDDC"		"on"

save xorg.conf

you should now be able to boot while plugged into your old KVM with your chosen resolution

**note that "ignorEDID" is NOT a typo

hope this helps someone

---

### Post by jfab199 on 2009-03-13
Do the xorg.conf changes work while running the live cd?

---

