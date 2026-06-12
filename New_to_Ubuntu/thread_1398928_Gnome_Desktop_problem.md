---
title: "Gnome Desktop problem"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Black Sun on 2010-02-05
I have got a serious problem with Gnome that if I by mistake somehow change the desktop (for example by pressing alt+clt+{right arrow}), then my desktop goes blank and no matter what i do I am not able to get back the app bar at the bottom and all the programs I had had opened at that particular moment go missing, however I can see they all are running with the ps command...
What should I do?

---

### Post by nhasian on 2010-02-05
go to System->Preferences->Keyboard Shortcuts

scroll down to the bottom where it says "Switch to workspace on the right of the current workspace" and disable that shortcut.

---

### Post by whitethorn on 2010-02-05
Why don't you just switch back to the desktop you were using?  Just press ctrl alt left and continue using your applications.

---

### Post by Black Sun on 2010-02-05
as I said, I am not able to switch back with clt+alt+left, it shows me yet another blank desktop...

and I nhasian I can not access what u have pointed cause even the menu bar is missing...

---

### Post by saif_held on 2010-02-05
**ALt + F2** and type **gnome panel**...should work.

---

### Post by nhasian on 2010-02-06
i believe its:

```
gnome-panel
```

> **saif_held said:**
> **ALt + F2** and type **gnome panel**...should work.

---

### Post by mushwars on 2010-02-06
for a second I thought you said it killed X.
Look down on the right lower corner of your screen there is a little box with 4 smaller boxes in it. those are your virtual desktops, learn to love them and you will never want to go back.

Basically they show a picture of the running applications. I see a little firefox icon in this window, and a few boxes in some of my other ones for my terminals. 

You can click those boxes and it will take you to those virtual desktops.

The programs do not carry over but you can move them to the other workspace by rightclicking the title bar and saying move left or move to workspace.

---

### Post by Enigmapond on 2010-02-06
> **mushwars said:**
> for a second I thought you said it killed X.
Look down on the right lower corner of your screen there is a little box with 4 smaller boxes in it. those are your virtual desktops, learn to love them and you will never want to go back.

Basically they show a picture of the running applications. I see a little firefox icon in this window, and a few boxes in some of my other ones for my terminals. 

You can click those boxes and it will take you to those virtual desktops.

The programs do not carry over but you can move them to the other workspace by rightclicking the title bar and saying move left or move to workspace.

I couldn't do with out my many desktops. Also BTW you can just drag an application or browser all the way to one side of the screen and the cube will automatically turn..


Cheers!

---

### Post by mushwars on 2010-02-06
> **Enigmapond said:**
> I couldn't do with out my many desktops. Also BTW you can just drag an application or browser all the way to one side of the screen and the cube will automatically turn..


Cheers!
yep, compiz is so amazing, you can also set it up so if you move your mouse to the edge of the screen it will switch workspaces too.

---

### Post by Black Sun on 2010-02-09
> **mushwars said:**
> for a second I thought you said it killed X.
Look down on the right lower corner of your screen there is a little box with 4 smaller boxes in it. those are your virtual desktops, learn to love them and you will never want to go back.

Basically they show a picture of the running applications. I see a little firefox icon in this window, and a few boxes in some of my other ones for my terminals. 

You can click those boxes and it will take you to those virtual desktops.

The programs do not carry over but you can move them to the other workspac by rightclicking the title bar and saying move left or move to workspace.

mushwars, you didn't get it, I have been using ubuntu for more than a year now and I know what virtual desktops are, my problem is that, if by mistake I change my virtual desktop... all is gone , i.e, no titlebar, no menu bar , no icons , no nothing...
but I can access my terminal through it cause I have a keyboard shortcut defined for it, but I can not define keyboard shortcuts for each and every program and moreover the bigger problem is that I can not access the programs that were already running when the desktop changed...

---

### Post by mushwars on 2010-02-09
can you take a screenshot? 

hit the printscreen button then save it somewhere.

post a reply here with it as an attachment.

---

### Post by Black Sun on 2010-02-09
> **mushwars said:**
> can you take a screenshot? 

hit the printscreen button then save it somewhere.

post a reply here with it as an attachment.

mushwars, there is actually nothing to see, it is plain wallpaper only....
if I send you my wallpaper that would be like what can be seen on the screen, that's it...
It's plain blank...

---

### Post by mushwars on 2010-02-09
gnome-panel died/crashed or nautilus.

hit alt + f2
```
gnome-panel
```

```
nautilus
```

---

### Post by Black Sun on 2010-02-13
thanks buddy, I will check this solution the next time my gnome crashes...(wierdly it hasn't crashed for last 2 days...:D)

---

