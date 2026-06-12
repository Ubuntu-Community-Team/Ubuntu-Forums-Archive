---
title: "Accidentally deleted Rhythmbox from system tray"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Ivkosky on 2010-06-22
Hi all


I have accidentally deleted Rhythmbox from system tray... :( I have tried to turn off and on the status icon plugin but no change... :( I loved that feature, could somebody please bring it back to me? :)

Thank you!

---

### Post by Arla on 2010-06-22
Should be the indicator applet, I just deleted mine, and re-added it by adding back in the indicator applet (you probably lost the volume control and possibly other indicators too).

---

### Post by yetiman64 on 2010-06-22
> **Ivkosky said:**
> Hi all


I have accidentally deleted Rhythmbox from system tray... :( I have tried to turn off and on the status icon plugin but no change... :( I loved that feature, could somebody please bring it back to me? :)

Thank you!

First up are you using Lucid (10.04)? I'm assuming you are, if not let us know.

If so the only way I could see that as possible if you accidently removed the Indicator Applet.

Try right clicking on the panel (where rhythmbox used to show) and select Add To Panel.

In the box that then shows up scroll down to Indicator Applet select it then click Add then close.
It should now come back when you next open rhythmbox.

Edit: just noted you use 10.04 :)

---

### Post by conorsulli on 2010-06-22
What those 2 fellas said, however you should also check you have it enabled first before you go fiddling with the panel! it could be so simple that its disabled!.. But I'm not sure when you refer to have "deleted it"... so if you are missing the sound indicator you should proceed with the steps above, if not it is disabled ...

Rythmbox > edit > Plugins > Status icon : Make sure the check box is ticked.

Good luck I'm sure there should be enough info in these posts to get you on your way!

---

### Post by Ivkosky on 2010-06-22
Thank you both for your really quick responses! :) Yes, it was the indicator applet. Thanks a lot!

The other thing I encountered is that I am not able to open Rhythmbox just by single click on the tray icon. I have to click on it and choose "Show Rhythmbox" from the dropdown list... Very annoying :( Is there any solution?


P.S.: These are my first hours of using Lucid, I switched from Karmic today - clean install.

**EDIT:** Thanks conorsulli, I have checked the plugin before and it was ticked.

---

### Post by yetiman64 on 2010-06-22
> **Ivkosky said:**
> ...The other thing I encountered is that I am not able to open Rhythmbox just by single click on the tray icon. I have to click on it and choose "Show Rhythmbox" from the dropdown list... Very annoying :( Is there any solution?....

Have noted and am a bit annoyed by that myself but am yet to hear of a way to change it. Think it's just how its programmed / designed. Would love to hear otherwise myself. 

Anyone ?

---

### Post by conorsulli on 2010-06-22
> **Ivkosky said:**
> Thank you both for your really quick responses! :) Yes, it was the indicator applet. Thanks a lot!

The other thing I encountered is that I am not able to open Rhythmbox just by single click on the tray icon. I have to click on it and choose "Show Rhythmbox" from the dropdown list... Very annoying :( Is there any solution?


P.S.: These are my first hours of using Lucid, I switched from Karmic today - clean install.

**EDIT:** Thanks conorsulli, I have checked the plugin before and it was ticked.

Unfortunately not in the new indicator layout, However If you drag "Rythmbox" from Applications > Sound & Video onto a location of the panel where you want it, It will act as a sort of unhider if it is already running when single clicked, Or launcher if not already running.

---

### Post by Ivkosky on 2010-06-22
> **conorsulli said:**
> Unfortunately not in the new indicator layout, However If you drag "Rythmbox" from Applications > Sound & Video onto a location of the panel where you want it, It will act as a sort of unhider if it is already running when single clicked, Or launcher if not already running.

So I understand that there isn't more elegant way of overcoming this problem. :( I would be curious why it was possible in Karmic and not anymore in Lucid. What was the main reason for changing of layout...

---

### Post by conorsulli on 2010-06-22
> **Ivkosky said:**
> So I understand that there isn't more elegant way of overcoming this problem. :( I would be curious why it was possible in Karmic and not anymore in Lucid. What was the main reason for changing of layout...

The new one in 10.04 uses the "Indicator applet" the old one used "notification area" like the wifi applet still does now, actually if you can find the plugin for notification area or if it could be re-enabled through gconf or something you could very well disable the newer one .... I don't use rhythmbox so I wouldn't know if this old notification area widget thing is still in synaptic/gconf or what the story is...

Maybe someone is a little more enlightened on using the old one would know? perhaps?

---

### Post by Cavsfan on 2010-09-09
> **Ivkosky said:**
> Thank you both for your really quick responses! :) Yes, it was the indicator applet. Thanks a lot!

The other thing I encountered is that I am not able to open Rhythmbox just by single click on the tray icon. I have to click on it and choose "Show Rhythmbox" from the dropdown list... Very annoying :( Is there any solution?


P.S.: These are my first hours of using Lucid, I switched from Karmic today - clean install.

**EDIT:** Thanks conorsulli, I have checked the plugin before and it was ticked.

> **yetiman64 said:**
> Have noted and am a bit annoyed by that myself but am yet to hear of a way to change it. Think it's just how its programmed / designed. Would love to hear otherwise myself. 

Anyone ?

Not sure if this is what you are asking, but I was kind of annoyed myself how when you open Rhythmbox, 
it just goes to the panel at the top right and likewise when you close it. I searched and searched how to fix this and finally found it.
Open terminal and enter **gconf-editor** click **apps **then **Rhythmbox** then **plugins **then **status-icon** and 
look at the value of **status-icon-mode**. It is defaulted to 3 and I changed mine to 0.

Now when I open Rhythmbox it opens and displays on the desktop and when I close it, it just closes
and does not just go to the panel. I am pretty sure that is all I changed to get it to work like that.
When I close something I want it to close and not just hide.

---

### Post by yetiman64 on 2010-09-19
> **Cavsfan said:**
> Not sure if this is what you are asking, but I was kind of annoyed myself how when you open Rhythmbox, 
it just goes to the panel at the top right and likewise when you close it. I searched and searched how to fix this and finally found it.
Open terminal and enter **gconf-editor** click **apps **then **Rhythmbox** then **plugins **then **status-icon** and 
look at the value of **status-icon-mode**. It is defaulted to 3 and I changed mine to 0.

Now when I open Rhythmbox it opens and displays on the desktop and when I close it, it just closes
and does not just go to the panel. I am pretty sure that is all I changed to get it to work like that.
When I close something I want it to close and not just hide.

@ Cavsfan, found I actually like to use the status icon as is (ie. mode 3,) but I like to have it open to the window when launched from the menu (and not just directly to the panel), with your info above I ticked the setting "window-visible" and now everything works perfectly as I like. 

Thanks for this info, and cheers from yetiman64 :-D

---

### Post by Baldrick_NZ on 2010-09-19
> **yetiman64 said:**
> Have noted and am a bit annoyed by that myself but am yet to hear of a way to change it. Think it's just how its programmed / designed. Would love to hear otherwise myself. 

Anyone ?

I upgraded to the 10.10 Maverick version of RhythmBox, and dicovered that you have to right-click the RhythmBox icon in the panel to get the options you're looking for. Left click now either displays or hides RhythmBox.

Hope that helps..

---

### Post by Cavsfan on 2010-09-20
> **yetiman64 said:**
> @ Cavsfan, found I actually like to use the status icon as is (ie. mode 3,) but I like to have it open to the window when launched from the menu (and not just directly to the panel), with your info above I ticked the setting "window-visible" and now everything works perfectly as I like. 

Thanks for this info, and cheers from yetiman64 :-D
Glad I could help! I just put a check by "window visible" and nothing changed. But, I have the mode set to 0.
I like mine to be visible when it's open. Don't like extra steps to open it.

---

### Post by xouns on 2011-03-09
Thanks guys, the plugin tip worked for me. It did show in the volume-dropdown menu, which is cool, but I like to open it in one click in stead of click, menu, click. Thanks for the tip!

---

