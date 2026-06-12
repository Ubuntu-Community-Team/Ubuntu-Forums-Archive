---
title: "Compiz isn't showing advanced things even after compiz-fusion-plugins-extra"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by thejakeman on 2010-08-04
I use compiz along with the advanced plugins, but after a while of flawless operation the advanced options disappeared. I reinstalled the advanced plugin pack-thing but they're still not there. How do I refresh them?

Thanks!

---

### Post by Specs4 on 2010-08-09
First make sure that "Animations Add-On" and "Animations" in CompizConfig are checked, if add ons are not showing try restarting, or installing it again. If it still doesn't work try reinstalling the addons and CompizConfig Settings Manager.
I had the same thing happen to me not long ago, and reinstalling them both seemed to work.

If your going to reinstall, install it through terminal, not through the Software Centre.
To uninstall them find "compizconfig-settings-manager" and "compiz-fusion-plugins-extra" in Synaptic Package Manager then right click on them and select "Mark for Complete Removal" then "Apply"
after uninstalling them both go to System > Preferences > Appearance then go to Visual Effects and make sure its on "Extra"
Then install them both again with these commands
> sudo aptitude install compizconfig-settings-manager
then when that finishes
> sudo aptitude install compiz-fusion-plugins-extra
and the addons should be back.

---

### Post by zwayon on 2011-03-03
or after u finish installing Compiz, type the following in the terminal :

sudo apt-get install compiz-fusion-plugins-extra

---

### Post by beew on 2011-03-03
Not sure what you mean by the "advanced plugins" but by the title of the thread you have already installed compiz-plugins-extra. There are plugins which are not in the extra or even the compiz-plugins-unsupported package (like screen saver and anaglyph) You can get all Compiz plugins (those are not in the repository) with a script, but be warned that some are labeled "experimental".

[URL="http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html"]http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html
[/URL]

---

