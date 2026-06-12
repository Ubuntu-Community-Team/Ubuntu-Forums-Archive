---
title: "Starting Gnome from command line"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by harisund on 2009-09-22
So I have renamed /etc/init.d/gdm to /etc/init.d/gdm.old 

When I boot, I am taken to a command prompt. I then do "startx" 

However, I notice that if I go to Gnome this way, (1) user-switch applet dies with an error. Ok cool, I understand that, I can't really switch users so it's fine, but (2) Sound doesn't work !

ps ax | grep ulseaudio  does give me a file running, but no sound playback at all whatosever. However, if I login through GDM login window it works. 

What am I missing?

---

### Post by wojox on 2009-09-22
What happens if you run:

```
/etc/init.d/gdm.old start
```

instead of startx? Do you get sound then?

---

### Post by harisund on 2009-09-22
That's pretty much the same thing as running GDM.
 
My question is how to run a Gnome session without GDM

---

### Post by wojox on 2009-09-22
Try this:

Create a file in your user directory called .xinitrc

Add:

```
exec gnome-session
```

That how I do it in Arch. Then do startx

---

