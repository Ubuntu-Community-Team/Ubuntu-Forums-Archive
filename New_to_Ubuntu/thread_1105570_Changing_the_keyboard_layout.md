---
title: "Changing the keyboard layout"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by bcasanov on 2009-03-24
Hi,

I am trying to change the keyboard layout in Xubuntu Intrepid Ibex from USA English (us) to Spanish (es).  I added the Keyboard Layout Switcher to my panel, but I was not able to switch layouts from there.  I implemented the tips in this link: [http://ubuntu.sabza.org/2006/10/13/xubuntu-easily-switch-keyboard-layout/#comments](http://ubuntu.sabza.org/2006/10/13/xubuntu-easily-switch-keyboard-layout/#comments) except I went with the ctrls_toggle option.  This did not work for me because when I logged back in and pressed both controls, the keyboard layout did not switch.

I really need to have an easy method of switching keyboard layouts (that does not involve fiddling with xorg.conf) as soon as possible for a paper in Spanish that I have to do, and I would tremendously appreciate any help you may give.

---

### Post by llamabr on 2009-03-24
Can't you just go to:
system>preferences>keyboard 

and switch?  Seems pretty quick.

---

### Post by bcasanov on 2009-03-25
I'm using Xubuntu, and it does not have System>Preferences>Keyboard.  It does have a Settings Manager under Applications>Settings, and there, I can go to Keyboard, but in this window, the keyboard layout section (under the layouts tab) only allows me to add or delete keyboard layouts, not switch from one to another.

---

### Post by bcasanov on 2009-03-25
Any ideas?

---

### Post by mkvnmtr on 2009-03-25
Add the keyboard that you wish to have as an alternate and the panel icon [applet] will allow you to switch. Watch to see that you get the keyboard you want, there are about five different spanish keyboards.

---

### Post by bcasanov on 2009-03-25
Hi mkvnmtr, 

Under Applications>Settings>Settings Manager>Keyboard Preferences>Layouts, I chose Spanish (es) with the No Dead Keys "nodeadkeys" variant as the other keyboard layout besides English (us).  I had to disable the option of "Use X configuration" to add the Spanish layout.  Once I have added it, I clicked on the panel icon (showing the US flag) and nothing happened; it did not switch to Spanish or show Spain's flag.  I checked the applet's Properties found from the right-click menu and I found that it only lists US as an option under Default Layout.

---

### Post by juanc44 on 2009-03-25
Thanks bcasanov, your comment help me, now I can switch between layouts.  I am using Ubuntu

---

### Post by bcasanov on 2009-03-25
You're welcome, juanc44.  I think with Ubuntu that keyboard layout switching is a lot easier than with Xubuntu, since there is a graphical panel applet that allows easy switching of layouts even with keyboard shortcuts.  I wish that Xubuntu were treated with the same level of attention.

---

