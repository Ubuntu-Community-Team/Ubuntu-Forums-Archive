---
title: "Desktop is missing - please help!"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Stovey on 2009-12-29
There are no icons on my desktop whatsoever, and right clicking on the desktop does nothing.  It doesn't seem to exist!  How do I make my desktop appear?

I installed Ubuntu Netbook Remix on my Acer AspireOne AOA150.  So far so good!  But the UNR seemed a little restricted, so I followed advice on this forum and deselected UNR desktop from startup applications.   Ahhh, much better. 

And then I installed Ubuntu-Desktop.  It appears in the synaptic program manager, but it does not appear in start-up applications.  

Would someone kindly help get my desktop working?

PS - this is my first day on LINUX ever.

---

### Post by stlsaint on 2009-12-29
do you see applications and places and system in your top left of screen?

---

### Post by tom.swartz07 on 2009-12-29
> **Stovey said:**
> There are no icons on my desktop whatsoever, and right clicking on the desktop does nothing.  It doesn't seem to exist!  How do I make my desktop appear?

I installed Ubuntu Netbook Remix on my Acer AspireOne AOA150.  So far so good!  But the UNR seemed a little restricted, so I followed advice on this forum and deselected UNR desktop from startup applications.   Ahhh, much better. 

And then I installed Ubuntu-Desktop.  It appears in the synaptic program manager, but it does not appear in start-up applications.  

Would someone kindly help get my desktop working?

PS - this is my first day on LINUX ever.

Log back out, and when it asks for your name and password, look at the bottom for a selector that says 'session' See if there's an option to set it to Gnome or Gnome-desktop.

You could always re-start the netbook launcher by hitting alt + F2 and typing ```
netbook-launcher
``` (it should autocomplete)

---

### Post by Mikaela1121 on 2009-12-29
Thanks for the info. I also got the same problem. I'll try your suggestion.

[]("http://www.beautyandhealthcare.org/anti-aging-wrinkle-cream/buy-dermajuv-at-up-to-50-percent-savings")

---

### Post by Stovey on 2009-12-29
> **stlsaint said:**
> do you see applications and places and system in your top left of screen?

No.  If I click on the Ubuntu icon on the top left, system and places show up on the list, but applications do not.  My screen looks like this:

[IMG]http://i128.photobucket.com/albums/p195/BassBucket/th_NoDesktop.png[/IMG]

[quote=tom.swartz07]Log back out, and when it asks for your name and password, look at the bottom for a selector that says 'session' See if there's an option to set it to Gnome or Gnome-desktop.[/quote]

OK, I logged out, and the session is set to Gnome.  There is no option for Gnome desktop.  But it gets worse: I could not log back in because I got this error:

"error initiating conversation with authentification system - general failure"

[quote=tom.swartz07]You could always re-start the netbook launcher by hitting alt + F2 and typing...[/quote] 

But I don't like the Netbook Remix environment  - it seems childish and restrictive.

Many thanks for your quick response!  What now?

---

### Post by tom.swartz07 on 2009-12-29
> **Stovey said:**
> No.  If I click on the Ubuntu icon on the top left, system and places show up on the list, but applications do not.  My screen looks like this:

[IMG]http://i128.photobucket.com/albums/p195/BassBucket/th_NoDesktop.png[/IMG]



OK, I logged out, and the session is set to Gnome.  There is no option for Gnome desktop.  But it gets worse: I could not log back in because I got this error:

"error initiating conversation with authentification system - general failure"

 

But I don't like the Netbook Remix environment  - it seems childish and restrictive.

Many thanks for your quick response!  What now?

Lets verify that you have the actual Ubuntu-desktop package installed.
Open synaptic and search for ubuntu-desktop. If its already ticked as installed, click it and select re-install. 

It seems that you have the panel installed, so you could add the application menu by right clicking on the panel and selecting 'add to panel' and clicking 'main menu'

you could also add notification applet, I cant see from your image if you have it or not. This holds your wifi, clock, volume, etc. all in one place.


You could also refer to this thread: [http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792) for some extra tweaks if you prefer.

---

### Post by Stovey on 2009-12-30
> **tom.swartz07 said:**
> ..You could also refer to this thread: [http://ubuntuforums.org/showthread.php?t=1308792](http://ubuntuforums.org/showthread.php?t=1308792) for some extra tweaks if you prefer.

OK, that did it!  I had to mark show desktop in Nautilus.  Many thanks Tom.

In hindsight I should have installed the basic 9.10. Regardless I am thrilled to have Linux up and running without major issues.  Thanks again!

---

