---
title: "downloading and firefox freeze issues"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by phooper75 on 2010-01-15
Hi. I just installed ubuntu 9.10 on my kids computer as the old hdd failed and I didn't have any win xp discs to reinstall it. Really like it and thinking about putting it on my old iBook too. Of course everything was fine while I was using it. Now that I've given it to them a couple of problems.

Q1- I was trying to show my daughter how to download new programes through the ubuntu software centre. An error message came up with - 'can't download while other download programme is in use' (or something like that). Sorry but don't have the unit in front of me. I rebooted but it was still there. How do I stop this? The last thing I tried to install was HP printer drivers and got an error saying wasn't completed properly.

Q2 - Again my daughter was on runescape in firefox and after a short time the whole desktop froze. The mouse moved but was inoperable. Again after reboot same thing.

Next issue is that I have to walk my 12 year old daughter throuh any fixes over the phone so step by step solutions would be fantastic as I am a 4 day old user!!

Thanks for your help.

---

### Post by deveric on 2010-01-15
The unit could have been going through an update at the time. The message you received is due to the process that Ubuntu uses to retrieve software (apt) is in use somewhere else. Automatic updates use apt, software installs via the package manager use apt. Try doing it again, you may not have issues. Otherwise determining what is using apt over the phone to a 12 year old might be a difficult task.

---

### Post by dearingj on 2010-01-15
> **phooper75 said:**
> Q1- I was trying to show my daughter how to download new programes through the ubuntu software centre. An error message came up with - 'can't download while other download programme is in use' (or something like that). Sorry but don't have the unit in front of me. I rebooted but it was still there. How do I stop this? The last thing I tried to install was HP printer drivers and got an error saying wasn't completed properly.

I think this is what you'll need to do to fix that:
1) Open a terminal (Applications->Accessories->Terminal)
2) Copy and paste this command into the terminal, putting in your password when asked:
```
sudo dpkg --configure -a
```
3) Check to see if your printer works, and reinstall its drivers if necessary.


> **phooper75 said:**
> Q2 - Again my daughter was on runescape in firefox and after a short time the whole desktop froze. The mouse moved but was inoperable. Again after reboot same thing.

Strange. Does this happen when she's not on runescape as well? I'd suggest installing all available software updates (use System->Administration->Update Manager) once you get your installation problem resolved. Perhaps also install some other web browsers and try runescape in them.

---

### Post by dearingj on 2010-01-15
> **deveric said:**
> The unit could have been going through an update at the time. The message you received is due to the process that Ubuntu uses to retrieve software (apt) is in use somewhere else. Automatic updates use apt, software installs via the package manager use apt. Try doing it again, you may not have issues. Otherwise determining what is using apt over the phone to a 12 year old might be a difficult task.

Good point, deveric, but from what phooper75 said about failing to install the HP printer drivers, I'd guess that apt/dpkg was interrupted during the driver installation process and left a stale lock file, so probably nothing is actually using apt now.

---

### Post by ajgreeny on 2010-01-15
This may be one of the more recent ubuntu foibles of not only telling you updates are available, but also opening Update Manager in the background, and therefore stopping any other downloads using package managers such as apt-get in terminal or synaptic.  Versions before jaunty just used the update notifier to let you know but did not open Update Manager.

You can go back to this older manner of doing things if you want by opening configuration-editor (type** gconf-editor** in terminal) and going to apps -> update-notifier and removing the tick in auto_launch.  After closing this you will just be notified of update availability, and the Update Manager will not auto-open and stop other apt-using applications from working.

---

### Post by phooper75 on 2010-01-17
Fantastic. Running that command seemed to cure both the download and firefox problems. And all done over the phone painlessly too.

Thankyou.

---

