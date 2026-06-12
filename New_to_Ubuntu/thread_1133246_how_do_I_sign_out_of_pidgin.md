---
title: "how do I sign out of pidgin?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by person8451 on 2009-04-22
I can't seem to get it to go away.  I am on 9.04 JJ.  

The little icon for restart/shut down/etc is now the pidgin status icon for some reason.  There is no other icon for Pidgin in the task bar.  If I click on the one that is there, it wants to know if I want to restart the computer.

So uhh...how do I make Pidgin go away now?

---

### Post by llamabr on 2009-04-22
ctrl-q

or right click on the little icon, and choose quit.

---

### Post by coldReactive on 2009-04-22
In the buddy list window, go to the buddies menu and select quit.

> **llamabr said:**
> or right click on the little icon, and choose quit.
the person said there was no other icon.

---

### Post by halitech on 2009-04-22
can you get pidgin to open? if you can, go to file - shut down. if not, you could try opening a terminal and run```
killall -9 pidgin
``` and that should kill it

---

### Post by person8451 on 2009-04-22
Thanks, that fixed it--it was hiding in the buddy menu.

Does anyone know why the reboot/shut down/switch user button turns into the Pidgin status thing now?  It seems to make no sense to do that, but idk, maybe there is some plan to it.

---

### Post by halitech on 2009-04-22
I'm thinking it was more a glich in the notification area then anything done on purpose

---

### Post by LowSky on 2009-04-22
mine works fine, can you show us a picture of your desktop?
Just press the print screen button on your keyboard, usually above the Home, Insert, Delete Keys

---

### Post by person8451 on 2009-04-22
screens of the corner, with pidgin off, then on.

[ATTACH]110642[/ATTACH]

A little envelope appears when pidgin is running, but it doesn't seem to do anything.  If I click on the green thing where the restart button used to be, I can change my pidgin status, but not sign out.

But I can do that from the Buddies menu I guess.  Just seems weird is all.

---

### Post by halitech on 2009-04-22
that little envelope is saying you have email in your hotmail/yahoo whatever account

almost looks like the pidgin icon is over riding the shutdown icon but no idea why

---

### Post by LowSky on 2009-04-22
close pidgin, delete the .purple folder form your home directory and see if that clear anything up.

---

### Post by coldReactive on 2009-04-22
That green icon taking over the shutdown icon is a NEW FEATURE of Ubuntu 8.10, to integrate Pidgin status into [Empathy](http://en.wikipedia.org/wiki/Empathy_(software)).

---

### Post by person8451 on 2009-04-22
Awesome  lol.

So we have gone from 'it works on my machine' to 'it's not a bug it's a feature' in under an hour.

Yay Linux   lol

Any tips on how to get rid of this "empathy" bug?

---

### Post by coldReactive on 2009-04-22
> **person8451 said:**
> Awesome  lol.

So we have gone from 'it works on my machine' to 'it's not a bug it's a feature' in under an hour.

Yay Linux   lol

Any tips on how to get rid of this "empathy" bug?

Have you tried right-clicking the envelope icon?

---

### Post by person8451 on 2009-04-22
Indeed I have right-clicked on the little envelope.  Right-click brings up a menu with the options to remove the icon from the panel or lock it.  Left click simply brings up a little bit of text that says "Pidgin Internet Messenger", and if I click that, it minimizes (or maximizes) the Pidgin buddy list.  In neither case is there an option for ending the program.

Perhaps I am supposed to reboot every time I want to exit Pidgin.  

Every other application in Ubuntu manages to do without covering/replacing the restart button. Why this one has to do so, I have no idea.  I hope I can find a way to remove this "feature".  For now I have just created my own shortcut to kill Pidgin and placed it on the panel.  

Perhaps I can find some other IM application that isn't so...integrated.

---

### Post by coldReactive on 2009-04-22
Did you try to right-click the "Pidgin Instant Messenger" text when you left clicked the envelope?

---

### Post by nanbanjin on 2009-04-22
I had some problem with Pidgin disappearing because of this envelope thingie. I dissabled it somhow so now Pidgin appears just the way it used to in the system tray.

---

### Post by person8451 on 2009-04-22
> **coldReactive said:**
> Did you try to right-click the "Pidgin Instant Messenger" text when you left clicked the envelope?

Yes.  That minimizes the buddy list.  I am still in Pidgin, it is still running, and there is no "quit" option.

Left on the envelope then right on the text, minimizes/maximizes.  Left on envelope and left-click on text, minimizes/maximizes...no 'quit' option either way.

No problem tho, as I am now using Kopete for now, at least until they start adding "features".

---

### Post by coldReactive on 2009-04-23
Pidgin in 9.04 has the tray icon set to "Never" show. Go into the preferences dialog under Tools menu. Then select from "Show system tray icon:" dropdown, **Always**. Then right-click the envelop and click Remove from Panel.

---

### Post by methodmarvel on 2009-04-23
> **coldReactive said:**
> Pidgin in 9.04 has the tray icon set to "Never" show. Go into the preferences dialog under Tools menu. Then select from "Show system tray icon:" dropdown, **Always**. Then right-click the envelop and click Remove from Panel.

that's what I was going to type - this is the "fix"

then you can remove the "envelope" icon by right clicking it and selecting remove from panel

ubuntu devs have been too clever for their own good

empathy is a crappy idea

---

