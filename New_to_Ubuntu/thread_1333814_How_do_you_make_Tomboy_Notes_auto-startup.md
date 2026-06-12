---
title: "How do you make Tomboy Notes auto-startup?"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by droadtrip on 2009-11-21
[SIZE=3]Hi 

I use Xubuntu 9.10 but I assume the same question can be asked of Ubuntu users. I want Tomboy Notes to automatically appear on my top taskbar, just like the Firefox icon, the battery life (its a laptop), volume control, time, etcetera. 

Is there a way I can have Tomboy Notes auto-launch at startup & log in?

I also want to make a few aliases on my Desktop (they were 'shortcuts" in windows) to some often used used applications. I have tried and looked, but not found how to do this. Wondering if it's an XFCE thing and if it is possible to do this.

Thank you.
[/SIZE]

---

### Post by cjohnston on 2009-11-21
I'm not completely sure how in XFCE, but in gnome you right click the desktop, hit add launcher and then add the path to the launcher, for the desktop shortcuts.

---

### Post by droadtrip on 2009-11-21
> **FFEMTcJ said:**
> I'm not completely sure how in XFCE, but in gnome you right click the desktop, hit add launcher and then add the path to the launcher, for the desktop shortcuts.

Thanks for your input. It is not as simple in XFCE I have found. I have only had this Ubuntu distro for 2 weeks and I installed it because a teenager I was mentoring who had an old Dell laptop from 2003 has Xubuntu, since I'm the one who installed it. From testing, it was the best distro for his aging laptop. Not knowing a whole lot about XFCE environment, I installed it on my system as well to learn my way around it better. I'm very impressed with it so far, aside from these questions I have. 

I can't right-click and select "add launcher", I can only create a launcher. This is where the confusion sets in. I don't know how to specify the precise path that I need, which is namely Tomboy Notes. Everything is a confusing technical gauntlet of system files. 

Any advice you or Xubuntu enthusiast is greatly appreciated.

---

### Post by sgosnell on 2009-11-21
The path to Tomboy is /usr/bin/tomboy.  Almost every installed executable is in /usr/bin, although some are put into other folders.

---

### Post by droadtrip on 2009-11-22
> **sgosnell said:**
> The path to Tomboy is /usr/bin/tomboy.  Almost every installed executable is in /usr/bin, although some are put into other folders.

Hey thanks! That last reply was exactly what I needed. Worked easily and now I can put whatever programs I want on the desktop!

---

### Post by beanco on 2009-12-05
Just wondering if there is a way to take it a step further...ie. i managed to ge the icon up on the task bar following the info here.. but can I have a given notebook open up when I turn on the computer...???? not just the icon on the taskbar, but an actual notebook open and therefor me to read...

thanks

robi

ps. I amon ubuntu,not xubuntu

---

### Post by ankspo71 on 2009-12-05
To beanco,

First remove your tomboy shortcut from your taskbar/panel that you created.

Then right click on an open area of the panel, then select "add to panel", then scroll all the way down down and select  "Tomboy Notes", then click add. This is an applet, which is different from launching Tomboy from a shortcut, and it should_**n't**_ start Tomboy on startup with having the note opened. It works for me.

Edit: this advice is for Ubuntu/gnome users (corrected typo too)

James

---

### Post by Sir Jasper on 2009-12-05
Hi,

If you want Tomboy and every other program, except Wine programs, to restart exactly as you leave it/them - tick ¨Save session for future logins¨ when you log out/shut down.

My regards

---

### Post by beanco on 2009-12-05
> **Sir Jasper said:**
> Hi,

If you want Tomboy and every other program, except Wine programs, to restart exactly as you leave it/them - tick ¨Save session for future logins¨ when you log out/shut down.

My regards
 

great idea but when I click shut down i do not have such an option as Save session... must be somewhere else hat U have to activate....

robi


edited to add

system/preferences/start up applications/options/automatically remember running sessions when logging off

---

### Post by Sir Jasper on 2009-12-05
Hi,

The thread starter is using Xubuntu - but otherwise go to settings Session and Startup and look at the first section.

My regards

---

