---
title: "All 'shared library' files (*.so) missing from Launchpad debs"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by inameiname on 2011-06-14
Anybody know why all '*.so' files found in '*orig.tar.gz' files are not being copied over to '*.tar.gz' ones? Several packages I've tried which have '*.so' files inside all fail to get copied over. 

First, I've successfully uploaded several packages to my PPA and they have resulted in debs just the way I wanted. As such, this isn't really a package problem or one with Launchpad.  

Currently, the 2 packages that fail to put the '*.so' shared library files inside are, 'nautilus-kill-thumbs' and 'nautilus-kill-metamac'. 

The first two packages above are actually made up of a single file, a '*.so' file, so it really hurts that they are missing. :P. I found these on Gnome-Look and am trying to upload them to a PPA for all to use. 

nautilus-kill-thumbs - [http://gnome-look.org/content/show.php/Nautilus+Extension+Kill+Thumbs?content=92143](http://gnome-look.org/content/show.php/Nautilus+Extension+Kill+Thumbs?content=92143)
nautilus-kill-metamac - [http://gnome-look.org/content/show.php/Nautilus+Extension+Kill+MetaMac?content=140033](http://gnome-look.org/content/show.php/Nautilus+Extension+Kill+MetaMac?content=140033)

Anybody know why this is occurring? I know its an issue with 'dpkg-buildpackage'. Oddly, all commands using it which create source packages, such as, 'debuild -S', 'debuild -i -us -uc -S', 'dpkg-buildpackage -rfakeroot -S', 'dpkg-buildpackage -rfakeroot -us -uc -S', etc... fail to include the '*.so' files. Funny though, as all of the ones that make the debian package right on your computer do include the '*.so' files inside the debs, such as, 'debuild -b', 'debuild -i -us -uc -b', 'dpkg-buildpackage -rfakeroot -b', 'dpkg-buildpackage -rfakeroot -us -uc -b'.

---

### Post by inameiname on 2011-06-18
I found sort of a workaround to this issue. What I did was compress any "*.so" files found inside the original deb, and using a postinst script, had them extracted after the deb installs. Doing this, Launchpad creates the deb on its server just fine, and everything installs and works correctly. Just remember not to delete the original tar file, and everything is good as gold.

Thus, its good enough. I'll mark this as solved.

---

