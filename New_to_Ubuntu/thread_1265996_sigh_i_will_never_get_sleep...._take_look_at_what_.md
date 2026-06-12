---
title: "sigh i will never get sleep.... take look at what happed"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-14
i was playing with things on my laptop and i make everything super big
and idk how to fix it.....

i cant go back in to the seting b/c i reset the comp ect ect.

---

### Post by nothingspecial on 2009-09-14
Stop messing around then.

What did you do?

---

### Post by I WILL DO IT on 2009-09-14
Everthing is super large.... i think i put it 720x400 but am not sher....

---

### Post by MelDJ on 2009-09-14
change the resolution back then. system-preferences-screen resolution

---

### Post by I WILL DO IT on 2009-09-14
thats the thing i cannt get to it b/c everthing is too big

---

### Post by nhasian on 2009-09-14
by any chance did you zoom in by using the Super button + mouse wheel?  try to zoom out.

---

### Post by lisati on 2009-09-14
I just had a play and had a similar problem. I went to System->Preferences->Display to set things back to a more sensible resolution. I had to drag the display properties up the screen to get the "apply" button visible to click on it. Logging off after doing so and then on again seems to have worked.

---

### Post by I WILL DO IT on 2009-09-14
i cannt drag it b/c the toolbar is stoping it

---

### Post by lisati on 2009-09-14
> **I WILL DO IT said:**
> i cannt drag it b/c the toolbar is stoping it

Does maximizing the window help?

---

### Post by sunchiqua on 2009-09-14
Hold down [COLOR=RoyalBlue]Alt[/COLOR] key and move your windows around so you could change your resolution.

---

### Post by ankspo71 on 2009-09-14
If you are using Ubuntu go to:

System > Preferences > Display to change your screensize.

Sorry, I'm not familiar with Kubuntu or Xubuntu.

A little Tip:

If you can't see something in a window that you need to see... Hold down the Alt key, and left click drag the windows around. You can even move the window up so you can see the bottom of the window. It works, but it doesn't always work for me. I think my PC is a little glitchy or something.

Hope this helps,
James

---

### Post by nothingspecial on 2009-09-14
It`s a little heavy handed but if you logout then log in to failsafe terminal or recovery mode or whatever it`s called nowadays and type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then ```
sudo shutdown -r now
```

Then you should be back to normal.

---

### Post by I WILL DO IT on 2009-09-14
there we go anuther problem solved. have a treat :popcorn:

---

### Post by The Cog on 2009-09-14
That doesn't work if you have special effects enabled - the window title bar bumps against the top taskbar so you can't move the window up any further. 

Try this:
Log out of the GUI, use Ctrl-Alt-F1 to get at text window, and log in there. Use the command
> mv ~/.config/gnome-session ~/.config/gnome-session-backup
then Ctrl-Alt-F7 to return to the GUI. Log in and see if it worked. If it did, you will have lost all your gnome settings, but that's not so hard to replace. If it didn't, then you might as well rename that directory back again:
> rm -rf ~/.config/gnome-session
mv ~/.config/gnome-session-backup ~/.config/gnome-session

---

