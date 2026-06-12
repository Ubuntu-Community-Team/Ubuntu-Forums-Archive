---
title: "Primer on themes?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by dndrich on 2009-03-18
Ubuntupals:

Recently I have perused Gnome Look for new icons and themes.  It isn't entirely clear to me how to install some of these things.  I am running a stock Intrepid 8.10 which I assume has compiz running and metacity for the borders?  So, I'll download a theme, and drag the tar into the appearances dialog box and it will install.  But some themes don't work correctly, such as aquadreams-theme which requires GTK+, whatever that is.  So, a basic primer on how this all is supposed to work would be really nice.  Can anybody point me in the right direction?

---

### Post by Therion on 2009-03-18
Well this is one of those "It all depends" questions.  Since not all authors who make themes (icon packs, etc.) package things the same way, how you need to install them can vary.  Some themes require different rendering engines as well, like Pixbuf for instance.  Then there's dealing with things like Emerald, Compiz, GTK, Metacity... Ugh.  It all gets pretty complicated.  Or, rather, it CAN get rather complicated.  It doesn't have to but it frequently does.

Are you referring to this AquaDreams theme:

[http://www.gnome-look.org/content/show.php/%22Aqua+Dreams%22+theme?content=72997](http://www.gnome-look.org/content/show.php/%22Aqua+Dreams%22+theme?content=72997)

The best thing to do, in my opinion, is when you run into an issue, post and ask for help with the specifics.  Give a link to the theme you're having a problem with and just ask for help until you kinda get a feel for how it all works, because no...  I've not seen a comprehensive "primer" on how to do stuff like this.  I've had to learn by doing. 

I'm happy to try and help you though...

---

### Post by philinux on 2009-03-18
> **dndrich said:**
> Ubuntupals:

Recently I have perused Gnome Look for new icons and themes.  It isn't entirely clear to me how to install some of these things.  I am running a stock Intrepid 8.10 which I assume has compiz running and metacity for the borders?  So, I'll download a theme, and drag the tar into the appearances dialog box and it will install.  But some themes don't work correctly, such as aquadreams-theme which requires GTK+, whatever that is.  So, a basic primer on how this all is supposed to work would be really nice.  Can anybody point me in the right direction?


Unfortunately as therion says it depends. In this case search in synaptic for gtk and install the app gkt2-engines

---

### Post by dndrich on 2009-03-18
Yes, that is the theme.  I did it from the french site which required a repository entry, which I made.  It requires the GTK engine, which I can install.  It just seems like there ought to be some sort of primer on this somewhere!  But this community is so helpful.  Thanks!

---

### Post by Therion on 2009-03-18
> **dndrich said:**
> Yes, that is the theme.  I did it from the french site which required a repository entry, which I made.  It requires the GTK engine, which I can install.  It just seems like there ought to be some sort of primer on this somewhere!  But this community is so helpful.  Thanks!
The problem with the whole "Primer" idea is that it would be well-nigh impossible to cover every possible scenario.  Your experience with this Aquadreams theme for example, I can assure you, is **quite **out of the ordinary (you had to add a repo??!!).

But yes, we're a pretty friendly bunch and I think we can all relate to the inherent frustration of an oddly packaged theme that we're drooling over.

---

### Post by dndrich on 2009-03-18
Admittedly an oddball theme.  Once I decided to get rid of it I apt-get autoremoved it and deleted the repo.  The theme can be gotten elsewhere without the repo.  Really nice icon group, though.

---

