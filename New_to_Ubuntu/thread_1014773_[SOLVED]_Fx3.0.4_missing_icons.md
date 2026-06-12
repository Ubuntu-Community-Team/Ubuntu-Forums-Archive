---
title: "[SOLVED] Fx3.0.4 missing icons"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by freesitebuilder on 2008-12-18
I upgraded to 8.10 in October and had no problems. In November I had problems which have finally required replacing the hard drive, so a couple of days ago I did a clean install of 8.10 and also ran all the updates.

I then restored my Firefox extensions using FEBE, and promptly lost the icons on my bookmarks bar. The bookmarks are there OK - using the bookmarks menu displays them OK, and they go to the correct site when clicked.

I also have no icons in the "customise" dialogue box. I've tried removing all extensions, and adding them one by one to find the culprit but no success. I've also tried safe mode to reset the defaults, again with no success.

If I remove Firefox completely using Synaptic, and then reinstall, is this going to cause any problems with Ubuntu?

TIA

---

### Post by aheckler on 2008-12-18
> **freesitebuilder said:**
> If I remove Firefox completely using Synaptic, and then reinstall, is this going to cause any problems with Ubuntu?

Nope.

---

### Post by freesitebuilder on 2008-12-19
That hasn't cured it - I'll have to think of something else.

---

### Post by flanagan on 2008-12-19
It sounds like your profile got corrupted when you restored your extensions using FEBE. This would not have been cured by an uninstall/re-install of Firefox, since that does not affect your profile.

I would try creating a new profile to see if the problem persists:

[http://kb.mozillazine.org/Profile_Manager#Creating_a_new_profile](http://kb.mozillazine.org/Profile_Manager#Creating_a_new_profile)

---

### Post by Moop on 2008-12-19
I think the icons are restored by visiting the site. Try opening all your bookmarks in tabs.

---

### Post by flanagan on 2008-12-19
I thought of that, too, Moop, but she said in the original post:
> **freesitebuilder said:**
> ...and they go to the correct site when clicked.

---

### Post by freesitebuilder on 2008-12-19
I finally deleted my profile and created a fresh one, which has cured the problem. Don't know why I didn't do that immediately, just got out of the habit after 2 years on Ubuntu i suppose! :)

---

