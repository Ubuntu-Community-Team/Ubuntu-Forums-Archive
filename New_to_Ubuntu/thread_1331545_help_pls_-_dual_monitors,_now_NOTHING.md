---
title: "help pls - dual monitors, now NOTHING"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by luckylucky on 2009-11-19
Sigh, please someone help me out here.  I of course tried googling for solutions first, now am forced to turn here for help from another computer.

I finally upgraded to 9.10 today (been too busy before) and have hit a snag.  I did a fresh install (not upgrade from 9.04, which didn't work btw), updated all updates, then proceeded to change my monitor settings... this caused some problems.

I have been using two monitors before in previous versions of ubuntu, and in the last one (9.04) it worked perfectly, but now arrrg.  One is laptop monitor (wide), and second is external monitor (4:3).

Going to System > Preferences > Screen resolution (or was it "monitor" or "display"?) I changed settings to off clone, then correct resolutions, then ok.  I just get a black screen showing my mouse pointer.

Upon rebooting and logging in all I get is black screens with the mouse pointer that can move around onto both screens (obviously I got dual monitors now).  I can't do anything, ctrl alt & backspace or even delete do nothing.  To shutdown to reboot I have to (yikes) push the power button.  Basically my computer seems pretty much bricked after logging in.

How can I log in another way to fix this issue, AND what should I do to fix the main issue?

Thanks in advance for any assistance on this.

---

### Post by realzippy on 2009-11-19
You could try:

press Alt+Ctrl+F1 to get to a shell;log in,type:

[B]xrandr -q
[/B]
can you post that? (output)

Also try:

 **xrandr  --output VGA --off **
*then:*
 [B]xrandr --output VGA --auto --right-of LVDS
[/B]
is there a error message?

*if VGA does not work,try VGA-0*

---

### Post by luckylucky on 2009-11-19
logged in via the safe mode, got to shell.  tried your suggestion of xrandr -q but simply got "Can't open display"
Also tried xrandr  --output VGA --off but got the same message

---

### Post by realzippy on 2009-11-19
safemode=recovery mode?
Might be that this will not work cause you need runlevel 3. (X must be started to run xrandr)

When you see the cursor and black screen, press Alt+Ctrl+F1  (orF2)

---

### Post by luckylucky on 2009-11-19
from black screen alt ctrl f1 got me to shell.  none of those commands worked (got "Can't open display").  Even tried with sudo.

---

### Post by realzippy on 2009-11-19
so (try) to start X:

**startx**

(might say X is running ;-) )   **???**

---

### Post by luckylucky on 2009-11-19
tried startx

typed out what I got below...

"
fatal server error:
server is already ative fordisplay 0
if this server is no longer running, remove /tmp/.XO-lock
and start again.

ddxSigGiveUp; Closing log
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: resource temporarily unavailable (errno 11): unable to coonect to X server
xinit: no such process (errno 3): Server error.
"

---

### Post by realzippy on 2009-11-19
Yes,X is running,dual screen messed up setup.

What graphics card do you run? (Ati/Nvidia/Intel?)  (lspci | grep VGA)
Do you have a xorg.conf file?

**nano /etc/X11/xorg.conf**

---

### Post by luckylucky on 2009-11-19
having a brain cell, I thought to try an experiment...
I manually (in shell) created a new user, rebooted, and logged in as the test user.  I got to gnome display like usual.  Now am trying to change the display...

system > preferences > appearance > visual effects to NONE

system > preferences > display --- set to dual monitors @ correct resolution

so far soo good.  it worked.  now to change visual effects to NORMAL
got the error message:
"Desktop effects could not be enabled"

I read somewhere (google) that a bug in 9.10 you have to turn off visual effects to have dual monitors.  seems this is confirmed.

Now I have 2 issues...

1) how to fix my main user account to log in
2) how to fix the issue of dual monitors to work with visual effects on

btw, thanks for your attempts to help me so far

---

### Post by realzippy on 2009-11-19
now you could have a look if there is a xorg.conf (post it) !
Your graphics card?

---

### Post by luckylucky on 2009-11-19
what the???
there is no xorg.conf file there!!!

I tripple-checked... it really isn't there!

---

### Post by realzippy on 2009-11-19
In Karmic there is no one by default.
Hoped there might be one created from your video driver;btw.what
videocard do you use?????And if Ati/intel/nvidia which driver?

---

### Post by luckylucky on 2009-11-19
it is an intel video card (don't remember exactly, but 910 rings a bell).  

Do you think there is hope to get this matter resolved, or do you think I should downgrade back to 9.04?

---

### Post by realzippy on 2009-11-19
[B]lspci | grep VGA
[/B]
should give you vga hardware

If single view and desktop effects run (as I understand),it should be possible to get 2 Monitors run,depending on your VGA RAM amount...



To repair main user:
What happens if you unplug 2. monitor when starting account?Normally xrandr should recognize this and run ...

---

### Post by luckylucky on 2009-11-19
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by luckylucky on 2009-11-19
unplugged monitor and rebooting now...

hmmm... it worked to get me back to main user.  

now turning off again, replugging monitor, and will report what happens then.

---

### Post by piousp on 2009-11-19
I also think the key here is to play with xrandr instead of using the gui.

---

### Post by luckylucky on 2009-11-19
didn't work... unplugging it again, to then login again, to then change the visual effects off.  trying to see if that helps

---

### Post by luckylucky on 2009-11-19
> **piousp said:**
> I also think the key here is to play with xrandr instead of using the gui.

I don't know anything about that... what is it, and what does it do?

---

### Post by realzippy on 2009-11-19
> **piousp said:**
> I also think the key here is to play with xrandr instead of using the gui.


Have you read whole thread?

---

### Post by realzippy on 2009-11-19
> **luckylucky said:**
> I don't know anything about that... what is it, and what does it do?


xrandr manages the screens.Here are two links:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

[http://blog.frith.co.za/2007/12/06/xrandr-finally-simple-monitor-configuration-for-linux/](http://blog.frith.co.za/2007/12/06/xrandr-finally-simple-monitor-configuration-for-linux/)


I now would start with the beginning of this thread:

[B]xrandr -q
[/B]

---

### Post by luckylucky on 2009-11-19
Ok, I've got access back to my account.  By disabling desktop effects I can now have dual monitors.  Now I have a new problem... I can't get desktop effects.

Thank you very much for your help this far.  I'm closing this thread for now, and starting a new help thread to get desktop effects up a!nd working as a separate issue.

Thank you

---

### Post by realzippy on 2009-11-19
...install intel drivers...

---

