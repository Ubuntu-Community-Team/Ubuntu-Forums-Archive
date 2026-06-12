---
title: "How to shutdown/restart a frozen screen?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Hagumi on 2009-08-30
I just installed ubuntu a couple of days ago, and pidgin is freezing my screen every time I use it.  And I really hate to cold boot my laptop.  So is there a way to restart the desktop screen?  I'm a windows user.  I was wonder is there anything equivalent to [ALT]+[Ctrl]+[DEL].  Then just ends explorer.exe and restarts it again?   I've tried [ALT]+[Ctrl]+[F1] and [ALT]+[F2] but they do not work.  And no, I can't even use my terminal.  Every thing except the mouse is frozen.

---

### Post by Lampi on 2009-08-30
try ctr+alt+backspace

this will force xserver to reload

---

### Post by TuckLive on 2009-08-30
If your using a version prior to 9.04, then you can use Ctrl + Alt + Backspace to restart X.

It was removed in 9.04, but I believe can be re-enabled some how.

---

### Post by freak42 on 2009-08-30
there are also keys to more or less savely reboot a linux system

press and hold the alt and sysRq keys while pressing the keys R-E-I-S-U-B one after another with about 5 secs breaks in between two keys. you can google them up to get more info, basically they instruct the kernel to save some stuff, unmount disks.. etc.. 

hth

---

### Post by tgeer43 on 2009-08-30
CTRL+ALT+BKSPC is the key combination to restart the X-server. Unfortunately it is disabled by default in 9.04 Jaunty.

To enable it, you'll need to edit the /etc/X11/xorg.conf file as root. MAKE A BACKUP FIRST!

Add the following code to the end of the file:
```
Section “ServerFlags”
   Option “DontZap” “false”
EndSection
```That's it. Reboot your system and you should now have CTRL-ALT-BKSPC functionality.

tgeer

---

### Post by TuckLive on 2009-08-30
> **tgeer43 said:**
> CTRL+ALT+BKSPC is the key combination to restart the X-server. Unfortunately it is disabled by default in 9.04 Jaunty.

To enable it, you'll need to edit the /etc/X11/xorg.conf file as root. MAKE A BACKUP FIRST!

Add the following code to the end of the file:
```
Section “ServerFlags”
   Option “DontZap” “false”
EndSection
```That's it. Reboot your system and you should now have CTRL-ALT-BKSPC functionality.

tgeer

Ah, thanks for finding that for me.

---

### Post by Paqman on 2009-08-30
CTRL-SYSRQ-K is the replacement for CTRL-ALT-BACK, no need to change your computer, just update the file in your head that stores this useful little bit of info! ;)

---

### Post by Copernicus1234 on 2009-08-30
Actually there is no need to kill the entire x server just because a application freezes it. What I do when it happens is press CTRL-ALT-F2, login, list processes (for example ps -ef | grep pidgin) and kill them off.

Then switch back to X with CTRL-ALT-F7.

---

### Post by tuxsheadache on 2009-08-30
> **freak42 said:**
> there are also keys to more or less savely reboot a linux system

press and hold the alt and sysRq keys while pressing the keys R-E-I-S-U-B one after another with about 5 secs breaks in between two keys. you can google them up to get more info, basically they instruct the kernel to save some stuff, unmount disks.. etc.. 

hth

The best way to do this is to remember it as a mnemonic, Raising Skinny Elephants Is Utterly Boring

---

### Post by PaulChamberlain on 2009-08-30
Hiya,
I am new to ubuntu and have been experiencing similar issues when I have the toolbars on auto hide and the screen appears to be frozen.  However ALT and TAB still gives me my terminal window.  (I was offered the advice to always have one open.)  Using the command 
sudo killall gnome-panel 
reset the toolbars and the screen came back as well.

If it helps cool if it doesn't someone might get a use out of it

---

### Post by TuckLive on 2009-08-30
> **Copernicus1234 said:**
> Actually there is no need to kill the entire x server just because a application freezes it. What I do when it happens is press CTRL-ALT-F2, login, list processes (for example ps -ef | grep pidgin) and kill them off.

Then switch back to X with CTRL-ALT-F7.

The OP tried CTRL-ALT-F2, it didn't work.

---

### Post by Paqman on 2009-08-30
> **PaulChamberlain said:**
> ALT and TAB still gives me my terminal window.  (I was offered the advice to always have one open.)  Using the command 
sudo killall gnome-panel 
reset the toolbars and the screen came back as well.


You could probably just Alt-F2 and run that command, no need to have a terminal running if that's the case.

---

### Post by PaulChamberlain on 2009-08-30
> **Paqman said:**
> You could probably just Alt-F2 and run that command, no need to have a terminal running if that's the case.
Thank you.  I hadn't used that.  Handy key combo to know
:)

---

### Post by Paqman on 2009-08-30
You won't need sudo on that command either. The panels are on your desktop, so owned by you.

---

