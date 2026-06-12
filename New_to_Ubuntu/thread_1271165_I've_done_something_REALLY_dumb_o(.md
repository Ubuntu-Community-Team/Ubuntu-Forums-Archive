---
title: "I've done something REALLY dumb :o("
date: 2009-09-20
forum: New to Ubuntu
---

### Post by mbaggia on 2009-09-20
Hello,

I'm running Ubuntu 9.04 (Jaunty), and decided to do a little pruning of the installation. I never use (and never plan to), Evolution mail, and so, using package manager, uninstalled all the entries marked Evolution, leaving only a couple (those concerning PalmOS and Pidgin).

Unfotunately, after applying the changes, I could not navigate to any of my directories, getting an error along the lines that no suitable application could be found to navigate.

On reboot, I get the login prompt, and having entered my credentials, I get a blank screen, with a cursor arrow on it. That's it. The cursor moves around, but nothing else appears onscreen at all.

Grub lists 3 different version of Ubuntu (2 older iterations), and I have the same result no matter which I choose.

I'm reluctant to do a fresh install, as I have documents which I don't want to lose.

Any help, please?

---

### Post by mapes12 on 2009-09-20
> I'm reluctant to do a fresh install, as I have documents which I don't want to lose.Boot from a Live CD and see if you can locate your critical stuff and copy it to external media.

Next time around, to protect your critical stuff you may want to put /home on its own partition. If this is alien speak then please post back for more info on how to do this.

Mark

---

### Post by themusicalduck on 2009-09-20
Slightly long shot here, but maybe if you log into a virtual terminal with ctrl+alt+f2 (if you can) and try to reinstall evolution with ```
sudo apt-get install evolution
``` it might reinstall everything including any dependencies that you removed and fix things.

Although backing up things with a live disc is the best thing to do first.

---

### Post by Paqman on 2009-09-20
The problem with uninstalling Evolution is that it unistalls a lot of other useful stuff.

If you can boot into recovery mode and get to a command line:
```
apt-get install ubuntu-desktop
```
(You won't need sudo at the recovery prompt, it's a root session)

This will reinstall Evolution, i'm afraid. But it will also reinstall all the good stuff you've lost.

---

### Post by scorp123 on 2009-09-20
> **mbaggia said:**
> The cursor moves around, but nothing else appears onscreen at all. And when you hit Alt+F1 or Alt+F2 do you get to see a text-mode login screen? If yes: You could try and get the desktop packages again:

```
sudo apt-get --reinstall install ubuntu-desktop gdm gnome-app-install gnome-desktop-data gnome-panel 
```

Above command *really* should pull in tons of other dependencies so you *really* really should get Ubuntu's GNOME desktop environment back.

BTW: When it prompts for your password nothing will be echoed back. Just keep typing your password blindly and hit the Enter key. If and when successful it will proceed and download the packages; if not it will prompt you for the password again.

And last but not least: The obligatory chastisement. Next time when you uninstall stuff **please read the messages!!** Both "apt" in text mode and the GUI-frontend Synaptic will tell you in details what is going to be removed. If all you wanted is to remove a single mail program and all of a sudden dozens of packages are going to be removed as well then it should be obvious that something is wrong and that you are removing way too much ...  ;)

---

### Post by scorp123 on 2009-09-20
> **Paqman said:**
> If you can boot into recovery mode and get to a command line Good idea. I keep forgetting about that one. So If the text-mode login prompts don't work for whatever reason then at least this should work.

---

### Post by mbaggia on 2009-09-22
Thanks all for your help and advice. I used LiveCD to backup my files to a USB stick and re-installed, as the commands given did go through the installation process, but didn't actually reinstall Evolution.

On the plus side, I decided to go the whole hog and get rid of WindowsXP for good...

---

### Post by t0p on 2009-09-22
> **scorp123 said:**
> And when you hit Alt+F1 or Alt+F2 do you get to see a text-mode login screen?

Just in case anyone reads this and gets confused when Alt+F1 doesn't switch thm to a "text-mode login screen": to get to the console scorp123 is referring to, you actually need to press **Ctrl+Alt+F1**.  There are actually 6 of these consoles, reached by pressing Ctrl+Alt+F1-F6.  Pressing Ctrl+Alt+F7 will return you to the GUI (Gnome or whatever).

---

