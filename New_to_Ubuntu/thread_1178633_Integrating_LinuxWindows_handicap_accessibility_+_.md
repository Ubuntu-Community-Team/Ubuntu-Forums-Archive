---
title: "Integrating Linux/Windows handicap accessibility + Visual Aids"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-04
The complexity of this question would probably justify multiple posts, but I will endeaver to compress it into one anyways.  I live with someone who is gravely visually impaired and also has muscle coordination problems.  Sometimes he likes to type things, has trouble even starting up the word processor himself.  

First off, in Linux, I saw a thing that does the stretch icon.  Can this be done in windows?  A giant icon would be really nice: less precision to click on and easier to see.  If not I head about this thing where you can actually virtulize linux under windows (install it like a regular program), possibly through various ways.  If I do this could I put it in the startup key under his user name?  

One thing he does is make black and white screen colors (ie, white text black backroud).  Is there any way to do this in Linux?  Also, I would need to create (as you would a template in windows) a defualt, well, template, in a word processor - could openoffice do that?  (Just link the template from his desktop?)

Then I suppose I would need a really easy login procedure.  

Then... is it possible to hook up a T.V. to either a desktop or a laptop?  That would be really nice as well, we could do that in his room. 

There are some issues with this I would appreciate it if someone could help me address as well:
Desktop: Our only readily available (for this dedicated task) desktop is about 500 mHz.
Laptop: I can't install linux, or even run a simple RAM linux such as parted magic.  It locks up.  Either the above linux-with-a-certain-user thing applies, or if someone could tell me why that is, that would be really nice.

Is there any way I could set up a key combination in windows to automatically log off?  I think he can use the welcome screen.

[SIZE=2]Any answers to any aspects of my questions or out-of-the-blue suggestions are welcome.


[/SIZE][SIZE=2]Oh, and thanks for any help!
[/SIZE]

---

### Post by durand on 2009-06-04
1) You could lower the screen DPI or the resolution.
2) Try virtual box ([www.virtualbox.org](www.virtualbox.org))
3) You could use a high contrast theme (System > Preferences > Appearance) or edit /etc/X11/xorg.conf as root.
4) Yes, openoffice can do that. It should be in the help.
5) Go to System > Administration > Login Window. Go to the Accessibility tab and enable accessible logon. Go to the security tab and enable automatic logon.
6) No idea.

General Tip: Try other lighter linux distributions, maybe puppy linux or something else. Investigate if System > Preferences > Assistive Technologies is useful.

---

