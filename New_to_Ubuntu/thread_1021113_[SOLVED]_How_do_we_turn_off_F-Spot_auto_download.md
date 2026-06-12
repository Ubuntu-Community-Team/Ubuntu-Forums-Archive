---
title: "[SOLVED] How do we turn off F-Spot auto download?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2008-12-25
Hi.
When I plug in my digital camera, F-spot automatically starts downloading the pictures. I don't want it to do this.

I tried going to System/prefs/removable drives and media and ticking off the box for auto downloading to f-spot and that did not stop f-spot. Next, I tried deleting the word f-spot in that box AND ticking off the box and f-spot is still persisting.  I would just remove the program from my PC but I use it for uploading pics to web albums. Is there no way to keep F-spot from automatically downloading my photos? It is really annoying.

Thanks

---

### Post by Elfy on 2008-12-25
Not sure where sys>prefs>removable drives is - at least I can't see it. Have you been to the media tab of nautilus preferences, it cna be turned off there

---

### Post by nhasian on 2008-12-25
yes thats right.  In my Ubuntu 8.10 its under System->Preferences->Removable Drives and Media.

---

### Post by mc4man on 2008-12-25
> I don't want it to do this.
Am figuring your using 8.04, in 8.10 control has been shifted to nautilus -> preferences -> media -> photos. (In 8.04 that setting is for digital photos on removable media, In 8.10 the function is combined, probably because more cameras are mounting.

You could check there any way, especially if your camera automounts (icon shows up. If no fix there..

What is it you'd like to happen and how reversible?

Removing f-spot from removable drives .... has no effect if you leave it blank, the box is to input a new setting, blank means - no change.

Do you get a prompt box or does fspot just open? The prompt box has an option for 'always perform this action', I *wouldn't check it* till you gain control over the action unless you already did. (have yet to figue out how to restore the prompt after doing that.

If you don't get the prompt and can't restore it then try replacing f-spot -import with something that won't work or something else you want to happen.( nautilus would open nautilus, nautilus-open-folder should have no effect, amarok will open amarok, ect.,ect.

---

### Post by Elfy on 2008-12-25
> **nhasian said:**
> yes thats right.  In my Ubuntu 8.10 its under System->Preferences->Removable Drives and Media.

Not on mine?

I remember seeing it at some point and it's not in menu to be turned on either :shrug:

---

### Post by nhasian on 2008-12-25
hmm well I did upgrade from 8.04.  Not sure if thats why or not, but maybe you have it in the menu but its just not enabled?  right click on Applications, then click on Edit Menus.  Under preferences, make sure that Removable Drives and Media has a checkbox next to it.

> **forestpixie said:**
> Not on mine?

I remember seeing it at some point and it's not in menu to be turned on either :shrug:

---

### Post by the.phantom on 2008-12-25
might try this?

gksudo nautilus

now when the window opens up
on the top
EDIT
Preferences
click the media tab
change photos to "do nothing"

save and exit

you can still start Fspot but it will not auto start ;-D

---

### Post by Motorhead Kaze on 2008-12-25
Ah! That was it! I went thru the gknautilus suggestion there, and switched it off from the "big boy" menu.

I am using Hardy btw. My computer is running awesome right now, and I see no reason to upgrade. So yes, my media preferences are under system/preferences/removable drives and media, BUT trying to change the Fspot pref did not work there. Rather dumb to have a box to untick there if I still have to go thru nautilus and change prefs as root.

But hey, that last thing worked!

Thanks for all the responses...and Merry Christmas!

---

