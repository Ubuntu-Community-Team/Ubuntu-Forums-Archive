---
title: "Kde: post log-in black screen - help!"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by BSAB_80 on 2009-02-23
Some packages upgraded during the night, didn't notice which ones, and at one point yesterday the system froze up and I had to restart. First I re-encountered the same problem I have after some updates where the log-in text is enormous, so I had to edit /etc/kde4/kdm/kdmrc to -dpi 96 in the server command line, which solved the problem, but now when I log in to kde I only get a  black screen with the mouse pointer, and that's it. 
Tried to reconfigure the xserver as advisedin other thread  but to no avail.
Also followed a suggestion in another thread to edit ~/.kde/share/config/kwinrc and change Compositing to Enabled=false, but the only thing that caused was that instead of a black screen now I have the wallpaper of the log-in screen but still just the mouse pointer and no actual desktop.
I'm at my wit's end here. 

Anyone can help?
I'm running KDE4 (.2, maybe? Not sure)

---

### Post by peterLinux on 2009-02-24
Had the same thing once, KDE 4.1 or 2 is still in development... never know what happens...

I created a new user, copied the ~/.kde directory to my profile and all was good
(Almost I had to change a couple path settings but those were obvious)

This is probably not the official way to fix thins but hey it worked for me, ymmv

---

### Post by BSAB_80 on 2009-02-24
I'm so desperate I'll try anything! 
Can you tell me how to do it?

---

### Post by HavocXphere on 2009-02-24
Switch off desktop effects from the console login.

[http://ubuntuforums.org/showpost.php?p=6350910&postcount=4](http://ubuntuforums.org/showpost.php?p=6350910&postcount=4)

..I posted more detailed instructions somewhere...but can't find them atm.

Edit: Found it:
[http://kubuntuforums.net/forums/index.php?topic=3101741.msg169997#msg169997](http://kubuntuforums.net/forums/index.php?topic=3101741.msg169997#msg169997)
Do note the user below my post saying there is a mistake in the instructions somewhere.  He never said what it is though.:rolleyes:

---

### Post by BSAB_80 on 2009-02-24
I did that before and nothing. 
Even managed to MV my .kde to kde4backup, so now I don't even have the Compositing option in my kwinrc and still nothing, just the black screen! 


> **HavocXphere said:**
> Switch off desktop effects from the console login.

[http://ubuntuforums.org/showpost.php?p=6350910&postcount=4](http://ubuntuforums.org/showpost.php?p=6350910&postcount=4)

..I posted more detailed instructions somewhere...but can't find them atm.

Edit: Found it:
[http://kubuntuforums.net/forums/index.php?topic=3101741.msg169997#msg169997](http://kubuntuforums.net/forums/index.php?topic=3101741.msg169997#msg169997)
Do note the user below my post saying there is a mistake in the instructions somewhere.  He never said what it is though.:rolleyes:

---

### Post by HavocXphere on 2009-02-24
> I don't even have the Compositing option in my kwinrc
Removing option completely = bad since you can't predict what its going to do then.

Looks like your going to have to edit xorg.conf to select the vesa driver until you can figure out whats wrong.

---

### Post by BSAB_80 on 2009-02-24
Read in some thread that it worked for some people so I gave it a shot.
You know how it is, you get to a point where you'll try anything. 

The all thing makes no sense. 
If I can see my log-in screen, obviously kubuntu recognizes that, hey, this thing must be working. 
So why the black screen afterwards?!
Oy.

Any ideas on editing the xorg file?
My graphic card is just an integrated intel chip.
And would it be better if I moved the settings back from kde4backup to .kde?
How do I do that?


> **HavocXphere said:**
> Removing option completely = bad since you can't predict what its going to do then.

Looks like your going to have to edit xorg.conf to select the vesa driver until you can figure out whats wrong.

---

### Post by BSAB_80 on 2009-02-25
Any ideas?
Or should I just give up altogether and install windows?

---

