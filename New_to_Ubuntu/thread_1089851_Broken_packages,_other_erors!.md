---
title: "Broken packages, other erors!"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by newbeeman on 2009-03-07
I have recently worked my way through a 'sticky' adding medibuntu correctly amongst java updates etc, plus other stuff. Now I find broken packages and updates which concern me.
Synaptic tells me 33 to upgrade, 830 to remove. Then it tells me I might stop my machine from working. Scary!!
Am I right to tell it to 'do' it?

---

### Post by thtrgremlin on 2009-03-07
If you could provide the specific output, could tell you better if you are about to break something. if it is suggesting removing 830 packages and you are not doing a distribution upgrade, I would be concerned. If everything was up to date before you added medibuntu, this is not right, but wiling to help you find what went awry.

---

### Post by cozmicharlie on 2009-03-07
> **newbeeman said:**
> I have recently worked my way through a 'sticky' adding medibuntu correctly amongst java updates etc, plus other stuff. Now I find broken packages and updates which concern me.
Synaptic tells me 33 to upgrade, 830 to remove. Then it tells me I might stop my machine from working. Scary!!
Am I right to tell it to 'do' it?

It is generally safe to update from Synaptic or the update manager.  You can first fix your broken packages by doing the following:

Open Synaptic
Custom filters>Broken (this should show all the broken packages)
In the menu go to edit>fix broken packages

I also recommend for people new to Ubuntu is to install a package called "Ubuntu Tweak".  Google it and install it per the instructions.  It provides an easy way to configure nautilus and clean your cache, clean un-needed packages etc.  Very easy - very handy.

Enjoy!

---

### Post by thtrgremlin on 2009-03-07
Wow, Just checked out ubuntu-tweak. I think that is a great app for anybody that wants to do a bit of tweaking for the way things work. Thanks for the recommendation. I have been using ubuntu for years, and that is a great interface for doing many things that puts many common desires in one simple place. Thanks.

---

### Post by newbeeman on 2009-03-07
> **cozmicharlie said:**
> I also recommend for people new to Ubuntu is to install a package called "Ubuntu Tweak".  Google it and install it per the instructions.  It provides an easy way to configure nautilus and clean your cache, clean un-needed packages etc.  Very easy - very handy.
Enjoy!

This is more serious than I thought, now I've lost Firefox, will not start.
On trying to sort out have loaded Tweak, that's fine and working, but I can't find broken packages in it. any comments?

---

### Post by thtrgremlin on 2009-03-07
Do you get any errors when you run ```
sudo apt-get update && sudo apt-get upgrade
```

I would bet it had something to do with thy mysterious and sudden desire for something to request the removal of 840 packages that did the trick, but can just move forward from here.

---

### Post by newbeeman on 2009-03-07
> **thtrgremlin said:**
> Do you get any errors when you run ```
sudo apt-get update && sudo apt-get upgrade
```

I would bet it had something to do with thy mysterious and sudden desire for something to request the removal of 840 packages that did the trick, but can just move forward from here.

Ok. Ran that and got 38 upgraded. So I'm going to say this is solved as I was about to migrate the whole thing to a d. drive.
Thanks for your help.

Cannot find the Solved button.

---

