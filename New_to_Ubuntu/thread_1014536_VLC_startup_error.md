---
title: "VLC startup error"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-17
Hi,

It seems that when i try to run VLC it tells me first (without even opening) to select a skin. when i do so from the list of skins that i downloaded, it doesnt open... i have uninstalled and reinstalled many times and the result is the same. i have noticed that in the /usr/share/vlc is still there even after uninstall leading me to believe that after the unstinsall has been performed, some settings remain (as in windows). Is there any way i can be sure to get rid of every ounce of vlc before installing again? Its my favorite player so itd be a shame to have to ditch it because of this. 

thanks in advance everyone!

---

### Post by Titan8990 on 2008-12-17
Try selecting purge from the synaptic package manager or:

sudo apt-get remove --purge vlc

---

### Post by 11010110 on 2008-12-17
no still the same thing. 

any other ideas?

---

### Post by 11010110 on 2008-12-17
good news! i must have missed a few things in synaptic so i went back and marked for COMPLETE removal everything pertaining to VLC and it worked... now it is reinstalled and now it opens up to a skin that gives no access to the menu on startup (dumb right?) it gives access to chose a skin but the skin chosen is not applied even upon restarting. any ideas on how to change the default skin setting without having access to the menu?

Thanks!

---

### Post by 11010110 on 2008-12-18
all fixed! thanks so much for your help!

---

