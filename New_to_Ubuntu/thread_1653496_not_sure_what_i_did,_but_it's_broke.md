---
title: "not sure what i did, but it's broke"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by Johnce on 2010-12-26
hello! i'm a newbie for sure. My firefox had 'lost' it's back - forward - and refresh button and it would not set back to default even in safe mode. I tried to download firefox as i was going to uninstall - reinstall. all of the sudden my cairo dock disappeared and i cannot access any applications. I used synaptic (accessed from terminal) to remove cairo and then tried to reset my gnome panels (gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel) and now i cannot even access anything from alt-f2, it just blinks and resets. when i hover my desktop something is running in the background but i dont know what. i'm really confused and frustrated . . . .

---

### Post by Johnce on 2010-12-27
fixed! sort of . . . 

I reset my gnome settings and I have my old firefox back! 

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

ps. I logged in to recovery mode to enter the code above.

---

