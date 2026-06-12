---
title: "Missing main taskbar"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-07-22
Hey,

I just ran Starcraft under Wine (running in a full-screen mode) for the first time, and when I exited the program, I had to re-login to Ubuntu.  When I did so, I get a completely blank desktop with no main taskbar at the top.

Believe me, it took forever to find a way to open Firefox.  There is no C:\Program Files anymore, and it was a good way to learn a bit about how programs are sorted and assembled in Linux.

So, how do I restore my toolbar?

On a side note, I can't maximize any windows either.  Is that a related issue?

Thanks,

--Red

---

### Post by Durden on 2009-07-22
so you have a terminal? If I read that wrong then type alt+f2 and type in "gnome-terminal"

Once the terminal is open type "gnome-panel" and let us know what happens. It's possible Wine resized your desktop and they are just hiding.

---

### Post by Durden on 2009-07-22
If you aren't worried about losing settings you can type "rm -rf .gnome2" in the terminal to reset gnome to the defaults.

---

### Post by Redmage913 on 2009-07-22
I didn't use the terminal to open firefox.  I had a shortcut to my external hard drive on the desktop (my only shortcut - I just installed a fresh copy of ubuntu netbook remix after having issues with xubuntu and mounting ISO files), so I started perusing the file system until I stumbled into a folder with shortcuts to various programs.  I can't even switch over to that window; I am stuck within Firefox, even though I can see the file manager behind this window.

---

### Post by Redmage913 on 2009-07-22
I had also switched over to the normal view after switching out of the netbook remix program launcher system without any issues before I had run starcraft.

---

### Post by Durden on 2009-07-22
so does alt+f2 not work?

Sounds like you lost metacity as well (the actual window manager).

If you can't do an alt+f2 try and alt+backspace and let me know what happens.

---

### Post by Redmage913 on 2009-07-22
nothing.  alt+backspace does nothing, along with alt-tab to attempt to switch back to the file browser.

---

### Post by Durden on 2009-07-22
Navigate around like you did for firefox again and look for gnome-terminal. Probably in /usr/bin or /usr/sbin, could also be in /usr/local/bin.

I'm not on Linux at the moment so I can't tell you for sure. Once you have the terminal type "mv .gnome2 .gnome2.backup" to set gnome back to defaults.

---

### Post by Durden on 2009-07-22
Just booted into linux for ya. It's in /usr/bin/gnome-terminal

Get that up and we can get this fixed for ya

---

### Post by Redmage913 on 2009-07-22
I managed to open up the main menu, so I switched over to the Netbook Remix layout.  I now have access to all programs, though I have to close each program to get access to another.  Rather annoying.

I typed in rm -rf .gnome2 like you said, and it didn't seem to do anything.  I restarted the computer after doing this and it still did not seem to have any effect.

---

### Post by wojox on 2009-07-22
Here you might be having this problem

[https://bugs.launchpad.net/desktop-switcher/+bug/349519](https://bugs.launchpad.net/desktop-switcher/+bug/349519)

---

### Post by Redmage913 on 2009-07-25
I reinstalled Ubuntu Netbook Remix.  So in short, I can't switch to the classic Ubuntu mode without messing up my operating system? Is this a common bug with the Netbook Remix?

---

### Post by groeswenphil on 2009-07-25
Are you using Netbook Remix?

Something awfully similar happened to me just after I changed from the standard netbook desktop to the standard Ubuntu desktop.

I was stuck with a blank desktop with no panel at the top.....and after fiddling I managed to get a quarter sized Firefox window.
Apparently it's an identified bug.
Check this out.

[http://ubuntuforums.org/showthread.php?t=1221659](http://ubuntuforums.org/showthread.php?t=1221659)

Phil

---

