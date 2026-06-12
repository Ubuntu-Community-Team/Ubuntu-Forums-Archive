---
title: "The Window list applet does not work properly when I try to minimize or restore a app"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-29
The Window list applet does not work properly.

sometimes (very random) I can not click on some of the running applications (open windows) icons in the list to minimize or restore them. a minute later it works fine with those window and stops responding for other window.

It is like that for example firefox item in the Window List does not receive the mouse click because it does not show any indication that it is pressed.

Thanks

---

### Post by cmavr8 on 2009-11-01
Any update on this?
I experience the exact same problem. It happened when I upgraded from 9.04 to 9.10...

Tried removing the panel and building it again, but it has no effect.
It is so annoying. Any help?

---

### Post by pauliephonic on 2009-11-01
I have the same problem after upgrading from 9.04 as well.

Before the upgrade the normal behaviour was that I could click the button in the window list of a running program and the application would minimise and restore. Now it sporadically ignores the click and does nothing. If I click on the window itself to focus it (bring it to the foreground) the window list seems to start working again.

I can hover over the button and use the mouse wheel to cycle the windows as a workaround, but it definitely looks like a bug.

---

### Post by legolas_w on 2009-11-03
> **pauliephonic said:**
> I have the same problem after upgrading from 9.04 as well.

Before the upgrade the normal behaviour was that I could click the button in the window list of a running program and the application would minimise and restore. Now it sporadically ignores the click and does nothing. If I click on the window itself to focus it (bring it to the foreground) the window list seems to start working again.

I can hover over the button and use the mouse wheel to cycle the windows as a workaround, but it definitely looks like a bug.

If you happened to find a solution, please share it with me.

Thanks

---

### Post by cmavr8 on 2009-11-04
I am experiencing many many problems after "up"grading to 9.10, and one of these is this one.

Fortunately it was fixed by itself or an update... 
Can't help you more... Update and restart until it's fixed,lol.

---

### Post by pauliephonic on 2009-11-04
It has actually gotten worse for me.

The inability to register mouse clicks, seems to have also spread beyond the window list applet, to standard buttons in applications.

Some buttons is dialogs popped up by applications are unable to be clicked. At the same time I can click on links in web pages, drag window title bars etc., without issue. 

I can also use keyboard accelerators (e.g. Alt-F) to trigger the un-clickable dialog buttons, which proves that the issue isn't one of an unresponsive program, the GUI simply doesn't send the mouse clicks to the underlying program.

I have also run all updates without fixing the issue.

Sad Days! 

Mr P

---

### Post by cmavr8 on 2009-11-04
Do you happen to have desktop effects turned on?

---

### Post by pauliephonic on 2009-11-04
> **cmavr8 said:**
> Do you happen to have desktop effects turned on?

No, my ati card doesn't support them. 

Mr P

---

### Post by ThorKier on 2009-11-05
A work around for the time being is to click on the desktop background and then click on the application that you would like to take focus. This will normally allow the application to take focus. The problem started with the 9.10 upgrade. 

Ubuntu: 9.10
Ram: 8gb
System: Dell Optiplex 745

---

### Post by julianjm on 2009-11-06
Same problem here just after upgrading to Karmic.

Sometimes the buttons on the window list don't respond to clicks. 

Julian.

---

### Post by DasBrot on 2009-11-08
I have the exact same problem. It is **really** quite frustrating.

I found this bug on launchpad, with some effort... For some reason, I could not find it there directly, but only by following a link from the archives on [www.mail-archive.com](www.mail-archive.com). Anyway, here's the link to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/470604]("https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/470604")

I am having this problem on a freshly installed system, not an upgraded one.

The launchpad report suggests a **[COLOR="DarkGreen"]workaround[/COLOR]**: Turning on desktop effects is supposed to help!

Unfortunately this is not an option for me on my ATI Radeon HD4200. If I did my research correctly, the problem there is that the karmic kernel 2.6.31 does not support DRI with fglrx. The open source driver, on the other hand does not support 3D on the newer chips like the HD4200 yet :( .
Aside from these two issues, Karmic is awesome :D .

---

### Post by Grone1985 on 2009-12-09
As DasBrot pointed out your problem seems to be related to that bug but the workaround they suggest on one of those posts is to run this command:

$ GDK_NATIVE_WINDOWS=1 gnome-panel --replace

It works as long as you keep the terminal opened.

---

### Post by mkro on 2010-01-03
Thank you, Grone, that worked. 

Frustrating bug, though. This, the Flash problems and the "Nautilus can't load some directories after moving files into them" issue, makes me regret updating from 8.10.

---

### Post by Grone1985 on 2010-01-06
I've had this issue for a while and even though we have a workaround I am tired of typing this every time I log in. I have this idea but I'd rather get some advice here first, if I load this command:

$ GDK_NATIVE_WINDOWS=1 gnome-panel --replace

on the startup applications menu, can it cause any problems? I don't want to mess anything up ;)

Any advice is appreciated!

---

