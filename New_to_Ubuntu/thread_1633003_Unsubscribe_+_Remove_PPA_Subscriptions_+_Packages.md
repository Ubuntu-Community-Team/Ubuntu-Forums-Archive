---
title: "Unsubscribe + Remove PPA Subscriptions + Packages"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Dark7man on 2010-11-28
Hey everyone, a few weeks ago I added a PPA to enable me to see the percentage of my battery charge when I clicked on the Power Management applet instead of the (estimating...) constantly show... now as it turns out the code I've installed is a little buggy in its early stages still and seems to be freezing (ex. When my battery is fully charged. I unplug the charger but the icon still states "Battery is fully charged" right up until the point when it reaches 10% and asks me to plug in a charger).

ANYHOW.. my question is, how do I go about removing this PPA from my Update manager and remove the packages I've installed?  Can I just locate them in Synaptic Package Manager... but then how do I remove them from popping up on my "Update Manager" ?

Any info or even a link would be great...
Thanks in advance!
:D

---

### Post by takisan on 2010-11-28
Run Software Sources from the system > administration menu. And on the "other software" tab, you should be able to de-check the repository for that program. To remove it, (I'd recommended doing this before removing the repository) Run Synaptic from the System Administration Menu and find your program, click it, and select either Mark for Removal or Mark for Complete Removal.

Best of luck!

---

### Post by Dark7man on 2010-11-28
> **takisan said:**
> Run Software Sources from the system > administration menu. And on the "other software" tab, you should be able to de-check the repository for that program. To remove it, (I'd recommended doing this before removing the repository) Run Synaptic from the System Administration Menu and find your program, click it, and select either Mark for Removal or Mark for Complete Removal.

Best of luck!

Thanks mate - I've attached a screenshot - When I go to remove the 2 packages listed in the PPA, Synaptics give me this pop up, just cuz I see Gnome etc in there I just want to clarify does it look safe?  I take it will be just removing the code it has modified and returning it to its previous state, or am in a bit of trouble?

I located the "Other Software" in "System>Administration>Software Sources-Other Software" tab... cheers mate :)

---

### Post by takisan on 2010-11-28
Yes, keep all of the gnome stuff. Even I can't (re)-install GUIs from the command line. Do you get those remove for both of them, or marking just one of them?

---

### Post by Dark7man on 2010-11-28
> **takisan said:**
> Yes, keep all of the gnome stuff. Even I can't (re)-install GUIs from the command line. Do you get those remove for both of them, or marking just one of them?

No, there are 2 packages that are listed on the guys PPA website

1. gnome-power-manager (This one doesn't seem to want to remove anything else)
2. upower - this one here wants to mark more packages for removal, as seen in the previous screenshot I posted...

Go with removing just the first one in synaptics? Reboot and cross my fingers I dont kill anything?

Thats a bit crap though if You install pretty much PPA's for little fixes etc, its a one way road, You can't safely remove them again without the risk of damage, or is this due to wrong coding in the packages I'm installing, or just because the package is linked to the gnome applets?

What I'm asking is guess-work, just trying to learn as I go along!

~Thanks for Your time and patience mate! :)

---

### Post by takisan on 2010-11-28
Try installing the gnome-power-manager from the standard ubuntu repository, and then that should autoremove the gnome-power-manager from the ppa you're subscribed to. Then also mark power-manager to be removed.

---

### Post by jmszr on 2010-11-28
Dark7man,

This might be what you want: [http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html](http://www.webupd8.org/2010/04/ppa-purge-now-available-via-getdeb.html)

---

### Post by netopalis45 on 2011-01-06
i am having a similar problem but when i try to open synaptic i get an error message saying that the list of sources cannot be read and gives me a specific ppa, which i believe is the problem, and then closes. is there a way to remove that ppa from the command line without using synaptic? i have seen several sites saying to use ppa-purge to remove a ppa but when i try to run that it says command not found

---

### Post by lidex on 2011-01-07
OK, what you need is PPA Purge. It will remove the PPA as well as revert any changes from it. I use it from within Ubuntu-Tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) and see screen below. I do see a package for ppa-purge in the universe repo if you want to use it manually.
@netopalis45
U-Tweak also has a source editor or use this terminal command:
```
gksu software-properties-gtk
```

---

### Post by oldos2er on 2011-01-07
> **netopalis45 said:**
>  is there a way to remove that ppa from the command line without using synaptic?

Edit your software sources file manually ```
gksu gedit /etc/apt/sources.list
``` Add a comment mark # in front of the PPA you don't want.

It's possible that the PPA will be listed in a file in /etc/apt/sources.list.d/ instead of /etc/apt/sources.list. In that case you would run ```
sudo rm foo.list
``` where foo is that appropriate file name.

When you're done with the above, run ```
sudo apt-get update
```

---

