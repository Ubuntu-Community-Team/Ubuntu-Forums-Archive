---
title: "Maxmizing Screen Space"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2010-01-12
I installed Ubuntu a few months ago and I love it.  I love the security, the lack of restrictions, the Free software philosophy; almost everything. 

One of the few things I didn't love is the way the top and bottom panels took up more space than in Windows. 

So I searched for ways around it.  I found some great addons to maximize the screenspace and functionality of firefox.  Here are a few. 

1. The Menu Bar
When it comes to dealing with the menu bar, many screen-conservatives opt for an addon that integrates the entire bar into a single dropdown menu. Personally, I've always found dropdown menus to be extremely annoying, especially if you're using a tablet mouse.  One wrong move and the menu dissappears.  So I wanted to avoid them.  I found a different addon, "[Hide Menubar]("https://addons.mozilla.org/en-US/firefox/addon/4762?collection_uuid=3db07423-7119-f8ef-f40e-6a6bd57ee6c9")", that hides the menu bar simply by pressing a button. That's a good solution, but I think we can do better.  The [Personal Menu]("https://addons.mozilla.org/en-US/firefox/addon/3895") addon turns all of the Menu Bar's menus into icons in the address bar.  Although it sacrifices some space in the location bar, it's worth it to me for the screen space that is saved. 
2. The Title Bar
The Title Bar has always struck me as one of the most useless parts of a window.  All it's really good for is moving and resizing/closing the window. Since the tabs display the title, there's really no need for it.  I found several addons to hide or remove the title bar, but my favorite is one that mimics google chrome by putting the tabs up at the top: [Chromin Frame. ]("https://addons.mozilla.org/en-US/firefox/addon/10091")

There are also addons to autohide the status bar, the address bar... you name it.  For those of you who are anal about screen space, thought I'd just lend a hand.

---

### Post by k64 on 2010-01-12
Here's another way to maximize screen space:

```
[root@$HOSTNAME:~]# sudo apt-get install gnome-shell
```

After this, you would have to set GNOME Shell as a startup application. To do this:

System > Preferences > Startup Applications, click "New Startup Application" and type, in the Name box, GNOME Shell, and in the Command box:

```
/usr/bin/gnome-shell --replace
```

Now you can reboot and see the real changes!

---

### Post by The_Pirate_King on 2010-01-12
Wow... thanks k64!  I think I like that window manager! 
But... is there any way to quickly switch between windows?

---

### Post by running_rabbit07 on 2010-01-12
> **k64 said:**
> Here's another way to maximize screen space:

```
[root@$HOSTNAME:~]# sudo apt-get install gnome-shell
```After this, you would have to set GNOME Shell as a startup application. To do this:

System > Preferences > Startup Applications, click "New Startup Application" and type, in the Name box, GNOME Shell, and in the Command box:

```
/usr/bin/gnome-shell --replace
```Now you can reboot and see the real changes!

Sweet!

---

### Post by The_Pirate_King on 2010-01-12
I just typed the command "gnome-shell --replace" into the terminal and it started up gnome shell.  I would like to know how to go back to normal Gnome without rebooting, if that's at all possible...

---

### Post by running_rabbit07 on 2010-01-12
As long as you didn't add it to startup apps, you should be able to log out and back in.

K64, does this shell use more or less GPU power? I like it.

---

### Post by The_Pirate_King on 2010-01-12
What do you mean, "lob out and back in"? 
I am running from live CD right now so I'd rather not restart... what is the command for the normal Gnome window manager?

---

### Post by running_rabbit07 on 2010-01-12
> **The_Pirate_King said:**
> What do you mean, "lob out and back in"? 
I am running from live CD right now so I'd rather not restart... what is the command for the normal Gnome window manager?

I meant log out, but if you are on a LiveCD, that isn't so easy. I haven't a clue on changing back without logging out or restarting.

---

### Post by The_Pirate_King on 2010-01-12
Figured it out.  The default window manager for gnome is Compiz.  Simply type Compiz into a terminal to restore window functionality if you're ever in a bind and don't have a running desktop environment.  
You'll also probably want to "gnome-panel" to activate the desktop panels.

---

