---
title: "trouble viewing photos"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-08-03
Every time I try to view a photo full screen,ubuntu stops and reboots and I have to log on again. Is this a problem with compiz?I dont want to have to turn off compiz everytime I look at photos so does anyone have any other ideas?Thanks!

---

### Post by Volt9000 on 2009-08-03
Try checking out the system logs. Go to the menu items System > Administration > System Log.

Sorry, I'm not sure specific log to look for, but they're all sorted by date and timestamped, so you should be able to find it easily. Just take note of your clock before going fullscreen, and then find that corresponding time in the logs.

---

### Post by philinux on 2009-08-03
> **gertrude58 said:**
> Every time I try to view a photo full screen,ubuntu stops and reboots and I have to log on again. Is this a problem with compiz?I dont want to have to turn off compiz everytime I look at photos so does anyone have any other ideas?Thanks!

Could be graphics driver related. What make is you graphics card?

System >admin >hardware drivers. Is all ok here.

---

### Post by gertrude58 on 2009-08-03
All seems to be ok with drivers.My graphics card is intel 965, I know I had trouble getting compiz to work after upgrading to Jaunty. so maybe I'll have to wait till Karmic Koala comes out before it works properly? I hope they can fix this problem if thats what is causing it.

---

### Post by philinux on 2009-08-03
The fault is that your x session is crashing, interaction with graphics driver and compiz I guess. Have a peep in the xorg log file.

---

### Post by gertrude58 on 2009-08-03
Sorry,I dont know how to find it and probably wouldnt understand it if I could! Being a complete computer [not just linux] newbie.

---

