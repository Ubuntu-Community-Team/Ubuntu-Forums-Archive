---
title: "Where is sensors-applet"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by tekiy on 2011-07-01
I installed the sensors-applet package, but where is the applet?
(ubuntu 11.04)

---

### Post by grahammechanical on 2011-07-01
Is this XSensors? If you are using Unity then click on the Dash (the Ubuntu icon in top left corner) and type in the search bar  x  and you will see an icon for XSensors, Click on it and the utility will load. Or drag the icon to the launcher. Right click on it and select Keep in Launcher. And it is there whenever you want to use it.

If you are referring to an applet that resides in the top panel then you need to be in Ubuntu Classic mode to see that. To get that type of applet appearing in Unity requires advice that I do not have.

Regards.

---

### Post by mcduck on 2011-07-01
> **tekiy said:**
> I installed the sensors-applet package, but where is the applet?
(ubuntu 11.04)
Just right-click on the panel, select "Add to Panel" and find the applet on the list. You can then drag&drop it to where you want in the panel.

Note that sensors-applet only works with classic Gnome panels. If you are using Unity, you'll need some indicator applet to do the task instead. Like this one, for example: [http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html]("http://www.webupd8.org/2011/04/indicator-sensors-displays-cpu.html")

---

### Post by tekiy on 2011-07-01
I am using the classic desktop, but I can't find any such applet in the 
'Add to Panel' ?

The should be an green applet for "hardware monitors" but it's not there?

---

### Post by Frogs Hair on 2011-07-01
```
sudo apt-get install lm-sensors
``` ```
sudo apt-get install sensors-applet
```

You may have to restart before the applet appears on the add to panel menu in Classic Gnome .

---

