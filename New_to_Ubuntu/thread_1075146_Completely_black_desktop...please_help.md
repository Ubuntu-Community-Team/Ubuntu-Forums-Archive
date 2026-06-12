---
title: "Completely black desktop...please help"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Adamantus on 2009-02-20
Right now I'm using my girlfriend's computer because I can't use mine. I'm running Ubuntu 8.04. I've been messing around with my desktop trying to see what I can do with it. I was trying to see if I could make it look like OSX, so I got AWN and tried using the Mac Menu applet, as described here:

[http://ubuntuforums.org/showpost.php?p=2591836&postcount=532]("http://ubuntuforums.org/showpost.php?p=2591836&postcount=532")

After reloading my desktop (CTRL-Alt-Backspace), I got to the login screen. After logging in, it went to the blank orange screen then went black. My cursor is still there. When I try some of the desktop effects like Compiz Cube, the cube will appear with completely black screens. I've tried loading terminal by the keyboard but I have no idea if it appears or not. Is there any way to fix this without reinstalling?

I'm pretty sure it had something to do with the dpkg -i *.deb part, because it said something along the lines of "Warning: downgrading gnome panel."

Lastly, I tried booting into an older kernel and I got the same black screen. 

Lastly lastly, for some reason, my skype box popped up. Nothing was wrong with it, but it was the only window. I can get into the terminal by using CTRL-Alt-F1. Is there some way to fix the problem that way?

---

### Post by bumanie on 2009-02-20
Try reinstalling gnome desktop. Hit ctrl-alt-F1 together; login with user name and password when asked. Then> sudo apt-get install gnome-desktopThen reboot via code > sudo shutdown -r nowHopefully your gnome desktop will be back after the reboot. Alternatively boot into recovery mode and try some of the options there.

---

### Post by Adamantus on 2009-02-20
Okay, I tried installing gnome-desktop, but it said it couldn't find that package. So I booted into recovery mode and repaired some packages using the 'dpkg' option. I also used the 'xfix' option. Now, it boots into the orange screen (after login) and doesn't go black. But I can't use the compiz cube. The only thing that loads is the skype window (no panels, can't right click, etc.). Could I try anything else? I'd be okay with completely re-installing the desktop...I just don't want to have to format anything since I have a lot of important data on my comp.

---

### Post by Adamantus on 2009-02-20
A couple new things: although it still loads to the light orange screen after the login screen, I realize that I have the ability to change desktops (It's just that compiz fusion is no longer installed, so I can only change it by pushing Super+left or right. My skype window pops up, and it connects, even without my ethernet cable connected, so the wireless is still working.

This seems like a really easy fix. Could I just uninstall gnome and try to install the desktop again (I kind of wanted to try out Xfce)? Or is this another problem due to the "dpkg -i *.deb" step when trying to install the Macmenu applet?

---

### Post by anewguy on 2009-02-20
Try again using the command line with this package name:

sudo apt-get install gdm  <enter>

That is the package name for the gnome display manager.

If you think it may have gone back to a previous version, you could always try:

sudo apt-get update

sudo apt-get upgrade (don't know if you are in 8.04 if this would upgrade you to 8.10 or not, so you may want to be a little careful with this one).


Dave :)

---

### Post by farsight on 2009-02-20
To my knowledge the sudo-apt get upgrade will not upgrade you to v.8.10 unless you expressly specify the repository from which to draw the upgrade using synaptic.

---

### Post by Adamantus on 2009-02-20
I've already done update and upgrade and neither have worked. I just tried to install gdm and it brought up a list of dependencies that aren't met.

---

### Post by Adamantus on 2009-02-20
Okay, I solved it. I'm just posting this in case anyone else has this same problem (especially when installing the Macmenu applet). I think while trying to install it, it took away some Gnome libraries or something. In the terminal (CTRL-Alt-F1), it suggested I do 'sudo apt-get -f install' and it worked. It installed all the dependencies (especially some, I think, necessary ones, like libgtk). Anyway, I rebooted and my desktop came back just as it was, except my graphics card driver had been disabled (and compiz fusion in turn), which was easy to re-enable.

How do I mark it as 'solved'?

---

### Post by anewguy on 2009-02-21
2 notes for you, 1 to answer your last question:

(1) If you try to install a package and come up with missing dependencies, just do sudo apt-get build-dep 'package name', when that finishes just do the sudo apt-get install 'package name'

(2) for now, the ability to mark a thread as solved is turned off.  However you can still do it:

go back to your original post, click edit, then click advanced.  Now you can edit the title - just either prefix the title with SOLVED or suffix it with SOLVED.  Not as handy or uniform as the solved function, but until it returns this is how to do it.

Dave :)

---

