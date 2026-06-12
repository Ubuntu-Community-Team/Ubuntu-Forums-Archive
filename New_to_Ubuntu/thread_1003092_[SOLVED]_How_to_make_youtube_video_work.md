---
title: "[SOLVED] How to make youtube video work"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-05
Can't remember how to make youtube video work, (No video works for that matter). I have installed the usual, (java, flash, etc) still no good.

---

### Post by gedit on 2008-12-05
It should work from the get-go. You can try installing the mplayer plugins through synaptic as opposed top the default Totem plugins. Go to the Synaptic Package Manager under System settings and search for mplayer. Mark it for install and apply the changes. 

Now open the Terminal under Accessories and type:

sudo wget [http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

Enter your Password when promted. No text will appear on the screen.

Now type this:

sudo dpkg -i mplayerplug-in_3.11-1_i386.deb

These plugins work with firefox to play any internet media. Once the above process is done, restart firefox and you're good to go.

Let me know if you have any problems.

---

### Post by Idaho Dan on 2008-12-05
Go to the Multimedia and Video forum and check out the sticky, it worked for me.

---

### Post by inxygnuu on 2008-12-05
when you go to youtube on FF, it will ask you if you want to get the plugins, select, and if FF can't retrieve it, it will give you a link it should work then.

FF=firefox:p

best regards,
3v4n;)

---

