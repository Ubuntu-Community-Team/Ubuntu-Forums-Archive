---
title: "Can't increase resolution!"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by rreznikoff on 2009-09-15
I have Intel Extreme Graphics with the correct driver installed. However, the best resolution I can get is 640 X 480. The monitor shows the display as VGA. What must I do to get back my previous high resolution and unlimited colors?

---

### Post by CatKiller on 2009-09-15
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by rreznikoff on 2009-09-15
I'm sorry, I must have erred in joining this forum. I'm not a developer and am totally lost in entering code. I am a non geek user and thought I could get a simple solution (if there is one) from some very knowledgeble people. Is it possible with your help to solve my problem with my limited knowledge?

---

### Post by bigboy7foru on 2009-09-15
as far as i can tell its the only way

---

### Post by Drone4four on 2009-09-15
rreznikoff: show the output for:```
xrandr
```

---

### Post by CatKiller on 2009-09-15
> **rreznikoff said:**
> I'm sorry, I must have erred in joining this forum.

Hardly. It's not like you're being asked to do brain surgery; you're only editing one text file.

Open up a Terminal (Applications &#8594; Accessories &#8594; Terminal)

Copy-and-paste the two commands, one after the other, into the Terminal window. The first command makes a backup of the file you're going to edit, and the second opens the file for editing.

Look for the block of text, and put in the HorizSync and VertRefresh lines, with the values from the documentation for your monitor. If you don't have the documentation for your monitor, post the details of your monitor here and hopefully someone can help you find the information that you need.

---

