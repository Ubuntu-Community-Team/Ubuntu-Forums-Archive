---
title: "Close Windows with Fire"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-06-11
I've seen videos where when they close a window it appears that the window is being lit on fire and burned into non existence.  I've been playing around with animations in compiz but still cant figure out how to make it do that fire effect.  Please help.

---

### Post by dookiebowser on 2010-06-11
Open terminal
sudo apt-get install compizconfig-settings-manager
sudo apt-get remove simple-ccsm
sudo apt-get update
sudo apt-get install simple-ccsm

System->Preferences->Simple ConfigCompiz Settings Manager

Under Animations tab, Select "Burn" for whenever you want the effect to occur. 

To change the specific settings of the Burn effect, like color, duration, etc. Navigate to System->Preferences->CompizConfig Settings Manager and expand the Burn section for it's settings.

---

