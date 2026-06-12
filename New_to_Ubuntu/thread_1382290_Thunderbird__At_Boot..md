---
title: "Thunderbird  At Boot."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by soryu on 2010-01-15
How Do I Make Thunderbird Start Up At Boot?
What Command Do I Use?

---

### Post by Cheesemill on 2010-01-15
System > Preferences > Startup Applications

Click on add and type Thunderbird for the name and thunderbird for the command.

Click add then close and you're sorted.

---

### Post by Greenwidth on 2010-01-15
You can add it in:
System > Preferences > Startup Applications

Click add:
name: Thunderbird
command: <depends what version you have>

To find your version, in a terminal type thunder then hit Tab which will auto complete the name. Add to the command section above.
eg mines thunderbird-3.1

---

### Post by spiderbatdad on 2010-01-15
> How Do I Make Thunderbird Start Up At Boot?
What Command Do I Use? 
As a command, this worked for me.:
```
sudo cp /usr/share/applications/thunderbird.desktop /etc/xdg/autostart
```

---

### Post by soryu on 2010-01-15
Thank's, How Do I Mark This Thread Solved?

---

### Post by bcn17 on 2010-01-15
soryu. I would reccomend using alltray. 

>>sudo aptitude install alltray

Then navigate to startup applications like Cheesemill and GreenWidth said and create a new application launcher. 

Make the command:

alltray -na thunderbird %u

This starts alltray, doesn't show alltray in the thunderbird title bar (no alltray), has alltray open thunderbird, and uses the %u option, which I just use because it is the default for thunderbird. 

Now, when you close thunderbird it will "minimize" to the thunderbird icon that now resides in the notification area, right next to the picture of a network cable and the volume control. You can click this icon to maximize, and minimize it. Alltray will have it running at all times. Very convienient. This way you can have pop ups that thunderbird gives saying when new email is found in your inbox, however you don't have to have it taking up spacein your Windows Selector bar with other running programs. 

You can use alltray for any other program you want as well.

---

