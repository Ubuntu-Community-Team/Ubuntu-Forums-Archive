---
title: "Uninstalling Flash Plugin,  in Firefox?!"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by daleybugle on 2009-06-24
I recently installed ubuntu and am enjoying it so far, despite not having a great deal of unix knowledge i have managed to use google & these forums as a crutch.

One thing is really bugging me though. When I started Firefox for the first time i visited a site which required Flash, and was prompted to install it by a pop up script.
There were 3 choices, and unsure of which I should choose, I opted for the one that said it was for Gnome, assuming this was the most compatible. WRONG
Now when I try to view Flash content or stream videos etc its all messed up.

Essentially what I want to do is remove this plug-in and start from scratch so I can get this prompt again, and select the correct plugin, which I am finding IMPOSSIBLE.:confused:

your help would be much appreciated, Thanx

---

### Post by Celauran on 2009-06-24
Open up Synaptic, search for flash, and uninstall the one that's installed. Once done, grab the .deb from the adobe site.

---

### Post by Kimm on 2009-06-24
this should fix it, run:

sudo apt-get remove gnash

then run:

sudo apt-get install flashplugin-nonfree

That should fix it :)

---

### Post by wpshooter on 2009-06-24
> **Celauran said:**
> Open up Synaptic, search for flash, and uninstall the one that's installed. Once done, grab the .deb from the adobe site.

Why is it that if these steps are necessary to get Flash to a point that it works correctly (and I certainly agree that they are), that someone does not suggest to whoever it is that is in charge of this O/S, that they abandon this Flash Plugin that is included in Synaptic and instead put a direction somewhere in the operating system "suggesting" that if you want Flash to work properly (read that as completely), then you need to go the Adobe Acrobat site and download and install the complete Linux version of Adobe Flashplayer ?

And *@$%#($@(* with the legalistics of it all !!!

---

### Post by daleybugle on 2009-06-24
thank you all for your advice, I have finally managed to get Flash working with your help.
i feel like a weight has been lifted! :P
@wpshooter I totally agree, I knew that getting to grips with a new O/S wouldnt be a walk in the park, and have managed with most things, but something as simple as running flash could be made a lot simpler in the first instance.

Thanks again!

---

