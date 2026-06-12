---
title: "Booting in xterm as opposed to ubuntu-desktop"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-09-16
Hi.
I am so stupid, I can't believe I did this.

The short story is I was trying to get Ubuntu to recognize this computer's resolution. I installed it to a PNY Attache 8gb thumb drive and it worked perfectly. When I brought it over to this computer, which has a way bigger resolution, I couldn't get it to switch over to another resolution. So I logged out, changed my session type to xterm, and tried sudo dpkg-reconfigure -phigh xserver-xorg. I figured that would work. I'm not sure if it did because I can't get it to go back to GDM.
I think what my issue is is that I'm set to log in automatically.

So basically, I just want my GUI back. Any way how? I tried entering gdm into Terminal, and that didn't work. Ditto for ubuntu-desktop. gdm gave me some kind of odd output, and ubuntu-desktop informed me command not found.

---

### Post by nothingspecial on 2010-09-16
Try ```
sudo service gdm start
```

---

### Post by DM was on fire! on 2010-09-16
Sorry for taking so long to reply.

When I enter it, it informs me that the service is already running. Should I try killing it (I guess "kill gdm?") and then try again?

---

### Post by nothingspecial on 2010-09-16
Try

```
sudo service gdm restart
```

---

### Post by DM was on fire! on 2010-09-16
'Fraid I still have Xterm even after doing that. 
Would it just be easier to reinstall? I didn't have anything installed on here (because the computer I installed it onto the thumb drive with has no internet), nothing configured except for theme.
I might end up doing it anyway.

I do thank you for your help btw, nothingspecial.

---

### Post by nothingspecial on 2010-09-16
> **DM was on fire! said:**
>  
Would it just be easier to reinstall? 

Well in this case, I have to say yes.

It is not the done thing around here to recommend a reinstall, and I would always try to fix a full installation first. However, as this is a usb install, and you have not done anything to the original install (except change the theme and (dare I say it?) bork the display (I`m joking, I have done a lot worse)), then the easiest quickest way to get you back up and running would be to do that.

Don`t get me wrong, we could probably fix this over the next 24 hours or so.......But, if you just want it to work as quickly as possible though, and have absolutely nothing important within this installation, then in this case - do it.

---

### Post by Nythain on 2010-09-16
see this thread for ways to edit your gdm settings from the command line

[http://ubuntuforums.org/showthread.php?t=1555988](http://ubuntuforums.org/showthread.php?t=1555988)

its really as easy as a simple edit to a config file.
sudo nano /etc/gdm/custom.conf and make the edits you need

---

