---
title: "Two more little problem with ubuntu"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sevic33 on 2009-08-17
Im using ubuntu for a couple months and im prity satisfied.
But i have a two little problems who anoying me sometimes so i will ask ,maybe someone can help.
1.When i watch online streams like youtube its all go well till i dont switch to full screen,then pictures starts freezinf every 20 secend for a 3 secend then continue and again and again same.
2.When im watching video with Movie Player or a MPlayer i turn sound to maximum,but its not so loud like when i boot to windows.I was check the Volume control and its all set to the maximum,but it still not loud even close like on windows.

Ubuntu is on a laptop so if i need to post some hardware specification let me know guys.
tnx.

---

### Post by northern lights on 2009-08-17
> **sevic33 said:**
> 1.When i watch online streams like youtube its all go well till i dont switch to full screen,then pictures starts freezinf every 20 secend for a 3 secend then continue and again and again same.
Please post the output of ```
aptitude search flashplugin && aptitude search totem-mozilla && aptitude search mozilla-mplayer
```

> **sevic33 said:**
> 2.When im watching video with Movie Player or a MPlayer i turn sound to maximum,but its not so loud like when i boot to windows.I was check the Volume control and its all set to the maximum,but it still not loud even close like on windows.Your last shot is checking ```
alsamixer
``` whether all channels are turned up. However, this might be something you have to live with. My new laptop's never seen Windows, so I can't say how it'd behave. But my old one (2005) used to be louder under Windows as well.

I resorted to external speakers and headphones. Further, vlc is helpful as it's own volume control let's you play files considerably louder than any other player.

---

### Post by sevic33 on 2009-08-17
this is the output:

```
i   adobe-flashplugin               - Adobe Flash Player plugin version 10      
p   flashplugin-installer           - Adobe Flash Player plugin installer       
p   flashplugin-nonfree             - Adobe Flash Player plugin installer (trans
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
i   totem-mozilla                   - Totem Mozilla plugin                      
p   mozilla-mplayer                 - MPlayer-Plugin for Mozilla   
```

About sound:

-i try alsamixer,its all set to 100 %
-i will definitly try VLC
-there is also equalizer in MPlayer ,its hase 10 diferent frequency for boosting,so if i boost them all i got louder sound but not so clear,its require a little tuning.Bad part is equalizer reset after exit so its not realy practical to tune it every time when i wana watch movie or something.

---

### Post by northern lights on 2009-08-17
Run```
sudo apt-get install flashplugin-nonfree mozilla-mplayer
```Since 10 is installed, *flashplugin-nonfree* is optional. *mozilla-mplayer* is the crucial package.

In VLC, do not use the equalizer instead just out the volume all the way up (Ctrl+ArrowUp).

---

### Post by kansasnoob on 2009-08-17
Regarding the sound try installing 'gnome-alsamixer' either from Synaptic or run the command:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. Especially pay attention to the VIA controls:

[ATTACH]125294[/ATTACH]

---

### Post by sevic33 on 2009-08-18
-i install alsa mixer and i dont have half of stuff like in your picture,i check the options and there is nothing to turn on,maybe i miss some drivers or my audio card is not so quality.
-i still have same problem when watching fulscreen youtube
-VLC help me to get louder sound when watching movies,tnx :)

---

