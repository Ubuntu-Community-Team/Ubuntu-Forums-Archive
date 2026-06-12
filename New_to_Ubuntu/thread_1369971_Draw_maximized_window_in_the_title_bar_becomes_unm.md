---
title: "Draw maximized window in the title bar becomes unmaximized, how to disable?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by ehalls on 2010-01-01
Hi,

When I draw a maximized window on the title bar, it becomes unmaximized. Where are the settings for disable that function, or decide how long it can be drawn until it unmaximizes?

Cheers

---

### Post by gsmanners on 2010-01-01
Beg pardon? "Draw"?

---

### Post by ehalls on 2010-01-02
> **gsmanners said:**
> Beg pardon? "Draw"?

If you click and hold the mouse button on the title bar then move the mouse while holding the button pressed, the window becomes unmaximized.

---

### Post by warfacegod on 2010-01-02
I'm taking a complete shot in the dark here.

System> Preferences> Mouse> Accessibility tab: Check to see if Simulated Secondary Click is enabled. Unless you need or use it, uncheck it.

If you do use it then you'll have to change the behavior itself.

System> Preferences> Windows> Title Bar action: Try setting this to none.

---

### Post by ehalls on 2010-01-02
> **warfacegod said:**
> I'm taking a complete shot in the dark here.

System> Preferences> Mouse> Accessibility tab: Check to see if Simulated Secondary Click is enabled. Unless you need or use it, uncheck it.

If you do use it then you'll have to change the behavior itself.

System> Preferences> Windows> Title Bar action: Try setting this to none.

Nope, that didn't make it... there's got to be some setting somewhere :S

---

### Post by warfacegod on 2010-01-02
I usually use Ubuntu Tweak for settings like that so I don't know where to tell you to look. If you are using compiz, it could easily be in there.

---

### Post by Houbos on 2010-01-02
Download Compiz Composition Manager settings by sudo *apt-get install compizconfig-settings-manager* and then go to System/Preferences/CompizConfig..., then find *Move Window* and uncheck **Snapoff maximized windows**. Voilá, window stays maximized.

---

### Post by ehalls on 2010-01-02
> **Houbos said:**
> Download Compiz Composition Manager settings by sudo *apt-get install compizconfig-settings-manager* and then go to System/Preferences/CompizConfig..., then find *Move Window* and uncheck **Snapoff maximized windows**. Voilá, window stays maximized.

Wow! Thanks. not easy to find :S

---

### Post by warfacegod on 2010-01-02
If you haven't used Compiz much or at all, I suggest using Synaptic to install simple-ccsm, it's a good way to get familiar with the basics.

---

### Post by Houbos on 2010-01-02
I'm not sure if it's included in [I]simple-ccsm. Can't find it throught Configuration Manager.

[/I]Simply press *ALT+F2*, type *ccsm* and then search for *Move Window*. Really, not easy. Inspired by Windows Vista/7 Control Panel. :-)

---

### Post by Cuco3 on 2010-01-02
Does anyone know how to make it so that when you drag a window to the top, it maximizes?

---

### Post by warfacegod on 2010-01-02
> I'm not sure if it's included in simple-ccsm. Can't find it throught Configuration Manager.

I suggested it in case Houbos wanted an idea of what Compiz can do. I was totally overwhelmed when I first saw ccsm, simple-ccsm gave me a way to make changes without fear of making my GUI unusable.

Does anyone know how to make it so that when you drag a window to the top, it maximizes?

I think I know what you mean but please clarify for us.

---

### Post by Cuco3 on 2010-01-02
> **warfacegod said:**
> 
> Does anyone know how to make it so that when you drag a window to the top, it maximizes?I think I know what you mean but please clarify for us.I have an un-maximized window. I want it so that, when I drag that windows to the top of the screen, it will maximize. Like in Windows 7.

I know you can drag a maximized window away and it will unmaximize - and if you're still dragging that window - it will maximize again if you drag it to the top. But I want it like in Windows 7 where it will maximize if you drag an un-maximized window to the top of the screen.

---

### Post by Houbos on 2010-01-03
This function is caller *Aero-snap* on Windows 7. On Mac, there is Cinch. [http://www.irradiatedsoftware.com/cinch/](http://www.irradiatedsoftware.com/cinch/)). Very addictive feature, indeed.

Sorry, nothing useful for Gnome (desktop manager used in Ubuntu). You can try [http://lifehacker.com/5402090/emulate-windows-7s-aero-snap-sizing-in-linux](http://lifehacker.com/5402090/emulate-windows-7s-aero-snap-sizing-in-linux), but it's useles, test and you'll see.

---

### Post by Houbos on 2010-01-03
I almost forgot, try click the *the Maximize window* button with *right mouse button* and *middle mouse button*.  ;-) With window-snapping (default settings), it's kind of substitute. It simply maximizes window horizontally and vertically. Btw: also try scroll up on the windows title. Compiz required.

---

### Post by Cuco3 on 2010-01-03
> **Houbos said:**
> I almost forgot, try click the *the Maximize window* button with *right mouse button* and *middle mouse button*.  ;-) With window-snapping (default settings), it's kind of substitute. It simply maximizes window horizontally and vertically. Btw: also try scroll up on the windows title. Compiz required.It's not what I was lookin for but thanks for the tip anyways I like those features :)

---

