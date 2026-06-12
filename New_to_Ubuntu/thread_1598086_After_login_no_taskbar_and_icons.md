---
title: "After login no taskbar and icons"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by booyootoo on 2010-10-16
Hi Guys,
I have downloaded UBUNTU 10.10 the day it was released (no beta). After installing a few times and also booting from CD it appears my taskbar is not showing up after logging in.
 
I installed on different partitions and tried booting from CD. All gave the same result
 
On the login screen I see the grey bars on top and in the bottom of the window. After logging in I just see the purple wallpaper.
 
I have tried some commands after using Alt-F2:
(all with sudo)
synaptic
gnome-terminal
gnome-panel
 
I've also removed gnome-panel and reinstalled it and afterwards installed ubuntu-desktop.
 
After this I could not start Gnome. It said something like could not start because window manager is not working.
 
What else can I try?
Edit: Solved. See post 8. Note: I have an ATI RADEON HD4870

---

### Post by Hippytaff on 2010-10-16
Are there any entries in the log files that might indicate problems

/var/logs

---

### Post by booyootoo on 2010-10-16
Hi Thanks for the quick reply.
I have to reboot from windows to ubuntu, because it looks like I cant run any graphical programs...

I have checked the logfiles in that dir and found nothing that looked like an issue.

In auth.log however I found the following line: gdm-session-worker[1636]: pam-succeed-if(gdm:auth) requirement "user ingroup nopasswdlogin" not met by user "booyootoo"

I'm googling now and see that some people could use startx after booting into recovery. Guess I'll try that.

If you have any suggestions let me know.

Edit: Well startx gave me a mouse cursor, but a totally black screen... Rebooted back into Windows. Tried installing kde (kdm) but I also have no internet connection. I had managed to fix that before, but doesn't seem to work. Hope there is a solution without internet access

---

### Post by Hippytaff on 2010-10-16
Have you got a live cd? bit of a bigger, but could reinstall ubuntu and see if that fixes it...though there is probably a better way...maybe download it again, check the md5sum and burn at the slowest speed, maybe something got corrupted in one or other of the process of getting it to CD!?

---

### Post by booyootoo on 2010-10-16
I had already tried that a few times... I alsoo get the same problem if I boot from a cd with Kubuntu I dont have any issues. Maybe I have to settle for Kubuntu.

---

### Post by Hippytaff on 2010-10-16
Don't know why GDM is being dodgy for you...KDE is just as good though, in my opinion...some would say better :-)

---

### Post by booyootoo on 2010-10-17
Well, installed KDE and typing from there now. Now installing ubuntu-desktop to get GNOME. Hope it will work. Marked as solved...

---

### Post by booyootoo on 2010-10-22
Just an update if anyone comes here via search:
 
I have tried different distro's since my last post. And none worked perfectly and there was little support (googling that is). I also couldn't stand that I couldn't get UBUNTU to work for me.
 
I'm at work now, so can't really look and see what the buttons are called, but you must be able to manage with my description below.
 
So I tried again.
I still got the blank background and could not do anything. 
[LIST=1]
[*]I restarted
[*]This time I had logged in via safe mode (you can choose this from the bottom of the login screen, after clicking on your name) All menus were showing and I could actually use GNOME
[*]DONT try to change your graphics yet! This will get you back to the old situation where you see no menu's.
[*]If you logout/restart now, you can still use GNOME, but without the graphical enhancements (Called Composite I think?)
[*]Internet was working and I searched for new drivers (from the menu)
[*]Selected the ATI Legacy drivers to update.
[*]Rebooted
[*]Logged in again (in normal mode).
[*]Now I could try and set the graphics to a higer level and everything worked as it should.
[/LIST]At the moment there are still some graphical glitches, like white dots when moving windows, but I can live with it. Hoping ATI will release new drivers soon.

---

