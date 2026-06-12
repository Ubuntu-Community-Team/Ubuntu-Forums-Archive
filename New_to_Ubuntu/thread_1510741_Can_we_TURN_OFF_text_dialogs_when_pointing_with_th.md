---
title: "Can we TURN OFF text dialogs when pointing with the cursor?"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by doublewitt on 2010-06-15
Whenever you point the cursor to an item on the panel, you see little text dialogs that open up such as: 
"shut down the computer"
"Current workspace 1"
"Clipboard manager"
"Browse and run installed applications"
and many more...

Can we turn this off? When you get familiar with your desktop environment, you no longer need those dialogs... Can we turn this off in applications also...? I'm actually beginning to find those things annoying...:

---

### Post by bigsmitty64 on 2010-06-16
Alt+f2 & type"gconf-editor", when it opens, look in the left panel, expand "apps"/expand "panel"/click "global",
now in the right panel, scroll down to "tooltips-enabled" and uncheck it.

---

### Post by doublewitt on 2010-06-16
Thanks!
That was simple to do.
Can we go one step further and remove all tooltips for all applications? Is there a sort of system "global" override for all apps?

---

### Post by bigsmitty64 on 2010-06-16
O.K. Here's what I just did, and it worked. Do you have Compiz? If not, go to System/Administration/Synaptic Package Manager, and search for compiz. Check the boxes that appear for, "compizconfig-settings_manager", and "compiz-fusion-plugins-extra", and when prompted choose, "mark for installation" then click apply at the top.

Once thats done, go to system/preferences/compizconfig settings manager. In here you will see on the left side, "accessibility" click that and then in the right panel you will see, opacity,brightness and saturation. Click that balloon button and then in there about half way down you will see, "window specific settings" highlight the text in the window and click "edit". You can then click the add (the + button), your cursor will turn into a cross. Go up to an empty spot on the panel and click. It will auto add gnome panel to the list (you will see
& class=) thats it. Then set the opacity level (using the window values slider)to zero. You WILL have to remove the dropdown main menu from the list (just highlight and remove it) or that will be invisible also!  I hope this helps. Good luck,
Smitty

---

### Post by doublewitt on 2010-06-17
Yeah, I have compiz.
What exactly am I doing when I follow these steps? That's not clear to me...

On the other hand, if I proceed to go to "window specific settings", there is no text there - it is blank. So what do I do from there...?

BTW, thanks for your help.

---

### Post by doublewitt on 2010-06-27
Figured it out - but - that's not quite what I want!
 There must be a way to turn off all tooltips (globally) for the entire system. Basically, tooltips are good for beginners but after a while, you don't need them anymore. It's like a youth that begins to ride a bicycle with training wheels till he becomes good enough to remove them. I don't want to be stuck forever with "training wheels" on my system...! When you become familiar with things or when you become an advanced user, you don't need to be bothered with tooltips popping up everywhere - grief, what a nuisance...

---

### Post by doublewitt on 2010-08-14
I found the solution (for me),

"The way to get rid of ALL tool tips is open your Compiz Config Settings Manager, enable "Opacity, Brightness and Saturation" under "Accessibility". Click on the button to go into the settings.

Under the "Opacity" tab go down to "Window Specific Settings" and click "Add". Type "Tooltip" and slide the opacity down to zero. Click "Close".

You're done."

[NB: It is possible you already have "Tooltip" included under another entry, for example if you've made your menus, popups, dropdowns etc transparent. If so just edit that entry and remove "Tooltip" form it so you don't have two conflicting opacity settings.]

from:  [http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html]("http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html")

**[SIZE="6"]*[/SIZE]***[COLOR="Blue"]there are other alternatives on this page...[/COLOR]*

---

