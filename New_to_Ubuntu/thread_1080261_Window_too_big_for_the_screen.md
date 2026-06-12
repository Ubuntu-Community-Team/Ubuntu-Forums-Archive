---
title: "Window too big for the screen"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-25
What do you do when you have a window that is to long to fit in the display and the action buttons (such as Cancel, Apply, OK etc) are below the bottom of the screen ?

In Windows, a scrollbar normally opens along the right side of the window to allow you to scroll down to the bottom but on 8.10 (at least in this window) there is no scrollbar and I cannot resize, drag or manipulate the window so that I can get to the "action" buttons at the bottom.

Is there a workaround?

Page Dn does not work, Shif pg dn does not work and so forth.

resolution is set to 1280 x 1024 (max available)

Off the cuff it seems like a ubuntu bug.

thx

---

### Post by ktemkin on 2009-02-25
This isn't a Ubuntu bug, but rather a mismatch between the size of your application and the size of your screen. If you press ALT+F7, it'll allow you to 'grab' your window and move it about the screen, allowing you to hopefully access the buttons.

As with Windows, it is up to the application designer to decide how the program will interface with a screen that's too small for it. Many programs, especially those that work with documents or web pages, utilize scroll bars; you'll find that Ubuntu (technically GNOME/GTK+) includes the ability for developers to use these as well.

What application are you using?

---

### Post by mistypotato on 2009-02-25
GOOD JOB Ktemkin  :KS

That worked  


thx ):P



ps...it's a drop tables screen in MySQL

---

### Post by stim on 2009-02-25
Also if you hold ALT and click on the window it will allow you to drag it until you can find an edge to resize with.

---

### Post by mistypotato on 2009-02-25
hi stim,

I tried that and it didn't work :(

---

### Post by stim on 2009-02-25
O rly? It works for me and the three other guys here at work that are running ubuntu..... Sorry for the incorrect tip then!

---

### Post by mistypotato on 2009-02-25
could just be my system since Im also having trouble with ipblock right now

---

### Post by jaminux on 2009-02-25
> **mistypotato said:**
> could just be my system since Im also having trouble with ipblock right now

Think it is. I can confirm a fourth case of it working.

---

### Post by mcduck on 2009-02-25
Alt-left mouse button allows moving windows from any point in the window, and Alt+middle mouse button allows resizing window from any point.

These are standard features on most Unix/Linux window managers.

If they don't work for you, the problem is definitely on your system.

---

### Post by mistypotato on 2009-02-25
ok,

now, how do I go about finding out what causes these abnormal things to happen 

):P

---

### Post by derway on 2009-02-25
Actually, in ubuntu 8.10, it seems the default for grabbing the screen is ctrl left-click!!!

You go into preferances=>windows menu, and you can change it to alt-click.

This drove me crazy, as I always use ctrl-left clock to open a link in a new tab, in firefox.  I thought they disabled it in the linux version.

But no, it was the screen grabbing setting!!  Thank goodness.

---

### Post by Therion on 2009-02-25
If you're running Compiz...

Open CCSM.
Scroll down to the Utilities section.
Open the "Workarounds" plugin.
UN-tic the check-box for **Legacy Fullscreen Support**.

---

### Post by mcduck on 2009-02-26
> **Therion said:**
> If you're running Compiz...

Open CCSM.
Scroll down to the Utilities section.
Open the "Workarounds" plugin.
UN-tic the check-box for **Legacy Fullscreen Support**.

That is not related to this kind of problems, and thus won't help. ;)

The app is not running in full-screen mode, the window is simply bigger than display resolution.

---

### Post by zerena on 2009-02-28
I think I'm having the same problem. The firefox window that I'm working in now doesn't allow me to resize it. The little resizey thingy in the bottom right hand corner is showing, but not doing anything when I try to click and drag it. At the top, the menus are at the very top of my screen, and the little minimize/resize/close icons are not there. Neither ctrl+f7 nor alt+f7 allow me to do anything about it. None of these problems exist in any of the other applications that I'm using. I also have a program that has a little chooser thing down at the bottom of my screen, kind of like a mac. That usually shows up on top of the active window if I move my mouse to the bottom of the screen. That's not showing up either. The only way to see my desktop again is to close exit firefox. That's a real pain.

Any ideas?

---

### Post by ugm6hr on 2009-02-28
zerena:
Sounds like you have maximised your Firefox (different issue than OP), and perhaps put it into fullscreen mode.

Try pressing F11 to get out of it.

Other wise, post a screenshot of what you're talking about.

---

### Post by zerena on 2009-03-02
> **ugm6hr said:**
> zerena:
Sounds like you have maximised your Firefox (different issue than OP), and perhaps put it into fullscreen mode.

Try pressing F11 to get out of it.

Other wise, post a screenshot of what you're talking about.



You are so right!!! I fell asleep with my laptop on in bed, and my cats walked all over the keyboard. 

Thanks!!!

---

### Post by howlingmadhowie on 2009-03-02
> **zerena said:**
> You are so right!!! I fell asleep with my laptop on in bed, and my cats walked all over the keyboard. 

Thanks!!!

:lolflag: :)

---

### Post by mistypotato on 2009-03-03
> **zerena said:**
> You are so right!!! I fell asleep with my laptop on in bed, and my cats walked all over the keyboard.

Yeah, my cats do that too.

Did you notice what site they last visited ?  Maybe you need to block those sites if they're not litter oriented.

---

