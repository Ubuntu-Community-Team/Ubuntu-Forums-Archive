---
title: "I need an answer!"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by myrtle001 on 2010-08-13
I am a noob at this so this may be a stupid question...

Ok, while installing updates for Ubuntu (Wubi), a dialog comes up asking if I want to Continue Without Installing GRUB. I need to know this before I click forward!

Thanks in advance!:D

**EDIT**: Here's the dialog:
[ATTACH]166339[/ATTACH]

---

### Post by Paul820 on 2010-08-13
I've never used wubi, but did you click that little help button i see there? :D

---

### Post by myrtle001 on 2010-08-13
Here's what the help dialog says:
[ATTACH]166340[/ATTACH]
I take it by saying that *I* chose not to install GRUB to any devices (I never chose anything) that that is what *Wubi* decided.

Just curious which is the **safe** route to go when you're not sure whether to install GRUB or not. I just want to make sure I know what I'm doing since I'm a noob.;)

Thanks!:)

---

### Post by da burger on 2010-08-13
Wait for someone to confirm this but I think you should leave the box checked and continue. If GRUB isn't already installed it's because wubi doesn't need it.

---

### Post by bodhi.zazen on 2010-08-13
wubi uses the windows boot loader, so no you do not want to install grub.

With that said, IMO, if you are going to use Ubuntu long term you should bite the bullet and perform a standard install.

---

### Post by myrtle001 on 2010-08-13
Alright, what I did was kept the box ticked and went on forward (not installing GRUB).

Thanks guys, I'll boot into Windows after a restart here to tell you if it worked!:D

---

### Post by myrtle001 on 2010-08-13
Ok, so I just decided to boot into Ubuntu this time, but now I've got a problem (probably in no way related to the update).

The boot all worked fine, but now once I logged into Ubuntu and got Chromium up and running, my touchpad quit working!. I can move the mouse around, but I can't click! I put a mouse into the computer, seemed promising at first, but has the same problem - no clicking!

I was able to navigate to here by clicking the tab button quite a few times and enter a few.

I was typing in a question for rebooting my computer without the mouse, and right as I was about to post: it started working!

But, its now back down (right as I was writing this message). What is the reboot command on the keyboard?

Thanks in advance!:D:D

---

### Post by theozzlives on 2010-08-13
Try using FireFox instead of Chromium.

---

### Post by mikewhatever on 2010-08-13
The reboot command is 
```
sudo reboot
```

---

### Post by myrtle001 on 2010-08-13
I'm not able to get to the terminal or any application. I'm stuck inside Chromium with my mouse icon being the one like when you're typing inside a text box and the icon doesn't change. I saw there is a keyboard command (something like Ctrl+Alt+Del+R+S+U+D, but I'm not sure) to make a clean reboot. I'm not able to make a hard reboot since I'm using the Wubi-Installed version or Ubuntu Lucid.

I'm not able to do anything outside of somewhat using chromium. Even if I click somewhere else it just highlights the address box, so I am able to refresh pages. But it won't go back to the normal mouse icon.

Thanks in advance!:D

---

### Post by ajgreeny on 2010-08-13
You can get a terminal with **Ctrl+T** normally, but if that does not work use **Alt+F2** and in the box enter **gnome-terminal** and you will get the terminal start for you.  You can then stop chromium with ```
killall chromium-browser
``` and see if your cursor goes back to normal.

If none of that works try **sudo reboot** or **sudo shutdown -h now** in the terminal, or even the keyboard trick you referred to:-

Hold down AltGr+PrintScreen/SysRq and slowly type R E I S U B with a second or two between key presses.  I am assuming that works on a wubi install, and have no reason to think it will not.

---

### Post by mikewhatever on 2010-08-13
Looks like this chromium thing will have to go.;)
Anyway, alt+ctrl+del brings up a shut down prompt on my system,
alt+f1 should bring up the menu, which is a way to Terminal.

---

### Post by Zorgoth on 2010-08-13
If you're computer is completely locked up you can type Ctrl-Alt-F1 to get to a terminal session, and Ctrl-Alt-F7 to get back.  This often works when other methods fail.  From a security perspective, if you care, remember to manually log out from such a session - otherwise anyone could get in as the session has no automatic timeout.

And by the way, responding to the title, 42!

---

