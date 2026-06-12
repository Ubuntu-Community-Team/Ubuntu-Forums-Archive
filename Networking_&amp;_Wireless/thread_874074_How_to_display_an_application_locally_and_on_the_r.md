---
title: "How to display an application locally and on the remote machine using SSH"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by dandyx on 2008-07-29
Using SSH I can either start and display an application on the remote machine or start it on the remote machine and display it on my local machine. I wonder how to start it on the remote machine and display the application both on the remote machine and locally. Gutsy is running on both. Would be lovely to equip my highly computerallergic mother with a computer, which I could manage remotely, start applications like Skype etc. 
Could anyone please point me in the right direction?

---

### Post by kdorf on 2008-07-29
The best thing to do would be configure VNC. There is an option in GNOME (System > Preferences > Remote Desktop) to allow users to remotely control your session, either with a password or with your authorization (or both). You should then both see the same desktop.

EDIT: Sorry, didn't look at the kubuntu flag. In that case, look for a similar option in KDE.

---

### Post by dandyx on 2008-07-30
Yeah, thanks kdorf! 
After fiddling around with ssh and krdc I realized that it might be much easier to just install edubuntu on my mothers machine and on an unused partition of my own box. And doing that realized that gnome has become pretty sexy. Wow, basic tools, just working out of the box! Got it all working in just two hours. Made my day!

---

