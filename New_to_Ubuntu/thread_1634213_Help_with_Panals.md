---
title: "Help with Panals"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by max00355 on 2010-11-30
Ok so i deleted the bottom panel to make more space to see my screen because i have a netbook but now i need it back and i dont kno how to get it. Im not talking about the panal on top where you can drag things  on to it and stuff im talking about the one where when you minimize a window you can see it in the bar.

please help

---

### Post by MooPi on 2010-11-30
Each of these in terminal
1: ```
gconftool --recursive-unset /apps/panel
```
2: ```
rm -rf ~/.gconf/apps/panel
```
3: ```
pkill gnome-panel
```
This should reset to default config

---

### Post by rusty149 on 2010-11-30
1. Right-click your current panel and select New Panel. 
 
2. If the new panel does not appear at the bottom, then right-click select properties and select bottom. 
 
3. Right-click bottom panel and select Add To Panel
 
4. Select Window List and click Add.

---

### Post by mkarr on 2010-11-30
Thanks Moopi! I've been having all kinds of problems with gnome-panel and the weather report app and following your post I can finally reset and start over. Great post! It's a keeper. :D

---

### Post by max00355 on 2010-11-30
thank you so much this was a  life saver i had so many windows open and i dint even know 
-thanks

---

