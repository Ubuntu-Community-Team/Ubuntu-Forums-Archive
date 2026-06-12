---
title: "Better graphics card running slower?"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by MrSnuggles on 2010-03-11
I recently changed to a Nvidia graphics card from my Radeon for obvious reasons on a linux (Lack of support). Well, I've noticed  that any games I played previously (Such as puzzle pirates...) runs significantly slower and has a huge amount of delay with the new graphics card. I can't really understand why. Heres a comparison thing of the two cards, my current is the one on the left. [http://www.gpureview.com/show_cards.php?card1=610&card2=476](http://www.gpureview.com/show_cards.php?card1=610&card2=476)

I have installed the Nvidia driver through Hardware Drivers.

---

### Post by TeDiouS on 2010-03-11
I want to say it's the driver... but, I'll wait for more info.

What version of Ubuntu, or the Distro you are using?
What driver is it? (Version) It may be found in the driver name, not sure.

Also keep in mind that PCI is slower than the AGPx8, unless you meant the PCI-Express.

---

### Post by MrSnuggles on 2010-03-11
Using Ubuntu 9.10, and driver 185, the "[Recommended]" one.

---

### Post by TeDiouS on 2010-03-11
The latest may help w/ some speed.

And this thread may help to upgrade it.
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

But... be careful, if not done properly you can render your Ubuntu GUI dekstop not usable until fixed.

**Read the documentation.** I suggest tolerating what you have now, and read up on how to do this. Then to go through w/ it. 

*Correct me if I'm wrong, people.*

---

### Post by MrSnuggles on 2010-03-11
K, so I'm trying the upgrade, but for some reason it wont let me log in. Asks for my password, I type the password I use for Sudo and giving admin rights to programs, and it says it's invalid. It also wont accept a blank box, so I don't know what to do now.

---

### Post by TeDiouS on 2010-03-11
That's no good.

Make sure the username and password you're typing are correct.

What steps did you take before this happened?

Have you installed the driver, Did you reboot, etc.

---

### Post by MrSnuggles on 2010-03-11
All I've done up to that point is download the driver, and when I hit the Alt+Ctrl+F1 it takes me to the terminal thing, and says something like MrSnuggles login: (MrSnuggles is my log in name) if I type anything it goes down a line with "Password:" and if I type my password and hit enter it says invalid password.

---

### Post by albert s on 2010-03-11
CAPSLOCK on ?
just a thought...

---

### Post by MrSnuggles on 2010-03-11
Nope, capslock is off.

---

### Post by TeDiouS on 2010-03-11
Oh you're in a terminal, (lol).

Just reboot to get back to GDM, the login manager. 
Hit CTRL+ALT+DELETE. Or press the power button on the desktop/laptop, if there is one. 
Unless you have work you need to save... in that case skip this for now.

Those screens are quite useful. I enjoy switching from one work point to the next in a swift tap of the keys.

When you are to login that way, remember. UserName/ID is lowercase, and password is case sensitive. 

MrSnuggles should be **mrsnuggles**

---

### Post by MrSnuggles on 2010-03-11
Well, it says "mrsnuggles-desktop login" so would I type mrsnuggles again?

Figured it out, k, so when I try to "cd desktop" it says cannot find "desktop"

When I try to stop gdm it says it's a service command and I'd have to type something like "service gdm stop", and when I try that it says it can't find gdm.

And finally when I try to run the installer, it says type N and hit tab and it should find it, yeah, does nothing. I'm fairly sure I'm in the right folder with it, as it's in Home.

---

### Post by TeDiouS on 2010-03-11
Gah, sorry for the delay, I didn't see a new page..

The Linux terminal is case sensitive as well. So "Desktop" isn't the same as "desktop". 

And try this:
Instead of typing the whole file name out. Type part of it (while in the folder), and press the tab key. it should finish it for you.

You can use this to see what is in the folder you're currently in. ```
ls
```And to stop gdm, type this out fully:
```
sudo /etc/init.d/gdm stop
```It's from the link in my post earlier, but I tried it on my system (Not w/ gdm mind you, but it worked)

Hope that helps some.

---

### Post by marshmallow1304 on 2010-03-11
[This PPA]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") might be of help to get the latest drivers rather than installing manually.  Once you add it and upgrade to the new packages, you simply go to System->Administration->Hardware Drivers, deactivate the old driver, and activate the current one.

---

### Post by TeDiouS on 2010-03-11
Much more simple, thank you marshmallow1304.

---

