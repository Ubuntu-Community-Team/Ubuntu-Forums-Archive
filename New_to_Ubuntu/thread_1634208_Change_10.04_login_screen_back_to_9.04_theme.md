---
title: "Change 10.04 login screen back to 9.04 theme"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-30
Hi,
Anyone know how to change the Login Screen in 10.04 back to the login screen for 9.04 ?

Where can I get that image?  I believe it's a PNG file?

I particularly liked that login screen.

Cheers!

---

### Post by BrandonC19 on 2010-11-30
I can't give you any direct links, but I can tell you how to accomplish it. First you need to open the terminal and type (or Software Center and click for it ;)) ```
sudo apt-get install ubuntu-tweak
```. Then go on line and find a copy of the image, and save to your hard drive, preferably the "Pictures" folder, and open Ubuntu Tweak. (Applications > System Tools > Ubuntu Tweak) and on the left pane navigate to the Login Settings sub-item under the "Startup" category, and you'll see an "Unlock" button in the bottom-right corner, click it and enter your password. Now all you have to do id simply click the picture under the text "Click the button to change the login screen background", navigate to your picture you downloaded earlier, apply it, logout and enjoy.
Hope this helps!
/Brandon

---

### Post by mistypotato on 2010-11-30
From another thread....

This worked fine....but..you'll still will get the 10.04 widget where you actually choose your login (the large square box smack dab in the center), instead of the small, neat, attractive place you entered your login and password in 9.04

**Credit..BrokeMahPC**
You want to change the login screen background?
Here is how:
It's best to chage your image to the resolution of your monitor - use gimp?
It may be easier to put the background image you wish in /usr/share/backgrounds first if not already there, doesn't really matter

-log out
-at the log in screen press CTRL+Alt+F1,
-enter user name and password
-Code:
export DISPLAY=:0.0
-press enter
Code:
-sudo -u gdm gnome-control-center
-press enter, expect errors,
-when terminal output stops press CTRL+Alt+F8

The Gnome Control Center should appear (it looks exactly the same as Appearance preferences from the Gnome Desktop, but , it relates to the login screen in this case.)
In Appearance
-choose Add and pick a new background, (or browse to one if it's in a different folder)
-close Gnome Control Center,
-press CTRL+Alt+F1
-at the terminal cursor type code:
sudo reboot

---

### Post by mistypotato on 2010-12-04
Final word.....

The 9.04 Login and Desktops wer the best looking.

Ever since then Ubuntu has gone with some pretty lame looking pastel-ish...very unattractive Login Splash and Desktop themes.

Good thing we can change them :KS

---

### Post by BrandonC19 on 2010-12-05
Well the ugly login is gnome2's fault, there's a program called gdm2setup that kind of helps, if it bothers you that bad, you could always try downgrading to gnome1, not reccommended, but essential if you want the 9.04 type gdm logins.

---

### Post by mistypotato on 2010-12-14
I did manage to do this.

When I boot now in 10.04 it looks like I'm booting into 9.04.....except for the square box where you actually enter the UN/PW

I may change that back eventually.

It was just a really smooth and appealing gateway into Ubuntu :KS

---

