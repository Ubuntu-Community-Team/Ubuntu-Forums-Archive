---
title: "Where can I find the icons????"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by bytescribe on 2010-06-29
I have an interesting problem that I'm hoping someone can help me with.

My bf was over at my place helping me get my ethernet cable installed and working while I was at work. He added what I think was a separator line next to the default icons for volume control and internet connections. I don't like to use such a line, so I attempted to delete it, but what I actually ended up deleting were those default icons.

I want them back on my panel but the only icons for sound (change sound volume and sound events) and internet (network manager) I found were in the applications list for adding things to the launcher panel. Is there anywhere in the dropdown menus or online I can go to add these default icons, or am I going to have to completely reinstall ubuntu just to get those icons back on the panel?

Secondly, I would love to know why those oh-so-helpful icons are NOT in the applications pop-up window (among the ones for dictionary, terminal, etc). It would seem logical that they'd be there in case someone--like yours truly-- accidentally deletes them from the main launcher task bar.

---

### Post by xpod on 2010-06-29
> **bytescribe said:**
> I have an interesting problem that I'm hoping someone can help me with.

My bf was over at my place helping me get my ethernet cable installed and working while I was at work. He added what I think was a separator line next to the default icons for volume control and internet connections. I don't like to use such a line, so I attempted to delete it, but what I actually ended up deleting were those default icons.

I want them back on my panel but the only icons for sound (change sound volume and sound events) and internet (network manager) I found were in the applications list for adding things to the launcher panel. Is there anywhere in the dropdown menus or online I can go to add these default icons, or am I going to have to completely reinstall ubuntu just to get those icons back on the panel?

Secondly, I would love to know why those oh-so-helpful icons are NOT in the applications pop-up window (among the ones for dictionary, terminal, etc). It would seem logical that they'd be there in case someone--like yours truly-- accidentally deletes them from the main launcher task bar.

If i understand you correctly you need to replace your indicator applet(for volume etc) and notification area(for network etc). You can do this by right clicking on your panel and choosing "add to panel". Then just add the applets i`ve mentioned above.

---

### Post by bytescribe on 2010-06-30
Hi xpod...

Hmmm...maybe I didn't make myself clear enough...

What I want are the default icons for:

1)Showing that the internet is connected. (the network manager icon that I found in the applications list is different-looking and does not directly disable or enable an internet connection such as Auto-ethO, which I have. )

2)Adjusting just the sound volume, not the sound event volume. (Again, the icon that I found is different-looking.)

I tried looking in the applications list before I went to work today and after you suggested to do so.

I was actually hoping there was some sort of "icon repository" where all the system default icons are kept so they could be put on this applications list, if the user so chose.

I hate to have to completely reinstall just to get the default icons back on the system tray, but if I must, I must...*sighs*...

---

### Post by Elfy on 2010-06-30
You don't need to add icons - you need to add the applet you deleted from the panel.

That is indicator-applet now - did you try to add it back as xpod suggested and it not work?

---

### Post by BugBuster on 2010-06-30
Run this in the terminal;
```

rm -r ~/.gconf/apps/panel

```
Then logout and login again. This will restore the default icons and panels that ship with ubuntu.

---

### Post by bytescribe on 2010-06-30
Hehe...I talked with my bf on Skype and he cleared things up for me...

I kinda feel silly and stupid right now, but at least I know it's called "notification area" in the app launcher list instead of "default icons." ;P

So this thread can be considered "SOLVED."

---

