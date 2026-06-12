---
title: "deleted volume applet"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by mustard greens on 2009-11-12
I deleted my original volume applet from my top panel and there is no replacement in add to panel.

I was able to place a volume applet from system/preferences/volume control, but it doesn't have the same slider drop down.

does anyone know where to find the original volume applet with master volume drop down?

---

### Post by JugglinPhil on 2009-11-12
The Volume applet is in the notification area, so add to panel => Notification Area. :)

---

### Post by mustard greens on 2009-11-12
@ jugglinphil

there is no volume applet in add to panel

can you explain what you mean.

---

### Post by mustard greens on 2009-11-12
@ jugglinphil

I figured it ou.

the volume applet in within the notification area applet within the add to panel menu. 

thank you for the help.

---

### Post by JugglinPhil on 2009-11-12
You're welcome, I'm sorry if it wasn't quite clear.

---

### Post by ricardo.gloe on 2009-11-12
I did the same thing but I must be a bit dense. 

I understand what I have to do but can't seem to do it. I knoe the notification applet, but how do I add an applet to it?

---

### Post by mustard greens on 2009-11-12
I dont think you can add an applet to the notification area, but you can add the notification area if you have deleted it, and within the notification area is the volume applet and the network applet.  

I must say that I dont like them being joined at the hip like this and I will attempt to complain to someone at gnome about it.

---

### Post by JugglinPhil on 2009-11-13
> **mustard greens said:**
> I must say that I dont like them being joined at the hip like this and I will attempt to complain to someone at gnome about it.
Yeah but on the other side it would be rather annoying to manually move around all those applets one by one, with the notification area you've got them all in one.

---

### Post by singfoo on 2009-12-19
I have the same problem and can not be fixed by using the notification area. 
I upgraded to 9.10 from 9.04 and my panels stayed the same. I accidentally removed the volume applet.  Adding the notification area only gives an empty space in the panel. There are no volume or any applets but the notification area is there.  Meanwhile,the add to panel menu now no longer have the volume applet selection. The function is working in boot up since it still is checked in the system startup application menu BUT I can not use it. 
anyone know where are the applet files located? Thanks.

---

### Post by Popaul on 2009-12-21
The sound icon is linked to the gnome volume control applet, which may not start at boot.
Go to System / Preferences / Start-Up Applications : there're plenty of little things that can be ticked on or off to load at start-up. If the Volume Control is not ticked on, it will of course no show up in the notification area. Tick it on, and it should appear.
And.. check that in the 'option' tab the box is checked also for "automatically remember running applications ...".

---

### Post by peternickson on 2010-05-19
**NOT SOLVED:**  I've read all the messages in this thread and none solve the problem for me.  The volume applet is still missing.
[LIST][*] Notification area is on the panel, but it doesn't have the volume applet in it.
[*] Under System > Perferences > Startup Application Preferences, there is no volume applet under the additional startup programs list or the options tab.
[*] Under System > Preferences > Sound, there is no option to put a volume applet on the panel.
[/LIST]
Can anyone help?  If I knew where the applet files were then I could add it to the startup applications list.

---

### Post by JugglinPhil on 2010-05-19
It all depends on which version of Ubuntu you are using, in 10.04 the volume applet is inside the so called "Indicator applet". Again, right click on the panel, select "Add to Panel..." and type "Indicator Applet". Once you've chosen it click "Add" and that should be it. 
The panels don't have anything to do with your start-up applications as far as I know..

---

### Post by hiacynt on 2010-08-31
If I remember correctly the applet itself is a program called "indicator-sound". Obviously, it will show in the indicator applet only if it is installed.

---

### Post by corny on 2010-11-15
I also lost the volume control from indicator applet after having upgraded from 9.10 to 10.04.

Solution was to 
sudo apt-get remove --purge indicator-sound
remove the indicator applet from panel
sudo apt-get install indicator-sound
put back the indicator applet to panel

---

### Post by rungss on 2011-02-13
> **JugglinPhil said:**
> It all depends on which version of Ubuntu you are using, in 10.04 the volume applet is inside the so called "Indicator applet". Again, right click on the panel, select "Add to Panel..." and type "Indicator Applet". Once you've chosen it click "Add" and that should be it. 
The panels don't have anything to do with your start-up applications as far as I know..

Thanks, that worked for me.

---

### Post by inearlygaveup on 2011-02-13
Thanks JugglinPhil
It also worked for me.):P

---

### Post by TPM on 2011-02-13
To show volume control icon in notification area i use:

$ gnome-volume-control-applet

---

### Post by Sean Moran on 2011-02-17
> **TPM said:**
> To show volume control icon in notification area i use:

$ gnome-volume-control-applet

Thanks mate.  That was the magic command I was looking for.

---

