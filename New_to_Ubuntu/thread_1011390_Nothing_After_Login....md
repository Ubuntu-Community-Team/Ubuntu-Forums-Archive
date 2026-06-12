---
title: "Nothing After Login..."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Kong on 2008-12-14
I believe I'm having some problems after installing Ubuntu. I've gone through every step of the install process; I've configured my keyboard and time settings, name, etc. I finally restart, enter my username and pass, and... nothing. I must have waited at least 20 minutes last time I logged in. I just get a black screen with a cursor. No desktop or anything.

I have reinstalled multiple times and the problem remains. I also reserved all my space for Ubuntu, so I can't load up Windows or anything. 

Oh, and I'm online because I clicked to view the release notes for Ubuntu. Since it loaded up Firefox, I thought you guys might be able to help.

---

### Post by Kong on 2008-12-14
Bump. I'm reeaaally pressed for time here. I just need to know if waiting is my best option or not.

---

### Post by chrisod on 2008-12-14
If you don't have a desktop how did you click a link to see the release notes?

---

### Post by Kong on 2008-12-14
I don't really get a desktop, I just get wallpaper and a window for installation. On the page where you choose your language, there's an option to view the release notes.

I found this weird because the documentation says that I should get a desktop with an installation icon on it. :-|

---

### Post by chrisod on 2008-12-14
Assuming you are using the Live CD to do the install the first suggestion when it isn't working is usually to try the alternate install CD that is text based and thus less likely to be stymied by video card issues.

Although if Firefox is running I would think the video card is fine. What are your system specs?

---

### Post by Kong on 2008-12-14
I just burned the ISO to a CD, so I don't have an alternate. 

I've also got no idea what my specs are, and I don't know how to check.

---

### Post by karlr42 on 2008-12-14
Ok, reboot the PC, and when the first menu appears, select "Try Ubuntu without affecting your computer"(or something along those lines) - that gives you a desktop where you can try out ubuntu . I suspect you chose the "install Ubuntu option" first?

---

### Post by agathian on 2008-12-14
This is kind of confusing here..

you say you have gone thru the installation steps and completed it, and rebooted?

Did you encounter any problems during intallation?

Did you pop-out you CD before rebooting?

---

### Post by chrisod on 2008-12-14
If the specs don't meet the minimums, you can try installing for the next 24 hours and it may never work. You may need to use Xbuntu or one of the lighter flavors of Linux if it's an older machine. If you want us to help, you have to give us something to work with.

Follow karlr42's instructions for loading the Live CD and when the desktop comes up click system--->Preferences--->Hardware Info and let us know what the CPU and memory stats are on the machine. Or if you are dual booting with Windows you can get the info from Windows.

If th Live CD isn't working at all you can get the alternate text based installer from [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) - but I wouldn't do anything until you can confirm that you have a relatively modern CPU and 384 MB of RAM for the Live Cd install, or 256 MB for the alternate CD.

---

### Post by karlr42 on 2008-12-14
> **Kong said:**
> I just get wallpaper and a window for installation. On the page where you choose your language, there's an option to view the release notes... documentation says that I should get a desktop with an installation icon on it. :-|
He's clearly running a LiveCD at the installation stage. He wants to get the Live desktop environment, I think!

---

### Post by anjilslaire on 2008-12-14
Take the cd out, turn off th computer, turn it back on. What happens?

---

### Post by Kong on 2008-12-14
I've tried the "Try Ubuntu" option multiple times as well, the result is the same. No point anyways, I've used Ubuntu before and I want the operating system, I don't want to test drive it.

[LIST]
[*]Yes, I've completed and rebooted. At that point I get a logon screen, but when I log in, nothing happens for a long period of time. At that point I tried reinstalling again.
[*]I had no installation problems.
[*]I removed the disk when I finished.
[/LIST]

---

### Post by agathian on 2008-12-14
Sounds like graphical login hangs - you might want to hit ctrl-alt-F1[ or 2 or 3], to get command line login. login thru that and look for error messages.. to begin with, check these files

~/.xsession-errors
/var/log/syslog
/var/log/daemon.log


First login thru the gui and after it hangs, go to the command line login - that way you will be able to see/capture the errors..

If you cant interpret the errors, post them here - someone might be able to help.

---

