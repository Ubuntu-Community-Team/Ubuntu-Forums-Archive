---
title: "Keyboard not working correctly after crash"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-23
I was trying to see what the new gnome 3 looked like and mistakenly entered the run application line "gnome-shell --replace" in the bash terminal.  When I entered "metacity --replace" to go back to the old configuration, I then lost everything from the desktop except for the 3 icons I had placed there, one of those being the bash terminal icon.  I was able to shut the computer off by running "sudo shutdown -r now" from the terminal. On reboot I had my old desktop back.

 Now the laptop keyboard is not working correctly.  The letters j k l produce the numbers 1 2 3 and u i o produce 4 5 6.  The wireless keyboard seems to be working just fine. 

 How do I fix the keyboard?  

How do I find out what else I messed up in the system? Is there a system diagnostic that will check everything to make sure it is working correctly?

---

### Post by jtarin on 2010-08-23
Go to Gnome Control Center and check your keyboard settings there. What version of Ubuntu are you using?

---

### Post by Sleven7 on 2010-08-23
Just installed Ubuntu 10.04 and am brand new to Linux and Ubuntu.  

Where is the Gnome Control Center?

---

### Post by jtarin on 2010-08-23
Press Alt+F2 and type &#8216;gnome-control-center&#8216;.It can also be found via the MainMenu. Have you rebooted since this happened? How did you aquire the new Gnome3?

---

### Post by Sleven7 on 2010-08-23
Yes I have rebooted a couple of times.  I also do not see the Gnome Control Center anywhere, I looked under main --> system --> administration to see if it was an option that was not turned on but did not see it.  I do have a Control Center under Systems if that is the same thing, I was specifically looking for a Gnome Control Center.  Does it look kinda like the Control Panel in Windows when opened?

---

### Post by jtarin on 2010-08-23
Yes...that is the one...as I said I am not on my Linux machine at the moment so I'm working from memory.
You might also try this if you find nothing amiss there.
[COLOR="Red"]**Very Importan!**[/COLOR] Before you do the below...answer this question....**_How did you aquire the new Gnome3?_**
Reboot and choose the Failsafe kernel. When you get to the desktop open a terminal and run these commands.
```

sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session

Then reboot.
```

---

### Post by Sleven7 on 2010-08-23
I was reading an article from this page

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

this is the paragraph 

The upcoming version 3.0 of the GNOME desktop  environment uses GNOME Shell which is a new interface for interacting  with your desktop. If you'd like to try it, there is a version in the  Ubuntu repos. Launch it by hitting Alt+F2 to open the "Run Applicatoin"  dialog and enter "gnome-shell --replace". Switch back by doing the same  thing but enter "metacity --replace" instead. 

[Click here]("apt:gnome-shell") to install gnome-shell

I clicked the link, followed the instruction and then made the mistake of entering "gnome-shell --replace" in the bash terminal instead of the run application box.  When I entered "metacity --replace" in the bash terminal I lost everything except a few icons on the desktop.

I have looked in the keyboard icon under the Control Center but see nothing that is obviously wrong.

---

### Post by Sleven7 on 2010-08-23
Should I go ahead and run the commands?

---

### Post by jtarin on 2010-08-23
Run the commands I listed above and follow the procedure exactly as I have outlined. if you don't know...ask. Reboot after. If that doesn't reconigure your installation tell me. Then you can try ```
sudo aptitude reinstall ubuntu-desktop
```but lets try to avoid that .

---

### Post by Sleven7 on 2010-08-23
After I restart in failsafe, is it ok to open firefox to copy the command lines?

---

### Post by Sleven7 on 2010-08-23
I entered the commands just as you said, then rebooted.  The keyboard is still not working.

---

### Post by jtarin on 2010-08-23
> **Sleven7 said:**
> I entered the commands just as you said, then rebooted.  The keyboard is still not working.In your terminal enter the command  ```
gnome-about
``` and tell me the Gnome version number.

---

### Post by Sleven7 on 2010-08-23
2.30.2

---

### Post by jtarin on 2010-08-23
Is this a wireless,usb or PS2 keyboard?

---

### Post by Sleven7 on 2010-08-23
I'm using my wireless keyboard to respond to you.  It is the keyboard that is on the laptop itself that is not working.

Th5s 5s an exa0*3e 6f what the 6nb6ard 2eyb6ard 5s d65ng <--- This is an example of what the onboard keyboard is doing.

---

### Post by jtarin on 2010-08-23
> **Sleven7 said:**
> I'm using my wireless keyboard to respond to you.  It is the keyboard that is on the laptop itself that is not working.

Th5s 5s an exa0*3e 6f what the 6nb6ard 2eyb6ard 5s d65ng <--- This is an example of what the onboard keyboard is doing.Make and model laptop?

---

### Post by Sleven7 on 2010-08-23
Toshiba Satellite L455D-S5976

---

### Post by jtarin on 2010-08-23
[You can look here and try]("https://help.ubuntu.com/community/MultimediaKeys")  or   [HERE]("https://help.ubuntu.com/community/KeyTouch") or.........Go with the ```
sudo aptitude reinstall ubuntu-desktop
``` its a Gnome problem and this is short of reinstalling.

---

### Post by Sleven7 on 2010-08-23
That did not work either.

---

### Post by jtarin on 2010-08-23
> **Sleven7 said:**
> That did not work either.
Well it would be easier to reinstall at this point. If you have any data you need to backup or move to a windows partition I would do that. Linux like Windows is a learning experience. You can't do things out of the ordinary and not expect consequences. I wish I had a nickel for everytime I reinstalled Windows,Linux and BSD. I now backup my clean installs with all the software I "need" to another drive.It takes about 15 minutes to revert back after a screw-up. It can still happen....we're human. I had read about Gnome 3 and would have liked to have downloaded it myself, but its not ready yet for a stable system, so I wait. Learn your way around your present system before going out in the wild. It will help prepare you for the worst case scenario.[Here's what I use]("http://www.paragon-software.com/home/db-express/index.html")...it can be booted from a USB or CD. it's free

---

### Post by Sleven7 on 2010-08-23
Thank you for all the help.  I have my keyboard back but am unsure of why.  I tried a reinstall only to partition the drive again.  I've started a new thread on that issue.

---

