---
title: "Can't Access Shutdown Button in Lucid"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by mrphud on 2010-08-03
Hello,

I am having an issue with shutting down Lucid through the GUI. The problem is the button is missing. Instead the name button that normally sits next to it is messed up and covers the shutdown icon. See the attached image to see what I mean.

I like the current configuration and don't what to change icon location if I can help it.

Does anyone have any ideas?

Thanks
mrphud

---

### Post by Gone fishing on 2010-08-03
Mine does that on occasion – annoying. 

I just added a shutdown applet to the top panel

---

### Post by mcduck on 2010-08-03
For a quick fix hit Alt-F2 and run "killall gnome-panel". That will restart the panel which will probably get the applets to draw correctly again.

---

### Post by mrphud on 2010-08-03
Hey the restart worked. Is there a more permanent solution? Or is this just a glitch?

---

### Post by mcduck on 2010-08-03
> **mrphud said:**
> Alt-F2 causes the run application in terminal box to show up. Not the redraw command.

you have to type the command into the box and press enter. :)

---

### Post by windfix on 2010-08-14
> **mrphud said:**
> Hey the restart worked. Is there a more permanent solution? Or is this just a glitch?

I've seen this occur on several machines, and for whatever reason - increasing the vertical size of the panel seems to fix it.  Right-click on the panel, go to Properties, and increase the size by a few pixels (I keep mine at 32 to 36)

---

### Post by viking350 on 2010-08-14
So button on the top panel is gone it should be there at the top panel and then you just click on it and hit shut down.:D

---

### Post by enochpc on 2010-08-31
I tried both fixes and no dice.  I added the shutdown button using the add under the right click menu, but it's bright red, doesn't look near as nice as the old one did.  It's not a big deal but I would like to have the old one back.  It disappeared when I was messing with the Facebook, Twitter, envelope button (I don't remember what it's actually called).

THanks in advance.

---

### Post by RedRat on 2010-08-31
I have this problem occasionally on my 10.04 System76 laptop. I use the Cairo dock at the bottom and it has the shutdown app that is very similar to that in the panel. I like the placement of the shutdown-logout app in 8.04 which is in the middle of the panel, at least on my machine. I think that shutdown app in 10.04 just runs out of real estate.

---

### Post by ds_shellback on 2010-09-18
I've been having this problem on lucid ever since I upgraded - periodically, for no apparent reason you get two "Me Menu"s and no "Shutdown" menu and next time I boot it's fine. (Annoying - Kept hoping one of the updates would make it go away).

Then I came across this thread and post #6
> Originally posted by **Windfix**
*I've seen this occur on several machines, and for whatever reason - increasing the vertical size of the panel seems to fix it. Right-click on the panel, go to Properties, and increase the size by a few pixels (I keep mine at 32 to 36)*

So tried that and hey, as you resize the panel, the "Shutdown" menu magically reappears - fantastic!

Question is though - why does it do that, this was a clean installation (I didn't fiddle with the panel height before) - is this just some obscure redraw Bug?

---

### Post by shuamu on 2010-09-18
That's definitely a panel bug that happens from time to time. A restart always fixes it.

As for shutting down, you've always got lots of options.

Ctrl+alt+delete brings up a dialogue box to shut down...

Or you can always use the command line in Terminal. Just type "reboot"

---

