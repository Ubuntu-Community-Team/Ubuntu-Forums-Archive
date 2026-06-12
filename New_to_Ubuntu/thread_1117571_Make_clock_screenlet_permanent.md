---
title: "Make clock screenlet permanent"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by longtom on 2009-04-06
Hi,

I love the clock screenlet - gives the desktop some bling and even shows the time.

However - it doesn't appear to stay.  Sometime it just disaapears and it certainly isn't there anymore after a restart.

How can I permanently put my clock on my desktop so it will stay?

---

### Post by pastalavista on 2009-04-06
Open the Screenlet manager and select the clock... then click the box on the left-lower panel that says "auto-start on login"

---

### Post by longtom on 2009-04-06
That works great and is simple.  Now the clock is there on startup.  But somehow, during a days work, it just dissappears again without a trace.

I restart it - and again...etc.  When I reboot into Ubuntu I suddenly have 3 clocks....

Something I'm still doing wrong...

---

### Post by JohnLM_the_Ghost on 2009-04-06
Dunno about disappearing, but you can right-click and pick "Delete Screenlet..." on those surplus clocks. That will make them not to reappear after restarts.

Also you might want to make your clock show up on all workspaces.
You can do this right-clicking on clock and checking "Window->Sticky"

---

### Post by KhaaL on 2009-04-06
I also had this behaviour with screenlets, its a very annoying bug and honestly I never managed to get it working right.

---

### Post by LTFC2020 on 2009-04-06
ditto khall
seems to have a mind (?!) of its own

---

### Post by longtom on 2009-04-07
> **LTFC2020 said:**
> ditto khall
seems to have a mind (?!) of its own

As Sherlock Holmes of the lower class and can report the following findings:

If you minimize your windows with the horizontal stripe on the window itself, the clock stays.

If you use the "show desktop" option in the lower left corner of the desktop - clock disappears.

Is there a bug-report section for screenlets?

---

### Post by KhaaL on 2009-04-07
> **longtom said:**
> 
Is there a bug-report section for screenlets?

Just go on launchpad and report the bug there, in the project field choose screenlet. 

Welcome to the bugreporting world :KS

---

### Post by longtom on 2009-04-07
Well - I tried.  It appears I first have to do my degree in informatic.

It says cairo-clock is not covered by launchpad.  Ah well...

---

### Post by KhaaL on 2009-04-07
just for clarification, you're using cairo-clock and not a clock in screenlets? 

I went to macslows homepage and there was no bugtracker presented there, but I belive you can send bug reports here:

[https://bugs.launchpad.net/ubuntu/+source/cairo-clock](https://bugs.launchpad.net/ubuntu/+source/cairo-clock)

---

### Post by longtom on 2009-04-07
Well - I am ot sure anymore.  This is what it says:

> A screenlet version of MacSLows's cairo-clock with allarm function and different time zones...

I do open it from >Applications>Accessories>Screenlets.

Now you tell me...:p

---

### Post by KhaaL on 2009-04-07
ha, a challenge i see!

Type in a terminal:
aptitude show cairo-clock && aptitude show screenlets

And see the State: section of each package to make sure which is installed.

Otherwise, rightclick on the main menu, click edit menu, navigate to the mysterious clock and right click on it and choose properties, and paste the command field there :)

---

### Post by longtom on 2009-04-07
Alright - it is not cairo-clock....

---

### Post by longtom on 2009-04-07
Alright - got the original cairo clock - and guess what?  It has the same bug.

When you use the desktop shortcut it obliterates the clock somehow...

---

### Post by JohnLM_the_Ghost on 2009-04-07
> **longtom said:**
> If you use the "show desktop" option in the lower left corner of the desktop - clock disappears.

Hmm... I doubt it is a bug (at least this point).
As far as I know it is normal behaviour of (any) screenlets disappearing on pressing "show desktop" button.

They should reappear when "Show desktop" is pressed again.

However it doesn't mean you shouldn't report it if you feel like it... it will not be considered a bug, but as a wishlist (feature requests).

btw Do you use compositing window manager? (Compiz Desktop effects)
I know certain screenlets might behave (or look) abnormally when there is no compositing WM present.

---

### Post by longtom on 2009-04-07
> **JohnLM_the_Ghost said:**
> They should reappear when "Show desktop" is pressed again.


It does reappear - but so does the application from which you wanted to switch from...

Yeah - it is probably more an annoyance and not a bug.  Still would deserve some attention before it gets to 1.0....way to go.

---

