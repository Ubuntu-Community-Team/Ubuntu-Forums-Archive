---
title: "Program doesn't remember window positions"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by The Bright Side on 2010-03-08
I am using the wiki-style notes and calendar application "Zim". Whenever I start it or bring it back up from the tray icon, the window appears stuck to the top left of the screen instead of centered, where I dragged it before.

How can I get Ubuntu to remember its window position?

---

### Post by FrankT-Qc on 2010-03-08
Window position is a handled differently by different programs... 

Some programmers will explicitly save / restore this position. Sometimes they screw up and a bug report is your best bet but read on, there are "workarounds" for bad programming.

Most of the time, window placement is handled by your window manager and there, you have a little more power.

If you use compiz or you want to give it a try (I personnally would not live without compiz), here's what you could do :

[LIST=1]
[*]Go to Applications->Ubuntu Software Center
[*]In the search box, write "compiz" (no quotes)
[*]Install "Advanced Destop Effects Settings(ccsm)" (there are other setting managers, this is the one I prefer...)
[*]After installation, go to System->Preferences->CompizConfig Settings Manager
[*]You'll see a huge list of tweaks and settings : You definitely want to poke around; some effects are amazing
[*]Somewhere toward the end, there's one called "Place Windows", this is where you can tune the way windows are placed on your desktop. Make sure it is checked (activated)
[*]Click on this icon and look at the settings. Mouse hovering should get you enough tooltips to find your way around.
[*]Notice that there are two tabs to this setting section, one for "global" settings and one for specific windows (like, let's say, Zim...) if some windows behave weird.
[/LIST]

Of course, from this point, the magic word is "compiz" in your googling journey... Be carefull, if you dig too much into compiz, you'll never be able to live without it again...

Have fun,
Frank

---

### Post by tgalati4 on 2010-03-08
zim --doc

---

### Post by The Bright Side on 2010-03-09
The last one doesn't do it:

> /usr/bin/zim: option --doc not recognized

I'll tinker with compiz (using it, yeah^^) now though. Thanks!

---

### Post by The Bright Side on 2010-03-09
I tried several settings with the Compiz manager, but couldn't get it to work. I didn't really get what I was doing either :-(

Thanks for the suggestion though!

---

### Post by dullard on 2010-03-09
As an example, in my Compiz "Place Windows" settings:

In the Fixed Window Placement tab, I have title=Thunar 100  150. This opens Thunar with the top left corner at 100,150 (x.y) pixels.

So... first open the program you wish to specifically position onscreen, check System Monitor to see how the program is named when it is running (**case sensitive**). Note: Thunar's window title says File Manager but we use Thunar as its name.

Then click "New" in Compiz and enter **title=program name** and adjust the x/y values accordingly.  Be sure to leave no spaces either side of the "=" symbol.

And, as mentioned, make sure the "Enable Place Windows" checkbox over to the left is activated.

---

### Post by The Bright Side on 2010-03-09
Thanks for the in-depth description! It makes perfect sense, but it doesn't work. The window appears in the top left corner of my screen unchanged :-(

---

### Post by tgalati4 on 2010-03-09
zim --doc should bring up a manual/help page in zim.  I'm running this in a terminal in Jaunty.  There may be a gtk style variable that you can put in a configuration file to place it where you want it.

You can also install devilspie

sudo apt-get install devilspie
man devilspie

---

### Post by kaibob on 2010-03-09
I don't use zim, but I looked up the man page and it shows a geometry option, which allows you to set the location, height, and width of the main window. If nothing else works, you may want to give this a try.

[http://manpages.ubuntu.com/manpages/jaunty/man1/zim.1p.html](http://manpages.ubuntu.com/manpages/jaunty/man1/zim.1p.html)

---

