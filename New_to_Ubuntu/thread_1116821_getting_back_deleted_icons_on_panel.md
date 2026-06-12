---
title: "getting back deleted icons on panel"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by rajnikhil on 2009-04-05
Hi, I accidentaly deleted the network icon on top panel. Can some one guide me on how to get it. My network gives me trouble without it. Would some one please help me out. I need the exact same on which gets displayed by default with the installation.

---

### Post by trinidadflores on 2009-04-05
> **rajnikhil said:**
> Hi, I accidentaly deleted the network icon on top panel. Can some one guide me on how to get it. My network gives me trouble without it. Would some one please help me out. I need the exact same on which gets displayed by default with the installation.

right click and select "add to panel"

---

### Post by rajnikhil on 2009-04-05
I tried it but I ain't getting those options which I used to get earlier and that is causing me humongous network probs!

---

### Post by tea for one on 2009-04-05
Right click and choose "Add to Panel"
Select "Notification Area"

I am fairly sure that the Network Monitor applet will appear in the notification area.

---

### Post by rajnikhil on 2009-04-08
No, tea for one, that didn't work! Any other trick?

---

### Post by plucky on 2009-04-08
Alt F2 and use ```
nm-applet &
```


Good Luck

---

### Post by Jakey_TheSnake on 2009-04-08
^ If that doesn't work, what options are you getting?

Upload a screenshot of the "Add to Panel" box with "network" typed in the find bar at the top. 

If it does work, use this to save your panel settings:

```
sudo apt-get install gconftool-2
```
```
gconftool-2 --dump /apps/panel > ~/ubuntu.entries
```

Once you have done that, you can load previous panel configurations exactly as you saved them with:

```
gconftool-2 --load ~/ubuntu.entries
```

---

### Post by tea for one on 2009-04-08
Are you looking for the Network Monitor Applet?

If you are:-

Right click panel
Click "Add to Panel"
Select "Network Monitor" applet (version 2.12.1 in Ubuntu Hardy)

I hope that this is the one you are looking for?

---

